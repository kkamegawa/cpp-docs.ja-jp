---
title: ファイルのフレーム ウィンドウへのドラッグ アンド ドロップ
ms.date: 11/04/2016
helpviewer_keywords:
- drag and drop [MFC], files
- drag and drop [MFC], File Manager
- Windows Explorer [MFC]
- File Manager drag and drop support [MFC]
- files [MFC], drag and drop
- frame windows [MFC], dragging and dropping files in
- drag and drop [MFC], Windows Explorer
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
ms.openlocfilehash: 0129b939e0fe2afd5dd29623bb44418bfd16c20d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240661"
---
# <a name="dragging-and-dropping-files-in-a-frame-window"></a>ファイルのフレーム ウィンドウへのドラッグ アンド ドロップ

フレーム ウィンドウは、ファイル エクスプ ローラーまたはファイル マネージャーとの関係を管理します。

オーバーライドで呼び出し、いくつかの初期化を追加、`CWinApp`メンバー関数は`InitInstance`」の説明に従って、 [CWinApp:アプリケーション クラス](../mfc/cwinapp-the-application-class.md)、フレーム ウィンドウにファイル エクスプ ローラーまたはファイル マネージャーからドラッグ アンド ドロップ ファイルを直接開くフレーム ウィンドウがあることができます。 参照してください[ファイル マネージャーでのドラッグ アンド ドロップ](../mfc/special-cwinapp-services.md)します。

## <a name="see-also"></a>関連項目

[フレーム ウィンドウの使用](../mfc/using-frame-windows.md)
