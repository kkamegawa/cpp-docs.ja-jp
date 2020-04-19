---
title: フレーム ウィンドウ クラス
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], about frame window classes
- frame window classes [MFC]
- windows [MFC], MDI
- document frame windows [MFC], classes
- single document interface (SDI), frame windows
- window classes [MFC], frame
- MFC, frame windows
- MDI [MFC], frame windows
- classes [MFC], window
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
ms.openlocfilehash: d42fa475fca7c92e4ba46b164a9beda9869231c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219783"
---
# <a name="frame-window-classes"></a>フレーム ウィンドウ クラス

各アプリケーションでは、「メイン フレーム ウィンドウ」、デスクトップ ウィンドウを通常のキャプションでアプリケーション名を持つ 1 つがあります。 各ドキュメントが通常は 1 つの「ドキュメント フレーム ウィンドウ」 ドキュメント フレーム ウィンドウには、ドキュメントのデータを表示するには少なくとも 1 つのビューが含まれています。

## <a name="frame-windows-in-sdi-and-mdi-applications"></a>SDI と MDI アプリケーションでのフレームの Windows

SDI アプリケーションの場合は、1 つのフレーム ウィンドウ クラスから派生した[CFrameWnd](../mfc/reference/cframewnd-class.md)します。 このウィンドウはメイン フレーム ウィンドウとドキュメント フレーム ウィンドウの両方です。 MDI アプリケーションのメイン フレーム ウィンドウ クラスから派生して[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)、MDI 子ウィンドウには、ドキュメント フレーム ウィンドウ クラスから派生し、 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)します。

## <a name="use-the-frame-window-class-or-derive-from-it"></a>フレーム ウィンドウ クラスを使用またはそこから派生

これらのクラスは、ほとんどのアプリケーションに必要なフレーム ウィンドウ機能を提供します。 通常の状況で、既定の動作と外観を提供するは、ニーズに合うされます。 追加の機能が必要な場合は、これらのクラスから派生します。

### <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [アプリケーション ウィザードで作成されるフレーム ウィンドウ クラス](../mfc/frame-window-classes-created-by-the-application-wizard.md)

- [フレーム ウィンドウ スタイル](../mfc/frame-window-styles-cpp.md)

- [MFC で作成したウィンドウのスタイルを変更します。](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>関連項目

[フレーム ウィンドウ](../mfc/frame-windows.md)
