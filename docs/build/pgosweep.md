---
title: pgosweep
ms.date: 03/14/2018
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
ms.openlocfilehash: 3ba31671fc3794e1cc959d86d914ba1eef2e01e4
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341198"
---
# <a name="pgosweep"></a>pgosweep

.Pgc ファイルを実行中のプログラムからすべてのプロファイル データを書き込むプロファイル ガイド付き最適化のために使用します。

## <a name="syntax"></a>構文

> **pgosweep** [*options*] *image* *pgcfile*

### <a name="parameters"></a>パラメーター

*options*<br/>
(省略可能)有効な値*オプション*は。

- **/?** または **/help**ヘルプ メッセージが表示されます。

- **/noreset**ランタイム データ構造体の数を保持します。

*image*<br/>
使用して作成された .exe または .dll ファイルの完全なパス、 [/GENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)、 [/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)、または[/LTCG:PGINSTRUMENT](reference/ltcg-link-time-code-generation.md)オプション。

*pgcfile*<br/>
このコマンドの書き込み先データをカウントする .pgc ファイル。

## <a name="remarks"></a>Remarks

**Pgosweep**コマンドを使用してビルドされたプログラムで機能、 [/GENPROFILE または/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)オプション、または非推奨とされる[/LTCG:PGINSTRUMENT](reference/ltcg-link-time-code-generation.md)オプション。 これにより、実行中のプログラムを中断し、新しい .pgc ファイルにプロファイル データを書き込みます。 既定では、コマンドは、個々 の書き込み操作の後にカウントをリセットします。 指定した場合、 **/noreset**オプション、コマンドは、値が記録されますが、プログラムの実行にリセットされません。 このオプションにより、重複するデータ、プロファイル データを後で取得する場合。

用途**pgosweep**だけ、アプリケーションの通常の動作のプロファイル情報を取得することができます。 たとえば、実行する**pgosweep**直後にアプリケーションを起動し、そのファイルを破棄します。 これは、起動時のコストに関連付けられているプロファイル データを削除します。 その後、実行**pgosweep**アプリケーションを終了する前にします。 収集されたデータになりました時間からのみプロファイル情報、ユーザーがプログラムと対話できます。

.Pgc ファイル名を指定する場合 (を使用して、 *pgcfile*パラメーター) は、標準の形式を使用する*appname! n*.pgc します。 この形式を使用する場合、コンパイラがでこのデータを自動的に見つけます、 **/LTCG/USEPROFILE**または **/LTCG:PGO**フェーズ。 使用する必要がある、標準の形式を使用しない場合[pgomgr](pgomgr.md) .pgc ファイルをマージします。

> [!NOTE]
> このツールは、Visual Studio 開発者コマンド プロンプトからのみ起動できます。 システム コマンド プロンプトやエクスプローラーからは開始できません。

実行可能ファイル内からプロファイル データをキャプチャする方法については、次を参照してください。 [PgoAutoSweep](pgoautosweep.md)します。

## <a name="example"></a>例

この例では、 **pgosweep** myapp!1.pgc に myapp.exe の現在のプロファイル情報を書き込みます。

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>関連項目

[ガイド付き最適化のプロファイル](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
