---
title: コンパイラ エラー C3374
ms.date: 11/04/2016
f1_keywords:
- C3374
helpviewer_keywords:
- C3374
ms.assetid: 41431299-bd20-47d4-a0c8-1334dd79018b
ms.openlocfilehash: 760eb1bafdaab9995d3238c8bc4e3114acd743eb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755578"
---
# <a name="compiler-error-c3374"></a>コンパイラ エラー C3374

delegate インスタンスを作成する場合以外に、'関数' のアドレスを指定できません

delegate インスタンスを作成する以外のコンテキストで、関数のアドレスが取得されました。

次の例では警告 C3374 が生成されます。

```cpp
// C3374.cpp
// compile with: /clr
public delegate void MyDel(int i);

ref class A {
public:
   void func1(int i) {
      System::Console::WriteLine("in func1 {0}", i);
   }
};

int main() {
   &A::func1;   // C3374

   // OK
   A ^ a = gcnew A;
   MyDel ^ StaticDelInst = gcnew MyDel(a, &A::func1);
}
```

## <a name="see-also"></a>参照

[方法: デリゲートを定義および使用する (C++/CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)
