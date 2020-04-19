---
title: 'リファレンス: vcperf コマンド'
description: コマンドラインユーティリティ vcperf のリファレンスです。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b85320ce4517eb41410c59a11bd79553405b8402
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333882"
---
# <a name="reference-vcperf-commands"></a>リファレンス: vcperf コマンド

::: moniker range="<=vs-2017"

Visual C++ Studio 2019 では、Build Insights ツールを使用できます。 そのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range="vs-2019"

この記事では、 *vcperf*で使用できるコマンドとその使用方法について説明します。

## <a name="commands-to-start-and-stop-traces"></a>トレースを開始および停止するコマンド

*重要: 次のコマンドにはすべて管理者特権が必要です。*

| オプション           | 引数と説明 |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | 指定されたセッション名でトレースを開始するように*vcperf*に指示します。 指定されたコンピューターには、一度に1つのアクティブなセッションしか存在できません。 <br/><br/> `/nocpusampling` オプションを指定した場合、 *vcperf*では CPU サンプルが収集されません。 Windows Performance Analyzer で CPU 使用率 (サンプリング) ビューを使用できなくなりますが、収集されたトレースは小さくなります。 <br/><br/> トレースが開始されると、 *vcperf*はすぐに制御を戻します。 イベントは、コンピューター上で実行されているすべてのプロセスに対してシステム全体で収集されます。 これは、 *vcperf*を実行するために使用したものと同じコマンドプロンプトからプロジェクトをビルドする必要がないことを意味します。 たとえば、Visual Studio からプロジェクトをビルドできます。 |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | 指定されたセッション名で識別されるトレースを停止します。 トレースで処理後の手順を実行して、Windows Performance Analyzer (WPA) で表示可能なファイルを生成します。 最適な表示エクスペリエンスを得るには、 C++ Build Insights アドインを含む WPA のバージョンを使用します。 詳細については、「 [Build C++ Insights の概要](/cpp/build-insights/get-started-with-cpp-build-insights)」を参照してください。 `<outputFile.etl>` パラメーターは、出力ファイルを保存する場所を指定します。 |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | 指定されたセッション名で識別されるトレースを停止し、未処理の未処理データを指定された出力ファイルに書き込みます。 生成されたファイルは、WPA で表示するためのものではありません。 <br/><br/> `/stop` コマンドに含まれる処理後の手順は、時間がかかることがあります。 `/stopnoanalyze` コマンドを使用すると、この処理後の手順を遅らせることができます。 Windows Performance Analyzer で表示できるファイルを生成する準備ができたら、`/analyze` コマンドを使用します。 |

## <a name="miscellaneous-commands"></a>その他のコマンド

| オプション     | 引数と説明 |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | `/stopnoanalyze` コマンドによって生成された生のトレースファイルを受け入れます。 このトレースの処理後の手順を実行して、Windows パフォーマンスアナライザーで表示可能なファイルを生成します。 最適な表示エクスペリエンスを得るには、 C++ Build Insights アドインを含む WPA のバージョンを使用します。 詳細については、「 [Build C++ Insights の概要](/cpp/build-insights/get-started-with-cpp-build-insights)」を参照してください。 |

## <a name="see-also"></a>参照

[ビルドインサイトC++\ を使って](/cpp/build-insights/get-started-with-cpp-build-insights)みる
[チュートリアル: Windows パフォーマンスアナライザーの基本](/cpp/build-insights/tutorials/wpa-basics)\
[リファレンス: Windows パフォーマンスアナライザーのビュー](wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
