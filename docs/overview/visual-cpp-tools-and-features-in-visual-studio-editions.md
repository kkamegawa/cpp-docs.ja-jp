---
title: さまざまな Visual Studio エディションの C++ ツールと機能
ms.date: 05/21/2019
helpviewer_keywords:
- tools and platforms [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: a7514e5cc52b24740b82cc067e77955c4784c9f0
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400639"
---
# <a name="c-tools-and-features-in-visual-studio-editions"></a>さまざまな Visual Studio エディションの C++ ツールと機能


::: moniker range=">=vs-2019"


次の C++ 機能を Visual Studio 2019 で使用できます。 特に示されていない限り、すべての機能をすべてのエディションで使用できます。Visual Studio Community、Visual Studio Professional、Visual Studio Enterprise。 一部の機能には、特定のワークロードまたはオプション コンポーネントが必要です。これは、Visual Studio インストーラーを使ってインストールできます。

## <a name="platforms"></a>プラットフォーム

- Windows デスクトップ
- ユニバーサル Windows プラットフォーム ((タブレット、PC、Xbox、IoT、HoloLens))
- Linux
- Android
- iOS

## <a name="compilers"></a>コンパイラ

- x86、x64、ARM、ARM64 用の MSVC 32 ビット コンパイラ
- x86、x64、ARM、ARM64 用の MSVC 64 ビット コンパイラ
- ARM 用の GCC クロス コンパイラ
- Clang/LLVM
  - Windows 上の x86 または x64 を対象とする Clang/LLVM 7.0 (CMake サポートのみ)。 その他の Clang バージョンは機能しますが、公式にはサポートされません。
  - Linux 上で配布によってサポートされる任意の Clang/LLVM インストール。
 
## <a name="c-workloads"></a>C++ ワークロード

Visual Studio には C++ 開発に対して次のワークロードが含まれます。 .NET デスクトップ開発、Python 開発、Azure の開発、Visual Studio 拡張機能の開発など、その他のワークロードと共に、これらの一部またはすべてをインストールできます。

### <a name="desktop-development-with-c"></a>C++ によるデスクトップ開発

対象:
- C++ コア デスクトップ機能

オプション コンポーネント:
- MSVC v142 - VS 2019 C++ x64/x86 ビルド ツール (v14.21)
- Windows 10 SDK (10.0.17763.0)
- Just-In-Time デバッガー
- C++ のプロファイル ツール
- Windows 用 C++ CMake ツール
- v142 ビルド ツールの C++ ATL (x86 & x64)
- Test Adapter for Boost.Test
- Test Adapter for Google Test
- Live Share
- IntelliCode
- IntelliTrace (Enterprise のみ)
- v142 ビルド ツールの C++ MFC (x86 & x64)
- v142 ビルド ツールの C++/CLI サポート (14.21)
- v142 ビルド ツール用の C++ モジュール (x64/x86 – 実験)
- Windows 用 Clang コンパイラ
- IncrediBuild - ビルド アクセラレーション
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- MSVC v141 - VS 2017 C++ x64/x86 ビルド ツール (v14.16)
- MSVC v140 - VS 2015 C++ ビルド ツール (v14.00)

### <a name="linux-development-with-c"></a>C++ による Linux 開発

対象:
- C++ コア機能
- Windows ユニバーサル C ランタイム
- Linux 開発用 C++

オプション コンポーネント:
- Linux 用の C++ CMake ツール
- 埋め込み開発ツールと IoT 開発ツール

### <a name="universal-windows-platform-development"></a>ユニバーサル Windows プラットフォーム開発

対象:
- Blend for Visual Studio
- .NET ネイティブと .NET Standard
- NuGet パッケージ マネージャー
- ユニバーサル Windows プラットフォーム ツール
- Windows 10 SDK (10.0.17763.0)

オプション コンポーネント:
- IntelliCode
- IntelliTrace (Enterprise のみ)
- USB デバイスの接続
- C++ (v142) ユニバーサル Windows プラットフォーム ツール
- C++ (v141) ユニバーサル Windows プラットフォーム ツール
- DirectX 用グラフィックス デバッガーおよび GPU プロファイラー
- Windows 10 SDK (10.0.18362.0)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- アーキテクチャおよび分析ツール

### <a name="c-game-development"></a>C++ ゲーム開発

対象:
- C++ コア機能
- Windows ユニバーサル C ランタイム
- C++ 2019 再頒布可能パッケージの更新プログラム
- MSVC v142 - VS 2019 C++ x64/x86 ビルド ツール (v14.21)

オプション コンポーネント:
- C++ のプロファイル ツール
- Windows 10 SDK (10.0.17763.0)
- IntelliCode
- IntelliTrace (Enterprise のみ)
- Windows 10 SDK (10.0.17134.0)
- Windows 10 SDK (10.0.16299.0)
- IncrediBuild - ビルド アクセラレーション
- Cocos
- Unreal Engine のインストーラー
- Unreal Engine 用の Android IDE サポート

### <a name="mobile-development-with-c"></a>C++ でのモバイル開発

対象:
- C++ コア機能
- Android SDK セットアップ (API レベル 25) (C++ を使用したモバイル開発のためにローカルにインストール)

オプション コンポーネント:
- Android NDK (R16B)
- Apache Ant (1.9.3)
- C++ Android 開発ツール
- IntelliCode
- Google Android Emulator (API レベル 25) (ローカル インストール)
- Intel Hardware Accelerated Execution Manager (HAXM) (ローカル インストール)
- Android NDK (R16B) (32 ビット)
- C++ iOS 開発ツール
- IncrediBuild - ビルド アクセラレーション


## <a name="individual-components"></a>個々のコンポーネント

任意のワークロードからこれらのコンポーネントを個別にインストールできます。

- JavaScript 診断
- Live Share
- v142 ビルド ツールの C++ ユニバーサル Windows プラットフォーム ランタイム
- ClickOnce Publishing
- Microsoft Visual Studio インストーラー プロジェクト

## <a name="libraries-and-headers"></a>ライブラリおよびヘッダー

- Windows ヘッダーおよびライブラリ
- Windows ユニバーサル C ランタイム (CRT)
- C++ 標準ライブラリ
- ATL
- MFC
- .NET Framework クラス ライブラリ
- .NET 用 C++ サポート ライブラリ
- OpenMP 2.0
- vcpkg カタログ経由の 900 個を超えるオープンソース ライブラリ

## <a name="build-and-project-systems"></a>ビルド システムとプロジェクト システム

- CMake
- [フォルダーを開く] による任意のビルド システム
- コマンド ライン ビルド (msbuild.exe)
- ネイティブ マルチ ターゲット
- マネージド マルチ ターゲット
- 平行ビルド
- カスタマイズのビルド
- プロパティ ページの機能拡張

## <a name="project-templates"></a>プロジェクト テンプレート

次のプロジェクト テンプレートは、インストールしたワークロードによって利用できるものが異なります。

Windows デスクトップ:
- 空のプロジェクト
- コンソール アプリ
- Windows デスクトップ ウィザード
- Windows デスクトップ アプリケーション
- 共有アイテム プロジェクト
- MFC アプリ
- ダイナミック リンク ライブラリ
- CLR 空プロジェクト
- CLR コンソール アプリ
- スタティック ライブラリ
- CMake プロジェクト
- ATL プロジェクト
- MFC ダイナミック リンク ライブラリ
- CLR クラス ライブラリ
- メイクファイル プロジェクト (Windows)
- MFC ActiveXControl
- ネイティブ単体テスト プロジェクト
- Google Test

ユニバーサル Windows プラットフォーム (C++/CX):
- 空のアプリケーション
- DirectX 11 および XAML アプリ
- DirectX 11 アプリ
- DirectX 12 アプリ 
- 単体テスト アプリ 
- [DLL] 
- Windows ランタイム コンポーネント 
- スタティック ライブラリ 
- Windows アプリケーション パッケージ プロジェクト

Linux の場合:
- コンソール アプリ (Linux)
- 空のプロジェクト (Linux)
- Raspberry Pi Blink
- メイクファイル プロジェクト (Linux)

## <a name="tools"></a>ツール

- インクリメンタル リンカー (Link.exe)
- Microsoft メイクファイル ユーティリティ (Nmake.exe)
- Lib ジェネレーター (Lib.exe)
- Windows リソース コンパイラ (Rc.exe)
- Windows Resource to Object Converter (CvtRes.exe)
- Browse Information Maintenance Utility (BscMake.exe)
- C++ Name Undecorator (Undname.exe)
- COFF/PE Dumper (Dumpbin.exe)
- COFF/PE Editor (Editbin.exe)
- MASM (Ml.exe)
- Spy++
- ErrLook
- AtlTrace
- 推論規則
- ガイド付き最適化のプロファイル

## <a name="debugging-features"></a>デバッグ機能

- ネイティブ デバッグ
- natvis (ネイティブ型の視覚エフェクト)
- グラフィックスのデバッグ
- マネージド デバッグ
- GPU 使用率
- メモリ使用量
- Remote Debugging
- SQL デバッグ
- スタティック コード分析

## <a name="designers-and-editors"></a>デザイナーおよびエディター

- XAML デザイナー
- CSS スタイル デザイナー/エディター
- HTML デザイナー/エディター
- XML エディター
- ソース コード エディター
- 生産性機能: リファクタリング、EDG IntelliSense エンジン、C++ コードの書式設定
- Windows フォーム デザイナー
- データ デザイナー
- ネイティブ リソース エディター (.rc ファイル)
- リソース エディター
- モデル エディター
- シェーダー デザイナー
- ライブ依存関係検証 (Enterprise のみ)
- アーキテクチャ レイヤー図 (Enterprise のみ)
- アーキテクチャの検証 (Enterprise のみ)
- コード クローン (Enterprise のみ)

## <a name="data-features"></a>データ機能

- データ デザイナー
- データ オブジェクト
- Web サービス
- サーバー エクスプローラー

## <a name="automation-and-extensibility"></a>オートメーションおよび機能拡張

- 機能拡張オブジェクト モデル
- コード モデル
- プロジェクト モデル
- リソース エディター モデル
- ウィザード モデル
- デバッガー オブジェクト モデル

## <a name="application-lifecycle-management-tools"></a>アプリケーション ライフサイクル管理ツール

- 単体テスト (Microsoft Native C++、Boost.Test、Google Test、CTest)
- コード マップと依存関係グラフ (Professional と Enterprise)
- コード カバレッジ (Enterprise のみ)
- 手動テスト (Enterprise のみ)
- 探索的テスト (Enterprise のみ)
- テスト ケースの管理 (Enterprise のみ)
- コード マップ デバッガーの統合 (Enterprise のみ)
- Live Unit Testing (Enterprise のみ)
- IntelliTrace (Enterprise のみ)
- IntelliTest (Enterprise のみ)
- Microsoft Fakes (単体テストの分離) (Enterprise のみ)
- コード カバレッジ (Enterprise のみ)

## <a name="see-also"></a>関連項目

[Visual Studio のインストール](/visualstudio/install/install-visual-studio)<br/>
[Visual Studio の新機能](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Visual Studio の C++ プロジェクトの種類](../build/reference/visual-cpp-project-types.md)

::: moniker-end

::: moniker range="<=vs-2017"

Visual Studio 2017 で使用できる Visual C++ の機能を次の表に示します。 セル内の X は機能が使用できることを示し、空のセルは機能が使用できないことを示します。 かっこ内の説明は機能が制限付きで使用できることを示します。

## <a name="platforms"></a>プラットフォーム

||||||
|-|-|-|-|-|
|プラットフォーム|Visual Studio Express for Windows 10|Visual Studio Express for Windows Desktop|Visual Studio Community/Professional|Visual Studio Enterprise|
|Windows デスクトップ||x|x|x|
|ユニバーサル Windows プラットフォーム ((電話、タブレット、PC、Xbox、IoT、HoloLens))|x||x|x|
|Linux|x|x|
|Microsoft ストア 8.1|||x|x|
|Windows Phone 8.0|||x|x|
|Android|||x|x|
|iOS|||x|x|

## <a name="compilers"></a>コンパイラ

|コンパイラ|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|MSVC 32 ビット X86 コンパイラ|x|x|x|x|
|X86_arm cross-compiler|x||x|x|
|MSVC 64 ビット x64 コンパイラ|||x|x|
|X86_ x64 クロス コンパイラ|x|x|x|x|

## <a name="libraries-and-headers"></a>ライブラリおよびヘッダー

|ライブラリまたはヘッダー|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Windows ヘッダー、ライブラリ、CRT ライブラリ|(X)|x|x|x|
|C++ 標準ライブラリ|x|x|x|x|
|ATL|||x|x|
|MFC|||x|x|
|.NET Framework クラス ライブラリ||x|x|x|
|.NET 用 C++ サポート ライブラリ||x|x|x|
|OpenMP 2.0|x|x|x|x|

## <a name="project-templates"></a>プロジェクト テンプレート

|テンプレート|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|UWP、Windows 8.1、Windows Phone 8.0 向け XAML テンプレート|x||x|x|
|Direct3D アプリケーション|x||x|x|
|DLL (ユニバーサル Windows)|x||x|x|
|スタティック ライブラリ (ユニバーサル Windows)|x||x|x|
|Windows ランタイム コンポーネント|x||x|x|
|単体テスト アプリ (ユニバーサル Windows)|x||x|x|
|ATL プロジェクト|||x|x|
|クラス ライブラリ (CLR)||x|x|x|
|CLR コンソール アプリケーション||x|x|x|
|CLR 空プロジェクト||x|x|x|
|カスタム ウィザード|||x|x|
|空のプロジェクト||x|x|x|
|メイクファイル プロジェクト||x|x|x|
|MFC ActiveX コントロール|||x|x|
|MFC アプリケーション|||x|x|
|MFC DLL|||x|x|
|テスト プロジェクト|x|x|x|x|
|Win32 コンソール アプリケーション||x|x|x|
|Win32 プロジェクト||x|x|x|

## <a name="tools"></a>ツール

|ツール|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|インクリメンタル リンカー (Link.exe)|x|x|x|x|
|Program Maintenance Utility (Nmake.exe)||x|x|x|
|Lib ジェネレーター (Lib.exe)|x|x|x|x|
|Windows リソース コンパイラ (Rc.exe)|x|x|x|x|
|Windows Resource to Object Converter (CvtRes.exe)||x|x|x|
|Browse Information Maintenance Utility (BscMake.exe)|x|x|x|x|
|C++ Name Undecorator (Undname.exe)|x|x|x|x|
|COFF/PE Dumper (Dumpbin.exe)|x|x|x|x|
|COFF/PE Editor (Editbin.exe)|x|x|x|x|
|MASM (Ml.exe)|||x|x|
|Spy++|||x|x|
|ErrLook|||x|x|
|AtlTrace|||x|x|
|Devenv.com|||x|x|
|推論規則|||x|x|
|VCBuild .vcproj プロジェクトの MSBuild (VCUpgrade.exe) へのアップグレード|x|x|x|x|
|ガイド付き最適化のプロファイル|||x|x|

## <a name="debugging-features"></a>デバッグ機能

|デバッグ機能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|ネイティブ デバッグ|x|x|x|x|
|natvis (ネイティブ型の視覚エフェクト)|x|x|x|x|
|グラフィックスのデバッグ|x||x|x|
|マネージド デバッグ||x|x|x|
|GPU 使用率|x||x|x|
|メモリ使用量|x||x|x|
|Remote Debugging|x|x|x|x|
|SQL デバッグ|||x|x|
|スタティック コード分析|制限|制限|x|x|

## <a name="designers-and-editors"></a>デザイナーおよびエディター

|デザイナーまたはエディター|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|XAML デザイナー|x||x|x|
|CSS スタイル デザイナー/エディター|x|x|x|x|
|HTML デザイナー/エディター|x|x|x|x|
|XML エディター|x|x|x|x|
|ソース コード エディター|x|x|x|x|
|生産性機能: リファクタリング、IntelliSense、C++ コードの書式設定|x|x|x|x|
|Windows フォーム デザイナー||x|x|x|
|データ デザイナー|||x|x|
|ネイティブ リソース エディター (.rc ファイル)|||x|x|
|リソース エディター|x|x|x|x|
|モデル エディター|x||x|x|
|シェーダー デザイナー|x||x|x|

## <a name="data-features"></a>データ機能

|データ機能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|データ デザイナー|||x|x|
|データ オブジェクト|||x|x|
|Web サービス|||x|x|
|サーバー エクスプローラー|||x|x|

## <a name="build-and-project-systems"></a>ビルド システムとプロジェクト システム

|ビルドまたはプロジェクトの機能|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|コマンド ライン ビルド (msbuild.exe)|x|x|x|x|
|ネイティブ マルチ ターゲット||x|x|x|
|マネージド マルチ ターゲット||x|x|x|
|平行ビルド|x|x|x|x|
|カスタマイズのビルド|x|x|x|x|
|プロパティ ページの機能拡張|x|x|x|x|

## <a name="automation-and-extensibility"></a>オートメーションおよび機能拡張

|オートメーションおよび機能拡張|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|機能拡張オブジェクト モデル|||x|x|
|コード モデル|||x|x|
|プロジェクト モデル|||x|x|
|リソース エディター モデル|||x|x|
|ウィザード モデル|||x|x|
|デバッガー オブジェクト モデル|||x|x|

## <a name="application-lifecycle-management-tools"></a>アプリケーション ライフサイクル管理ツール

||||||
|-|-|-|-|-|
|ツール|Visual Studio Express for Windows|Visual Studio Express for Windows Desktop|Visual Studio Professional/Community|Visual Studio Enterprise|
|単体テスト (ネイティブ フレームワーク)|x|x|x|x|
|単体テスト (マネージド フレームワーク)||x|x|x|
|コード カバレッジ||||x|
|手動テスト||||x|
|探索的テスト||||x|
|テスト ケース管理||||x|
|コード マップと依存関係グラフ|||読み取り専用|x|
|コード マップ デバッグ||||x|

## <a name="see-also"></a>関連項目

[Visual Studio のインストール](/visualstudio/install/install-visual-studio)<br/>
[Visual Studio の新機能](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Visual Studio の C++ プロジェクトの種類](../build/reference/visual-cpp-project-types.md)

::: moniker-end
