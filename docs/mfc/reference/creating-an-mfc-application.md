---
title: MFC アプリケーションの作成
ms.date: 08/28/2019
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
ms.openlocfilehash: 5f3a24a46db1c9013e5458143812faa079ade013
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108505"
---
# <a name="creating-an-mfc-application"></a>MFC アプリケーションの作成

MFC アプリケーションは、MFC (Microsoft Foundation Class) ライブラリに基づく Windows 対応の実行可能なアプリケーションです。 MFC の実行可能ファイルは、一般に、標準の Windows アプリケーション、ダイアログボックス、フォームベースのアプリケーション、エクスプローラースタイルのアプリケーション、および Web ブラウザースタイルのアプリケーションの5種類に分類されます。 詳細については次を参照してください:

- [クラスを使用した Windows アプリケーションの記述](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [ダイアログ ボックスの作成と表示](../../mfc/creating-and-displaying-dialog-boxes.md)

- [フォーム ベースの MFC アプリケーションの作成](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [エクスプローラー形式の MFC アプリケーションの作成](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [Web ブラウザー形式の MFC アプリケーションの作成](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

MFC アプリケーション ウィザードでは、これらのアプリケーションのすべてに適したクラスやファイルが生成されます。作成されるクラスやファイルは、ウィザードで選択したオプションによって異なります。


MFC アプリケーションを作成する最も簡単な方法は、MFC アプリケーションウィザード (Visual Studio 2019 の**Mfc アプリプロジェクト**) を使用することです。 Mfc コンソールアプリケーション (MFC ライブラリを使用し、コンソールウィンドウで実行されるコマンドラインプログラム) を作成するには、Windows デスクトップウィザードを使用して、 **[コンソールアプリケーション]** オプションと **[MFC ヘッダー]** オプションを選択します。

::: moniker range=">=vs-2019"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>MFC フォームまたはダイアログベースのアプリケーションを作成するには

1. メインメニューから、[**ファイル** > ] [**新規作成** > ] **[プロジェクト]** の順に選択します。
1. 検索ボックスに「MFC」と入力し、結果の一覧で **[Mfc アプリ]** を選択します。
1. 必要に応じて既定値を変更し、 **[作成]** をクリックして、 **MFC アプリケーションウィザード**を開きます。
1. 必要に応じて構成値を変更し、 **[完了]** を押します。

詳細については、「[フォームベースの MFC アプリケーションの作成](creating-a-forms-based-mfc-application.md)」を参照してください。

![MFC アプリケーション ウィザード](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>MFC コンソールアプリケーションを作成するには

MFC コンソールアプリケーションは、MFC ライブラリを使用するコマンドラインプログラムであり、コンソールウィンドウで実行されます。

1. メインメニューから、[**ファイル** > ] [**新規作成** > ] **[プロジェクト]** の順に選択します。
1. 検索ボックスに「デスクトップ」と入力し、結果の一覧から **[Windows デスクトップウィザード]** を選択します。
1. 必要に応じてプロジェクト名を変更し、 **[次へ]** をクリックして**Windows デスクトップウィザード**を開きます。
1. **[MFC ヘッダー]** ボックスを確認し、必要に応じて他の値を設定して、 **[完了]** を押します。

![MFC アプリケーション ウィザード](media/windows-desktop-wizard.png)

::: moniker-end

::: moniker range="=vs-2017"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>MFC フォームまたはダイアログベースのアプリケーションを作成するには

1. メインメニューから、[**ファイル** > ] [**新規作成** > ] **[プロジェクト]** の順に選択します。
1. [**インストールされ**たテンプレート] で、  > [ **Visual C++**  **MFC/ATL**] を選択します。 これらが表示されない場合は、Visual Studio インストーラーを使用して追加します。
1. 中央のウィンドウで **[MFC アプリケーション]** を選択します。
1. 必要に応じて構成値を変更し、 **[完了]** を押します。

詳細については、「[フォームベースの MFC アプリケーションの作成](creating-a-forms-based-mfc-application.md)」を参照してください。

![MFC アプリケーション ウィザード](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>MFC コンソールアプリケーションを作成するには

MFC コンソールアプリケーションは、MFC ライブラリを使用するコマンドラインプログラムであり、コンソールウィンドウで実行されます。

1. メインメニューから、[**ファイル** > ] [**新規作成** > ] **[プロジェクト]** の順に選択します。
1. [**インストールされ**たテンプレート] で、 > [ **Visual C++**  **Windows デスクトップ**] を選択します。
1. 中央のウィンドウで、 **[Windows デスクトップウィザード]** を選択します。
1. 必要に応じてプロジェクト名を変更し、[ **OK]** をクリックして**Windows デスクトップウィザード**を開きます。
1. **[MFC ヘッダー]** ボックスを確認し、必要に応じて他の値を設定して、 **[完了]** を押します。

![MFC アプリケーション ウィザード](media/windows-desktop-wizard-2017.png)

::: moniker-end

::: moniker range="=vs-2015"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>MFC フォームまたはダイアログベースのアプリケーションを作成するには

1. メインメニューから、[**ファイル** > ] [**新規作成** > ] **[プロジェクト]** の順に選択します。
1. [**インストールされ**たテンプレート] で、 > [ **Visual C++**  **MFC**] を選択します。
1. 中央のウィンドウで **[MFC アプリケーション]** を選択します。
1. **[次へ]** をクリックして、 **MFC アプリケーションウィザード**を起動します。

詳細については、「[フォームベースの MFC アプリケーションの作成](creating-a-forms-based-mfc-application.md)」を参照してください。

![MFC アプリケーション ウィザード](media/mfc-app-wizard-2015.png)

## <a name="to-create-an-mfc-console-application"></a>MFC コンソールアプリケーションを作成するには

MFC コンソールアプリケーションは、MFC ライブラリを使用するコマンドラインプログラムであり、コンソールウィンドウで実行されます。

1. メインメニューから、[**ファイル** > ] [**新規作成** > ] **[プロジェクト]** の順に選択します。
1. [**インストールされ**たテンプレート] で、 > [**ビジュアルC++**  **Win32**] を選択します。
1. 中央のウィンドウで **[Win32 コンソールアプリケーション]** を選択します。
1. 必要に応じてプロジェクト名を変更し、[ **OK]** をクリックします。
1. ウィザードの2ページ目で、 **[MFC の共通ヘッダーを追加]** する ボックスをオンにし、必要に応じて他の値を設定して、 **[完了]** をクリックします。

::: moniker-end

プロジェクトを作成したら、**ソリューション エクスプローラー**で、作成したファイルを表示できます。 ウィザードでプロジェクト用に作成されるファイルの詳細については、プロジェクトが生成する ReadMe.txt ファイルを参照してください。 ファイルの種類の詳細については、「[Visual Studio の C++ プロジェクトに対して作成されるファイルの種類](../../build/reference/file-types-created-for-visual-cpp-projects.md)」を参照してください。

## <a name="see-also"></a>関連項目

[コード ウィザードを使用した機能の追加](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[プロパティ ページ](../../build/reference/property-pages-visual-cpp.md)