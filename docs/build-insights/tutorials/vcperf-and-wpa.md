---
title: 'チュートリアル: vcperf と Windows パフォーマンスアナライザー'
description: Vcperf と WPA を使用してビルドトレースをC++分析する方法に関するチュートリアルです。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 091e366da9342f2561620d975ead2f01b5439bad
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334044"
---
# <a name="tutorial-vcperf-and-windows-performance-analyzer"></a>チュートリアル: vcperf と Windows パフォーマンスアナライザー

::: moniker range="<=vs-2017"

Visual C++ Studio 2019 では、Build Insights ツールを使用できます。 そのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range="vs-2019"

このチュートリアルでは、 *vcperf*を使用してC++ビルドのトレースを収集する方法について説明します。 また、Windows パフォーマンスアナライザーでこのトレースを表示する方法についても説明します。

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>手順 1: Windows パフォーマンスアナライザーをインストールして構成する

WPA は、Windows アセスメント & amp; デプロイメントキット (ADK) で利用可能なトレースビューアーです。 これは、Visual Studio インストーラーを使用してインストールできるコンポーネントの一部ではない、独立したユーティリティです。

現在、Build Insights をサポートC++するバージョンの WPA は、Windows ADK Insider Preview でのみ使用できます。 このプレビューにアクセスするには、 [Windows Insider program](https://insider.windows.com)にサインアップする必要があります。 Windows ADK preview を入手するために、Windows 10 Insider Preview オペレーティングシステムをインストールする必要はありません。 Microsoft アカウントを登録する必要があるのは、Windows Insider Program だけです。

### <a name="to-download-and-install-wpa"></a>WPA をダウンロードしてインストールするには

注: windows パフォーマンスアナライザーをインストールするには、Windows 8 以降が必要です。

1. Windows ADK Insider Preview[ダウンロードページ](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewADK)に移動します。

1. Windows ADK Insider Preview をダウンロードします。 ディスクイメージです。

1. ディスクイメージを開き、 *adksetup*インストーラーを実行します。

1. インストールする機能の入力を求められたら、 **[Windows パフォーマンスツールキット]** を選択します。 必要に応じて他の機能を選択することもできますが、WPA のインストールは必須ではありません。

   ![Windows Performance Analyzer インストーラーの [機能の選択] 画面](media/wpa-installation.png)

### <a name="configuration-steps"></a>ビルドインサイトを構成するには

1. WPA を起動します。

1. [テーブルの選択 **] > [** **テーブル (試験段階)** ] を選択します。

1. **[診断]** セクションまで下にスクロールします。

1. すべての MSVC Build Insights ビューを選択します。

   ![Windows Performance Analyzer のテーブル選択パネル](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>手順 2: vcperf を使用してビルドをトレースする

ビルドインC++サイトデータを表示するには、次の手順に従って、まずそのデータをトレースファイルに収集します。

1. 管理者モードで Visual Studio 2019 用のネイティブツールまたはクロスツール開発者コマンドプロンプトを開きます。 (スタート メニュー項目を右クリックし、**その他** > **管理者として実行** を選択します)。

1. コマンドプロンプトウィンドウで、次のコマンドを入力します。

   **vcperf の/start の_セッション名_**

   セッション*名を選択してください*。

1. 通常どおりにプロジェクトをビルドします。 同じコマンドプロンプトウィンドウを使用してビルドする必要はありません。

1. コマンドプロンプトウィンドウで、次のコマンドを入力します。

   **vcperf. ファイル_名_ _. .etl_**

   *前のセッション名に選択*したのと同じセッション名を使用します。 *Tracefile .etl*トレースファイルに適切な名前を選択します。

開発者コマンドプロンプトウィンドウで、一般的な*vcperf*コマンドシーケンスは次のようになります。

![単純な vcperf の使用シナリオ](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>Vcperf に関する重要な注意事項

- *Vcperf*のトレースを開始または停止するには、管理者特権が必要です。 **[管理者として実行]** を使用して開いた開発者コマンドプロンプトウィンドウを使用します。

- コンピューター上で実行できるトレースセッションは一度に1つだけです。

- トレースを開始するために使用したセッション名を忘れないようにしてください。 実行中のセッションを停止すると、名前がわからなくなることがあります。

- *Cl.exe*や setup.exe と同じよう*に、* コマンドラインユーティリティ*vcperf*は MSVC のインストールに含まれています。 このコンポーネントを取得するために追加の手順は必要ありません。

- *vcperf*は、システムで実行されているすべての MSVC ツールに関する情報を収集します。 その結果、トレースの収集に使用したのと同じコマンドプロンプトからビルドを開始する必要がなくなります。 プロジェクトは、別のコマンドプロンプトから、または Visual Studio でもビルドできます。

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>手順 3: Windows パフォーマンスアナライザーでトレースを表示する

WPA を起動し、先ほど収集したトレースを開きます。 WPA はこれをC++ Build Insights トレースとして認識し、左側のグラフエクスプローラーパネルに次のビューを表示する必要があります。

- ビルド エクスプローラー
- ファイル
- Function

これらのビューが表示されない場合は、[手順 1](#configuration-steps). で説明したように、WPA が正しく構成されていることを再確認します。 次に示すように、右側の空の分析ウィンドウにビューをドラッグすると、ビルドデータを表示できます。

![Windows Performance C++ Analyzer でのビルドインサイトトレースの表示](media/wpa-viewing-trace.gif)

その他のビューは、グラフエクスプローラーパネルで使用できます。 含まれている情報に関心がある場合は、それらを [分析] ウィンドウにドラッグします。 1つは CPU (サンプリングされた) ビューで、ビルド全体の CPU 使用率を示しています。

## <a name="more-information"></a>詳細情報

[チュートリアル: Windows パフォーマンスアナライザーの基本](wpa-basics.md)\
ビルドトレースの分析に役立つ一般的な WPA 操作について説明します。

[リファレンス: vcperf コマンド](/cpp/build-insights/reference/vcperf-commands)\
*Vcperf .exe*コマンドリファレンスには、使用可能なすべてのコマンドオプションが一覧表示されます。

[リファレンス: Windows パフォーマンスアナライザーのビュー](/cpp/build-insights/reference/wpa-views)\
WPA の Build Insights ビューの詳細にC++ついては、こちらの記事を参照してください。

[Windows パフォーマンスアナライザー](/windows-hardware/test/wpt/windows-performance-analyzer)の\
公式の WPA ドキュメントサイト。

::: moniker-end
