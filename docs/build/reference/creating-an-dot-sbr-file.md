---
title: .sbr ファイルの作成
ms.date: 11/04/2016
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
ms.openlocfilehash: 6a2e685d33b108ce542fdc6e3e0565cc37299c1c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294071"
---
# <a name="creating-an-sbr-file"></a>.sbr ファイルの作成

> [!WARNING]
> BSCMAKE は、現在も Visual Studio と共にインストールされていますが、IDE では使用されなくなりました。 Visual Studio 2008 以降、ブラウザーとシンボルの情報は、ソリューション フォルダー内の SQL Server の .sdf ファイルに自動的に格納されます。

BSCMAKE の入力ファイルは、.sbr ファイルです。 コンパイラは、コンパイルされる各オブジェクト ファイル (.obj) の .sbr ファイルを作成します。 ビルドまたはブラウザー情報ファイルを更新すると、プロジェクトのすべての .sbr ファイルをディスク上にある必要があります。

すべての可能な情報を含む .sbr ファイルを作成するには、指定[/FR](fr-fr-create-dot-sbr-file.md)します。

ローカル シンボルを含まない .sbr ファイルを作成するには、指定[/Fr](fr-fr-create-dot-sbr-file.md)します。 .Sbr ファイルにローカル シンボルが含まれている場合でも削除できます .bsc ファイルから BSCMAKE を使用して[/El オプション](bscmake-options.md)`.`

完全なコンパイルを実行せず、.sbr ファイルを作成できます。 たとえば、/Zs 構文チェックを実行し、まだ/FR または/fr を指定する場合、.sbr ファイルを生成するコンパイラ オプションを指定できます。

ビルド プロセスは、.sbr ファイルをパックして、参照されていない定義を削除する場合より効率的にすることはできます。 コンパイラは、.sbr ファイルを自動的にパックします。

## <a name="see-also"></a>関連項目

[.bsc ファイルのビルド](building-a-dot-bsc-file.md)
