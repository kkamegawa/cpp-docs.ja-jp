---
title: ウィンドウ クラスの派生
ms.date: 11/04/2016
helpviewer_keywords:
- window class hierarchy
- hierarchies, window classes
- classes [MFC], derived
- CWnd class [MFC], classes derived from
- derived classes [MFC], window classes
- window classes [MFC], derived
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
ms.openlocfilehash: e86ca139b8470dce614564f0c0134a611adeda2c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153379"
---
# <a name="derived-window-classes"></a>ウィンドウ クラスの派生

Windows から直接作成できます[CWnd](../mfc/reference/cwnd-class.md)から新しいウィンドウ クラスを派生または`CWnd`します。 これは、独自のカスタム ウィンドウを作成する一般的な方法です。 ただし、フレームワーク プログラムで使用されるほとんどのウィンドウは、MFC に用意されている、`CWnd` から派生するフレーム ウィンドウ クラスのいずれかから作成されます。

## <a name="frame-window-classes"></a>フレーム ウィンドウ クラス

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
単一ドキュメントとそのビューを囲む SDI フレーム ウィンドウに使用されます。 フレーム ウィンドウは、アプリケーションのメイン フレーム ウィンドウであり、現在のドキュメントのフレーム ウィンドウでもあります。

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
MDI アプリケーションのメイン フレーム ウィンドウとして使用されます。 メイン フレーム ウィンドウは、すべての MDI ドキュメント ウィンドウのコンテナーであり、そのメニュー バーを MDI ドキュメント ウィンドウと共有します。 MDI フレーム ウィンドウはデスクトップに表示される最上位ウィンドウです。

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
MDI メイン フレーム ウィンドウで開かれる個々のドキュメントに使用されます。 各ドキュメントとそのビューは、MDI メイン フレーム ウィンドウに含まれている MDI 子フレーム ウィンドウの中に収まります。 MDI 子ウィンドウの外観は一般的なフレーム ウィンドウと非常に似ていますが、デスクトップ上に表示されるのではなく、MDI フレーム ウィンドウの内部に格納されます。 ただし、MDI 子ウィンドウには独自のメニュー バーがなく、それを含む MDI フレーム ウィンドウのメニュー バーを共有する必要があります。

詳細については、次を参照してください。[フレーム Windows](../mfc/frame-windows.md)します。

## <a name="other-window-classes-derived-from-cwnd"></a>CWnd から派生するその他のウィンドウ クラス

フレーム ウィンドウに加え、次に示すその他のいくつかの主なウィンドウ カテゴリが `CWnd` から派生しています。

*ビュー*<br/>
ビューを作成するを使用して、 `CWnd`-クラスを派生[CView](../mfc/reference/cview-class.md) (またはその派生クラスのいずれか)。 ビューはドキュメントにアタッチされ、ドキュメントとユーザーの仲介役として機能します。 ビューは、一般に SDI フレーム ウィンドウまたは MDI 子フレーム ウィンドウのクライアント領域 (または、ツール バーやステータス バーで占有されていないクライアント領域の部分) を占める子ウィンドウです (MDI 子ウィンドウではありません)。

*ダイアログ ボックス*<br/>
ダイアログ ボックスを使用して作成、 `CWnd`-クラスを派生[CDialog](../mfc/reference/cdialog-class.md)します。

*フォーム*<br/>
クラスを使用して、ダイアログ ボックスなどのダイアログ テンプレート リソースに基づくフォーム ビューが作成された[CFormView](../mfc/reference/cformview-class.md)、 [CRecordView](../mfc/reference/crecordview-class.md)、または[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)します。

*コントロール*<br/>
ボタン、リスト ボックス、コンボ ボックスなどのコントロールは、`CWnd` から派生する他のクラスを使用して作成されます。 参照してください[制御トピック](../mfc/controls-mfc.md)します。

*コントロール バー*<br/>
コントロールを含む子ウィンドウ。 たとえば、ツール バーやステータス バーが該当します。 参照してください[コントロール バー](../mfc/control-bars.md)します。

## <a name="window-class-hierarchy"></a>ウィンドウ クラスの階層構造

参照してください、 [MFC 階層グラフ](../mfc/hierarchy-chart.md)で、 *MFC リファレンス*します。 ビューについてで[ドキュメント/ビュー アーキテクチャ](../mfc/document-view-architecture.md)します。 ダイアログ ボックスについてで[ ダイアログ ボックス](../mfc/dialog-boxes.md)します。

## <a name="creating-your-own-special-purpose-window-classes"></a>独自の特殊用途ウィンドウ クラスの作成

クラス ライブラリに用意されているウィンドウ クラスに加えて、特殊用途の子ウィンドウが必要な場合があります。 このようなウィンドウを作成するには、独自に作成[CWnd](../mfc/reference/cwnd-class.md)-クラスを派生し、フレームまたはビューの子ウィンドウになります。 フレームワークは、ドキュメントのフレーム ウィンドウのクライアント領域の範囲を管理することに注意してください。 クライアント領域のほとんどはビューによって管理されますが、コントロール バーや独自のカスタム ウィンドウなど、他のウィンドウは、ビューと領域を共有する場合があります。 クラスの機構を操作する必要があります[CView](../mfc/reference/cview-class.md)と[CControlBar](../mfc/reference/ccontrolbar-class.md)フレーム ウィンドウのクライアント領域内の子ウィンドウの位置を指定します。

[Windows を作成する](../mfc/creating-windows.md)ウィンドウ オブジェクトと、windows の管理の作成について説明します。

## <a name="see-also"></a>関連項目

[Window オブジェクト](../mfc/window-objects.md)
