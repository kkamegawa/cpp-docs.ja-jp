---
title: 構造体と共用体のメンバー
ms.date: 11/04/2016
helpviewer_keywords:
- member-selection operators
- structure members, referencing
- -> operator, structure and union members
- dot operator (.)
- referencing structure members
- . operator
- operators [C], member selection
- structure member selection
ms.assetid: bb1fe304-af49-4f98-808d-afdc99b3e319
ms.openlocfilehash: db47362096506cf1c00f1ac566565b894253d798
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151365"
---
# <a name="structure-and-union-members"></a>構造体と共用体のメンバー

"メンバー選択式" は構造体と共用体のメンバーを参照します。 このような式には、選択したメンバーの値と型が割り当てられます。

> *postfix-expression* **.** *identifier*
> *postfix-expression* **->** *identifier*

ここでは、メンバー選択式の 2 つの形式について説明します。

1. 最初の形式で、*postfix-expression* は **struct** 型または **union** 型の値を表し、*identifier* はその構造体または共用体のメンバーを指定します。 *postfix-expression* が左辺値の場合、この演算の値は *identifier* の値で、左辺値です。 詳細については、「[左辺値と右辺値の式](../c-language/l-value-and-r-value-expressions.md)」を参照してください。

1. 2 番目の形式では、*postfix-expression* は構造体または共用体へのポインターを表し、*identifier* はその構造体または共用体のメンバーを指定します。 値は *identifier* の値で、左辺値です。

どちらの形式のメンバー選択式でも同じ結果が得られます。

実際、ピリオド (**.**) を用いた式の左側部分に間接演算子 (<strong>\*</strong>) が適用されている場合、その簡潔バージョンとしてメンバー選択演算子 (**->**) を用いた式を使用できます。 次に例を示します。

```cpp
expression->identifier
```

上記の式は、次の式と同じです。

```cpp
(*expression).identifier
```

*expression* はポインター値になります。

## <a name="examples"></a>使用例

次に、この構造体宣言の例を示します。 これらの例で使用されている間接演算子 (<strong>\*</strong>) については、「[間接演算子とアドレス演算子](../c-language/indirection-and-address-of-operators.md)」を参照してください。

```
struct pair
{
    int a;
    int b;
    struct pair *sp;
} item, list[10];
```

`item` 構造体のメンバー選択式は次のようになります。

```
item.sp = &item;
```

上の例では、`item` 構造体のアドレスが、この構造体の `sp` メンバーに割り当てられます。 つまり、`item` にはそれ自体へのポインターが格納されます。

```
(item.sp)->a = 24;
```

この例では、ポインター式 `item.sp` とメンバー選択演算子 (**->**) を使用して、メンバー `a` に値を割り当てています。

```
list[8].b = 12;
```

このステートメントは、構造体の配列から個々の構造体メンバーを選択する方法を示しています。

## <a name="see-also"></a>関連項目

[メンバー アクセス演算子: . および ->](../cpp/member-access-operators-dot-and.md)
