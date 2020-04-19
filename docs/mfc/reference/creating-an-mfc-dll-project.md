---
title: MFC DLL プロジェクトの作成
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.mfcdll.project
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
ms.openlocfilehash: 649a47abea23aedb9aa97bb4923e7a800348e27e
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108478"
---
# <a name="creating-an-mfc-dll-project"></a>MFC DLL プロジェクトの作成

MFC DLL とは、複数のアプリケーションで同時に利用できる関数の共有ライブラリとして機能する、バイナリ ファイルです。 MFC DLL プロジェクトを作成する最も簡単な方法は、MFC DLL ウィザードを使用する方法です。

> [!NOTE]
>  IDE に表示される機能は、有効にされている設定やエディションに依存し、ヘルプに記載されている内容とは異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>MFC DLL ウィザードを使用して MFC DLL プロジェクトを作成するには

1. ヘルプトピック「 [Mfc アプリケーションの作成](creating-an-mfc-application.md)」の手順に従いますが、使用可能なテンプレートの一覧から**Mfc ダイナミックリンクライブラリ**または**mfc DLL**を選択します。

1. [MFC DLL ウィザード](../../mfc/reference/mfc-dll-wizard.md)の [[アプリケーションの設定](../../mfc/reference/application-settings-mfc-dll-wizard.md)] ページを使用して、アプリケーションの設定を定義します。

    > [!NOTE]
    >  ウィザードの既定の設定を使用する場合は、この手順を省略します。

1. **[完了]** をクリックしてウィザードを終了し、**ソリューションエクスプローラー**で新しいプロジェクトを開きます。

プロジェクトを作成したら、**ソリューション エクスプローラー**で、作成したファイルを表示できます。 ウィザードでプロジェクト用に作成されるファイルの詳細については、プロジェクトが生成する ReadMe.txt ファイルを参照してください。 ファイルの種類の詳細については、「[Visual Studio の C++ プロジェクトに対して作成されるファイルの種類](../../build/reference/file-types-created-for-visual-cpp-projects.md)」を参照してください。

## <a name="see-also"></a>関連項目

[Visual Studio の C++ プロジェクトの種類](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[コード ウィザードを使用した機能の追加](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[プロパティ ページ](../../build/reference/property-pages-visual-cpp.md)

