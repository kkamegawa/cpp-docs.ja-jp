---
title: ATL プロジェクトの作成
ms.date: 05/06/2019
f1_keywords:
- vc.appwiz.ATL.project
helpviewer_keywords:
- ATL projects, creating
- ATL70.DLL
- _ATL_MIN_CRT macro
- distributing files with ATL components
ms.assetid: 061d5f98-f669-440e-9380-42f017a0f9e8
ms.openlocfilehash: 971d6c05ad4669f32e3b232d5e91c501e197be30
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707426"
---
# <a name="creating-an-atl-project"></a>ATL プロジェクトの作成

ATL プロジェクトを作成する最も簡単な方法は、**[新しいプロジェクト]** ダイアログ ボックスの **[Win32 プロジェクト]** フォルダーにある ATL プロジェクト ウィザードを使用することです。

## <a name="to-create-an-atl-project-using-the-atl-project-wizard"></a>ATL プロジェクト ウィザードを使用して ATL プロジェクトを作成するには

1. Visual Studio で、メイン メニューから **[ファイル] > [新規作成] > [プロジェクト]** の順に選択します。

1. **[テンプレート]** ウィンドウの **[ATL プロジェクト]** アイコンを選択し、**ATL プロジェクト ウィザード**を開きます。

1. **ATL プロジェクト ウィザード**の [[アプリケーションの設定]](../../atl/reference/application-settings-atl-project-wizard.md) ページを使用して、アプリケーションの設定を定義します。

   > [!NOTE]
   > ウィザードの既定の設定を使用する場合は、この手順を省略します。

1. **[完了]** をクリックしてウィザードを閉じ、新しいプロジェクトを開発環境で開きます。

プロジェクトを作成したら、**ソリューション エクスプローラー**で、作成したファイルを表示できます。 ウィザードでプロジェクト用に作成されるファイルの詳細については、プロジェクトが生成する ReadMe.txt ファイルを参照してください。 ファイルの種類の詳細については、「[Visual Studio の C++ プロジェクトに対して作成されるファイルの種類](../../build/reference/file-types-created-for-visual-cpp-projects.md)」を参照してください。 新しい ATL プロジェクトの構成の詳細とそれらの変更方法については、「[ATL プロジェクトの既定の構成](../../atl/reference/default-atl-project-configurations.md)」を参照してください。

## <a name="see-also"></a>関連項目

[コード ウィザードを使用した機能の追加](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[プロパティ ページ](../../build/reference/property-pages-visual-cpp.md)
