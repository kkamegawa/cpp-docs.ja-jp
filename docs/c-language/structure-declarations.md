---
title: 構造体宣言
ms.date: 11/04/2016
helpviewer_keywords:
- structure declarations
- anonymous structures
- types [C], declarations
- structure members
- embedded structures
ms.assetid: 5be3be77-a236-4153-b574-7aa77675df7f
ms.openlocfilehash: a17bb996f13fdbe11bb569c8af5669a9d0c5363f
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152288"
---
# <a name="structure-declarations"></a>構造体宣言

"構造体宣言" では、型に名前を付け、異なる型を持つことのできる変数値のシーケンス (構造体の "メンバー" または "フィールド" と呼びます) を指定します。 "タグ" と呼ばれる省略可能な識別子で構造体の型に名前を付けると、その後はタグを使用してその構造体型を参照できます。 構造体型の変数は、その型で定義されているシーケンス全体を保持します。 C の構造体は、他の言語で "レコード" と呼ばれる型に似ています。

## <a name="syntax"></a>構文

*struct-or-union-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union* *identifier*<sub>opt</sub> **{** *struct-declaration-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union* *identifier*

*struct-or-union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**struct**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**union**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration-list* *struct-declaration*

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifier-qualifier-list* *struct-declarator-list* **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *specifier-qualifier-list*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *specifier-qualifier-list*<sub>opt</sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declarator* *struct-declarator-list* **,** *struct-declarator*

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declarator*<sub>opt</sub> **:** *constant-expression*

構造体型の宣言では、構造体の領域は確保されません。 これは、後で構造体変数を宣言するためのテンプレートにすぎません。

以前に定義済みの *identifier* (タグ) を使用して、他の場所で定義された構造体型を参照することができます。 この場合、定義が参照可能である限り、*struct-declaration-list* を繰り返すことはできません。 構造体へのポインターの宣言や構造体型の typedef では、構造体型を定義する前に構造体タグを使用できます。 ただし、構造体の定義は、フィールドのサイズが実際に使用される前に検出される必要があります。 この状態では、型および型のタグの定義は不完全です。 この定義を完全なものにするには、同じスコープ内に後で型定義を記述する必要があります。

*struct-declaration-list* は構造体メンバーの型と名前を指定します。 *struct-declaration-list* 引数は、1 つまたは複数の変数またはビット フィールドの宣言を含みます。

*struct-declaration-list* で宣言された各変数は構造体型のメンバーとして定義されます。 *struct-declaration-list* 内での変数宣言は、このセクションで説明されている他の変数宣言と同じ形式ですが、ストレージ クラスの指定子または初期化子を含むことはできません。 構造体メンバーは、`void`、不完全な型、または関数型を除く任意の変数型を持つことができます。

メンバーを、そのメンバーを含む構造体の型を持つように宣言することはできません。 ただし、構造体型にタグがある場合は、メンバーを、そのメンバーを含む構造体型へのポインターとして宣言できます。 これにより、構造体のリンク リストを作成できます。

構造体は、他の識別子と同じスコープに従います。 構造体の識別子は、同じ可視性を持つ他の構造体タグ、共用体タグ、および列挙タグとは異なる必要があります。

*struct-declaration-list* 内の各 *struct-declaration* は、リスト内で一意である必要があります。 ただし、*struct-declaration-list* 内の識別子名は、通常の変数名や他の構造体宣言リストの識別子と別にする必要はありません。

入れ子構造にも、ファイル スコープ レベルで宣言されているかのようにアクセスできます。 たとえば、次の宣言があるとします。

```C
struct a
{
    int x;
    struct b
    {
      int y;
    } var2;
} var1;
```

次の宣言は、どちらも有効です。

```C
struct a var3;
struct b var4;
```

## <a name="examples"></a>使用例

以下の各例は、構造体宣言を示しています。

```C
struct employee   /* Defines a structure variable named temp */
{
    char name[20];
    int id;
    long class;
} temp;
```

`employee` 構造体は、3 つのメンバー、`name`、`id`、`class` を持ちます。 `name` メンバーは 20 要素の配列で、`id` と `class` は、それぞれ `int` 型と **long** 型を持つ単純なメンバーです。 識別子 `employee` は構造体識別子です。

```C
struct employee student, faculty, staff;
```

この例では、3 種類の構造体変数 (`student`、`faculty`、および `staff`) を定義しています。 各構造体は、3 つのメンバーで構成される同じリストを持ちます。 メンバーは、前の例で定義した構造体型 `employee` を持つように宣言されています。

```C
struct           /* Defines an anonymous struct and a */
{                /* structure variable named complex  */
    float x, y;
} complex;
```

`complex` 構造体は、**float** 型の 2 つのメンバー、`x` および `y` を持ちます。 この構造体型にはタグがないため、無名または匿名になります。

```C
struct sample   /* Defines a structure named x */
{
    char c;
    float *pf;
    struct sample *next;
} x;
```

この構造体の最初の 2 つのメンバーは `char` 変数と **float** 値へのポインターです。 3 番目のメンバー `next` は、定義されている構造体型へのポインターとして宣言されています (`sample`)。

無名構造体は、名前が付いたタグが不要な場合に便利です。 1 つの宣言ですべての構造体インスタンスが定義される場合は、これに該当します。 次に例を示します。

```C
struct
{
    int x;
    int y;
} mystruct;
```

多くの場合、埋め込み構造体は無名です。

```C
struct somestruct
{
    struct    /* Anonymous structure */
    {
        int x, y;
    } point;
    int type;
} w;
```

**Microsoft 固有の仕様**

コンパイラは、構造体の最後のメンバーとして可変長配列またはサイズが 0 の配列を許可します。 これは、使用されるさまざまな状況によって定数配列のサイズが異なるときに便利な場合があります。 このような構造体の宣言は次のようになります。

**struct** *identifier* **{** *set-of-declarations* *type* <em>array-name</em>**\[]; };**

可変長配列は、構造体の最後のメンバーとしてのみ使用できます。 可変長配列宣言を含む構造体は、外側のどの構造体でもそれ以上メンバーが宣言されていなければ、他の構造体内に入れ子にできます。 ただし、そのような構造体を配列にすることはできません。 この型の変数またはこの型自体に `sizeof` 演算子を適用すると、可変長配列のサイズには 0 が想定されます。

構造体宣言は、別の構造体または共用体のメンバーである場合は、宣言子なしで指定できます。 フィールド名は、外側を囲む構造に昇格されます。 たとえば、無名の構造体では次のようになります。

```C
struct s
{
    float y;
    struct
    {
        int a, b, c;
    };
    char str[10];
} *p_s;
.
.
.
p_s->b = 100;  /* A reference to a field in the s structure */
```

構造体の参照については、「[Structure and Union Members (構造体と共用体のメンバー)](../c-language/structure-and-union-members.md)」を参照してください。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[宣言子と変数宣言](../c-language/declarators-and-variable-declarations.md)
