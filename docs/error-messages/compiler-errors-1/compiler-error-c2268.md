---
title: コンパイラ エラー C2268
ms.date: 11/04/2016
f1_keywords:
- C2268
helpviewer_keywords:
- C2268
ms.assetid: 0ed055c9-3c6f-4df2-a5b6-85cf0e01a249
ms.openlocfilehash: 11e0c2c81e9bcd2249321e83a506aeaa832c2ee8
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301796"
---
# <a name="compiler-error-c2268"></a>コンパイラ エラー C2268

'function' は、コンパイラで定義済みのライブラリ ヘルパーです。 ライブラリ ヘルパーは /GL でサポートされていません。オブジェクト ファイル 'file' を /GL なしでコンパイルしてください。

ソース コードで定義されている関数に、内部コンパイラ関数と同じ名前があります。 その関数が含まれているモジュールを [/GL](../../build/reference/gl-whole-program-optimization.md)なしでコンパイルしてください。

次の例では C2268 が生成されます。

```c
// C2268.c
// compile with: /c
// processor: x86
extern int SHFusionLoadLibrary(int lpLibFileName);

int __cdecl _except_handler3(void) {
   return SHFusionLoadLibrary(0);
}

extern int main(void);

void* mainCRTStartup(void* p) {
   p = main;
   return p;
}
```

この場合、次のようになります。

```c
// C2268b.c
// compile with: C2268.c /EHsc /GL /Ob0 /O2 /Fa /GS- /link /nodefaultlib
// processor: x86
extern int SHFusionLoadLibrary(int lpLibFileName);

extern int __cdecl _except_handler3(void);
extern void mainCRTStartup(void*);
int g = 2;

#define ENTERCONTEXT(fail) \
   int ulCookie = 0;\
   if (!SHActivateContext(&ulCookie)) \
      return fail;\
   __try {

#define LEAVECONTEXT \
    } __finally {SHDeactivateContext(ulCookie);}

int SHActivateContext(int* a) {
    return *a == g || !*a ||_except_handler3();
}

void SHDeactivateContext(int a) {
    g = a;
}

int SHFusionLoadLibrary(int lpLibFileName) {   // C2268
    ENTERCONTEXT(0)
    g = lpLibFileName;
    LEAVECONTEXT

    return lpLibFileName;
}

int main(void) {
    g = SHFusionLoadLibrary(10);
    return 0;
}
```
