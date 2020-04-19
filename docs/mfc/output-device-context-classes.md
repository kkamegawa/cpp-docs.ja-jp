---
title: 出力 (デバイス コンテキスト) クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.output
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
ms.openlocfilehash: 1d76570e7bfd4ce587b3803235394ec5406d30b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410201"
---
# <a name="output-device-context-classes"></a>出力 (デバイス コンテキスト) クラス

これらのクラスには、Windows で使用可能なデバイス コンテキストのさまざまな種類がカプセル化します。

次のクラスのほとんどは、Windows デバイス コンテキストを識別するハンドルをカプセル化します。 デバイス コンテキストは、ディスプレイやプリンターなどのデバイスの描画属性に関する情報を含む Windows オブジェクトです。 すべての描画呼び出しは、デバイス コンテキスト オブジェクトを介して行われます。 その他のクラスから派生した`CDC`Windows メタファイルのサポートなど、特殊化されたデバイス コンテキストの機能をカプセル化します。

[CDC](../mfc/reference/cdc-class.md)<br/>
デバイス コンテキストの基本クラスです。 画面全体にアクセスするためには、直接、プリンターなどのディスプレイ コンテキストにアクセスするために使用されます。

[CPaintDC](../mfc/reference/cpaintdc-class.md)<br/>
使用されるディスプレイ コンテキスト`OnPaint`windows のメンバー関数。 自動的に呼び出します`BeginPaint`コンス トラクターでと`EndPaint`消滅します。

[CClientDC](../mfc/reference/cclientdc-class.md)<br/>
Windows のクライアント領域のディスプレイ コンテキスト。 マウス イベントをすぐに応答を描画するときに使用など。

[CWindowDC](../mfc/reference/cwindowdc-class.md)<br/>
クライアントと非クライアント領域を含む、全体の windows のディスプレイ コンテキスト。

[CMetaFileDC](../mfc/reference/cmetafiledc-class.md)<br/>
Windows メタファイル デバイス コンテキスト。 Windows メタファイルには、イメージを作成するために再生できますグラフィック デバイス インターフェイス (GDI) コマンドのシーケンスが含まれています。 メンバー関数への呼び出しを`CMetaFileDC`メタファイルに記録されます。

## <a name="related-classes"></a>関連するクラス

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
(X, y) 座標ペアの保持されます。

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
距離、相対位置、または値のペアを保持します。

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
四角形領域の座標を保持します。

[CRgn](../mfc/reference/crgn-class.md)<br/>
ウィンドウ内の楕円、多角形、または不定期的な領域を操作するための GDI 領域をカプセル化します。 クラスのクリッピングのメンバー関数と組み合わせて使用`CDC`します。

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
表示し、サイズ変更および四角形のオブジェクトを移動するためのユーザー インターフェイスを処理します。

[CColorDialog](../mfc/reference/ccolordialog-class.md)<br/>
色を選択するためには、標準のダイアログ ボックスを提供します。

[CFontDialog](../mfc/reference/cfontdialog-class.md)<br/>
フォントを選択するためには、標準のダイアログ ボックスを提供します。

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
ファイルの印刷には、標準のダイアログ ボックスを提供します。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
