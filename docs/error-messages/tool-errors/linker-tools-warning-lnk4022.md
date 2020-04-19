---
title: リンカー ツールの警告 LNK4022
ms.date: 11/04/2016
f1_keywords:
- LNK4022
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
ms.openlocfilehash: 1c9ccfe6ca201ae4deed69c7d01429c67cce4bda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298467"
---
# <a name="linker-tools-warning-lnk4022"></a>リンカー ツールの警告 LNK4022

シンボル 'symbol' の一意の一致を見つけることができません。

指定された装飾されていないシンボルのリンクまたは LIB が複数見つかりましたが一致して、あいまいさが解決できませんでした。 出力ファイル (.exe、.dll、.exp、または .lib) は生成されません。 この警告は、1 つの警告の後に[LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md)ごとのシンボルを複製し、致命的なエラーが最後に[LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md)します。

この警告を回避するには、修飾された形式で、シンボルを指定します。 実行[DUMPBIN](../../build/reference/dumpbin-options.md)装飾名のオブジェクトを参照してください。