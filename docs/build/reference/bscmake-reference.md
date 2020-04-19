---
title: BSCMAKE リファレンス
ms.date: 05/06/2019
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
ms.openlocfilehash: 72ad297ee5a24bc0c7ffd3ed25959031d0b8a309
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220563"
---
# <a name="bscmake-reference"></a>BSCMAKE リファレンス

> [!WARNING]
> BSCMAKE は、現在も Visual Studio と共にインストールされていますが、IDE では使用されなくなりました。 Visual Studio 2008 以降、ブラウザーとシンボルの情報は、ソリューション フォルダー内の SQL Server の .sdf ファイルに自動的に格納されます。

Microsoft Browse Information Maintenance Utility (BSCMAKE.EXE) は、コンパイル時に作成された .sbr ファイルから、ブラウザー情報ファイル (.bsc) を作成します。 特定のサード パーティ製ツールでは、コード分析の .bsc ファイルを使用します。

プログラムをビルドするときに、BSCMAKE を使用してファイルをビルドすれば、プログラムのブラウザー情報ファイルを自動的に作成できます。 Visual Studio 開発環境でブラウザー情報ファイルを作成する場合は、BSCMAKE を実行する方法を理解する必要はありません。 ただし、このトピックを読めば、利用可能な選択肢を理解することができます。

開発環境の外部でプログラムをビルドする場合は、その環境で確認することができるカスタム .bsc ファイルを作成できます。 コンパイル中に作成した .sbr ファイル上で BSCMAKE を実行します。

> [!NOTE]
>  このツールは、Visual Studio 開発者コマンド プロンプトからのみ起動できます。 システム コマンド プロンプトやエクスプローラーからは開始できません。

ここでは、次のトピックについて説明します。

- [ブラウザー情報ファイルのビルド: 概要](building-browse-information-files-overview.md)

- [.Bsc ファイルのビルド](building-a-dot-bsc-file.md)

- [BSCMAKE コマンドライン](bscmake-command-line.md)

- [BSCMAKE コマンド ファイル](bscmake-command-file-response-file.md)

- [BSCMAKE オプション](bscmake-options.md)

- [BSCMAKE 終了コード](bscmake-exit-codes.md)

## <a name="see-also"></a>関連項目

[追加の MSVC ビルド ツール](c-cpp-build-tools.md)
