---
title: C++プロパティページのデバッグ
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 78115a6b-3799-4515-814e-8566b5bdc55d
f1_keywords:
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCLocalDebugPageObject.AmpDefaultAccelerator
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.Environment
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.AmpDefaultAccelerator
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
ms.openlocfilehash: 5f7a7bc0e2c696365daa38696fde6f1a480644b4
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927733"
---
# <a name="c-debugging-property-pages"></a>C++プロパティページのデバッグ

これらのプロパティページは、[**プロジェクト** > の**プロパティ** > ] [**構成プロパティ** > ] **[デバッグ]** の下にあります。 ドロップダウンコントロールでデバッガーの種類を選択します。 コードのデバッグC++の詳細について[は、「チュートリアル:Visual Studio](/visualstudio/debugger/getting-started-with-the-debugger-cpp)をC++使用してコードをデバッグし、[ネイティブコードをデバッグ](/visualstudio/debugger/debugging-native-code)する方法について説明します。

## <a name="local-windows-debugger-property-page"></a>[ローカル Windows デバッガー] プロパティページ

### <a name="command"></a>コマンド

実行するデバッグ コマンドです。

### <a name="command-arguments"></a>コマンド引数

アプリケーションに渡すコマンドライン引数。

### <a name="working-directory"></a>作業ディレクトリ

アプリケーションの作業ディレクトリ。 既定では、プロジェクトファイルが格納されているディレクトリです。

### <a name="attach"></a>Attach

デバッグの開始時に、デバッガーを既存のプロセスにアタッチするかどうかを指定します。

### <a name="debugger-type"></a>デバッガーの種類

使用するデバッガーの種類を指定します。 [自動] に設定した場合、デバッガーの種類は exe ファイルの内容に基づいて選択されます。

**いずれ**

- **ネイティブのみ**-ネイティブのみ
- **マネージのみ**-マネージドのみ
- **Mixed** -mixed
- **自動**-自動
- **スクリプト**-スクリプト
- **GPU のみ (C++ amp)** -gpu のみ (C++ amp)

### <a name="environment"></a>環境

デバッグするプログラムの環境、または既存の環境とマージする変数を指定します。

### <a name="debugging-accelerator-type"></a>デバッグアクセラレータの種類

GPU コードのデバッグに使用するデバッグアクセラレータの種類。 (GPU デバッガーがアクティブなときに使用できます。)

### <a name="gpu-default-breakpoint-behavior"></a>GPU の既定のブレークポイントの動作

GPU デバッガーが中断する頻度を設定します。

**いずれ**

- ワープごとに 1**回中断**-ワープごとに1回中断
- **すべてのスレッド (cpu の動作など) の中断**-すべてのスレッドで中断 (cpu の動作など)

### <a name="merge-environment"></a>マージ環境

指定された環境変数を既存の環境にマージします。

### <a name="sql-debugging"></a>SQL デバッグ

SQL デバッガーをアタッチします。

### <a name="amp-default-accelerator"></a>AMP の既定のアクセラレータ

AMP C++の既定のアクセラレータの選択をオーバーライドします。 マネージコードをデバッグする場合、プロパティは適用されません。

## <a name="remote-windows-debugger-property-page"></a>[リモート Windows デバッガー] プロパティページ

リモートデバッグの詳細については、「 [Visual Studio C++での Visual プロジェクトのリモートデバッグ](/visualstudio/debugger/remote-debugging-cpp)」を参照してください。

### <a name="remote-command"></a>リモート コマンド

実行するデバッグ コマンドです。

### <a name="remote-command-arguments"></a>リモート コマンド引数

アプリケーションに渡すコマンドライン引数。

### <a name="working-directory"></a>作業ディレクトリ

アプリケーションの作業ディレクトリ。 既定では、プロジェクトファイルが格納されているディレクトリです。

### <a name="remote-server-name"></a>リモート サーバー名

リモートサーバー名を指定します。

