---
title: リンカ ツール エラー LNK2008
ms.date: 11/04/2016
f1_keywords:
- LNK2008
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
ms.openlocfilehash: 97bb2be18da5d166d1d5fba42e4ec8ce1f0439fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386526"
---
# <a name="linker-tools-error-lnk2008"></a>リンカ ツール エラー LNK2008

Fixup ターゲットは、アラインされた 'symbol_name' ではありません。

リンクでは、配置が正しくがないオブジェクト ファイルの fixup ターゲットが見つかりません。

このエラーは、カスタム セクション配置によって発生することができます (たとえば、#pragma[パック](../../preprocessor/pack.md))、 [align](../../cpp/align-cpp.md)修飾子は、またはセクション配置を変更するアセンブリ言語コードを使用しています。

コードが、上記のいずれにも使わない場合はこれ、コンパイラによって発生する可能性があります。