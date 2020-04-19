---
title: コンパイラ エラー C3894
ms.date: 11/04/2016
f1_keywords:
- C3894
helpviewer_keywords:
- C3894
ms.assetid: 6d5ac903-1dea-431d-8e3a-cebca4342983
ms.openlocfilehash: c08a7eca473a4ae043879b49266efec6b8afe7b1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749439"
---
# <a name="compiler-error-c3894"></a>コンパイラ エラー C3894

' var ': initonly 静的データメンバーの左辺値の使用は、クラス ' class ' のクラスコンストラクターでのみ許可されています

静的な[initonly](../../dotnet/initonly-cpp-cli.md)データメンバーは、宣言の時点、または静的コンストラクターの左辺値としてのみ使用できます。

インスタンス (静的でない) initonly データメンバーは、宣言の時点、またはインスタンス (非静的) コンストラクターで左辺値としてのみ使用できます。

次の例では、C3894 が生成されます。

```cpp
// C3894.cpp
// compile with: /clr
ref struct Y1 {
   initonly static int data_var = 0;

public:
   // class constructor
   static Y1() {
      data_var = 99;   // OK
      System::Console::WriteLine("in static constructor");
   }

   // not the class constructor
   Y1(int i) {
      data_var = i;   // C3894
   }

   static void Test() {}

};

int main() {
   Y1::data_var = 88;   // C3894
   int i = Y1::data_var;
   Y1 ^ MyY1 = gcnew Y1(99);
   Y1::Test();
}
```
