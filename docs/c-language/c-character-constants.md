---
title: C 文字定数
ms.date: 11/04/2016
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
ms.openlocfilehash: 5d87b57726f741cc96f2180de33cae01403786ec
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152769"
---
# <a name="c-character-constants"></a>C 文字定数

"文字定数" は、表現できる文字セットの 1 文字を単一引用符 (**' '**) で囲むことによって作成されます。 文字定数は、[実行文字セット](../c-language/execution-character-set.md)の文字を表すために使用されます。

## <a name="syntax"></a>構文

*character-constant*: **'** *c-char-sequence* **'**

**L'** *c-char-sequence* **'**

*c-char-sequence*: *c-char*

*c-char-sequence c-char*

*c-char*:単一引用符 (**'**)、円記号 (**\\**)、および改行文字を除くソース文字セットのメンバー

*escape-sequence*

*escape-sequence*: *simple-escape-sequence*

*octal-escape-sequence*

*hexadecimal-escape-sequence*

*simple-escape-sequence*: **\a \b \f \n \r \t \v** のいずれか

**\\' \\" \\\ \\?**

*octal-escape-sequence*: **\\**  *octal-digit*

**\\**  *octal-digit octal-digit*

**\\**  *octal-digit octal-digit octal-digit*

*hexadecimal-escape-sequence*: **\x**  *hexadecimal-digit*

*hexadecimal-escape-sequence hexadecimal-digit*

## <a name="see-also"></a>関連項目

[C 定数](../c-language/c-constants.md)
