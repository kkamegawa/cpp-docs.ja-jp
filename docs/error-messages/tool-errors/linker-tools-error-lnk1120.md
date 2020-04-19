---
title: リンカー ツール エラー LNK1120
description: リンク内の未解決の外部シンボルエラーの数を報告する LNK1120 リンカーエラーについて説明します。
ms.date: 10/31/2019
f1_keywords:
- LNK1120
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
ms.openlocfilehash: 21a1ede07a69cdc065dd897715e243115529600d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626582"
---
# <a name="linker-tools-error-lnk1120"></a>リンカー ツール エラー LNK1120

> 未解決の外部の*数*

Error LNK1120 は、現在のリンクにある[未解決の外部シンボル](linker-tools-error-lnk2001.md#what-is-an-unresolved-external-symbol)エラーの数を報告します。

未解決の外部シンボルは、まず、 [LNK2001](linker-tools-error-lnk2001.md)または[LNK2019](linker-tools-error-lnk2019.md)エラーによって報告されます。 LNK1120 メッセージは最後に到着し、未解決のシンボルエラー数を示します。

> [!IMPORTANT]
> **このエラーを修正する必要はありません。** このエラーは、すべての LNK2001 および LNK2019 リンカーエラーをビルド出力の前に修正すると消えます。 最初に報告されたエラー以降の問題は常に修正してください。 それより後のエラーは、以前のエラーによって発生する可能性があり、以前のエラーが修正されたときに解決されます。
