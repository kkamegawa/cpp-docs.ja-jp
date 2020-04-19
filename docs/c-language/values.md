---
title: 値
ms.date: 11/04/2016
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
ms.openlocfilehash: a745b9cc45ed3e58cab4ec7355707d93a0557c04
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150039"
---
# <a name="values"></a>値

**ANSI 3.1.2.5** 浮動小数点数のさまざまな型の表現と値セット

**float** 型は 32 ビットです。符号が 1 ビット、指数部が 8 ビット、仮数部が 23 ビットです。 その範囲は 7 桁以上の精度で、+/- 3.4E38 です。

**double** 型は 64 ビットです。符号が 1 ビット、指数部が 11 ビット、仮数部が 52 ビットです。 その範囲は 15 桁以上の精度で、+/- 1.7E308 です。

**long double** 型は 80 ビットです。符号が 1 ビット、指数部が 15 ビット、仮数部が 64 ビットです。 その範囲は 19 桁以上の精度で、+/- 1.2E4932 です。 Microsoft C コンパイラでは、**long double** 型の表現は **double** 型と同じであることに注意してください。

## <a name="see-also"></a>関連項目

[浮動小数点演算](../c-language/floating-point-math.md)
