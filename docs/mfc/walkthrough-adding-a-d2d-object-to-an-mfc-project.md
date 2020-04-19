---
title: 'チュートリアル: MFC プロジェクトへの D2D オブジェクトの追加'
ms.date: 04/25/2019
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
ms.openlocfilehash: 5e1c75e32899ef9697025d662eeec4a6a2482f2b
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304302"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>チュートリアル: MFC プロジェクトへの D2D オブジェクトの追加

このチュートリアルでは、基本的な Direct2D (D2D) オブジェクトをビジュアルC++、MICROSOFT FOUNDATION CLASS ライブラリ (MFC) プロジェクトに追加した後、"Hello, World!" を出力するアプリケーションにプロジェクトをビルドする方法について説明します。 グラデーションの背景。

このチュートリアルでは、次のタスクを実行する方法について説明します。

- MFC アプリケーションを作成します。

- 純色ブラシと線状グラデーションブラシを作成します。

- グラデーションブラシを変更して、ウィンドウのサイズが変更されたときに適切に変化するようにします。

- D2D 描画ハンドラーを実装します。

- 結果を確認します。

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>前提条件

このチュートリアルを完了するには、ワークロードを**使用C++したデスクトップ開発**と、オプションの**visual C++ MFC (x86 および x64 コンポーネント用**) を使用して、visual Studio をインストールする必要があります。

## <a name="to-create-an-mfc-application"></a>MFC アプリケーションを作成するには

1. Mfc**アプリケーションウィザード**を使用して、mfc アプリケーションを作成します。 お使いのバージョンの Visual Studio のウィザードを開く方法については[、「チュートリアル: 新しい MFC シェルコントロールの使用](walkthrough-using-the-new-mfc-shell-controls.md)」を参照してください。

1. **[名前]** ボックスに「 *MFCD2DWalkthrough*」と入力します。 **[OK]** をクリックします。

1. **MFC アプリケーションウィザード**で、設定を変更せずに **[完了]** を選択します。

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>純色ブラシと線状グラデーションブラシを作成するには

1. **ソリューションエクスプローラー**の**MFCD2DWalkthrough**プロジェクトで、 **[ヘッダーファイル]** フォルダーの MFCD2DWalkthroughView を開きます。 次のコードを `CMFCD2DWalkthroughView` クラスに追加して、3つのデータ変数を作成します。

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   ファイルを保存して閉じます。

1. **[Source Files]** フォルダーで、MFCD2DWalkthroughView を開きます。 `CMFCD2DWalkthroughView` クラスのコンストラクターに、次のコードを追加します。

   ```cpp
   // Enable D2D support for this window:
   EnableD2DSupport();

   // Initialize D2D resources:
   m_pBlackBrush = new CD2DSolidColorBrush(
       GetRenderTarget(),
       D2D1::ColorF(D2D1::ColorF::Black));

   m_pTextFormat = new CD2DTextFormat(
       GetRenderTarget(),
       _T("Verdana"),
       50);

   m_pTextFormat->Get()->SetTextAlignment(
       DWRITE_TEXT_ALIGNMENT_CENTER);

   m_pTextFormat->Get()->SetParagraphAlignment(
       DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

   D2D1_GRADIENT_STOP gradientStops[2];

   gradientStops[0].color =
       D2D1::ColorF(D2D1::ColorF::White);

   gradientStops[0].position = 0.f;
   gradientStops[1].color =
       D2D1::ColorF(D2D1::ColorF::Indigo);

   gradientStops[1].position = 1.f;

   m_pLinearGradientBrush = new CD2DLinearGradientBrush(
       GetRenderTarget(),
       gradientStops,
       ARRAYSIZE(gradientStops),
       D2D1::LinearGradientBrushProperties(
           D2D1::Point2F(0,0),
           D2D1::Point2F(0,0)));
   ```

   ファイルを保存して閉じます。

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>グラデーションブラシを変更して、ウィンドウのサイズを変更したときに適切に変更されるようにするには

1. **[プロジェクト]** メニューの **[クラスウィザード]** をクリックします。

1. **MFC クラスウィザード**の **[クラス名]** で、[`CMFCD2DWalkthroughView`] を選択します。

1. **メッセージ** タブの **メッセージ** ボックスで、`WM_SIZE` を選択し、**ハンドラーの追加** を選択します。 この操作により、`OnSize` メッセージハンドラーが `CMFCD2DWalkthroughView` クラスに追加されます。

1. **[既存のハンドラー]** ボックスで、[`OnSize`] を選択します。 **[コードの編集]** を選択して `CMFCD2DWalkthroughView::OnSize` メソッドを表示します。 メソッドの最後に、次のコードを追加します。

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   ファイルを保存して閉じます。

## <a name="to-implement-a-d2d-drawing-handler"></a>D2D drawing ハンドラーを実装するには

1. **[プロジェクト]** メニューの **[クラスウィザード]** をクリックします。

1. **MFC クラスウィザード**の **[クラス名]** で、[`CMFCD2DWalkthroughView`] を選択します。

1. **[メッセージ]** タブで、 **[カスタムメッセージの追加]** を選択します。

1. **[カスタムメッセージの追加]** ダイアログボックスの **[カスタム Windows メッセージ]** ボックスに、「 *AFX_WM_DRAW2D*」と入力します。 **[メッセージハンドラー名]** ボックスに「 *OnDraw2D*」と入力します。 **[登録済みメッセージ]** オプションを選択し、[ **OK]** を選択します。 この操作により、AFX_WM_DRAW2D メッセージのメッセージハンドラーが `CMFCD2DWalkthroughView` クラスに追加されます。

1. **[既存のハンドラー]** ボックスで、[`OnDraw2D`] を選択します。 **[コードの編集]** を選択して `CMFCD2DWalkthroughView::OnDraw2D` メソッドを表示します。 `CMFCD2DWalkthroughView::OnDrawD2D` メソッドには次のコードを使用します。

   ```cpp
   afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(
       WPARAM wParam,
       LPARAM lParam)
   {
       CHwndRenderTarget* pRenderTarget = (CHwndRenderTarget*)lParam;
       ASSERT_VALID(pRenderTarget);

       CRect rect;
       GetClientRect(rect);

       pRenderTarget->FillRectangle(rect, m_pLinearGradientBrush);

       pRenderTarget->DrawText(
           _T("Hello, World!"),
           rect,
           m_pBlackBrush,
           m_pTextFormat);

       return TRUE;
   }
   ```

   ファイルを保存して閉じます。

## <a name="to-verify-the-results"></a>結果を確認するには

アプリケーションをビルドして実行します。 ウィンドウのサイズを変更すると、グラデーション四角形が変化します。 "Hello World!" 四角形の中央に表示されます。

## <a name="see-also"></a>参照

[チュートリアル](../mfc/walkthroughs-mfc.md)
