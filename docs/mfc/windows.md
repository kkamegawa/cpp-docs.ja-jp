---
title: Windows
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], window
- windows [MFC]
- MFC, windows
- window objects [MFC], MFC Framework
ms.assetid: dd92bf34-842e-40fe-8aea-3028b55314d5
ms.openlocfilehash: ee5e6fef58b9ddfa2172b9024d414bdb03e93283
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338000"
---
# <a name="windows"></a>Windows

この一連のトピックでは、ウィンドウ オブジェクトの MFC フレームワークについて説明します。 クラスから派生するすべての MFC windows [CWnd](../mfc/reference/cwnd-class.md)(フレーム ウィンドウ、ビュー、ダイアログ ボックスに、コントロールなど)。

記事の最初のグループについて説明します[ウィンドウ オブジェクト](../mfc/window-objects.md)一般にします。 C++ ウィンドウ オブジェクト、詳細については、このグループを参照してくださいカプセル化の方法、 `HWND`、および使用する方法に子ウィンドウなどの独自のウィンドウを作成するときにします。

記事の 2 番目のグループ[フレーム ウィンドウ](../mfc/frame-windows.md)-コンテンツの周囲にフレームを配置する windows-具体的には。 MFC フレームワークがフレーム ウィンドウおよびコントロール バーやビューなどのフレームの内容を管理する方法については、このグループを参照してください。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

*ウィンドウ オブジェクトの概要に関するトピック*

- [ウィンドウ オブジェクト](../mfc/window-objects.md)

- [C++ 関係ウィンドウ オブジェクトと HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)

- [ウィンドウ クラスの派生](../mfc/derived-window-classes.md)

- [ウィンドウ オブジェクトの作成](../mfc/creating-windows.md)

- [ウィンドウ オブジェクトの破棄](../mfc/destroying-window-objects.md)

- [ウィンドウ「クラス」の登録](../mfc/registering-window-classes.md)

- [ウィンドウ オブジェクトの操作](../mfc/working-with-window-objects.md)

- [デバイス コンテキスト](../mfc/device-contexts.md): 描画の Windows デバイスに依存するオブジェクト

- [グラフィック オブジェクト](../mfc/graphic-objects.md): ペン、ブラシ、フォント、ビットマップ、パレット、リージョン

*フレーム ウィンドウのトピック*

- [フレーム ウィンドウ](../mfc/frame-windows.md): ウィンドウ オブジェクトのフレームを提供します。

- [フレーム ウィンドウとビュー](../mfc/frame-windows.md)

- [フレーム ウィンドウ クラス](../mfc/frame-window-classes.md)

- [フレーム ウィンドウ スタイル](../mfc/frame-window-styles-cpp.md)

- [MFC で作成したウィンドウのスタイルを変更します。](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

- [フレーム ウィンドウ](../mfc/what-frame-windows-do.md)

- [フレーム ウィンドウの使用](../mfc/using-frame-windows.md)

- [MD/子ウィンドウ ([クイック ウォッチ] ウィンドウ) の管理](../mfc/managing-mdi-child-windows.md)

- [メニューのコントロール バー、およびアクセラレータの管理](../mfc/managing-menus-control-bars-and-accelerators.md)

- [CFrameWnd](../mfc/reference/cframewnd-class.md)

- [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)

- [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)

- [ビューの使い方](../mfc/using-views.md)

- [複数のドキュメント タイプ、ビュー、およびフレーム Windows (分割ウィンドウ)](../mfc/multiple-document-types-views-and-frame-windows.md)

- [メッセージ (マップおよびハンドラー関数)](../mfc/messages.md)

*作成し、Windows の破棄*

- [一般的なウィンドウ作成順序](../mfc/general-window-creation-sequence.md)

- [ウィンドウ オブジェクトを破棄します。](../mfc/destroying-window-objects.md)

- [ドキュメント フレーム ウィンドウを作成します。](../mfc/creating-document-frame-windows.md)

- [フレーム ウィンドウを破棄します。](../mfc/destroying-frame-windows.md)

*Windows のスプリッターを作成します。*

- [分割ウィンドウを作成します。](../mfc/multiple-document-types-views-and-frame-windows.md)

*Windows の子と、現在のビューを管理します。*

- [MDI 子ウィンドウを管理します。](../mfc/managing-mdi-child-windows.md)

- [現在のビューを管理します。](../mfc/managing-the-current-view.md)

- [メニューのコントロール バー、およびアクセラレータを管理します。](../mfc/managing-menus-control-bars-and-accelerators.md)

*デバイス コンテキストおよびウィンドウ スタイルを使用します。*

- [デバイス コンテキストでペンやその他のグラフィック オブジェクトを使用します。](../mfc/graphic-objects.md)

- [MFC で作成したウィンドウのスタイルを変更します。](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>関連項目

[ユーザー インターフェイス要素](../mfc/user-interface-elements-mfc.md)<br/>
[ダイアログ ボックス](../mfc/dialog-boxes.md)<br/>
[ツールバー](../mfc/toolbars.md)<br/>
[ステータス バー](../mfc/status-bars.md)<br/>
[ダイアログ バー](../mfc/dialog-bars.md)
