---
title: '方法: windows デスクトップアプリケーションで Windows 10 SDK を使用する'
description: Windows 10 SDK を使用するように Windows デスクトップアプリケーションプロジェクトでターゲット SDK のバージョンを設定する方法について説明します。
ms.custom: get-started-article
ms.date: 01/22/2020
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: c1d71b591398453f7cee02aa22cd2e377991588f
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725735"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>方法: windows デスクトップアプリケーションで Windows 10 SDK を使用する

Visual Studio で新しいクラシック Windows デスクトッププロジェクトを作成すると、既定で Windows 10 SDK が対象となります。 デスクトップワークロードをインストールすると、Visual Studio によっC++てこの SDK のバージョンがインストールされます。 Windows 10 SDK は、Windows 7 SP1 以降のコードの記述をサポートしています。 特定のバージョンの Windows を対象とする方法の詳細については、「 [Windows ヘッダーの使用](/windows/win32/WinProg/using-the-windows-headers)」および「 [Update WINVER と _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md)」を参照してください。

既存のプロジェクトをアップグレードする場合は、プロジェクトで指定されているターゲット Windows SDK を使用し続けることができます。 または、プロジェクトを再ターゲットして、Windows 10 SDK を使用することもできます。 Windows 10 SDK を使用すると、最新のオペレーティングシステムと言語標準をサポートする利点を得ることができます。

## <a name="use-the-right-windows-sdk-for-your-project"></a>プロジェクトに適切な Windows SDK を使用する

Visual Studio 2015 以降では、C ランタイム (CRT) ライブラリは2つの部分に分けられていました。1つの部分である ucrtbase には、ユニバーサル Windows アプリで使用できる標準 C および Microsoft 固有の CRT 関数が含まれています。 このライブラリは、ユニバーサル CRT (UCRT) と呼ばれるようになり、Windows 10 SDK に移行されました。 UCRT には、最新C++の言語標準をサポートするために必要な多数の新しい関数 (C99 関数など) が含まれています。 元の CRT のもう1つの部分は vcruntime です。 これには、C ランタイムのサポート、スタートアップ、終了コードが含まれています。また、UCRT にはないすべてのものが含まれています。 Vcruntime ライブラリは、Visual Studio のC++コンパイラおよびツールセットと共にインストールされます。 詳細については、「 [CRT ライブラリの機能](../c-runtime-library/crt-library-features.md)」を参照してください。

UCRT は、Windows 10 のすべてのバージョンにインストールされたシステムコンポーネントになりました。 また、以前にサポートされていたすべてのバージョンの Windows で、インストール可能なコンポーネントとしても使用できます。 Windows 10 SDK を使用して、サポートされているすべてのバージョンの Windows を対象にすることができます。 サポートされているオペレーティングシステムの完全な一覧については、「 [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)」を参照してください。

Visual Studio 2015 より前のプロジェクトバージョンからアップグレードするときに、Windows 10 SDK を使用するようにプロジェクトを再ターゲットするには、次の手順を実行します。

### <a name="to-target-the-windows-10-sdk"></a>Windows 10 SDK をターゲットとするには

1. Windows 10 SDK がインストールされていることを確認します。 Windows 10 SDK は、ワークロード**を使用C++したデスクトップ開発**の一部としてインストールされます。 スタンドアロンバージョンについては、「 [Windows 10 用のダウンロードとツール](https://developer.microsoft.com/windows/downloads)」を参照してください。

1. プロジェクトノードのショートカットメニューを開き、[プロジェクトの再**ターゲット**] を選択します。 (以前のバージョンの Visual Studio では、 **[SDK バージョン]** の再ターゲット を選択します)。 **[ソリューションアクションの確認]** ダイアログが表示されます。

   ![ソリューションアクションの確認](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

1. **[ターゲットプラットフォームのバージョン]** ドロップダウンリストで、対象とする WINDOWS 10 SDK のバージョンを選択します。 一般に、インストールされている最新バージョンを選択することをお勧めします。 **[OK** ] をクリックして、変更を適用します。

   このコンテキストの8.1 は Windows 8.1 SDK を参照します。

   この手順が成功すると、出力ウィンドウに次のテキストが表示されます。

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

1. [プロジェクトのプロパティ] ダイアログを開きます。 **[構成プロパティ]**  >  **[全般**] セクションで、 **[Windows ターゲットプラットフォームバージョン]** の値を確認します。 ここで値を変更することは、この手順を実行するのと同じ効果があります。 詳しくは、「[[全般] プロパティ ページ (プロジェクト)](../build/reference/general-property-page-project.md)」をご覧ください。

   ![ターゲットプラットフォームのバージョン](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   この操作は、ヘッダー ファイルとライブラリ ファイルへのパスを含むプロジェクトのマクロの値を変更します。 変更内容を確認するには、 **[プロジェクトのプロパティ]** ダイアログボックスの **[ビジュアルC++ディレクトリ]** セクションを開きます。 **[インクルードディレクトリ]** など、プロパティのいずれかを選択します。 次に、プロパティ値のドロップダウンリストを開き、[ **> の編集\<** ] を選択します。 **[インクルード ディレクトリ]** ダイアログが表示されます。

   ![[ディレクトリを含める] ダイアログボックス](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   **[マクロ > >]** ボタンをクリックし、マクロの一覧を Windows SDK マクロにスクロールして、すべての新しい値を表示します。

   ![Windows SDK マクロ](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

1. 必要に応じて、他のソリューションプロジェクトに対して再ターゲットプロシージャを繰り返し、ソリューションをリビルドします。

### <a name="to-target-the-windows-81-sdk"></a>Windows 8.1 SDK をターゲットとするには

1. ソリューションエクスプローラーでプロジェクトノードのショートカットメニューを開き、[プロジェクトの再**ターゲット**] を選択します。 (以前のバージョンの Visual Studio では、[ **SDK バージョン**の再ターゲット] を選択します)。

2. **[ターゲットプラットフォームバージョン]** ドロップダウンリストで、 **[8.1]** を選択します。

## <a name="see-also"></a>関連項目

[チュートリアル: 従来の Windows デスクトップアプリケーションを作成C++する ()](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)
