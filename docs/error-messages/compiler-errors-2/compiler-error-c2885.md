---
title: コンパイラ エラー C2885
ms.date: 11/04/2016
f1_keywords:
- C2885
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
ms.openlocfilehash: e60f3fff2ef61f4d6374072c05a2ad3e64a57031
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760929"
---
# <a name="compiler-error-c2885"></a>コンパイラ エラー C2885

' class:: identifier ': 非クラススコープでは有効な using 宣言ではありません

[Using](../../cpp/using-declaration.md)宣言を正しく使用しませんでした。

## <a name="example"></a>使用例

このエラーは、Visual Studio 2005 で実行されたコンパイラ準拠作業の結果として生成される場合があります。入れ子になった型への `using` 宣言を持つことは無効になります。入れ子になった型に対しては、各参照を明示的に修飾するか、名前空間に型を配置するか、typedef を作成する必要があります。

次の例では、C2885 が生成されます。

```cpp
// C2885.cpp
namespace MyNamespace {
   class X1 {};
}

struct MyStruct {
   struct X1 {
      int i;
   };
};

int main () {
   using MyStruct::X1;   // C2885

   // OK
   using MyNamespace::X1;
   X1 myX1;

   MyStruct::X1 X12;

   typedef MyStruct::X1 abc;
   abc X13;
   X13.i = 9;
}
```

## <a name="example"></a>使用例

`using` キーワードをクラスメンバーと共に使用する場合C++ 、では、そのメンバーを別のクラス (派生クラス) 内で定義する必要があります。

次の例では、C2885 が生成されます。

```cpp
// C2885_b.cpp
// compile with: /c
class A {
public:
   int i;
};

void z() {
   using A::i;   // C2885 not in a class
}

class B : public A {
public:
   using A::i;
};
```
