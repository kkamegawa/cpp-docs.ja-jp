---
title: 一次式
ms.date: 11/04/2016
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
ms.openlocfilehash: e7dcb8290c0130fa9376e48f065e82163a1ca5b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312311"
---
# <a name="primary-expressions"></a>一次式

基本式は、より複雑な式のビルド ブロックです。 つまり、リテラル、名前、スコープ解決演算子 (`::`) で修飾された名前です。  基本式は次のいずれかの形式になります。

```
literal
this
name
::name ( expression )
```

A*リテラル*プライマリ定数式です。 その型は、リテラルの指定の形式によって決まります。 参照してください[リテラル](../cpp/numeric-boolean-and-pointer-literals-cpp.md)リテラルを指定する詳細についてはします。

**this**キーワードはクラス オブジェクトへのポインター。 非静的メンバー関数内で使用でき、その関数が呼び出されたクラスのインスタンスを参照します。 **this**クラス メンバー関数の本体の外にキーワードを使用できません。

種類、**this**ポインターが`type` **\*const** (場所`type`クラスの名前を指定) 特に変更関数内で、**this**ポインター。 次の例では、関数の宣言と型のメンバーを示しています**this**:

```cpp
// expre_Primary_Expressions.cpp
// compile with: /LD
class Example
{
public:
    void Func();          //  * const this
    void Func() const;    //  const * const this
    void Func() volatile; //  volatile * const this
};
```

参照してください[this ポインター](this-pointer.md)の種類の変更の詳細については、**this**ポインター。

名前の前のスコープ解決演算子 (`::`) は基本式です。  そのような名前は、メンバー名ではなく、グローバル スコープでの名前であることが必要です。  この式の型は名前の宣言によって決まります。 宣言名が左辺値である場合は、左辺値 (代入演算子式の左辺になる式) です。 スコープ解決演算子を使用すると、グローバル名が現在のスコープでは隠されていても、その名前を参照できます。 参照してください[スコープ](../cpp/scope-visual-cpp.md)スコープ解決演算子を使用する方法の例についてはします。

かっこで囲まれた式も基本式であり、その型と値はかっこで囲まれていない式のものと一致します。 この式は、かっこで囲まれていない式が左辺値であれば、左辺値です。

次に示しているのは、基本式の例です。

```cpp
100 // literal
'c' // literal
this // in a member function, a pointer to the class instance
::func // a global function
::operator + // a global operator function
::A::B // a global qualified name
( i + 1 ) // a parenthesized expression
```

次の例では、内容はすべてと*名*、さまざまな形式で、つまり基本式。

```cpp
MyClass // a identifier
MyClass::f // a qualified name
operator = // an operator function name
operator char* // a conversion operator function name
~MyClass // a destructor name
A::B   // a qualified name
A<int> // a template id
```

## <a name="see-also"></a>関連項目

[式の型](../cpp/types-of-expressions.md)