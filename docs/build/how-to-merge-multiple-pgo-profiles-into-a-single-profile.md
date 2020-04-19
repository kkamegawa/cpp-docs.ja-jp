---
title: '方法: 複数の PGO プロファイルを 1 つのプロファイルにマージします。'
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 451c0f30a271f5dce3974e172766da4a23340b93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188874"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>方法: 複数の PGO プロファイルを 1 つのプロファイルにマージします。

最適化のガイド付きプロファイル (PGO) は、プロファイリングが実行されているシナリオに基づく最適化されたバイナリを作成するための優れたツールです。 しかし、いくつかの重要なまだ個別のシナリオを含むアプリケーションがある場合でしょうか。 複数の異なるシナリオから PGO を使用できる 1 つのプロファイルを作成します。 Visual studio で、PGO マネージャー [pgomgr.exe](pgomgr.md)、このジョブによって自動的に行わします。

プロファイルをマージするための構文です。

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

場所`num`はこのマージによって追加された .pgc ファイルを使用するオプションの重み。 他のユーザーよりも重要なシナリオがある場合、または複数回実行するシナリオがある場合、重みが通常使用されます。

> [!NOTE]
> PGO Manager は、古いプロファイル データでは機能しません。 .Pgd ファイル .pgc ファイルをマージするには、.pgd ファイルを生成したのと同じリンク呼び出しによって作成された実行可能ファイルから .pgc ファイルを生成する必要があります。

## <a name="examples"></a>使用例

この例では、PGO Manager に追加されます pgcFile.pgc pgdFile.pgd 6 回。

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

この例では、PGO Manager は、各 .pgc ファイルを 2 回の pgdFile.pgd に pgcFile1.pgc と pgcFile2.pgc を追加します。

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

.Pgc ファイル引数を使用せず、PGO Manager を実行した場合は、後に感嘆符 (!) と、1 つまたは複数任意文字 .pgd ファイルとして同じ基本名を取得する .pgc ファイルをすべてのローカル ディレクトリを検索します。 たとえば、ローカル ディレクトリにファイル test.pgd、test!1.pgc、test2.pgc、および test!hello.pgc、し、次のコマンドが、ローカルのディレクトリから実行**pgomgr** test!1.pgc と test!hello.pgc test.pgd にマージします。

`pgomgr /merge test.pgd`

## <a name="see-also"></a>関連項目

[ガイド付き最適化のプロファイル](profile-guided-optimizations.md)
