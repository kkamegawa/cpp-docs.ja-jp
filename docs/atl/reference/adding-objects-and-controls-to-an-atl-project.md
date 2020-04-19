---
title: ATL プロジェクトへのオブジェクトとコントロールの追加
ms.date: 05/09/2019
f1_keywords:
- vc.appwiz.ATL.controls
helpviewer_keywords:
- ATL projects, adding objects
- wizards [C++], ATL projects
- ATL projects, adding controls
- controls [ATL], adding to projects
- objects [C++], adding to ATL projects
- ATL Control Wizard
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
ms.openlocfilehash: deaac8f2d6aac02d0cd751e6abebb3b67051200f
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706844"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>ATL プロジェクトへのオブジェクトとコントロールの追加

> [!NOTE] 
> ATL COM+ 1.0 コンポーネント ウィザード、ATL OLE DB コンシューマー ウィザード、ATL Active Server Page コンポーネント ウィザードは、Visual Studio 2019 以降で使用できません。

ATL または MFC ベースのプロジェクトにオブジェクトまたはコントロールを追加するには、いずれかの ATL コード ウィザードを使用できます。 ウィザードでは、追加する COM オブジェクトまたはコントロールごとに、.cpp および .h ファイルのほか、スクリプト ベースのレジストリのサポートのために、.rgs ファイルが生成されます。 次の ATL コード ウィザードを Visual Studio で使用できます。

||||
|-|-|-|
|[ATL シンプル オブジェクト](../../atl/reference/atl-simple-object-wizard.md)|[ATL ダイアログ](../../atl/reference/atl-dialog-wizard.md)|[ATL コントロール](../../atl/reference/atl-control-wizard.md)|
|[ATL プロパティ ページ](../../atl/reference/atl-property-page-wizard.md)|[ATL Active Server Page コンポーネント](../../atl/reference/atl-active-server-page-component-wizard.md)|[ATL OLE DB コンシューマー](../../atl/reference/atl-ole-db-consumer-wizard.md)|
|[MFC に ATL サポートを追加する](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[ATL COM+ 1.0 コンポーネント ウィザード](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[ATL OLE DB プロバイダー](../../atl/reference/atl-ole-db-provider-wizard.md)|

> [!NOTE]
> プロジェクトに ATL オブジェクトを追加する前に、関連するヘルプ トピックでオブジェクトの詳細と要件を確認する必要があります。

## <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>ATL コントロール ウィザードを使用してオブジェクトまたはコントロールを追加するには

1. **ソリューション エクスプローラー**で、プロジェクト ノードを右クリックし、ショートカット メニューの **[追加]** をクリックします。 **[クラスの追加]** をクリックします。

   [[クラスの追加]](../../ide/add-class-dialog-box.md) ダイアログ ボックスが表示されます。

1. **[カテゴリ]** ウィンドウで **[ATL]** フォルダーが選択された状態で、**[テンプレート]** ウィンドウから挿入するオブジェクトを選択します。 **[開く]** をクリックします。 選択したオブジェクトのコード ウィザードが表示されます。

   > [!NOTE]
   > MFC プロジェクトに ATL オブジェクトを追加する場合、既存のプロジェクトに ATL サポートを追加する必要があります。 これは、「[MFC プロジェクトへの ATL サポートの追加](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)」の手順に従って行うことができます。

   または、以前に ATL サポートを追加していない MFC プロジェクトに ATL オブジェクトを追加しようとする場合は、Visual Studio から ATL サポートをプロジェクトに追加するかどうかを指定するように求められます。 **[はい]** をクリックして、プロジェクトに ATL サポートを追加し、選択した ATL ウィザードを開きます。

## <a name="see-also"></a>関連項目

[ATL プロジェクト ウィザード](../../atl/reference/atl-project-wizard.md)<br/>
[Visual Studio の C++ プロジェクトの種類](../../build/reference/visual-cpp-project-types.md)<br/>
[ATL COM オブジェクトの基礎](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[ATL および C ランタイム コードによるプログラミング](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL プロジェクトの既定の構成](../../atl/reference/default-atl-project-configurations.md)
