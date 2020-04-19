---
title: C 列挙体の宣言
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, enumerations
- define directive (#define), alternative to
- enumerators, declaring
- '#define directive, alternative to'
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
ms.openlocfilehash: bc238dd0088558233d84f8bbd15d06743e133449
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149233"
---
# <a name="c-enumeration-declarations"></a>C 列挙体の宣言

列挙体は、名前が付いた一連の整数定数で構成されます。 列挙型の宣言では、列挙タグ (省略可能) の名前を指定し、名前が付いた一連の整数識別子を定義します (これらの識別子は、"列挙セット"、"列挙定数"、"列挙子"、または "メンバー" と呼ばれます)。 列挙型の変数には、その型で定義された列挙セットの 1 つの値が格納されます。

`enum` 型の変数はインデックス式で使用でき、すべての算術演算子および関係演算子のオペランドとしても使用できます。 列挙体は `#define` プリプロセッサ ディレクティブの代わりとして使用できます。これには、値が自動的に生成され、標準のスコープ規則に準拠できるという利点があります。

ANSI C では、列挙定数の値を定義する式は常に `int` 型となります。したがって、列挙変数に関連付けられる変数は、1 つの `int` 値で必要となるストレージです。 列挙定数または列挙型の値は、C 言語の整数式が許可されているすべての場所で使用できます。

## <a name="syntax"></a>構文

*enum-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**enum** *identifier*<sub>opt</sub> **{** *enumerator-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**enum** *identifier*

*identifier* (省略可能) は、*enumerator-list* で定義される列挙型を指定します。 この識別子は、列挙子リストで指定された列挙体の"タグ" とも呼ばれます。 次に例を示します。

```
enum identifier
{
    enumerator-list
}
```

上記の形式の型指定子は、*enumerator-list* 非終端要素で指定された列挙型のタグとして *identifier* を宣言しています。 *enumerator-list* は "列挙定数" を定義します。 *enumerator-list* については、この後で詳しく説明します。

タグの宣言を参照できる場合、それ以降の宣言でそのタグを使用し、*enumerator-list* を省略しているときは、その前に宣言された列挙型を指定します。 タグは定義された列挙型を参照する必要があり、その列挙型は現在のスコープに含まれている必要があります。 列挙型は他の場所で定義されるため、*enumerator-list* はこの宣言に含まれません。 列挙体から派生した型の宣言、および列挙型の `typedef` 宣言では、列挙型を定義する前に列挙タグを使用できます。

## <a name="syntax"></a>構文

*enumerator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerator-list* **,** *enumerator*

*enumerator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumeration-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumeration-constant* **=** *constant-expression*

*enumeration-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

*enumeration-list* 内の各 *enumeration-constant* は、列挙型セットを構成する 1 つの値に名前を付けます。 既定では、最初の *enumeration-constant* は 0 の値に関連付けられます。 リスト内の次の *enumeration-constant* は、他の値を明示的に関連付けない限り、(*constant-expression* + 1) の値に関連付けられます。 *enumeration-constant* の名前はその値と同じです。

*enumeration-constant = constant-expression* を使用すれば、既定の値の順序をオーバーライドできます。 したがって、*enumerator-list* に *enumeration-constant = constant-expression* がある場合、*enumeration-constant* は *constant-expression* が指定する値に関連付けられます。 *constant-expression* は `int` 型であることが条件となりますが、負の値でもかまいません。

列挙セットのメンバーには次の規則が適用されます。

- 列挙セットには重複する定数値を含めることができます。 たとえば、同じセット内の異なる 2 つの識別子に値 0 を関連付け、それぞれ `null` および `zero` という名前を付けることができます。

- 列挙リストの識別子は、参照範囲が同じである同一スコープ内の他の識別子と異なっている必要があります。これは、他の列挙リストの通常の変数名や識別子についても同様です。

- 列挙タグは通常のスコープ規則に従います。 参照範囲が同じである他の列挙体タグ、構造体タグ、共用体タグと異なる必要があります。

## <a name="examples"></a>使用例

次に、列挙体宣言の例を示します。

```
enum DAY            /* Defines an enumeration type    */
{
    saturday,       /* Names day and declares a       */
    sunday = 0,     /* variable named workday with    */
    monday,         /* that type                      */
    tuesday,
    wednesday,      /* wednesday is associated with 3 */
    thursday,
    friday
} workday;
```

既定では、値 0 は `saturday` に関連付けられます。 ここでは、識別子 `sunday` を明示的に 0 に設定しています。 既定では、その他の識別子には値 1 ～ 5 が割り当てられます。

この例では、`DAY` セットの値を `today` 変数に割り当てます。

```
enum DAY today = wednesday;
```

列挙定数の名前を使用して値を割り当てていることに注意してください。 `DAY` 列挙型は前に宣言されているので、必要なのは `DAY` 列挙タグのみです。

列挙データ型の変数に整数値を明示的に割り当てるため、型キャストを使用します。

```
workday = ( enum DAY ) ( day_value - 1 );
```

C ではこのキャストをお勧めしますが、必須ではありません。

```
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */
{
    false,     /* false = 0, true = 1 */
    true
};

enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */
```

この宣言は次のように指定できます。

```
enum BOOLEAN { false, true } end_flag, match_flag;\
```

また、次のように指定することもできます。

```
enum BOOLEAN { false, true } end_flag;
enum BOOLEAN match_flag;
```

これらの変数の使用例を次に示します。

```
if ( match_flag == false )
    {
     .
     .   /* statement */
     .
    }
    end_flag = true;
```

名前のない列挙データ型を宣言することもできます。 データ型の名前を省略して、変数を宣言できます。 `response` 変数は、定義された型の変数です。

```
enum { yes, no } response;
```

## <a name="see-also"></a>関連項目

[列挙型](../cpp/enumerations-cpp.md)
