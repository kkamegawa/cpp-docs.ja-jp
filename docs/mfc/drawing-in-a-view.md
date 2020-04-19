---
title: ビューの描画
ms.date: 11/04/2016
helpviewer_keywords:
- drawing [MFC], in views
- views [MFC], printing
- views [MFC], updating
- printing [MFC], views
- views [MFC], rendering
- printing views [MFC]
- paint messages in view class [MFC]
- device contexts, screen drawings
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
ms.openlocfilehash: bc461347b56379976cdf62014507e3a15529f081
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408025"
---
# <a name="drawing-in-a-view"></a>ビューの描画

ビューは、アプリケーションのほぼすべての描画`OnDraw`メンバー関数は、ビュー クラスでオーバーライドする必要があります。 (例外は、描画、マウス[を解釈するユーザー入力ビューを使用した](../mfc/interpreting-user-input-through-a-view.md))。`OnDraw`をオーバーライドします。

1. ドキュメントの指定したメンバー関数を呼び出すことによって、データを取得します。

1. フレームワークからに渡されるデバイス コンテキスト オブジェクトのメンバー関数を呼び出すことによって、データを表示します。`OnDraw`します。

ドキュメントのデータが何らかの方法で変更、ビューは、変更を反映するように再描画する必要があります。 通常、ユーザーがドキュメントのビューでの変更を行ったときにこれが発生します。 この場合、ビューがドキュメントを呼び出す[UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)メンバー関数は同一のドキュメントを更新するようにすべてのビューに通知します。 `UpdateAllViews` それぞれのビューを呼び出す[OnUpdate](../mfc/reference/cview-class.md#onupdate)メンバー関数。 既定の実装`OnUpdate`ビューのクライアント領域全体を無効になります。 ドキュメントの変更後の部分に割り当てられたクライアント領域の領域のみを無効にする上書きすることができます。

`UpdateAllViews`クラスのメンバー関数`CDocument`と`OnUpdate`クラスのメンバー関数`CView`変更されたドキュメントのどの部分を記述する情報を渡すようにします。 この「ヒント」メカニズムでは、ビューの再描画する領域を制限できます。 `OnUpdate` 「ヒント」の 2 つの引数を受け取ります。 まず、 *lHint*、型の**LPARAM**の 2 番目のように、データの受け渡しすることができます*pHint*、型の`CObject`*、派生したオブジェクトにポインターを渡すことができます`CObject`します。

ビューが無効になると、Windows 送信、 **WM_PAINT**メッセージ。 ビューの[OnPaint](../mfc/reference/cwnd-class.md#onpaint)ハンドラー関数がクラスのデバイス コンテキスト オブジェクトを作成して、メッセージに応答[CPaintDC](../mfc/reference/cpaintdc-class.md)呼び出しビューのおよび`OnDraw`メンバー関数。 書き込むをオーバーライドする通常必要は`OnPaint`ハンドラー関数。

A[デバイス コンテキスト](../mfc/device-contexts.md)ディスプレイやプリンターなどのデバイスの描画属性に関する情報を格納する Windows のデータ構造です。 すべての描画呼び出しは、デバイス コンテキスト オブジェクトを介して行われます。 画面に描画するため`OnDraw`が渡される、`CPaintDC`オブジェクト。 プリンターでの描画に渡される、 [CDC](../mfc/reference/cdc-class.md)オブジェクトの現在のプリンターを設定します。

ビューを描画するため、コードはまず、ドキュメントへのポインターを取得し、デバイス コンテキストから描画呼び出しを実行します。 以下の単純な`OnDraw`の例は、プロセスを示しています。

[!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]

この例で定義して、`GetData`ドキュメントの派生クラスのメンバーとして機能します。

例では、ビューの中央に、ドキュメントから取得した文字列を出力します。 場合、`OnDraw`画面の描画の呼び出しは、`CDC`で渡されるオブジェクト*pDC*は、`CPaintDC`コンス トラクターは既に呼び出されて`BeginPaint`します。 関数の描画呼び出しは、デバイス コンテキスト ポインターを通じて行われます。 デバイス コンテキストおよび描画呼び出しについては、クラスを参照してください。 [CDC](../mfc/reference/cdc-class.md)で、 *MFC リファレンス*と[ウィンドウ オブジェクトの操作](../mfc/working-with-window-objects.md)します。

記述する方法の例について`OnDraw`を参照してください、 [MFC サンプル](../overview/visual-cpp-samples.md)します。

## <a name="see-also"></a>関連項目

[ビューの使い方](../mfc/using-views.md)
