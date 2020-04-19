---
title: typedef 宣言
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, typedef
- typedef declarations
- types [C], declarations
ms.assetid: e92a3b82-9269-4bc6-834a-6f431ccac83e
ms.openlocfilehash: b4bf7bc82cdf792e5a23f6d5533cc4d800fe4252
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149623"
---
# <a name="typedef-declarations"></a>typedef 宣言

typedef 宣言は、ストレージ クラスとしての typedef による宣言です。 宣言子は、新しい型になります。 typedef 宣言を使用して、既に C で定義されている型や、宣言した型に対して、より短い、またはわかりやすい名前を作成できます。 Typedef 名を使用して、変更可能な実装の詳細をカプセル化できます。

typedef 宣言は、変数または関数宣言と同様に解釈されますが、宣言によって指定された型を想定する代わりに識別子は型のシノニムになります。

## <a name="syntax"></a>構文

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers init-declarator-list*<sub>opt</sub> **;**

*declaration-specifiers*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier declaration-specifiers*<sub>opt</sub>

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**typedef**

*type-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**signed**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**unsigned**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

*typedef-name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

typedef 宣言は型を作成しないことに注意してください。 既存の型のシノニム、またはその他の方法で指定できる型の名前を作成します。 Typedef 名を型指定子として使用するときは、特定の型指定子と組み合わせることはできますが、それ以外とはできません。 使用できる修飾子には **const** と `volatile` が含まれます。

typedef 名は、通常の識別子を使用して名前空間を共有します (詳細については、「[名前空間](../c-language/name-spaces.md)」を参照してください)。 そのため、プログラムは同じ名前の typedef 名とローカル スコープ識別子を持つことができます。 次に例を示します。

```C
typedef char FlagType;

int main()
{
}

int myproc( int )
{
    int FlagType;
}
```

Typedef と同じ名前でローカル スコープの識別子を宣言するとき、あるいは同じスコープまたは内部スコープで構造体または共用体のメンバーを宣言するときは、型指定子を指定する必要があります。 この例では、この制約を示しています。

```C
typedef char FlagType;
const FlagType x;
```

識別子、構造体メンバー、または共用体メンバーに対して `FlagType` 名を再利用するには、次のように型を指定する必要があります。

```C
const int FlagType;  /* Type specifier required */
```

次のような記述だけでは不十分です。

```C
const FlagType;      /* Incomplete specification */
```

`FlagType` は再宣言された識別子ではなく、型の一部であると見なされるためです。 この宣言は、次のような正しくない宣言であると見なされます。

```C
int;  /* Illegal declaration */
```

ポインター、関数、配列型を含め、あらゆる型を typedef で宣言できます。 構造体型または共用体型を定義する前に、構造体型または共用体型へのポインターの typedef 名を宣言できます。ただし、定義が宣言と同じ可視性である必要があります。

Typedef 名を使用して、コードの読みやすさを向上させることができます。 次の `signal` の宣言 3 つはすべて同じ型を指定します。1 つ目は、typedef 名を使用せずに指定します。

```C
typedef void fv( int ), (*pfv)( int );  /* typedef declarations */

void ( *signal( int, void (*) (int)) ) ( int );
fv *signal( int, fv * );   /* Uses typedef type */
pfv signal( int, pfv );    /* Uses typedef type */
```

## <a name="examples"></a>使用例

typedef 宣言の例を次に示します。

```C
typedef int WHOLE; /* Declares WHOLE to be a synonym for int */
```

`WHOLE` を `WHOLE i;`、`const WHOLE i;` などの変数宣言で使用できることに注意してください。 ただし、宣言 `long WHOLE i;` は無効です。

```C
typedef struct club
{
    char name[30];
    int size, year;
} GROUP;
```

このステートメントは、3 つのメンバーを持つ構造体の型として `GROUP` を宣言します。 構造体タグ `club` も指定されているため、typedef 名 (`GROUP`) またはその構造体タグを宣言で使用できます。 struct キーワードはタグで使用する必要があります。typedef 名で struct キーワードを使用することはできません。

```C
typedef GROUP *PG; /* Uses the previous typedef name
                      to declare a pointer            */
```

型 `PG` は、構造体型として定義される `GROUP` 型へのポインターとして宣言されています。

```C
typedef void DRAWF( int, int );
```

この例は、値を返さず 2 つの int 引数を取る関数に対して、型 `DRAWF` を提供します。 つまり、たとえば、宣言

```C
DRAWF box;
```

は、次の宣言と同じです。

```C
void box( int, int );
```

## <a name="see-also"></a>関連項目

[宣言と型](../c-language/declarations-and-types.md)
