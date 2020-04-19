---
title: コントロール バー クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.control
helpviewer_keywords:
- control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
ms.openlocfilehash: 3426d84eab888a6fe78b663945776fff2fe708dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301956"
---
# <a name="control-bar-classes"></a>コントロール バー クラス

コントロール バーは、フレーム ウィンドウにアタッチされます。 ボタン、ステータス ウィンドウ、またはダイアログのテンプレートが含まれます。 フローティング状態であるコントロール バー、ツールのパレットとも呼ばれますがアタッチすることによって実装される、 [CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)オブジェクト。

## <a name="framework-control-bars"></a>フレームワークのコントロール バー

これらのコントロール バーは、MFC フレームワークの不可欠な部分です。 使いやすく、フレームワークに統合されているため、Windows コントロール バーより強力なは。 ほとんどの MFC アプリケーションでは、Windows のコントロール バーではなく、これらのコントロール バーを使用します。

[CControlBar](../mfc/reference/ccontrolbar-class.md)<br/>
このセクションに記載の MFC コントロール バーの基本クラスです。 コントロール バーは、フレーム ウィンドウの端に揃えて配置ウィンドウです。 コントロール バーには、いずれかが含まれています`HWND`-ベースの子コントロールまたはコントロールに基づいていない、 `HWND`、ツール バー ボタンなどです。

[CDialogBar](../mfc/reference/cdialogbar-class.md)<br/>
ダイアログ ボックスのテンプレートに基づくコントロール バーです。

[CReBar](../mfc/reference/crebar-class.md)<br/>
コントロールの形式で追加の子ウィンドウを含むことのできるツールバーをサポートしています。

[CToolBar](../mfc/reference/ctoolbar-class.md)<br/>
コマンド ボタン ビットマップにはが含まれていないツール バー コントロールのウィンドウがに基づいて、`HWND`します。 ほとんどの MFC アプリケーションは、このクラスを使用してなく`CToolBarCtrl`します。

[CStatusBar](../mfc/reference/cstatusbar-class.md)<br/>
ステータス バー コントロールの windows の基本クラスです。 ほとんどの MFC アプリケーションは、このクラスを使用してなく`CStatusBarCtrl`します。

## <a name="windows-control-bars"></a>Windows のコントロール バー

これらのコントロール バーは、対応する Windows コントロールのシン ラッパーです。 いないフレームワークと統合されている、ためにが困難になる前に示したコントロール バーを使用します。 ほとんどの MFC アプリケーションでは、上記のコントロール バーを使用します。

[CRebarCtrl](../mfc/reference/crebarctrl-class.md)<br/>
内部のコントロールを実装、`CRebar`オブジェクト。

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
水平方向のウィンドウでは、通常はウィンドウ、アプリケーションが状態情報を表示できますに分かれています。

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Windows ツール バー コモン コントロールの機能が用意されています。

## <a name="related-classes"></a>関連するクラス

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
単一のアプリケーションでのツールの目的を説明するテキストを表示する小さなポップアップ ウィンドウ。

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
ドッキング コントロール バーの状態データの永続的なストレージを処理します。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