### <a name="connection"></a>Connection

接続の種類を指定します。

**いずれ**

- **Windows 認証を使用したリモート**- [windows 認証](/windows-server/security/windows-authentication/windows-authentication-overview)を使用したリモート。
- **認証なしのリモート**-認証なし。

### <a name="debugger-type"></a>デバッガーの種類

使用するデバッガーの種類を指定します。 [自動] に設定した場合、デバッガーの種類は exe ファイルの内容に基づいて選択されます。

**いずれ**

- **ネイティブのみ**-ネイティブのみ
- **マネージのみ**-マネージドのみ
- **Mixed** -mixed
- **自動**-自動
- **スクリプト**-スクリプト
- **GPU のみ (C++ amp)** -gpu のみ (C++ amp)

### <a name="environment"></a>環境

デバッグするプログラムの環境、または既存の環境とマージする変数を指定します。

### <a name="debugging-accelerator-type"></a>デバッグアクセラレータの種類

GPU コードのデバッグに使用するデバッグアクセラレータの種類。 (GPU デバッガーがアクティブなときに使用できます。)

### <a name="gpu-default-breakpoint-behavior"></a>GPU の既定のブレークポイントの動作

GPU デバッガーが中断する頻度を設定します。

**いずれ**

- ワープごとに 1**回中断**-ワープごとに1回中断
- **すべてのスレッド (cpu の動作など) の中断**-すべてのスレッドで中断 (cpu の動作など)

### <a name="attach"></a>Attach

デバッグの開始時に、デバッガーを既存のプロセスにアタッチするかどうかを指定します。

### <a name="sql-debugging"></a>SQL デバッグ

SQL デバッガーをアタッチします。

### <a name="deployment-directory"></a>配置ディレクトリ

リモートコンピューターでデバッグする場合、プロジェクト出力の内容 (PDB ファイルを除く) をリモートコンピューターにコピーするには、ここでパスを指定します。

### <a name="additional-files-to-deploy"></a>追加の配置ファイル

リモートコンピューターでデバッグする場合、ここで指定したファイルとディレクトリ (プロジェクト出力を除く) が配置ディレクトリにコピーされます (指定されている場合)。

### <a name="deploy-visual-c-debug-runtime-libraries"></a>Visual C++ デバッグ ランタイム ライブラリの配置

アクティブなプラットフォーム (Win32、x64、または ARM) 用のデバッグランタイムライブラリを配置するかどうかを指定します。

### <a name="amp-default-accelerator"></a>AMP の既定のアクセラレータ

AMP C++の既定のアクセラレータの選択をオーバーライドします。 マネージコードをデバッグする場合、プロパティは適用されません。

## <a name="web-browser-debugger-property-page"></a>[Web ブラウザーデバッガー] プロパティページ

### <a name="http-url"></a>HTTP URL

プロジェクトの URL を指定します。

### <a name="debugger-type"></a>デバッガーの種類

使用するデバッガーの種類を指定します。 [自動] に設定した場合、デバッガーの種類は exe ファイルの内容に基づいて選択されます。

**いずれ**

- **ネイティブのみ**-ネイティブのみ
- **マネージのみ**-マネージドのみ
- **Mixed** -mixed
- **自動**-自動
- **スクリプト**-スクリプト

## <a name="web-service-debugger-property-page"></a>[Web サービスデバッガー] プロパティページ

### <a name="http-url"></a>HTTP URL

プロジェクトの URL を指定します。

### <a name="debugger-type"></a>デバッガーの種類

使用するデバッガーの種類を指定します。 [自動] に設定した場合、デバッガーの種類は exe ファイルの内容に基づいて選択されます。

**いずれ**

- **ネイティブのみ**-ネイティブのみ
- **マネージのみ**-マネージドのみ
- **Mixed** -mixed
- **自動**-自動
- **スクリプト**-スクリプト

### <a name="sql-debugging"></a>SQL デバッグ

SQL デバッガーをアタッチします。