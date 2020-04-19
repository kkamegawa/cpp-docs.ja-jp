---
title: ポインター宣言
ms.date: 11/04/2016
helpviewer_keywords:
- pointer declarations
- declarations, pointers
- const keyword [C]
- pointers, declarations
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
ms.openlocfilehash: 0ee6e9e78f3793cd1912ece7f8627a4be68e929c
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152002"
---
# <a name="pointer-declarations"></a>ポインター宣言

*ポインター宣言*はポインター変数に名前を付け、変数が指すオブジェクトの型を指定します。 ポインターとして宣言された変数は、メモリ アドレスを保持します。

## <a name="syntax"></a>構文

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *declarator* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **[** *constant-expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *parameter-type-list* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator* **(** *identifier-list*<sub>opt</sub> **)**

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub> *pointer*

*type-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-list* *type-qualifier*

*type-specifier* は、オブジェクトの型を指定します。指定できる型は、任意の基本型、構造体型、または共用体型です。 ポインター変数は、関数、配列、および他のポインターを指すこともできます (より複雑なポインター型の宣言および解釈については、「[さらに複雑な宣言子の解釈](../c-language/interpreting-more-complex-declarators.md)」を参照)。

*type-specifier* **void** を作成すると、ポインターが参照する型を後から指定できます。 このような項目は、"**void** へのポインター" と呼ばれ、`void *` と記述します。 *void* へのポインターとして宣言された変数は、任意の型のオブジェクトを指すために使用できます。 ただし、ポインターに対する操作やポインターが指すオブジェクトに対する操作のほとんどは、それが指す型を操作ごとに明示的に指定して実行する必要があります (**char** <strong>\*</strong> 型と **void** <strong>\*</strong> 型の変数は代入互換性があり、型キャストは不要です)。このような変換には型キャストを使用します (詳細については、「[型キャスト変換](../c-language/type-cast-conversions.md)」を参照)。

*type-qualifier* には、**const** か **volatile** のいずれか、または両方を指定できます。 **const** はポインターがプログラム自体によって変更できないことを指定し、**volatile** はプログラムによるコントロール以外のプロセスによって適切に変更できることを指定します  (**const** と **volatile** の詳細については、「[型修飾子](../c-language/type-qualifiers.md)」を参照)。

*declarator* は変数に名前を付けます。これには、型修飾子を含めることができます。 たとえば、*declarator* が配列を表す場合、ポインターの型を配列へのポインターに変更できます。

構造体型、共用体型、または列挙型へのポインターは、構造体型、共用体型、または列挙型を定義する前に宣言できます。 ポインターの宣言には、次の例に示すように、構造体タグまたは共用体タグを使用します。 このような宣言ができるのは、コンパイラがポインター変数の領域を割り当てるのに、構造体や共用体のサイズが不要であるためです。

## <a name="examples"></a>使用例

ポインター宣言の例を次に示します。

```
char *message; /* Declares a pointer variable named message */
```

*message* ポインターは、**char** 型の変数を指しています。

```
int *pointers[10];  /* Declares an array of pointers */
```

*pointers* 配列には 10 個の要素があり、各要素は **int** 型の変数へのポインターです。

```
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */
```

この*ポインター*変数は、10 個の要素を持つ配列を指します。 この配列の各要素は **int** 型です。

```
int const *x;      /* Declares a pointer variable, x,
                      to a constant value */
```

ポインター *x* が別の **int** 値を指すように変更することはできますが、指す値自体を変更することはできません。

```
const int some_object = 5 ;
int other_object = 37;
int *const y = &fixed_object;
int volatile *const z = &some_object;
int *const volatile w = &some_object;
```

これらの宣言の中で、変数 *y* は、**int** 値への定数ポインターとして宣言されています。 このポインターが指す値を変更することはできますが、ポインター自体は常に同じ場所、つまり *fixed_object* のアドレスを指す必要があります。 同様に、*z* は定数ポインターです。しかし、プログラムによって値を変更できない **int** を指すことが併せて宣言されています。 指定子 **volatile** を追加することで、*z* が指す **const int** の値はプログラムによって変更できないが、プログラムと同時に実行されているプロセスによって適切に変更できることが指定されます。 *w* の宣言は、指す値がプログラムによって変更できず、ポインターもプログラムによって変更できないことを指定しています。

```
struct list *next, *previous; /* Uses the tag for list */
```

この例では、構造体型 *list* を指す 2 つのポインター変数、*next* と *previous* が宣言されています。 この宣言は *list* 構造体型の定義の前に配置できます (次の例を参照)。ただし、その場合、*list* 型定義が宣言と同じ可視性を備える必要があります。

```
struct list
{
    char *token;
    int count;
    struct list *next;
} line;
```

変数 *line* には *list* という構造体型があります。 この *list* 構造体型には、**char** 値へのポインター、**int** 値、別の *list* 構造体へのポインター、の 3 つのメンバーが含まれています。

```
struct id
{
    unsigned int id_no;
    struct name *pname;
} record;
```

変数 *record* には *id* という構造体型があります。*pname* が、*name* という別の構造体型へのポインターとして宣言されていることに注意してください。 この宣言は、*name* 型を定義する前に指定できます。

## <a name="see-also"></a>関連項目

[宣言子と変数宣言](../c-language/declarators-and-variable-declarations.md)
