---
title: 宣言の概要
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
ms.openlocfilehash: 0ffda6522e632533b0aaa4ba146e8fad082ed435
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857061"
---
# <a name="overview-of-declarations"></a>宣言の概要

"宣言" は、一連の識別子の解釈と属性を指定します。 識別子に指定されたオブジェクトまたは関数のためにストレージを予約する宣言は "定義" と呼ばれます。 C における変数、関数、および型の宣言では、次の構文に従います。

## <a name="syntax"></a>構文

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *attribute-seq*<sub>opt</sub> *init-declarator-list*<sub>opt</sub> **;**

/\**属性-seq*<sub>opt</sub>は Microsoft 固有 */

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list* **,** *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *initializer*

> [!NOTE]
> この *declaration* 構文は、以降のセクションで繰り返されません。 以降のセクションの構文は通常、非終端要素である *declarator* から始まります。

*init-declarator-list* 内の宣言では、名前が付けられた識別子が含まれます。*init* は、initializer (初期化子) の省略形です。 *init-declarator-list* は、コンマで区切られた宣言子のシーケンスで、それぞれの宣言子が追加の型情報または初期化子 (またはその両方) を持ちます。 *declarator* には、宣言されている識別子 (存在する場合) が含まれます。 非終端要素である *declaration-specifiers* は、リンケージ、ストレージ存続期間、および少なくとも宣言子が示すエンティティの型の一部を指定する、一連の型指定子とストレージ クラス指定子で構成されます。 したがって、宣言は、ストレージ クラス指定子、型指定子、型修飾子、宣言子、および初期化子の組み合わせで構成されます。

宣言には *attribute-seq* に示されている省略可能な属性を 1 つ以上含めることができます。*seq* は、sequence (シーケンス) の省略形です。 これらの Microsoft 固有の属性は、さまざまな機能を実行します。詳細については、このブック全体で説明します。

変数宣言の一般的な形式では、*type-specifier* は変数のデータ型を示します。 型が **const** または `volatile` で変更される場合、*type-specifier* は複合型にすることができます。 `declarator` は、配列型またはポインター型を宣言するために変更される可能性がある変数の名前を示します。 たとえば、オブジェクトに適用された

```C
int const *fp;
```

このコードは、`fp` という名前の変数を、変更不可能な (**const**) `int` 値へのポインターとして宣言します。 コンマで区切った複数の宣言子を使用して、複数の変数を宣言で定義できます。

宣言は、少なくとも 1 つの宣言子を持つか、その型指定子が構造体タグ、共用体タグ、または列挙のメンバーを宣言する必要があります。 宣言子は、識別子に関するその他の情報を提供します。 宣言子は、配列、ポインター、または関数型を宣言するための角かっこ ( **[ ]** )、アスタリスク (<strong>\*</strong>)、またはかっこ ( **( )** ) で変更できる識別子です。 単純な変数 (文字、整数、浮動小数点項目など) または単純な変数の構造体/共用体を宣言する場合、`declarator` は単なる識別子です。 宣言子の詳細については、「[宣言子と変数宣言](../c-language/declarators-and-variable-declarations.md)」を参照してください。

すべての定義は暗黙の宣言ですが、すべての宣言が定義というわけではありません。 たとえば、`extern` ストレージ クラス指定子で始まる変数宣言は、"定義" 宣言ではなく "参照" 宣言になります。 外部変数を定義する前に参照する場合、または外部変数を使用されている場所とは異なるソース ファイルで定義する場合は、`extern` 宣言が必要です。 ストレージは "参照" 宣言によって割り当てられず、変数は宣言で初期化できません。

ストレージ クラスまたは型 (または両方) は変数宣言に必要です。 `__declspec` を除いて、1 個のストレージ クラス指定子のみを宣言で使用でき、すべてのストレージ クラス指定子をすべてのコンテキストで使用できるわけではありません。 `__declspec` ストレージ クラスは、他のストレージ クラス指定子と共に指定でき、複数回使用できます。 宣言のストレージ クラス指定子は、宣言された項目の格納と初期化の方法や、項目を参照できるプログラムの部分に影響を与えます。

C で定義されている *storage-class-specifier* 終端要素には、**auto**、`extern`、**register**、**static**、`typedef` などがあります。 また、Microsoft C には *storage-class-specifier* 終端要素である `__declspec` が含まれます。 `typedef` と `__declspec` 以外のすべての *storage-class-specifier* 終端要素については、「[ストレージ クラス](../c-language/c-storage-classes.md)」で説明しています。 `typedef` の詳細については、「[Typedef 宣言](../c-language/typedef-declarations.md)」を参照してください。 `__declspec` については、「[拡張ストレージ クラス属性](../c-language/c-extended-storage-class-attributes.md)」を参照してください。

ソース プログラム内の宣言の場所、および変数の他の宣言が存在するかどうかは、変数の有効期間を決定するにあたって重要な要因となります。 複数の再宣言を設定できますが、定義は 1 つだけです。 ただし、1 つの定義が、複数の翻訳単位内に含まれていることがあります。 内部リンケージを持つオブジェクトの場合、この規則は各翻訳単位に個別に適用されます。内部でリンクされたオブジェクトは翻訳単位に固有です。 外部リンケージを持つオブジェクトに対して、この規則はプログラム全体に適用されます。 可視性の詳細については、「[有効期間、スコープ、可視性、およびリンケージ](../c-language/lifetime-scope-visibility-and-linkage.md)」を参照してください。

型指定子は、識別子のデータ型に関する情報を提供します。 既定の型指定子は `int` です。 詳細については、「[型指定子](../c-language/c-type-specifiers.md)」を参照してください。 型指定子は、型のタグ、構造体、共用コンポーネント名、および列挙定数も定義できます。 詳細については、「[列挙の宣言](../c-language/c-enumeration-declarations.md)」、「[構造体の宣言](../c-language/structure-declarations.md)」、および「[共用体の宣言](../c-language/union-declarations.md)」を参照してください。

*type-qualifier* 終端要素は、**const** と `volatile` の 2 つがあります。 これらの修飾子は、関連する型の追加のプロパティを指定します (その型のオブジェクトに左辺値を通じてアクセスする場合のみ)。 **const** および `volatile` の詳細については、「[型修飾子](../c-language/type-qualifiers.md)」を参照してください。 左辺値の定義については、「[左辺値と右辺値の式](../c-language/l-value-and-r-value-expressions.md)」を参照してください。

## <a name="see-also"></a>参照

[C 言語の構文概要](../c-language/c-language-syntax-summary.md)<br/>
[宣言と型](../c-language/declarations-and-types.md)<br/>
[宣言の概要](../c-language/summary-of-declarations.md)
