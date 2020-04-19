---
title: ActiveX コントロール コンテナー:ダイアログではないコンテナーでコントロールの使用
ms.date: 11/04/2016
helpviewer_keywords:
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
ms.openlocfilehash: 70a67a6952d5361177b89e3ba514d7036b5799b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394872"
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>ActiveX コントロール コンテナー:ダイアログではないコンテナーでコントロールの使用

一部 SDI などのアプリケーションまたは MDI アプリケーションでは、アプリケーションのウィンドウにコントロールを埋め込むにはします。 **作成**、Visual C によって挿入された、ラッパー クラスのメンバー関数は、ダイアログ ボックスを必要としない、コントロールのインスタンスを動的に作成できます。

**作成**メンバー関数は、次のパラメーター。

*lpszWindowName*<br/>
(ある場合)、コントロールのテキストまたはキャプション プロパティに表示されるテキストへのポインター。

*dwStyle*<br/>
Windows のスタイル。 完全な一覧についてを参照してください。 [cwnd::createcontrol](../mfc/reference/cwnd-class.md#createcontrol)します。

*rect*<br/>
コントロールのサイズと位置を指定します。

*pParentWnd*<br/>
通常、コントロールの親ウィンドウを指定します、`CDialog`します。 できません**NULL**します。

*nID*<br/>
コントロールの ID を指定し、コントロールを参照するコンテナーで使用できます。

この関数を使用して ActiveX コントロールを動的に作成する 1 つの例は、SDI アプリケーションのフォーム ビューになります。 内のコントロールのインスタンスを作成できますし、`WM_CREATE`アプリケーションのハンドラー。

この例では、`CMyView`メイン ビュー クラスでは、`CCirc`はラッパー クラスと可変範囲H はヘッダー (します。H) ファイルのラッパー クラスです。

この機能の実装は、4 つの手順から成るプロセスです。

### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>非ダイアログ ウィンドウで、ActiveX コントロールを動的に作成するには

1. 可変範囲を挿入します。H CMYVIEW にします。H、直前に、`CMyView`クラスの定義。

   [!code-cpp[NVC_MFC_AxCont#12](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]

1. メンバー変数を追加 (型の`CCirc`) の保護されたセクションに、`CMyView`クラス CMYVIEW に定義します。H:

   [!code-cpp[NVC_MFC_AxCont#13](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]
    [!code-cpp[NVC_MFC_AxCont#14](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]

1. 追加、`WM_CREATE`メッセージ ハンドラー クラスを`CMyView`します。

1. ハンドラー関数で`CMyView::OnCreate`、コントロールの呼び出しを行う`Create`関数を使用して、**this**親ウィンドウとしてのポインター。

   [!code-cpp[NVC_MFC_AxCont#15](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]

1. プロジェクトをリビルドします。 円のコントロールは、アプリケーションのビューが作成されるたびに動的に作成されます。

## <a name="see-also"></a>関連項目

[ActiveX コントロール コンテナー](../mfc/activex-control-containers.md)
