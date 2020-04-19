---
title: コンパイラ エラー C3380
ms.date: 11/04/2016
f1_keywords:
- C3380
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
ms.openlocfilehash: 2e26b4b1af8ee3c078f3eae3c0cb6a2677c642c2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761882"
---
# <a name="compiler-error-c3380"></a>コンパイラ エラー C3380

'class': 無効なアセンブリ アクセス指定子です。'public' と 'private' のみ使用できます

マネージド クラスや構造体に適用される場合、 [public](../../cpp/public-cpp.md) キーワードと [private](../../cpp/private-cpp.md) キーワードはクラスがアセンブリ メタデータを通じて公開されるかどうかを示します。 `public` /clr `private` を指定してコンパイルされるプログラムのクラスには、 [または](../../build/reference/clr-common-language-runtime-compilation.md)以外は適用できません。

[/Clr](../../build/reference/clr-common-language-runtime-compilation.md)と共に使用する場合、`ref` キーワードと `value` キーワードは、クラスが管理されることを示します (「[クラスと構造体](../../extensions/classes-and-structs-cpp-component-extensions.md)」を参照してください)。

次の例では C3380 が生成されます。

```cpp
// C3380_2.cpp
// compile with: /clr
protected ref class A {   // C3380
// try the following line instead
// ref class A {
public:
   static int i = 9;
};

int main() {
   A^ myA = gcnew A;
   System::Console::WriteLine(myA->i);
}
```
