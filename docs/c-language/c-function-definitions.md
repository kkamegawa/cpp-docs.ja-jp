---
title: C 関数定義
ms.date: 11/04/2016
helpviewer_keywords:
- function declarators
- function definitions
- declaring functions, about function declarations
- declaring functions, declarators
- functions [C], parameters
- declarators, functions
- function parameters, function definitions
- function body
- declaring functions, variables
ms.assetid: ebab23c8-6eb8-46f3-b21d-570cd8457a80
ms.openlocfilehash: 5cf56375df417ac68b3e03d00f2bd7770ee571e8
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857139"
---
# <a name="c-function-definitions"></a>C 関数定義

関数定義は、関数の名前、受け取ることを想定するパラメーターの種類と数、および戻り値の型を指定します。 関数定義には、ローカル変数の宣言を持つ関数本体と、関数の処理を決定するステートメントも含まれます。

## <a name="syntax"></a>構文

*translation-unit*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*external-declaration* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*external-declaration*: /\* 外部 (ファイル) スコープでのみ使用できる \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*function-definition*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\**属性-seq*は Microsoft 固有の \*/

プロトタイプ パラメーターは次のとおりです。

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *declaration*

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*: /\* 関数宣言子 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)**  /\* 新しい形式の宣言子 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *identifier-list*<sub>opt</sub> **)**  /\* 古い形式の宣言子 \*/

定義のパラメーター リストは、この構文を使用します。

*parameter-type-list*: /\* パラメーター リスト \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **, ...**

*parameter-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **,**  *parameter-declaration*

*parameter-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *abstract-declarator*<sub>opt</sub>

旧式の関数定義のパラメーター リストは、この構文を使用します。

*identifier-list*: /\* 古い形式の関数定義と宣言で使用します \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier-list* **,**  *identifier*

関数本体の構文は次のとおりです。

*compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

関数宣言を変更できるストレージ クラスの指定子は **extern** と **static** のみです。 **extern** 指定子は、関数が他のファイルから参照できること、つまり、関数名がリンカーにエクスポートされることを指定します。 **static** 指定子は、関数が他のファイルから参照できないこと、つまり、名前がリンカーによってエクスポートされないことを示します。 関数定義にストレージ クラスが現れない場合、**extern** と見なされます。 いずれの場合も、関数は定義位置からファイルの末尾まで常に参照可能です。

省略可能な *declaration-specifiers* と必須の *declarator* によって、関数の戻り値の型と名前が指定されます。 *declarator* は、関数の名前を指定する識別子と、関数名の後に続くかっこの組み合わせです。 省略可能な *attribute-seq* 非終端要素は、「[関数の属性](../c-language/function-attributes.md)」で定義する Microsoft 固有の機能です。

(*declarator* 構文内の) *direct-declarator* は、定義されている関数の名前とそのパラメーターの識別子を指定します。 *direct-declarator* に *parameter-type-list* が含まれる場合、そのリストですべてのパラメーターの型を指定します。 このような宣言は、それ以降の関数の呼び出しに対する関数プロトタイプとしても機能します。

関数定義の *declaration-list* の *declaration* は、**register** 以外の *storage-class-specifier* を含めることはできません。 *declaration-specifiers* 構文の *type-specifier* は、**register** ストレージ クラスが **int** 型の値に対して指定されている場合にのみ省略できます。

*compound-statement* は、ローカル変数宣言、外部で宣言された項目への参照、およびステートメントを含む関数本体です。

「[関数の属性](../c-language/function-attributes.md)」、「[ストレージ クラス](../c-language/storage-class.md)」、「[戻り値の型](../c-language/return-type.md)」、「[パラメーター](../c-language/parameters.md)」、および「[関数本体](../c-language/function-body.md)」の各セクションでは、関数定義のコンポーネントについて詳しく説明します。

## <a name="see-also"></a>参照

[関数](../c-language/functions-c.md)
