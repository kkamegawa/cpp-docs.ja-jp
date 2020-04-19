---
title: サポートされるプラットフォーム (Visual C++)
ms.date: 12/02/2019
ms.technology: cpp-tools
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
ms.openlocfilehash: 049b28d23c7f5f5f023f3b2964577b75992c2998
ms.sourcegitcommit: 5f276064779d90a4cfda758f89e0c0f1e4d1a188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2020
ms.locfileid: "75793831"
---
# <a name="supported-platforms-visual-c"></a>サポートされるプラットフォーム (Visual C++)

Visual Studio を使用してビルドしたアプリケーションは、次のようにさまざまなプラットフォームを対象にすることができます。

|オペレーティング システム|x86|X64|ARM|ARM64\*\*\*\*|
|----------------------|---------|---------|---------|---------|
|Windows XP|X\*|X\*|||
|Windows Server 2003|X\*|X\*|||
|Windows Vista|x|x|||
|Windows Server 2008|x|x|||
|Windows 7|x|x|||
|Windows Server 2012 R2|x|x|||
|Windows 8|x|x|x||
|Windows 8.1|x|x|x||
|Windows 10|x|x|x|x|
|Android \*\*|x|x|x|x|
|iOS \*\*|x|x|x|x|
|Linux \*\*\*|x|x|x|x|

\* Visual Studio 2017、Visual Studio 2015、Visual Studio 2013、および Visual Studio 2012 Update 1 に含まれている Windows XP プラットフォーム ツールセットを使用して、Windows XP および Windows Server 2003 プロジェクトを構築できます。 このプラットフォーム ツールセットを使用する方法については、「[Windows XP 用プログラムの構成](../build/configuring-programs-for-windows-xp.md)」を参照してください。 プラットフォーム ツールセットの変更に関する詳細は、「[方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する](../build/how-to-modify-the-target-framework-and-platform-toolset.md)」を参照してください。

\*\***C++ によるモバイル開発**ワークロードを Visual Studio 2017 以降用のインストーラーでインストールすることができます。 Visual Studio 2015 のセットアップで、オプションの**クロス プラットフォーム モバイル開発向け Visual C++** のコンポーネントを選択して、iOS または Android プラットフォームをターゲットにします。 手順については、「[クロス プラットフォーム モバイル開発用の Visual C++ のインストール](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development)」を参照してください。 iOS コードをビルドするには、Mac コンピューターがあり、他の要件を満たしている必要があります。 前提条件とインストール手順については、「[iOS を使用してビルドするためのツールのインストールおよび構成](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios)」を参照してください。 ターゲット ハードウェアに合わせて、x86 または ARM コードをビルドできます。 iOS シミュレーター、Microsoft Visual Studio Emulator for Android、一部の Android デバイスのビルドには x86 構成を使用します。 iOS デバイスとほとんどのデバイスのビルドには ARM 構成を使用します。

\*\*\***C++ による Linux 開発**ワークロードを Visual Studio 2017 以降用のインストーラーでインストールし、Linux プラットフォームをターゲットにすることができます。 方法については、「[Linux ワークロードのダウンロード、インストール、セットアップ](../linux/download-install-and-setup-the-linux-development-workload.md)」を参照してください。 このツールセットは、サポートされているあらゆるアーキテクチャでビルドできるように、ターゲット マシンで実行可能ファイルをコンパイルします。

\*\*\*\* ARM64 は Visual Studio 2017 以降でサポートされています。

対象プラットフォームの構成を設定する方法については、「[How to: Configure Visual C++ Projects to Target 64-Bit, x64 Platforms](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)」(方法: Visual C++ プロジェクトを 64 ビット、x64 プラットフォーム用に設定する) を参照してください。

## <a name="see-also"></a>関連項目

- [さまざまな Visual Studio エディションの Visual C++ ツールおよび機能](visual-cpp-tools-and-features-in-visual-studio-editions.md)
- [はじめに](/visualstudio/ide/getting-started-with-cpp-in-visual-studio)
