---
title: C 関係演算子と等値演算子
ms.date: 10/18/2018
helpviewer_keywords:
- relational operators, syntax
- equality operator
- operators [C], equality
- equality operator, syntax
- operators [C], relational
ms.assetid: c89a3815-a65e-4e0d-8333-0e8dc7fdb30b
ms.openlocfilehash: 25e9bb65492e0c4b100ecd7a800491d238b1dd38
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400531"
---
# <a name="c-relational-and-equality-operators"></a>C 関係演算子と等値演算子

二項関係演算子および二項等値演算子は、最初のオペランドと 2 番目のオペランドを比較して、指定された関係の有効性をテストします。 テストした関係が true の場合、その式の結果は 1 になり、false の場合は 0 になります。 結果の型は `int` です。

**構文**

*relational-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **&lt;** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **>** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **&lt;=** *shift-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression* **>=** *shift-expression*

*equality-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression* **==** *relational-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*equality-expression* **!=** *relational-expression*

関係演算子と等値演算子は次の関係をテストします。

|演算子|テスト対象の関係|
|--------------|-------------------------|
|**&lt;**|1 番目のオペランドが 2 番目のオペランドより小さい|
|**>**|1 番目のオペランドが 2 番目のオペランドより大きい|
|**&lt;=**|1 番目のオペランドが 2 番目のオペランド以下|
|**>=**|1 番目のオペランドが 2 番目のオペランド以上|
|**==**|1 番目のオペランドが 2 番目のオペランドに等しい|
|**!=**|1 番目のオペランドが 2 番目のオペランドに等しくない|

上記の一覧で、最初の 4 つの演算子は等値演算子 (`==` と `!=`) より優先順位が高くなります。 [C 演算子の優先順位と結合規則](../c-language/precedence-and-order-of-evaluation.md)に関する表で優先順位を確認してください。

オペランドとしては、整数型、浮動小数点型、またはポインター型を指定できます。 オペランドの型はそれぞれ異なっていてもかまいません。 関係演算子は、整数型および浮動小数点型のオペランドに対して通常の算術変換を実行します。 また、関係演算子および等値演算子とオペランド型の次の組み合わせを使用できます。

- 関係演算子または等値演算子では、両方のオペランドが同じ型へのポインターである場合があります。 等値 (`==`) 演算子と非等値 (`!=`) 演算子の場合、比較の結果は、2 つのポインターが同じメモリ位置を指すかどうかを示します。 他の関係演算子 ( **\<** 、 **>** 、 **\<** =、 **>** =) の場合、比較の結果は、指し示されているオブジェクトの 2 つのメモリ アドレスの相対位置を表します。 関係演算子はオフセットのみを比較します。

   ポインターの比較は、同じオブジェクトの一部に対してのみ定義されます。 ポインターが配列のメンバーを参照している場合、比較は対応する添字の比較と同じになります。 最初の配列要素のアドレスは、最後の要素のアドレスよりも小さくなります。 構造体の場合、後で宣言された構造体メンバーへのポインターは、構造体で既に宣言されているメンバーへのポインター "より大きく" なります。 同じ共用体のメンバーへのポインターは等しくなります。

- ポインター値は、等値 (`==`) または非等値 (`!=`) の定数値 0 と比較できます。 値 0 のポインターは "null" ポインターと呼ばれます。つまり、有効なメモリ位置を指していません。

- 等値演算子は関係演算子と同じ規則に従いますが、追加のオプションがあります。ポインターは、値 0 の整数定数式、または `void` へのポインターと比較できます。 2 つのポインターが両方とも null ポインターの場合、それらは等しいと見なされます。 等値演算子はセグメントとオフセットの両方を比較します。

## <a name="examples"></a>使用例

次に関係演算子と等値演算子の例を示します。

```C
int x = 0, y = 0;
if ( x < y )
```

`x` と `y` が等しいので、この例の式は値 0 になります。

```C
char array[10];
char *p;

for ( p = array; p < &array[10]; p++ )
    *p = '\0';
```

この例のフラグメントは null 文字定数に `array` の各要素を設定します。

```C
enum color { red, white, green } col;
   .
   .
   .
   if ( col == red )
   .
   .
   .
```

これらのステートメントは、`col` タグを使用して `color` という列挙型変数を宣言します。 常に、この変数には整数値 0、1、または 2 が格納されます。これらの値は、`color` 列挙セットのいずれかの要素 (赤、白、緑) を表します。 **if** ステートメントが実行されるときに `col` に 0 が含まれていると、**if** に依存するすべてのステートメントが実行されます。

## <a name="see-also"></a>関連項目

[関係演算子: \<、>、\<=、および >=](../cpp/relational-operators-equal-and-equal.md)<br/>
[等値演算子: == および !=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)
