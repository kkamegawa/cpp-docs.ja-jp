---
title: 一般的なウィンドウ作成順序
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: 949cf72910654b502ca4b57be72bedc2db63c315
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219566"
---
# <a name="general-window-creation-sequence"></a>一般的なウィンドウ作成順序

フレームワークではるかのと同じプロセスを使用して、説明した子などの独自のウィンドウのウィンドウを作成するときに[ドキュメント/ビューの作成](../mfc/document-view-creation.md)です。

MFC の採用によって提供されるすべてのウィンドウ クラス[2 段階構築](../mfc/one-stage-and-two-stage-construction-of-objects.md)します。 つまり、C++ の呼び出し中に**新しい**演算子、コンス トラクターは、割り当てと C++ オブジェクトを初期化しますが、対応する Windows ウィンドウを作成できません。 後で呼び出すことによって実現されます、[作成](../mfc/reference/cwnd-class.md#create)ウィンドウ オブジェクトのメンバー関数。

`Create`メンバー関数は、Windows のウィンドウを格納してその`HWND`で、C++オブジェクトのパブリック データ メンバー [m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd)します。 `Create` 完全な作成パラメーターの柔軟性。 呼び出しの前に`Create`、グローバル関数をウィンドウ クラスを登録する[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)フレームのアイコンとクラスのスタイルを設定するためにします。

フレーム ウィンドウを使用することができます、 [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)メンバー関数の代わりに`Create`します。 `LoadFrame` 少ないパラメーターを使用して Windows のウィンドウになります。 フレームのキャプション、アイコン、アクセラレータ テーブル、およびメニューなどのリソースから多くの既定値を取得します。

> [!NOTE]
>  アイコン、アクセラレータ テーブル、およびメニュー リソースが必要、共通のリソース ID など**IDR_MAINFRAME**、LoadFrame によって読み込まれることにします。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ウィンドウ オブジェクト](../mfc/window-objects.md)

- [ウィンドウ「クラス」の登録](../mfc/registering-window-classes.md)

- [ウィンドウ オブジェクトの破棄](../mfc/destroying-window-objects.md)

- [ドキュメント フレーム ウィンドウの作成](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>関連項目

[ウィンドウの作成](../mfc/creating-windows.md)
