---
title: inline_recursion プラグマ
ms.date: 08/29/2019
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
ms.openlocfilehash: 0169e06e8e47f7b0a7b3f73e809ddc988bcf1e95
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220958"
---
# <a name="inline_recursion-pragma"></a>inline_recursion プラグマ

直接呼び出しまたは相互再帰関数の呼び出しのインライン展開を制御します。

## <a name="syntax"></a>構文

> **#pragma inline_recursion (** [{ **on** | **off** }] **)**

## <a name="remarks"></a>Remarks

このプラグマを使用して、[インライン](../cpp/inline-functions-cpp.md)としてマークされた関数[、または](../cpp/inline-functions-cpp.md)コンパイラ`/Ob2`がオプションの下で自動的に展開する関数を制御します。 このプラグマを使用するには、 [/Ob](../build/reference/ob-inline-function-expansion.md)コンパイラオプションを1または2のいずれかに設定する必要があります。 **Inline_recursion**の既定の状態は off です。 このプラグマは、プラグマが表示された後の最初の関数呼び出しで有効になり、関数の定義には影響しません。

**Inline_recursion**プラグマは、再帰関数を展開する方法を制御します。 **Inline_recursion**が off で、インライン関数がそれ自体を直接または間接的に呼び出す場合、関数は1回だけ拡張されます。 **Inline_recursion**が on の場合、関数は、 [inline_depth](../preprocessor/inline-depth.md)プラグマで設定された値に達するか、 `inline_depth`プラグマで定義されている再帰関数の既定値に達するか、容量の上限に達するまで、複数回展開されます。

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_depth](../preprocessor/inline-depth.md)\
[/Ob (関数のインライン展開)](../build/reference/ob-inline-function-expansion.md)
