---
title: ATL ダイアログ ボックスを追加します。
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
ms.openlocfilehash: ebbb610debe5d480cd1161149f89c4d357f9cd02
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261606"
---
# <a name="adding-an-atl-dialog-box"></a>ATL ダイアログ ボックスを追加します。

ATL ダイアログをプロジェクトに追加するに、プロジェクトは ATL プロジェクト、または ATL のサポートを含む MFC プロジェクトをする必要があります。 ATL アプリケーションを作成するか、[ATL オブジェクトを MFC アプリケーションに追加して](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) MFC アプリケーションの ATL サポートを実装するには、[ATL プロジェクト ウィザード](../../atl/reference/atl-project-wizard.md)を利用できます。

ATL ダイアログ ウィザード実装から派生したダイアログ ボックスを既定では、 [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)します。 このクラスには、ActiveX、Windows のコントロールをホストするためのサポートが含まれています。 ウィザードは、コードを生成した後に、ActiveX コントロール サポートのオーバーヘッドをしない場合は、すべてのインスタンスを置き換える`CAxDialogImpl`いずれかで[CSimpleDialog](../../atl/reference/csimpledialog-class.md)または[CDialogImpl](../../atl/reference/cdialogimpl-class.md)基底クラスとして.

> [!NOTE]
> `CSimpleDialog` Windows コモン コントロールのみをサポートするモーダル ダイアログ ボックスのみを作成します。 `CDialogImpl` いずれかのモーダルまたはモードレスのダイアログ ボックスを作成します。

## <a name="to-add-an-atl-dialog-resource-to-your-project"></a>ATL ダイアログ リソースをプロジェクトに追加するには

1. 使用して ATL プロジェクトを作成、 [ATL プロジェクト ウィザード](../../atl/reference/atl-project-wizard.md)します。

1. [クラス ビュー](/visualstudio/ide/viewing-the-structure-of-code)プロジェクト名を右クリックし、クリックして**追加**ショートカット メニューから。 クリックして**クラスを追加**します。

1. **テンプレート**のウィンドウ、[クラスの追加](../../ide/add-class-dialog-box.md)ダイアログ ボックスで、をクリックして**ATL ダイアログ**します。 クリックして**オープン**を表示する、 [ATL ダイアログ ウィザード](../../atl/reference/atl-dialog-wizard.md)します。

詳細については、次を参照してください。 [ ダイアログ ボックスを実装する](../../atl/implementing-a-dialog-box.md)します。

## <a name="see-also"></a>関連項目

[クラスの追加](../../ide/adding-a-class-visual-cpp.md)<br/>
[ウィンドウ クラス](../../atl/atl-window-classes.md)<br/>
[メッセージ マップ](../../atl/message-maps-atl.md)
