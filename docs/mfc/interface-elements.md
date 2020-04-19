---
title: インターフェイス要素
ms.date: 11/19/2018
helpviewer_keywords:
- architecture [MFC], MFC Feature Pack
- MFC Feature Pack, architecture
ms.assetid: eead6827-9602-40a3-8038-8986e8207385
ms.openlocfilehash: fa6dc78c95717f9201e18346f1cbe573fa3c48d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153586"
---
# <a name="interface-elements"></a>インターフェイス要素

このドキュメントでは、Visual Studio 2008 SP1 で導入されたインターフェイス要素について説明し、ライブラリの以前のバージョンとの違いについても説明します。

次の図は、新しいインターフェイスの要素を使用して構築されたアプリケーションを示します。

![サンプル アプリケーションの MFC Feature Pack](../mfc/media/mfc_featurepack.png "MFC Feature Pack のサンプル アプリケーション")

## <a name="window-docking"></a>ウィンドウのドッキング

ウィンドウのドッキング機能では、Visual Studio のグラフィカル ユーザー インターフェイスを使用して、ドッキング ウィンドウに似ています。

## <a name="control-bars-are-now-panes"></a>コントロール バーがウィンドウようになりました

コントロール バー ペインと呼ばれることは今すぐおよびからは派生[CBasePane クラス](../mfc/reference/cbasepane-class.md)します。 以前のバージョンの MFC では、コントロール バーの基本クラスが`CControlBar`します。

アプリケーションのメイン フレーム ウィンドウがによって表されるは、通常、 [CFrameWndEx クラス](../mfc/reference/cframewndex-class.md)または[CMDIFrameWndEx クラス](../mfc/reference/cmdiframewndex-class.md)します。 メイン フレームと呼ばれる、*ドッキング サイト*します。 ウィンドウは、親の 3 種類のいずれかを指定できます: ドッキング サイト、ドッキング バー、またはミニフレーム ウィンドウ。

ペインの 2 種類があります。 サイズを変更およびサイズを変更します。 ステータス バーやツールバーなどのサイズ変更可能なペイン スプリッターまたはスライダーを使用してサイズを変更できます。 サイズ変更可能なペインには、(別のウィンドウでは、それらの間の分割を作成するのには 1 つのペインをドッキングできる) コンテナーを形成できます。 ただし、サイズ変更可能なペインがあります (ドッキング) バーをドッキングするのにはアタッチできません。

アプリケーションでは、サイズを変更できないウィンドウを使用する場合は派生から[CPane クラス](../mfc/reference/cpane-class.md)します。  アプリケーションでは、サイズ変更可能なペインを使用する場合は派生から[CDockablePane クラス](../mfc/reference/cdockablepane-class.md)

## <a name="dock-site"></a>ドッキング サイト

ドッキング サイト (またはメイン フレーム ウィンドウ) は、すべてのペインと、アプリケーション内のミニフレーム ウィンドウを所有しています。 ドッキング サイトに含まれる、 [CDockingManager](../mfc/reference/cdockingmanager-class.md)メンバー。 このメンバーは、ドッキング サイトに属しているすべてのウィンドウのリストを保持します。 リストの順序は、ドッキング サイトの外側のエッジに作成されたウィンドウが一覧の先頭に配置されているようにします。 ドッキング サイトが再描画するために、フレームワーク、ときにこの一覧をループし、ドッキング サイトの現在の外接する四角形を含めるには、各ウィンドウのレイアウトを調整します。 呼び出すことができます`AdjustDockingLayout`または`RecalcLayout`ドッキングのレイアウトを調整する必要があるし、フレームワークは、ドッキング マネージャーには、この呼び出しをリダイレクトします。

## <a name="dock-bars"></a>ドッキング バー

各メイン フレーム ウィンドウを配置できます*ドッキング バー*に沿っての境界線。 ドッキング バーが属するウィンドウ、 [CDockSite クラス](../mfc/reference/cdocksite-class.md)します。 派生したオブジェクトを受け入れることができるドッキング バー [CPane](../mfc/reference/cpane-class.md)、ツールバーなど。 メイン フレーム ウィンドウが初期化されるときに、ドッキング バーを作成するには、呼び出す`EnableDocking`します。 自動的に隠すバーを有効にするには、呼び出す`EnableAutoHideBars`します。 `EnableAutoHideBars` 作成[CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md)オブジェクト、および各ドッキング バーの隣に配置します。

各ドッキング バーは、ドッキング行に分割されます。 ドッキングの行がによって表される、 [CDockingPanesRow クラス](../mfc/reference/cdockingpanesrow-class.md)します。 ドッキングの各行には、ツールバーの一覧が含まれています。 ユーザーがツールバーをドッキングまたは 1 つの行から同じドッキング バー内の別に、ツールバーを移動、フレームワークが新しい行を作成し、ドッキング バーのサイズを変更または既存の行を上にツールバーを配置します。

## <a name="mini-frame-windows"></a>ミニフレームの Windows

