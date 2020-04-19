---
title: '方法: コードでのトラッカーを実装します。'
ms.date: 11/04/2016
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
ms.openlocfilehash: 0f037480e83b8ca1ba12af56904afe25a33e4d6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160303"
---
# <a name="how-to-implement-tracking-in-your-code"></a>方法: コードでのトラッカーを実装します。

OLE 項目を追跡するには、項目をクリックするか、ドキュメントのビューの更新などのアイテムに関連する特定のイベントを処理する必要があります。 すべてのケースでは、一時的なを宣言するための十分な[CRectTracker](../mfc/reference/crecttracker-class.md)オブジェクトし、このオブジェクトを使用して、項目を操作します。

ユーザーが項目を選択するか、メニュー コマンドを使用してオブジェクトを挿入、OLE 項目の状態を示す適切なスタイルを使用してトラッカーを初期化する必要があります。 次の表では、OCLIENT サンプルで使用される規則について説明します。 これらのスタイルの詳細については、次を参照してください。`CRectTracker`します。

### <a name="container-styles-and-states-of-the-ole-item"></a>コンテナーのスタイルと OLE 項目の状態

|表示スタイル|OLE 項目の状態|
|---------------------|-----------------------|
|点線の枠|項目がリンクされています。|
|実線の境界線|項目は、ドキュメントに埋め込まれました。|
|サイズ変更ハンドル|項目が現在選択されています。|
|網掛け境界線|現在の実行中の項目が|
|() の陰影パターン オーバーレイ項目|項目のサーバーが開く|

OLE 項目の状態をチェックし、適切なスタイルを設定する手順を使用して簡単にこの初期化を処理することができます。 `SetupTracker` Oclient にある関数の追跡ツールの初期化を示します。 この関数のパラメーターは、トラッカーのアドレス*pTracker*トラッカーに関連付けられているクライアント アイテムへのポインターです*pItem*; と四角形を指すポインター *pTrueRect*. この関数のより完全な例は、MFC OLE サンプルを参照してください。 [OCLIENT](../overview/visual-cpp-samples.md)します。

**SetupTracker**のコード例は、1 つの関数を表示します。 関数の行は、関数の機能の説明が混在して。

[!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]

トラッカーは、最小サイズを設定してトラッカーのスタイルをクリアすることにより初期化されます。

[!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]

次の行は、項目が現在選択されているかどうかと、項目のドキュメントにリンクまたはそれに埋め込まれているかどうかを確認します。 境界線の内側にあるサイズ変更ハンドルは、項目が現在選択されていることを示す、スタイルに追加されます。 項目は、ドキュメントにリンクしている場合は、ピリオドで区切られた罫線のスタイルが使用されます。 実線の境界線は、項目が埋め込まれている場合に使用されます。

[!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]

次のコードのオーバーレイ斜線のパターンを使用している場合は、現在の項目を持つ項目を開きます。

[!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]

トラッカー必要があるたびに、この関数を呼び出すことができます。 たとえばからこの関数を呼び出す、`OnDraw`ビュー クラスの関数。 これにより、ビューが再描画されるたびに、トラッカーの外観が更新されます。 完全な例を参照してください、`CMainView::OnDraw`の MFC OLE サンプル関数[OCLIENT](../overview/visual-cpp-samples.md)します。

アプリケーションでは、サイズ変更、移動、またはヒットが検出されなどの追跡ツールのコードを必要とするイベントが発生します。 これらのアクションでは、通常の試行が選択またはアイテムを移動行わことを示します。 このような場合は、取得が何を決定する必要があります。 サイズ変更ハンドルまたはその一部の間の境界線のサイズ変更ハンドル。 `OnLButtonDown`メッセージ ハンドラーは、項目に関係するマウスの位置をテストすることをお勧めします。 呼び出す`CRectTracker::HitTest`します。 テストが以外の値を返す場合`CRectTracker::hitOutside`、項目がサイズを変更または移動します。 そのためへの呼び出しをする必要があります、`Track`メンバー関数。 参照してください、`CMainView::OnLButtonDown`関数は、MFC OLE サンプルである[OCLIENT](../overview/visual-cpp-samples.md)完全な例です。

`CRectTracker`クラスには、操作が行わスレッドで、移動、サイズ変更、またはドラッグするかどうかを示すために使用するいくつかの異なるカーソル図形が用意されています。 このイベントを処理するために、マウスの下に現在の項目が選択されているかどうかを確認します。 呼び出しを行う場合は、 `CRectTracker::SetCursor`、または既定のハンドラーを呼び出します。 次の例は、MFC OLE サンプル[OCLIENT](../overview/visual-cpp-samples.md):

[!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]

## <a name="see-also"></a>関連項目

[トラッカー:OLE アプリケーションでのトラッカーの実装](../mfc/trackers-implementing-trackers-in-your-ole-application.md)
