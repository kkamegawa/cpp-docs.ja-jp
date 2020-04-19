---
title: 致命的なエラー C1052
ms.date: 05/08/2017
f1_keywords:
- C1052
helpviewer_keywords:
- C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
ms.openlocfilehash: b381cc3cfe27d4c4a9d744a6b854a0e43727fe71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243682"
---
# <a name="fatal-error-c1052"></a>致命的なエラー C1052

> プログラム データベース ファイルでは、'*filename*'、;/DEBUG:fastlink のリンカーによって生成されたコンパイラできませんこのような PDB ファイルを更新; か削除してください、/Fd を使用して、別の PDB ファイル名を指定するには

コンパイラはリンカーによって生成された同じプログラム データベース (PDB) ファイルを更新できないときに、 [/DEBUG:fastlink](../../build/reference/debug-generate-debug-info.md)オプションを指定します。 通常、コンパイラによって生成された PDB ファイルと PDB リンカーによって生成されたファイルは、異なる名前を付けます。 同じ名前を使用する設定されている場合にこのエラーは発生します。

この問題を修正するには、前に、コンパイラ生成され、リンカーによって生成された PDB ファイルに異なる名前を作成する、もう一度コンパイルすることもに PDB ファイルを明示的に削除できます。

コマンドラインでコンパイラにより生成された PDB ファイル名を指定するには、使用、 [/Fd](../../build/reference/fd-program-database-file-name.md)コンパイラ オプション。 IDE では、コンパイラによって生成された PDB ファイル名を指定するには、開く、**プロパティ ページ**で、プロジェクトのダイアログ ボックス、**構成プロパティ**、 **C/C++**、 **出力ファイル** ページで、設定、**プログラム データベース ファイル名**プロパティ。 このプロパティは、既定では、`$(IntDir)vc$(PlatformToolsetVersion).pdb`します。

また、リンカーによって生成された PDB ファイル名を設定できます。 コマンドラインでは、リンカーによって生成された PDB ファイル名を指定するには、使用、 [/PDB](../../build/reference/pdb-use-program-database.md)リンカー オプション。 IDE のリンカーによって生成された PDB ファイル名を指定するには、開く、**プロパティ ページ**で、プロジェクトのダイアログ ボックス、**構成プロパティ**、**リンカー**、 **デバッグ** ページで、設定、**プログラム データベース ファイルの生成**プロパティ。 既定では、このプロパティは `$(OutDir)$(TargetName).pdb`に設定されています。
