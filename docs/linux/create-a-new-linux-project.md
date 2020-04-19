---
title: Visual Studio で新しい C++ Linux プロジェクトを作成する
ms.date: 10/24/2019
description: Visual Studio で新しい MSBuild ベースの Linux プロジェクトを作成します。
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 5d5fa67566d86edb2ed0389fdbe38866b47e2211
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626718"
---
# <a name="create-a-new-linux-project"></a>新しい Linux プロジェクトを作成する

::: moniker range="vs-2015"

Linux プロジェクトは Visual Studio 2017 以降で使用できます。

::: moniker-end

::: moniker range="vs-2017"

最初に、Visual Studio 対応の **Linux 開発ワークロード**を必ずインストールします。 詳細については、「[Linux ワークロードのダウンロード、インストール、セットアップ](download-install-and-setup-the-linux-development-workload.md)」を参照してください。

クロスプラットフォーム コンパイルの場合は、CMake を使用することをお勧めします。 CMake のサポートは、Visual Studio 2019 の方がより進んでいます。 CMake がオプションではなく、既存の Windows Visual Studio ソリューションを Linux 用のコンパイルのために拡張したい場合は、Visual Studio Linux プロジェクトを**共有項目**プロジェクトと共に Windows ソリューションに追加することができます。 共有項目プロジェクトの両方のプラットフォーム間で共有されるコードを配置し、そのプロジェクトへの参照を Windows および Linux プロジェクトから追加します。

## <a name="to-create-a-new-linux-project"></a>新しい Linux プロジェクトを作成するには

Visual Studio 2017 で新しい Linux プロジェクトを作成するには、次のように操作します。

1. Visual Studio で **[ファイル]、[新しいプロジェクト]** の順に選択するか、**Ctrl + Shift + N** キーを押します。
1. **[Visual C++]、[クロス プラットフォーム]、[Linux]** ノードの順に選択し、作成するプロジェクト タイプを選択します。 **[名前]** と **[場所]** を入力し、 **[OK]** を選択します。

   ![新しい Linux プロジェクト](media/newproject.png)

   | プロジェクトの種類 | 説明 |
   | ------------ | --- |
   | **点滅 (Raspberry)**           | Raspberry Pi デバイスを対象とするプロジェクト。LED を点滅させるようにサンプル コードが記述されています。 |
   | **C++ コンソール アプリケーション (Linux)** | すべての Linux コンピューターを対象とするプロジェクト。コンソールにテキストを出力するようにサンプル コードが記述されています。 |
   | **空のプロジェクト (Linux)**       | すべての Linux コンピューターを対象とするプロジェクト。サンプル コードは記述されていません。 |
   | **メイクファイル プロジェクト (Linux)**    | 標準のメイクファイル ビルド システムを使用して構築する、すべての Linux コンピューターを対象とするプロジェクト。 |

## <a name="next-steps"></a>次の手順

[Linux プロジェクトを構成する](configure-a-linux-project.md)

::: moniker-end

::: moniker range="vs-2019"

最初に、Visual Studio 対応の **Linux 開発ワークロード**を必ずインストールします。 詳細については、「[Linux ワークロードのダウンロード、インストール、セットアップ](download-install-and-setup-the-linux-development-workload.md)」をご覧ください。

Visual Studio で Linux の新しい C++ プロジェクトを作成する場合、Visual Studio のプロジェクトを作成するか、CMake のプロジェクトを作成するか選択することができます。 この記事では、Visual Studio のプロジェクトを作成する方法について説明します。 一般に、オープンソースのコードを含む、またはクロスプラットフォーム開発のためにコンパイルする予定がある新しいプロジェクトでは、Visual Studio で CMake を使用することをお勧めします。 CMake プロジェクトでは、Windows と Linux の両方で同じプロジェクトをビルドしてデバッグできます。 詳細については、[Linux CMake プロジェクトの作成と構成](cmake-linux-project.md)に関する記事を参照してください。

CMake がオプションではなく、既存の Windows Visual Studio ソリューションを Linux 用のコンパイルのために拡張したい場合は、Visual Studio Linux プロジェクトを**共有項目**プロジェクトと共に Windows ソリューションに追加することができます。 共有項目プロジェクトの両方のプラットフォーム間で共有されるコードを配置し、そのプロジェクトへの参照を Windows および Linux プロジェクトから追加します。

## <a name="to-create-a-new-linux-project"></a>新しい Linux プロジェクトを作成するには

Visual Studio 2019 で新しい Linux プロジェクトを作成するには、次のように操作します。

1. Visual Studio で **[ファイル]、[新しいプロジェクト]** の順に選択するか、**Ctrl + Shift + N** キーを押します。
1. **[言語]** を **[C++]** に設定し、「Linux」を検索します。 作成するプロジェクトの種類を選択し、 **[次へ]** を選択します。 **[名前]** と **[場所]** を入力し、 **[作成]** を選択します。

   ![新しい Linux プロジェクト](media/newproject-vs2019.png)

   | プロジェクトの種類 | 説明 |
   | ------------ | --- |
   | **点滅 (Raspberry)**           | Raspberry Pi デバイスを対象とするプロジェクト。LED を点滅させるようにサンプル コードが記述されています。 |
   | **C++ コンソール アプリケーション (Linux)** | すべての Linux コンピューターを対象とするプロジェクト。コンソールにテキストを出力するようにサンプル コードが記述されています。 |
   | **空のプロジェクト (Linux)**       | すべての Linux コンピューターを対象とするプロジェクト。サンプル コードは記述されていません。 |
   | **メイクファイル プロジェクト (Linux)**    | 標準のメイクファイル ビルド システムを使用して構築する、すべての Linux コンピューターを対象とするプロジェクト。 |

## <a name="next-steps"></a>次の手順

[Linux プロジェクトを構成する](configure-a-linux-project.md)

::: moniker-end
