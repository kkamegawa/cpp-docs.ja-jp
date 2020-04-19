---
title: 既定の印刷プロセス
ms.date: 11/04/2016
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
ms.openlocfilehash: 5019bcad769c4b7cdb699facef145a21d9b5e11c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508429"
---
# <a name="how-default-printing-is-done"></a>既定の印刷プロセス

この記事では、MFC フレームワークに関して、Windows の既定の印刷プロセスについて説明します。

MFC アプリケーションでは、ビュークラスにという名前`OnDraw`のメンバー関数があります。この関数には、すべての描画コードが含まれています。 `OnDraw`[CDC](../mfc/reference/cdc-class.md)オブジェクトへのポインターをパラメーターとして取得します。 このオブジェクトは、によって`OnDraw`生成されるイメージを受け取るデバイスコンテキストを表します。 `CDC` ドキュメントを表示しているウィンドウが[WM_PAINT](/windows/win32/gdi/wm-paint)メッセージを受信すると`OnDraw` 、フレームワークはを呼び出し、画面のデバイスコンテキスト (具体的には[CPaintDC](../mfc/reference/cpaintdc-class.md)オブジェクト) を渡します。 これに`OnDraw`より、の出力が画面に移動します。

Windows のプログラミングでは、プリンターに出力を送信することは、画面に出力を送信することとよく似ています。 これは、Windows グラフィックデバイスインターフェイス (GDI) がハードウェアに依存しないためです。 画面表示や印刷には、適切なデバイスコンテキストを使用するだけで、同じ GDI 関数を使用できます。 を`CDC` 受け取る`OnDraw`オブジェクトがプリンターを表している`OnDraw`場合、の出力はプリンターに送られます。

ここでは、MFC アプリケーションで簡単な印刷を実行する方法について説明します。 フレームワークでは、[印刷] ダイアログボックスを表示し、プリンターのデバイスコンテキストを作成します。 ユーザーが [ファイル] メニューから [印刷] コマンドを選択すると、このデバイスコンテキスト`OnDraw`は、プリンター上のドキュメントを描画するに渡されます。

ただし、印刷と画面表示には大きな違いがいくつかあります。 印刷するときは、ウィンドウに表示されている部分を表示するのではなく、ドキュメントを個別のページに分割し、一度に1つずつ表示する必要があります。 当然のことながら、用紙のサイズ (レターサイズ、リーガルサイズ、または封筒) に注意する必要があります。 横または縦モードなど、異なる向きで印刷することができます。 Microsoft Foundation Class ライブラリは、アプリケーションがこれらの問題をどのように処理するかを予測できないため、これらの機能を追加するためのプロトコルを提供します。

このプロトコルの詳細については、「[マルチページドキュメント](../mfc/multipage-documents.md)」を参照してください。

## <a name="see-also"></a>関連項目

[印刷](../mfc/printing.md)
