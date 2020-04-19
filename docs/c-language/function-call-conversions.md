---
title: 関数呼び出しでの変換
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, converting
- function calls, argument type conversions
- functions [C], argument conversions
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
ms.openlocfilehash: d9f205bbbbac353b57743f8e1211b20fa3d32f05
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152483"
---
# <a name="function-call-conversions"></a>関数呼び出しでの変換

関数呼び出しの引数に対して実行される変換の種類は、呼び出される関数の宣言された引数の型を持つ関数プロトタイプ (事前宣言) の有無によって異なります。

関数プロトタイプがあり、その関数プロトタイプに宣言された引数の型が含まれている場合、コンパイラは型チェックを実行します (「[関数](../c-language/functions-c.md)」を参照)。

関数プロトタイプがない場合、関数呼び出しの引数に対しては通常の算術変換だけが実行されます。 これらの変換は呼び出しの各引数に対して個別に実行されます。 つまり、**float** 値は **double** に変換され、`char` または **short** 値は `int` に変換され、`unsigned char` または **unsigned short** は `unsigned int` に変換されます。

## <a name="see-also"></a>関連項目

[型変換](../c-language/type-conversions-c.md)
