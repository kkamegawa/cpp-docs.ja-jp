---
title: do-while ステートメント (C)
ms.date: 11/04/2016
f1_keywords:
- do
- while
helpviewer_keywords:
- do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
ms.openlocfilehash: 052b02beca49f5de19c6f68cc475edb5f5daf6e2
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147504"
---
# <a name="do-while-statement-c"></a>do-while ステートメント (C)

*do-while* ステートメントを使用すると、指定した式が false になるまでステートメントまたは複合ステートメントを繰り返すことができます。

## <a name="syntax"></a>構文

*iteration-statement*: &nbsp;&nbsp;&nbsp;&nbsp;**do**  *statement*  **while (**  *expression*  **) ;**

*do-while* ステートメント内の *expression* は、ループの本体が実行された後で評価されます。 したがって、ループの本体は、常に少なくとも 1 回は実行されます。

*expression* は演算型またはポインター型であることが必要です。 次のように実行されます。

1. ステートメントの本体が実行されます。

1. 次に、*expression* が評価されます。 *expression* が false の場合、*do-while* ステートメントは終了し、プログラムの次のステートメントに制御が渡されます。 *式*が true (0 以外) の場合、プロセスは手順 1 から繰り返されます。

*do-while* ステートメントは、**break**、**goto**、または **return** ステートメントがステートメントの本体で実行されたときにも終了できます。

*do-while* ステートメントの例を次に示します。

```C
do
{
    y = f( x );
    x--;
} while ( x > 0 );
```

この *do-while* ステートメントでは、`x` の初期値に関係なく、2 つのステートメント `y = f( x );` および `x--;` が実行されます。 次に、`x > 0` が評価されます。 `x` が 0 より大きい場合、ステートメント本体が再度実行され、`x > 0` が再評価されます。 `x` が 0 より大きい間、ステートメント本体が繰り返し実行されます。 *do-while* ステートメントの実行は、`x` が 0 または負になると終了します。 ループの本体は、少なくとも 1 回は実行されます。

## <a name="see-also"></a>関連項目

[do-while ステートメント (C++)](../cpp/do-while-statement-cpp.md)
