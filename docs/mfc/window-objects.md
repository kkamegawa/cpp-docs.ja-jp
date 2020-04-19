---
title: ウィンドウ オブジェクト
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], window
- Windows window [MFC]
- MFC, windows
- frame windows [MFC], C++ window objects
- window objects [MFC]
- windows [MFC], C++ window objects
- window messages [MFC]
- HWND
- messages [MFC], Windows
- Visual C++, window objects [MFC]
- HWND, window objects [MFC]
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
ms.openlocfilehash: b62f43aa0d37c5e614636b3d7543bc927d41039b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378077"
---
# <a name="window-objects"></a>ウィンドウ オブジェクト

MFC クラスを提供する[CWnd](../mfc/reference/cwnd-class.md)をカプセル化する、`HWND`ウィンドウのハンドル。 `CWnd`オブジェクトは、C++ ウィンドウ オブジェクト、異なる、`HWND`を表す、Windows のウィンドウが、それを含むです。 使用して、`CWnd`子ウィンドウを派生するクラス、または多くの MFC クラスのいずれかから派生した`CWnd`します。 クラス`CWnd`フレーム ウィンドウ、ダイアログ ボックス、子ウィンドウ、コントロール、およびツールバーなどのコントロール バーを含む、すべての windows の基本クラスです。 十分に理解[C++ ウィンドウ オブジェクトと HWND の関係](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)MFC で効果的なプログラミングの非常に重要です。

MFC には、いくつかの既定の機能と、windows の管理が用意されていますが、独自のクラスから派生させることができます、`CWnd`そのメンバー関数を使用して、提供される機能をカスタマイズするとします。 作成することにより、子ウィンドウを作成できます、`CWnd`オブジェクトと呼び出し元の[作成](../mfc/reference/cwnd-class.md#create)メンバー関数は、次を使用して子ウィンドウをカスタマイズ`CWnd`メンバー関数。 派生したオブジェクトを埋め込むことができます[CView](../mfc/reference/cview-class.md)、フォーム ビューのフレーム ウィンドウのツリー ビューなど。 クラスで提供される、スプリッター ウィンドウからドキュメントの複数のビューをサポートできると[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)します。

クラスから派生した各オブジェクト`CWnd`メッセージ マップ使用する Windows メッセージのマッピングまたはコマンドのハンドラーを独自に Id にはが含まれています。

Windows が使用する方法を学習するための適切なリソースをプログラミングで一般的な資料、`CWnd`をカプセル化するメンバー関数、 `HWND` Api。

## <a name="functions-for-operating-on-a-cwnd"></a>CWnd に対する操作のための関数

`CWnd` その[ウィンドウ クラスを派生](../mfc/derived-window-classes.md)コンス トラクター、デストラクター、およびメンバー関数、オブジェクトを初期化するために、基になる Windows 構造体を作成し、カプセル化されたアクセスを提供`HWND`します。 `CWnd` ウィンドウの状態、更新、座標変換へのアクセス、メッセージを送信するための Windows Api をカプセル化するメンバー関数も提供スクロール、クリップボード、およびその他の多くのタスクにアクセスします。 実行するほとんどの Windows ウィンドウ管理 Api、`HWND`引数がのメンバー関数としてカプセル化された`CWnd`します。 関数とそのパラメーターの名前が保持、`CWnd`メンバー関数。 詳細については、Windows Api によってカプセル化された`CWnd`、クラスを参照してください。 [CWnd](../mfc/reference/cwnd-class.md)します。

## <a name="cwnd-and-windows-messages"></a>CWnd と Windows メッセージ

1 つの主な目的の`CWnd`WM_PAINT か WM_MOUSEMOVE などの Windows メッセージを処理するためのインターフェイスを提供することです。 メンバー関数の多くは`CWnd`は標準のメッセージのハンドラー: 識別子で始まる**afx_msg** 「で、」プレフィックスとなど`OnPaint`と`OnMouseMove`します。 [メッセージの処理とマップ](../mfc/message-handling-and-mapping.md)メッセージとメッセージ処理の詳細について説明します。 情報は、フレームワークの windows および特別な目的で作成したものに当てはまります。

### <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [C++ ウィンドウ オブジェクトと HWND の関係](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)

- [ウィンドウ クラスの派生](../mfc/derived-window-classes.md)

- [ウィンドウの作成](../mfc/creating-windows.md)

- [ウィンドウ オブジェクトの破棄](../mfc/destroying-window-objects.md)

- [CWnd と HWND の分離](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [ウィンドウ オブジェクトの操作](../mfc/working-with-window-objects.md)

- [デバイス コンテキスト](../mfc/device-contexts.md): Windows デバイスの描画を独立させるオブジェクト

- [グラフィック オブジェクト](../mfc/graphic-objects.md): ペン、ブラシ、フォント、ビットマップ、パレット、リージョン

## <a name="see-also"></a>関連項目

[Windows](../mfc/windows.md)
