---
title: リンカー ツールの警告 LNK4001
ms.date: 11/04/2016
f1_keywords:
- LNK4001
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
ms.openlocfilehash: 75ca9ec92bbba1c15efc11a731b3894ea03e33dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298790"
---
# <a name="linker-tools-warning-lnk4001"></a>リンカー ツールの警告 LNK4001

オブジェクト ファイルが指定されていません。ライブラリを使用します

リンカーは、.obj ファイルは、1 つまたは複数の .lib ファイルに渡されました。

リンカーは、.obj ファイルにアクセスすることは、.lib ファイル内の情報にアクセスできないため、この警告は、その他のリンカー オプションを明示的に指定する必要があるを示します。 たとえばを指定する必要があります、 [/機械](../../build/reference/machine-specify-target-platform.md)、 [/out](../../build/reference/out-output-file-name.md)、または[/ENTRY](../../build/reference/entry-entry-point-symbol.md)オプション。