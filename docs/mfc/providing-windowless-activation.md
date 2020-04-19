---
title: ウィンドウなしのアクティベーション
ms.date: 11/04/2016
helpviewer_keywords:
- windowless activation of MFC ActiveX controls
- activation [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], activate options
- activation [MFC], windowless
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
ms.openlocfilehash: 9d60c309d5644c106e6c85a0c7b3988916be7193
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386773"
---
# <a name="providing-windowless-activation"></a>ウィンドウなしのアクティベーション

ウィンドウを作成するコード (つまりを呼び出すときに発生するすべて`CreateWindow`) を実行するコストがかかります。 保持するコントロールを画面に表示されるウィンドウには、ウィンドウのメッセージを管理します。 ウィンドウなしのコントロールはウィンドウを持つコントロールよりも高速ではそのためです。

ウィンドウなしのコントロールの利点はさらは、ウィンドウのコントロールとは異なりウィンドウなしのコントロール サポート透過的な描画や四角形以外の画面領域です。 透明なコントロールの一般的な例は、透明の背景にテキスト コントロールです。 コントロールでは、テキストが、バック グラウンドではないため、あるものはすべて、テキストが透けてに描画します。 新しいフォームは、矢印などの四角形以外のコントロールを使用し、丸いボタンしまいがちです。

多くの場合、独自のウィンドウの必要はありませんし、代わりに、サービスを利用できるウィンドウ、コンテナーのウィンドウなしのオブジェクトをサポートするために、コンテナーが書き込まれたことです。 ウィンドウなしのコントロールは、古いコンテナーとの下位互換性です。 ウィンドウなしのコントロールをサポートするためには書き込まれません、古いコンテナーでは、ウィンドウなしのコントロールは、アクティブな際のウィンドウを作成します。

ウィンドウなしのコントロールは独自のウィンドウがあるないため、コンテナー (これには、ウィンドウが) は、コントロールのウィンドウで提供されてそれ以外の場合はサービスを提供する責任を負います。 たとえばをコントロールがキーボード フォーカスを照会、マウスのキャプチャ、またはデバイス コンテキストを取得する必要がある場合は、これらの操作がコンテナーによって管理されます。 コンテナーは、適切なウィンドウなしのコントロールには、そのウィンドウに送信されるユーザー入力メッセージをルーティングを使用して、`IOleInPlaceObjectWindowless`インターフェイス。 (を参照してください、 *ActiveX SDK*このインターフェイスの説明についてはします)。`COleControl`メンバー関数は、コンテナーからこれらのサービスを呼び出します。

ウィンドウなしのアクティベーションを使用して、コントロールを作成するには含める、 **windowlessActivate**フラグによって返される一連のフラグ[オン](../mfc/reference/colecontrol-class.md#getcontrolflags)します。 例:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-windowless-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/cpp/providing-windowless-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-windowless-activation_3.cpp)]

選択した場合、このフラグを追加するコードが自動的に生成、**ウィンドウなしのアクティベーション**オプションを[コントロール設定](../mfc/reference/control-settings-mfc-activex-control-wizard.md)MFC ActiveX コントロール ウィザードのページ。

コンテナーがコントロールの入力メッセージを委任するウィンドウなしのアクティベーションを有効にすると、`IOleInPlaceObjectWindowless`インターフェイス。 `COleControl`このインターフェイスの実装は、マウスの調整を適切に調整した後に、コントロールのメッセージ マップを通じてメッセージをディスパッチします。 メッセージ マップに対応するエントリを追加することで、通常のウィンドウ メッセージなどのメッセージを処理できます。 これらのメッセージのハンドラーでは、使用しないように、 *m_hWnd*メンバー変数 (またはそれを使用する任意のメンバー関数) の値が最初に確認**NULL**します。

`COleControl` マウスのキャプチャ、キーボード フォーカス、スクロール、およびなど、必要に応じて、コンテナーからその他のウィンドウ サービスを呼び出すメンバー関数を提供します。

- [GetFocus](../mfc/reference/colecontrol-class.md#getfocus)、 [SetFocus](../mfc/reference/colecontrol-class.md#setfocus)

- [GetCapture](../mfc/reference/colecontrol-class.md#getcapture)、 [SetCapture](../mfc/reference/colecontrol-class.md#setcapture)、 [ReleaseCapture](../mfc/reference/colecontrol-class.md#releasecapture)

- [GetDC](../mfc/reference/colecontrol-class.md#getdc)、 [ReleaseDC](../mfc/reference/colecontrol-class.md#releasedc)

- [InvalidateRgn](../mfc/reference/colecontrol-class.md#invalidatergn)

- [ScrollWindow](../mfc/reference/colecontrol-class.md#scrollwindow)

- [GetClientRect](../mfc/reference/colecontrol-class.md#getclientrect)

ウィンドウなしのコントロールでは、常に使用して、`COleControl`メンバー関数、対応するのではなく`CWnd`メンバー関数またはその関連する Win32 API 関数。

ウィンドウなしのコントロールを OLE ドラッグ アンド ドロップ操作のターゲットにすることができます。 通常、このコントロールのウィンドウは、ドロップ先として登録する必要があります。 コントロールに、独自のウィンドウがあるないため、コンテナーは、ドロップ先として、独自のウィンドウを使用します。 コントロールの実装を提供する、`IDropTarget`インターフェイスをコンテナーは、適切な時点の呼び出しを委任できます。 コンテナーにこのインターフェイスを公開するには、オーバーライド[COleControl::GetWindowlessDropTarget](../mfc/reference/colecontrol-class.md#getwindowlessdroptarget)します。 例:

[!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/cpp/providing-windowless-activation_4.cpp)]

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール: 最適化](../mfc/mfc-activex-controls-optimization.md)
