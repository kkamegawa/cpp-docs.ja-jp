---
title: 整数型
ms.date: 11/04/2016
helpviewer_keywords:
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
ms.openlocfilehash: 23da055b56e2ae77fed796d9ba8e7f227e572a9f
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56146880"
---
# <a name="integer-types"></a>整数型

各整数定数には、その値と表現方法に基づいて型が割り当てられます。 整数定数を **long** 型にするには、その定数の末尾に文字 **l** または **L** を追加します。整数定数を `unsigned` 型にするには、その値に **u** または **U** を追加します。 小文字の **l** は数字の 1 と区別しにくいので、使用しないでください。 次に、**long** 整数定数の形式をいくつか示します。

```
/* Long decimal constants */
10L
79L

/* Long octal constants */
012L
0115L

/* Long hexadecimal constants */
0xaL or 0xAL
0X4fL or 0x4FL

/* Unsigned long decimal constant */
776745UL
778866LU
```

定数に割り当てる型は、その定数が表す値に依存します。 定数の値は、その型で表現できる値範囲内にあることが条件となります。 式で定数を使用する場合やマイナス符号 (**-**) を適用する場合、定数がどのように変換されるかは、その定数の型によって決定されます。 整数定数の変換規則は次のとおりです。

- サフィックスのない 10 進定数の型は、`int`、**long int**、または**符号なし long int** です。これら 3 つのうち、定数の値を表すことができる最初の型が定数に割り当てられます。

- サフィックスのない 8 進定数または 16 進定数に割り当てられる型は、`int`、`unsigned int`、**long int**、または**符号なし long int** です (定数のサイズによって異なります)。

- **u** または **U** サフィックスが指定された定数に割り当てられる型は、**符号なし int** または**符号なし long int** です (定数のサイズによって異なります)。

- **l** または **L** サフィックスが指定された定数に割り当てられる型は、**long int** または**符号なし long int** です (定数のサイズによって異なります)。

- **u** または **U**、および **l** または **L** サフィックスが指定された定数に割り当てられる型は、**符号なし long int** です。

## <a name="see-also"></a>関連項目

[C 整数定数](../c-language/c-integer-constants.md)
