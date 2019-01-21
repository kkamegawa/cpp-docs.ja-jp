---
title: C 浮動小数点定数
ms.date: 11/04/2016
helpviewer_keywords:
- types [C], constants
- floating-point numbers, floating-point constants
- constants, floating-point
- floating-point constants
- floating-point constants, about floating-point constants
- double data type, floating-point constants
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
ms.openlocfilehash: 2bde8ecdfa7e93160a86829c466ab9a78b71d48e
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220375"
---
# <a name="c-floating-point-constants"></a>C 浮動小数点定数

"浮動小数点定数" は符号付き実数を表す 10 進数です。 符号付き実数の表現には、整数部分、小数部分、および指数が含まれます。 変更できない浮動小数点値を表すには、浮動小数点定数を使用します。

## <a name="syntax"></a>構文

*floating-point-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*fractional-constant* *exponent-part*<sub>opt</sub> *floating-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *exponent-part* *floating-suffix*<sub>opt</sub>

*fractional-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence*<sub>opt</sub> **.** *digit-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence*  **.**

*exponent-part*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**e** *sign*<sub>opt</sub> *digit-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**E** *sign*<sub>opt</sub> *digit-sequence*

*sign*: 次のいずれか<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*digit-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*floating-suffix*: 次のいずれか<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**f l F L**

小数点の前の桁 (値の整数の部分) または小数点の後の桁 (小数の部分) を省略できますが、両方を省略することはできません。 指数を含めた場合にのみ、小数点を省略することができます。 空白文字で定数の数値または文字を分離することはできません。

次の例では、浮動小数点定数と式のフォームをいくつか示します。

```C
15.75
1.575E1   /* = 15.75   */
1575e-2   /* = 15.75   */
-2.5e-3   /* = -0.0025 */
25E-4     /* =  0.0025 */
```

浮動小数点定数は、負符号 (**-**) が前にない限り、正の値です。 この場合、負符号は単項算術否定演算子として扱われます。 浮動小数点定数には、`float`、`double`、または `long double` 型があります。

**f**、**F**、**l**、または **L** のサフィックスのない浮動小数点定数は、`double` 型を持ちます。 文字 **f** または **F** がサフィックスの場合、定数の型は `float` になります。 末尾に文字 **l** また **L** が付いている場合、`long double` 型になります。 次に例を示します。

```C
10.0L  /* Has type long double  */
10.0F  /* Has type float        */
```

Microsoft C コンパイラは、`double` 型と同じように内部的に `long double` を表すことに注意してください。 `double`、`float`、および `long double` 型については、「[基本型の格納](../c-language/storage-of-basic-types.md)」を参照してください。

次の例に示すように、浮動小数点定数の整数の部分を省略できます。 数値 .75 は、次のようなさまざまな方法で表現されます。

```C
.0075e2
0.075e1
.075e1
75e-2
```

## <a name="see-also"></a>「

[C 定数](../c-language/c-constants.md)
