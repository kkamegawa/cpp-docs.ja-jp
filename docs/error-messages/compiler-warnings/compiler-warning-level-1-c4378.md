---
title: コンパイラの警告 (レベル 1) C4378
ms.date: 11/04/2016
f1_keywords:
- C4378
helpviewer_keywords:
- C4378
ms.assetid: d08e11ef-891a-4752-9a5e-360e7394acf7
ms.openlocfilehash: cc5e5365ffb53125085ce7b374f1362e93f4bb03
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966497"
---
# <a name="compiler-warning-level-1-c4378"></a>コンパイラの警告 (レベル 1) C4378

初期化子を実行するには、関数ポインターを取得する必要があります。System:: ModuleHandle:: ResolveMethodHandle を検討します。

**/Clr**の下では、初期化子シンボルに関数のポインターではなく関数トークンが含まれています。  <xref:System.ModuleHandle.ResolveMethodHandle%2A>を使用して、トークンをポインターに変換する必要があります。

## <a name="example"></a>例

次の例では、C4378 が生成されます。

```cpp
// C4378.cpp
// compile with: /W1 /clr /c
typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors to call
PF pfx[200];   // ptrs to those dtors, watch for overflow

int myexit (PF pf) {
   pfx[cxpf++] = pf;
   return 0;
}

struct A {
   A() {}
   ~A() {}
};

A aaaa;

#pragma data_seg(".mine$a")
PF InitSegStart = (PF)1;
#pragma data_seg(".mine$z")
PF InitSegEnd = (PF)1;
#pragma data_seg()

void InitializeObjects () {
   PF *x = &InitSegStart;
   for (++x ; x < &InitSegEnd ; ++x)
      if (*x)
         (*x)();
}

#pragma init_seg(".mine$m",myexit)   // C4378
A bbbb;   // crash

int main () {
   InitializeObjects();
}
```

## <a name="example"></a>例

次の例は、C4378 を解決する方法を示しています。

```cpp
// C4378_b.cpp
// compile with: /clr
#pragma warning(disable:4378)
using namespace System;
typedef void (__cdecl *PF)(void);
typedef void (__clrcall * CLRPF)(void);

int cxpf = 0;  // number of destructors we need to call
PF pfx[200];   // ptrs to those dtors. Watch out for overflow!

ref class TypeClassHolder {
public:
   static TypeClassHolder ^typeClass = gcnew TypeClassHolder();
};

CLRPF FuncTokenToFuncPtr(PF tknFunc) {
   ModuleHandle type =
      Type::GetTypeFromHandle(Type::GetTypeHandle(TypeClassHolder::typeClass))->Module->ModuleHandle;
   return (CLRPF)type.ResolveMethodHandle((int)(size_t)(tknFunc)).GetFunctionPointer().ToPointer();
}

int myexit (PF pf) {
   pfx[cxpf++] = pf;
   return 0;
}

struct A {
   A() {}
   ~A() {}
};

A aaaa;

#pragma data_seg(".mine$a")
PF InitSegStart = (PF)1;
#pragma data_seg(".mine$z")
PF InitSegEnd = (PF)1;
#pragma data_seg()

void InitializeObjects () {
   PF *x = &InitSegStart;
   for (++x ; x < &InitSegEnd ; ++x)
      if(*x) {
         CLRPF realppfunc;
         realppfunc = FuncTokenToFuncPtr(*x);
         (realppfunc)();
      }
}

#pragma init_seg(".mine$m",myexit)
A bbbb; // constructor call succeeds

int main () {
   InitializeObjects();
}
```