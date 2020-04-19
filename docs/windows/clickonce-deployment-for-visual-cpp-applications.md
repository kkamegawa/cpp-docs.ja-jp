---
title: Visual C++ アプリケーションの ClickOnce 配置
ms.date: 11/04/2016
helpviewer_keywords:
- deploying applications [C++], ClickOnce
- application deployment [C++], ClickOnce
- ClickOnce deployment [C++], C++ applications
ms.assetid: 9988c546-0936-452c-932f-9c76daa42157
ms.openlocfilehash: 4408db9d129c03ee5df9b006b03c6586df02afb1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513770"
---
# <a name="clickonce-deployment-for-visual-c-applications"></a>Visual C++ アプリケーションの ClickOnce 配置

Visual Studio では、Windows アプリケーションを配置するための 2 つのテクノロジを提供しています。ClickOnce による配置または [Windows インストーラーによる配置](/windows/win32/Msi/windows-installer-portal)です。

## <a name="clickonce-deployment-in-c"></a>C++ の ClickOnce 配置

ビジュアルC++開発環境では、ClickOnce を使用した visual C++ Studio プロジェクトの配置は直接サポートされていませんが、ツールを使用することができます。

> [!NOTE]
>  Visual Studio では Visual C# および Visual Basic の開発環境で ClickOnce をサポートします。 Visual Studio C++プロジェクトがビジュアルC#プロジェクトの依存関係である場合は、Visual C#開発環境から ClickOnce 配置を使用して、アプリケーション (依存関係を含む) を発行できます。

ClickOnce を使用して Visual C++ アプリケーションを配置するには、[Mage.exe (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool) またはそのグラフィカル ユーザー インターフェイス バージョン (詳細については「[MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)」を参照) を使用して、最初に [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)および [ClickOnce 配置マニフェスト](/visualstudio/deployment/clickonce-deployment-manifest)を作成する必要があります。

最初に、Mage.exe を使用してアプリケーション マニフェストをビルドします。作成されるファイルには拡張子 .manifest が付きます。 次に、Mage.exe を使用して配置マニフェストをビルドします。作成されるファイルには拡張子 .application が付きます。 次にマニフェストに署名します。

アプリケーション マニフェストでは、対象となるプロセッサ (**x86**、**x64**、または **ARM**) を指定する必要があります。 これらのオプションの詳細については、「[64 ビット アプリケーションの配置のための必要条件](/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications)」を参照してください。

また、アプリケーション マニフェストと配置マニフェストの名前は C++ アプリケーションの名前と異なっている必要があります。 これによって、Mage.exe で作成されるアプリケーション マニフェストと C++ アプリケーションの一部である外部マニフェストの間の競合を回避できます。

配置では、アプリケーションが依存する Visual C++ ライブラリをインストールする必要があります。 特定のアプリケーションの依存関係を確認するには、depends.exe または DUMPBIN ユーティリティを /DEPENDENTS オプションと共に使用します。 依存関係の詳細については、「[Visual C++ アプリケーションの依存関係の理解](understanding-the-dependencies-of-a-visual-cpp-application.md)」を参照してください。 VCRedist.exe の実行が必要な場合もあります。このユーティリティはターゲット コンピューターに Visual C++ ライブラリをインストールします。

さらに、アプリケーションが必須コンポーネントを配置するために、ブートストラップ (必須コンポーネント インストーラー) をビルドする必要があることもあります。ブートストラップの詳細については、「[ブートストラップ パッケージの作成](/visualstudio/deployment/creating-bootstrapper-packages)」を参照してください。

テクノロジの詳細については、「[ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)」を参照してください。 ClickOnce 配置の詳細な例については、「[Walkthrough:Manually Deploying a ClickOnce Application](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)」(チュートリアル: ClickOnce アプリケーションを手動で配置する) を参照してください。

## <a name="see-also"></a>関連項目

[Mage.exe (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)<br>
[MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)<br>
[Makecert.exe (証明書作成ツール)](/windows/win32/SecCrypto/makecert)<br>
[デスクトップ アプリケーションの配置](deploying-native-desktop-applications-visual-cpp.md)<br>
[アプリケーション、サービス、およびコンポーネントの配置](/visualstudio/deployment/deploying-applications-services-and-components)<br>
[ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[ブートストラップ パッケージの作成](/visualstudio/deployment/creating-bootstrapper-packages)<br>
[C++/CLI (Visual C++) による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br>
[ネイティブと .NET の相互運用性](../dotnet/native-and-dotnet-interoperability.md)
