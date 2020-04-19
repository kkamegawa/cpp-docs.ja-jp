---
title: while ステートメント (C)
ms.date: 11/04/2016
f1_keywords:
- while
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
ms.openlocfilehash: 4a789f248702f33342a19f95710a8ae313da1d94
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151898"
---
# <a name="while-statement-c"></a>while ステートメント (C)

`while` ステートメントを使用して、指定した式が false になるまでステートメントを繰り返すことができます。

## <a name="syntax"></a>構文

*iteration-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**while (**  *expression*  **)**  *statement*

*expression* は演算型またはポインター型であることが必要です。 次のように実行されます。

1. *expression* が評価されます。

1. 最初の時点で *expression* が false の場合、`while` ステートメントの本体は実行されず、`while` ステートメントからプログラムの次のステートメントへ制御が渡されます。

   *expression* が true (0 以外) の場合はステートメントの本体が実行され、手順 1 からプロセスが繰り返されます。

`while` ステートメントは、ステートメント本体内の **break**、`goto`、または `return` が実行されたときにも終了できます。 `while` ループが終了する前に反復を終了するには、**continue** ステートメントを使用します。 **continue** ステートメントは `while` ステートメントの次のイテレーションに制御を渡します。

`while` ステートメントの例を次に示します。

```C
while ( i >= 0 )
{
    string1[i] = string2[i];
    i--;
}
```

このコード例では、`string2` の文字を `string1` にコピーします。 `i` が 0 以上の場合、`string2[i]` が `string1[i]` に割り当てられ、`i` がデクリメントされます。 `i` が 0 に達するか、0 より小さくなると、`while` ステートメントの実行が終了します。

## <a name="see-also"></a>関連項目

[while ステートメント (C++)](../cpp/while-statement-cpp.md)
