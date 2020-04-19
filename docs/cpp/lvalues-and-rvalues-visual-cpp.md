---
title: 値のカテゴリ。左辺値と右辺値 (C++)
ms.date: 05/07/2019
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
ms.openlocfilehash: 4e3cfa87a8f1ae9b17f7c08afd8faeabea7102b3
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222013"
---
# <a name="lvalues-and-rvalues-c"></a>左辺値と右辺値 (C++)

すべての C++ 式の型を持つし、に属する、*値カテゴリ*します。 値のカテゴリは、コンパイラが作成、コピー、および式の評価中に一時オブジェクトを移動するときに従う必要があるルールの基礎です。

標準の c++ 17 では、次のように式の値のカテゴリを定義します。

- A *glvalue*式を指定するオブジェクト、ビット フィールド、または関数の id を決定します。
- A *prvalue*をオブジェクトまたはビット フィールドを初期化しますまたは、演算子のオペランドの値を計算コンテキストで指定された、その次のように表示されます。 式を指定します。
- *Xvalue*オブジェクトまたはビット フィールド (通常はその有効期間の末尾付近である) ために再利用できるリソースを示す glvalue です。 例:右辺値参照 (8.3.2) を含む式は、特定の種類は、戻り値の型が右辺値参照関数の呼び出しまたは参照型 rvalue へのキャストなど、xvalues を生成します。
- *左辺値*xvalue にない glvalue が。
- *Rvalue* prvalue または xvalue にします。

次の図は、カテゴリ間の関係を示しています。

![C++ 式の値のカテゴリ](media/value_categories.png "C++ 式の値のカテゴリ")

左辺値では、プログラムにアクセスできるアドレスがあります。 左辺値式の例を含む、変数名を含める**const**関数を左辺値参照をビット フィールド、共用体、およびクラス メンバーを返す呼び出しの変数、配列の要素。

Prvalue 式には、プログラムからアクセス可能なアドレスがありません。 Prvalue 式の例には、リテラル、非参照型を返す関数呼び出しと、コンパイラでのみアクセスできますが、式の評価中に作成される一時オブジェクトが含まれます。

Xvalue 式がアドレスをプログラムでアクセス不可能になってが式へのアクセスを提供する、右辺値参照を初期化するために使用できます。 例には、返された関数呼び出し、右辺値参照と配列の添字、メンバー、およびポインター メンバー式に、配列またはオブジェクトが右辺値参照が含まれます。

## <a name="example"></a>例

次の例は、左辺値と右辺値の正しい使用方法と間違った使用方法のいくつかを示しています。

```cpp
// lvalues_and_rvalues2.cpp
int main()
{
    int i, j, *p;

    // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.
    i = 7;

    // Incorrect usage: The left operand must be an lvalue (C2106).`j * 4` is a prvalue.
    7 = i; // C2106
    j * 4 = 7; // C2106

    // Correct usage: the dereferenced pointer is an lvalue.
    *p = i;

    // Correct usage: the conditional operator returns an lvalue.
    ((i < 3) ? i : j) = 7;
    
    // Incorrect usage: the constant ci is a non-modifiable lvalue (C3892).
    const int ci = 7;
    ci = 9; // C3892
}
```

> [!NOTE]
> このトピックの例では、演算子がオーバーロードしていないときの、正しい方法使用と正しくない使用方法を説明します。 演算子をオーバーロードすることにより、`j * 4` のような式を左辺値にできます。

条件*左辺値*と*rvalue*オブジェクト参照を参照する場合は、よく使用します。 参照の詳細については、次を参照してください。[左辺値参照宣言子: &](../cpp/lvalue-reference-declarator-amp.md)と[右辺値参照宣言子: & &](../cpp/rvalue-reference-declarator-amp-amp.md)します。

## <a name="see-also"></a>関連項目

[基本的な概念](../cpp/basic-concepts-cpp.md)<br/>
[左辺値参照宣言子: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[右辺値参照宣言子: &&](../cpp/rvalue-reference-declarator-amp-amp.md)
