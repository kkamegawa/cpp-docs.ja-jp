---
title: リンカー ツールの警告 LNK4206
ms.date: 12/05/2017
f1_keywords:
- LNK4206
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
ms.openlocfilehash: dc81df89609f59834c8a3271dd64f3b99b281f90
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395080"
---
# <a name="linker-tools-warning-lnk4206"></a>リンカー ツールの警告 LNK4206

> プリコンパイル済みの型情報が見つかりませんでした。'*filename*' いないリンクまたは上書きはありませんデバッグ情報オブジェクトをリンク。

*Filename*を使用してコンパイルされたオブジェクト ファイルは、 [/Yc](../../build/reference/yc-create-precompiled-header-file.md)、LINK コマンドで指定されなかったか、または上書きされました。

この警告の一般的なシナリオは、コードからその .obj にシンボル参照がないと/Yc でコンパイルされた .obj ファイルが、ライブラリの場合は。  その場合は、リンカーはいないを使用して (またはも参照してください)、.obj ファイル。  このような状況でコードを再コンパイルして使用する必要があります[/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)を使用してコンパイルされたオブジェクトの[/Yu](../../build/reference/yu-use-precompiled-header-file.md)します。