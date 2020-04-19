---
title: コンパイラ エラー C3379
ms.date: 11/04/2016
f1_keywords:
- C3379
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
ms.openlocfilehash: 9d99214f3ad7e7db1edc215d94c98e9cf9ec4ca2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742900"
---
# <a name="compiler-error-c3379"></a>コンパイラ エラー C3379

' class ': 入れ子になったクラスは、宣言の一部としてアセンブリアクセス指定子を持つことはできません

クラスや構造体などのマネージ型に適用される場合、 [public](../../cpp/public-cpp.md)キーワードと[private](../../cpp/private-cpp.md)キーワードは、クラスがアセンブリメタデータを通じて公開されるかどうかを示します。 `public` または `private` を入れ子になったクラスに適用することはできません。入れ子になったクラスには、外側のクラスのアセンブリアクセスが継承されます。

[/Clr](../../build/reference/clr-common-language-runtime-compilation.md)と共に使用する場合、`ref` キーワードと `value` キーワードは、クラスがマネージであることを示します (「[クラスと構造体](../../extensions/classes-and-structs-cpp-component-extensions.md)」を参照してください)。

次の例では、C3379 が生成されます。

```cpp
// C3379a.cpp
// compile with: /clr
using namespace System;

public ref class A {
public:
   static int i = 9;

   public ref class BA {   // C3379
   // try the following line instead
   // ref class BA {
   public:
      static int ii = 8;
   };
};

int main() {

   A^ myA = gcnew A;
   Console::WriteLine(myA->i);

   A::BA^ myBA = gcnew A::BA;
   Console::WriteLine(myBA->ii);
}
```
