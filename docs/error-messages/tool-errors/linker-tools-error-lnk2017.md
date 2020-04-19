---
title: リンカ ツール エラー LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: ce5332c2812740ef0b8c7d8e9c64a095d20a4e2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299056"
---
# <a name="linker-tools-error-lnk2017"></a>リンカ ツール エラー LNK2017

'symbol' relocation to 'segment' invalid without /LARGEADDRESSAWARE:NO

32 ビットのアドレスを持つ 64 ビット イメージをビルドしようとしました。 これを行うには、次の必要があります。

- 固定の読み込みアドレスを使用します。

- イメージは、3 GB に制限します。

- 指定[/largeaddressaware:no](../../build/reference/largeaddressaware-handle-large-addresses.md)します。