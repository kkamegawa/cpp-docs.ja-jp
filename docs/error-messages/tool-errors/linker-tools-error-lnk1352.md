---
title: リンカツールエラー LNK1352
description: リンカーツールエラー LNK1352 は、サポートされていないセクションのマージが試行された場合に発生します。
ms.date: 09/10/2019
f1_keywords:
- LNK1352
helpviewer_keywords:
- LNK1352
ms.openlocfilehash: 38f773bfd669529dfb1ada9c7bb59e6f0962c9c7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908394"
---
# <a name="linker-tools-error-lnk1352"></a>リンカツールエラー LNK1352

> '*section_name_1*' と '*section_name_2*' を別のセクションにマージすることはできません

## <a name="remarks"></a>Remarks

*Section_name_1*と*section_name_2*を同じセクションにマージする必要があるため、リンカーでは、許可されていないセクションのマージが検出されました。 たとえば、このエラーは、リンカーがセクション`.stls` `.tls`とセクションを別々のセクションにマージしようとしたことを検出した場合に発生します。

### <a name="to-correct-this-error"></a>このエラーを解決するには

この問題については、リンカーコマンドラインの[/merge](../../build/reference/merge-combine-sections.md)オプションを確認してください。

## <a name="see-also"></a>関連項目

[リンカー ツール エラーと警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