フローティング ウィンドウは、ミニフレーム ウィンドウに存在します。 ミニフレーム ウィンドウは、2 つのクラスによって表されます。[CMDITabInfo クラス](../mfc/reference/cmditabinfo-class.md)(これは、1 つのペインを含めることができます) と[CMultiPaneFrameWnd クラス](../mfc/reference/cmultipaneframewnd-class.md)(これは、いくつかのペインを含めることができます)。 コードでは、ペインをフローティング、呼び出す[CBasePane::FloatPane](../mfc/reference/cbasepane-class.md#floatpane)します。 ペインがフローティング状態になった後は、フレームワークがミニフレーム ウィンドウを自動的に作成し、ミニフレーム ウィンドウがフローティング ウィンドウの親になります。 フローティング ペインがドッキングし、フレームワークがその親をリセット フローティング ペイン (ツールバー) 用のドッキング バーまたはドッキング サイト (のサイズ変更可能なペイン) になります。

## <a name="pane-dividers"></a>ウィンドウの分割

ペインの区分線が (スライダーまたはスプリッターとも呼ばれます) がによって表される、 [CPaneDivider クラス](../mfc/reference/cpanedivider-class.md)します。 ユーザーは、ペインをドッキング、フレームワークは、ドック サイトまたは別のペインで、ペインはドッキングするかどうかに関係なく、ペインの区分線を作成します。 ペインをドッキング サイトにドッキング、ペイン分割バーが呼び出されます、*ペイン分割バーを既定*します。 既定ペイン分割バーでは、ドッキング サイト内のすべてのドッキング ペインのレイアウトを担当します。 ドッキング マネージャーには、この既定ペインの区分線の一覧と、ペインの一覧が維持されます。 ドッキング マネージャーは、すべてのドッキング ペインのレイアウトを行います。

## <a name="containers"></a>コンテナー

すべてのサイズ変更可能なペイン、相互にドッキングされているときは、コンテナーに保持されます。 コンテナーがによって表される、 [CPaneContainer クラス](../mfc/reference/cpanecontainer-class.md)します。 各コンテナーには左端と右端の部分の間で、左側のウィンドウ、右側のウィンドウ、サブ コンテナーの左、右のサブ コンテナーおよび分割線へのポインター。 (*左*と*右*物理辺を参照していませんではなくツリー構造の分岐を識別します)。この方法でウィンドウ、分割ウィンドウのツリーを構築をそのためにまとめてサイズを変更できるウィンドウの複雑なレイアウトを実現できます。 `CPaneContainer`クラスはコンテナーのツリーを保持; ペインと、このツリー内に存在するスライダーの 2 つのリストも保持されます。 コンテナー マネージャーのウィンドウは通常、既定のスライダーと複数のペインを実行するミニフレーム ウィンドウに埋め込まれます。

## <a name="auto-hide-control-bars"></a>コントロール バーを自動的に隠す

既定では、各`CDockablePane`自動的に隠す機能をサポートします。 ユーザーが暗証番号 (pin) ボタンのキャプションをクリックすると、`CDockablePane`フレームワークは、ウィンドウを自動非表示モードに切り替えます。 クリックを処理するために、フレームワークを作成、 [CMFCAutoHideBar クラス](../mfc/reference/cmfcautohidebar-class.md)と[CMFCAutoHideButton クラス](../mfc/reference/cmfcautohidebutton-class.md)に関連付けられている、`CMFCAutoHideBar`オブジェクト。 フレームワークは、新しい`CMFCAutoHideBar`上、 [CAutoHideDockSite](../mfc/reference/cautohidedocksite-class.md)します。 フレームワークもアタッチ、`CMFCAutoHideButton`ツールバーにします。 [CDockingManager Class](../mfc/reference/cdockingmanager-class.md)保持、`CDockablePane`します。

## <a name="tabbed-control-bars-and-outlook-bars"></a>タブ付きのコントロール バーおよび Outlook バー

[CMFCBaseTabCtrl クラス](../mfc/reference/cmfcbasetabctrl-class.md)切り離し可能なタブをタブ付きウィンドウの基本機能を実装します。 使用する、`CMFCBaseTabCtrl`オブジェクト、初期化、 [CBaseTabbedPane クラス](../mfc/reference/cbasetabbedpane-class.md)アプリケーションでします。 `CBaseTabbedPane` 派生`CDockablePane`へのポインターを保持し、`CMFCBaseTabCtrl`オブジェクト。 `CBaseTabbedPane`ドッキングしてタブ付きコントロール バーのサイズを変更することができます。 使用[cdockablepane::attachtotabwnd](../mfc/reference/cdockablepane-class.md#attachtotabwnd)ドッキングされ、タブ付きされるコントロール バーを動的に作成します。

Outlook バー コントロールがタブ バーにも基づいています。 [CMFCOutlookBar クラス](../mfc/reference/cmfcoutlookbar-class.md)から派生`CBaseTabbedPane`します。 Outlook バーを使用する方法の詳細については、次を参照してください。 [CMFCOutlookBar クラス](../mfc/reference/cmfcoutlookbar-class.md)します。

## <a name="see-also"></a>関連項目

[概念](../mfc/mfc-concepts.md)
