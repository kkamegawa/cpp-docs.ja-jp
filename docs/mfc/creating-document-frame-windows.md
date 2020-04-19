---
title: ドキュメント フレーム ウィンドウの作成
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
ms.openlocfilehash: 66a951994a75cbd99debeb2c6511739411cdd470
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174030"
---
# <a name="creating-document-frame-windows"></a>ドキュメント フレーム ウィンドウの作成

[ドキュメント/ビューの作成](../mfc/document-view-creation.md)を示していますが、どのように[CDocTemplate](../mfc/reference/cdoctemplate-class.md)オブジェクトは、フレーム ウィンドウ、ドキュメント、およびビューを作成し、それらすべてをまとめて接続を調整します。 次の 3 つ[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)への引数、`CDocTemplate`コンス トラクターは、フレーム ウィンドウ、ドキュメント、およびドキュメント テンプレートでファイルを新しいコマンドなどのユーザー コマンドへの応答で動的に作成されるビュー クラスを指定メニューまたは MDI ウィンドウ メニューには、[新規ウィンドウ] コマンド。 ドキュメント テンプレートは、ビューとドキュメントのフレーム ウィンドウを作成するときに、後で使用するためには、この情報を格納します。

[RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class)派生が正常に動作するためのメカニズムでフレーム ウィンドウ クラスを宣言する必要があります、 [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate)マクロ。 これは、フレームワークは、フレーム ウィンドウのクラスの動的生成メカニズムを使用してドキュメントを作成する必要があるため`CObject`します。

ユーザーがドキュメントを作成するコマンドを選択すると、ドキュメント オブジェクト、そのビュー、およびビューを表示するフレーム ウィンドウを作成するドキュメント テンプレートとフレームワークが呼び出します。 ドキュメント テンプレートが適切なクラスのオブジェクトを作成して、ドキュメント フレーム ウィンドウの作成時から派生したクラス[CFrameWnd](../mfc/reference/cframewnd-class.md) SDI アプリケーションまたはから[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) MDI のアプリケーション。 フレームワークを呼び出して、フレーム ウィンドウ オブジェクトの[LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)メンバー関数はリソースから作成情報を取得し、Windows のウィンドウを作成します。 フレームワークは、ウィンドウ ハンドルをフレーム ウィンドウ オブジェクトにアタッチします。 ドキュメント フレーム ウィンドウの子ウィンドウとして、ビューを作成します。

決定するときに注意が必要です。[初期化のタイミング](../mfc/when-to-initialize-cwnd-objects.md)、 `CWnd`-派生オブジェクト。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [(動的な作成メカニズムはその) CObject からクラスの派生](../mfc/deriving-a-class-from-cobject.md)

- [ドキュメント/ビューの作成 (テンプレートとフレーム ウィンドウの作成)](../mfc/document-view-creation.md)

- [フレーム ウィンドウの破棄](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>関連項目

[フレーム ウィンドウの使用](../mfc/using-frame-windows.md)
