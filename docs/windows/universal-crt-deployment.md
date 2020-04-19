---
title: ユニバーサル CRT の配置
ms.date: 05/11/2018
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
ms.openlocfilehash: 1f6e685cca65c4b31ac2e6147341c4b5a3fe8228
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344453"
---
# <a name="universal-crt-deployment"></a>ユニバーサル CRT の配置

Visual Studio .NET から Visual Studio 2013 では、各メジャー リリースの C++ コンパイラとツールに、新しいスタンドアロン バージョンの Microsoft C ランタイム (CRT) ライブラリが組み込まれました。 これらのスタンドアロン バージョンの CRT は互いに独立しており、程度の差はありますが、互換性はありませんでした。 たとえば、Visual Studio 2012 で使用される CRT ライブラリはバージョン 11 (名前は msvcr110.dll ) で、Visual Studio 2013 で使用される CRT はバージョン 12 (名前は msvcr120.dll) でした。 Visual Studio 2015 以降、できなくなった場合。 Visual Studio 2015 以降のバージョンの Visual Studio ではすべて 1 つのユニバーサル CRT を使用します。

ユニバーサル CRT は、Windows 10 オペレーティング システムの一部として含まれている Microsoft Windows オペレーティング システム コンポーネントです。 Windows Update を使用して以前のオペレーティング システムを Windows 8.1、Windows Vista の使用可能なは。 Universal CRT のローカル配置がサポート、いくつかの制限されます。

## <a name="central-deployment"></a>集中配置

ユニバーサル CRT を集中インストールするための推奨される方法は、Microsoft Windows Update を使用することです。 ユニバーサル CRT は、サポートされるすべての Microsoft Windows オペレーティング システムに対して推奨される更新プログラムです。したがって、既定では、ほとんどのコンピューターで通常の更新プロセスの一環としてインストールされます。 Universal CRT の最初のリリースが[KB2999226](https://support.microsoft.com/kb/2999226)します。 さまざまなバグ修正と以降の更新プログラムがで行われた[KB3118401](https://support.microsoft.com/kb/3118401)、さらにバグ修正と新機能の追加の更新プログラムがあったとします。 より新しい更新プログラムについては、[support.microsoft.com](https://support.microsoft.com) で Universal C ランタイムまたはユニバーサル CRT を検索してください。

すべての Microsoft Windows コンピューターで Windows Update を使用して定期的に更新プログラムがインストールされるわけではありません。一部のコンピューターでは推奨される更新プログラムがすべてインストールされない場合があります。 Visual Studio 2015 を使用してビルドし、後でアプリケーションの使用をサポートするC++ツールセットそれらのコンピューターのユニバーサル CRT 再頒布可能ファイルがオフラインの配布可能です。 それらの再頒布可能ファイルは、サポート技術情報へのリンクのいずれかからダウンロードできます。 再頒布可能パッケージの Universal CRT では、マシンが現在の service pack に更新されたことが必要です。 したがって、たとえば、Windows 7 用の再頒布可能パッケージは、Windows 7 RTM ではなく、Windows 7 SP1 にのみインストールされます。

ユニバーサル CRT がの基本的な依存関係であるため、C++ライブラリ、ビジュアルC++再頒布可能パッケージ (VCRedist) がインストールされているいずれかが設定されていないマシンでユニバーサル CRT (バージョン 10.0.10240) の最初のバージョンをインストールします。 このバージョンでは満たすために、C++ライブラリの依存関係。 Universal CRT のより新しいバージョンに依存するアプリケーション場合、は、Windows Update を使用して、完全に最新の状態でマシンを移行またはそのバージョンを明示的にインストールする必要があります。 再起動に必要な潜在的な複数を回避するために、VCRedist をインストールする前に、Windows Update または MSU を使用して、ユニバーサル C ランタイムをインストールすることをお勧めします。

すべてのオペレーティング システムでは、Windows Update を使用して、最新のユニバーサル C ランタイムの対象です。 Windows 10 で一元的に展開されているバージョンは、オペレーティング システムのバージョンと一致します。 さらに、ユニバーサル C ランタイムを更新するには、オペレーティング システムを更新する必要があります。 Windows 8.1 から Windows Vista では、最新使用可能なユニバーサル C ランタイムは現在な追加の修正プログラム (バージョン 10.0.14393)、Windows 10 Anniversary Update に含まれるバージョンに基づきます。

## <a name="local-deployment"></a>ローカル配置

ユニバーサル CRT のローカル配置はサポートされていますが、パフォーマンスとセキュリティの両方の理由から推奨されません。 ローカル配置用の DLL は Windows SDK の一部として、コンピューター アーキテクチャ固有の、Windows Kits\\10\\Redist\\ucrt\\DLLs のサブディレクトリに含まれています。 必要な DLL には、ucrtbase.dll、および api-ms-win-\*.dll という名前の APISet forwarder DLL のセットなどがあります。 各オペレーティング システムで必要な Dll のセットが異なります。 ローカルでデプロイするときにすべての Dll を含めることを強くお勧めします。

ローカル配置の場合は、次の 2 つの制限事項に注意してください。

- Windows 10 では、アプリケーションにユニバーサル CRT のアプリケーションのローカル コピーが含まれている場合でも、システム ディレクトリのユニバーサル CRT が常に使用されます。 Universal CRT はコア オペレーティング システムのコンポーネントを Windows 10 であるために、ローカルのコピーが新しい場合にも true です。

- Windows 8 の前に Windows のバージョンでは、Universal CRT パッケージ化できませんローカル プラグインをメイン アプリの実行可能ファイルのディレクトリ以外のディレクトリにある場合。 この場合、APISet forwarder DLL で ucrtbase.dll を正常に解決することはできません。 推奨される代替ソリューションをいくつか以下に示します。

  - ユニバーサル CRT を静的にリンクする。
  - ユニバーサル CRT を集中配置する。
  - アプリと同じディレクトリにユニバーサル CRT ファイルを配置する。

## <a name="deployment-on-microsoft-windows-xp"></a>Microsoft Windows XP での配置

Visual Studio 2015 と Visual Studio 2017 では、Microsoft Windows XP で使用されるソフトウェアの開発が引き続きサポートされます。 この開発をサポートするために、ユニバーサル CRT のバージョンが Microsoft Windows XP で機能します。 Microsoft Windows XP オペレーティング システムはメインストリーム サポートや延長サポートの対象外となったため、Microsoft Windows XP へのユニバーサル CRT の集中配置は他のオペレーティング システムとは異なります。

ときに、ビジュアルC++再頒布可能パッケージがインストールされている Windows xp、直接 Universal CRT とその依存関係のすべてをシステム ディレクトリにインストールします。 インストールは、任意の Windows 更新プログラムに依存またはことができます。 再頒布可能マージ モジュールの Microsoft_VC*バージョン*_CRT_\*.msm でも同様です。

Windows XP でのユニバーサル CRT のローカル配置は、サポートされている他のオペレーティング システムの場合と同じです。

## <a name="see-also"></a>関連項目

- [Visual C++ での配置](deployment-in-visual-cpp.md)
