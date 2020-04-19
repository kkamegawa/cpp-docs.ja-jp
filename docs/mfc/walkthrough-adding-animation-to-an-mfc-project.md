---
title: 'チュートリアル: MFC プロジェクトへのアニメーションの追加'
ms.date: 04/25/2019
helpviewer_keywords:
- animation [MFC]
- MFC, animation
ms.assetid: 004f832c-9fd5-4f88-9ca9-ae65dececdc2
ms.openlocfilehash: 07b0c5f712cd645246ecfb4e8c93543377a340a3
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64558193"
---
# <a name="walkthrough-adding-animation-to-an-mfc-project"></a>チュートリアル: MFC プロジェクトへのアニメーションの追加

このチュートリアルでは、Visual C、Microsoft Foundation Class ライブラリ (MFC) プロジェクトを基本的なアニメーション化されたオブジェクトを追加する方法について説明します。

このチュートリアルでは、これらのタスクを実行する方法を示します。

- MFC アプリケーションを作成します。

- メニューを追加し、コマンドを開始およびアニメーションを停止します。

- Start および stop コマンドのハンドラーを作成します。

- アニメーション化するオブジェクトをプロジェクトに追加します。

- センター ウィンドウでアニメーション化するオブジェクト。

- 結果を確認します。

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了するには、Visual Studio が必要です。

### <a name="to-create-an-mfc-application"></a>MFC アプリケーションを作成するには

1. 使用して、 **MFC アプリケーション ウィザード**MFC アプリケーションを作成します。 「[チュートリアル:新しい MFC シェル コントロールを使用して](walkthrough-using-the-new-mfc-shell-controls.md)Visual Studio のバージョンのウィザードを開く方法の詳細について。

1. **名前**ボックスに「 *MFCAnimationWalkthrough*します。 **[OK]** をクリックします。

1. **MFC アプリケーション ウィザード** ダイアログ ボックスで、いることを確認**アプリケーションの種類**は**複数のドキュメント**、**プロジェクト スタイル**は、**Visual Studio**、および**ドキュメント/ビュー アーキテクチャ サポート**オプションを選択します。 **[完了]** をクリックします。

### <a name="to-add-a-menu-and-then-add-commands-to-start-and-stop-an-animation"></a>メニューを追加し、開始およびアニメーションを停止するコマンドを追加するには

1. **ビュー**メニューで、**その他の Windows**  をクリックし、**リソース ビュー**します。

1. **リソース ビュー**に移動し、**メニュー**フォルダーを開きます。 ダブルクリックして、 **IDR_MFCAnimationWalkthroughTYPE**リソース変更用に開きます。

1. メニュー バーで、**ここへ入力**ボックスに「 *& nimation*アニメーション メニューを作成します。

1. **アニメーション**の**ここへ入力**ボックスに「*開始 (&) 転送*フォワード開始コマンドを作成します。

1. **フォワード開始**の**ここへ入力**ボックスに「*の開始日と下位*します。

1. **旧バージョンと開始**の**ここへ入力**ボックスに「 *S (& t)* を停止するコマンドを作成しますします。

1. MFCAnimationWalkthrough.rc を保存して閉じます。

1. **ソリューション エクスプ ローラー**変更用に開きます MainFrm.cpp をダブルクリックします。 `CMainFrame::OnCreate`メソッドへのいくつかの呼び出しがあるセクションを見つけます`lstBasicCommands.AddTail`します。 このセクションでは、直後後には、次のコードを追加します。

    ```cpp
    lstBasicCommands.AddTail(ID_ANIMATION_STARTFORWARD);
    lstBasicCommands.AddTail(ID_ANIMATION_STARTBACKWARD);
    lstBasicCommands.AddTail(ID_ANIMATION_STOP);
    ```

1. ファイルを保存して閉じます。

### <a name="to-create-handlers-for-the-start-and-stop-commands"></a>最初のハンドラーを作成し、コマンドを停止するには

1. **プロジェクト** メニューのをクリックして**クラス ウィザード**します。

1. **MFC クラス ウィザード**  **クラス名**、 **CMFCAnimationWalkthroughView**。

1. **コマンド** タブで、**オブジェクト Id**ボックスで、 **ID_ANIMATION_STARTFORWARD**、し、**メッセージ**ボックスで、の選択**コマンド**します。 クリックして**ハンドラーを追加**します。

1. **メンバー関数を追加**ダイアログ ボックスで、をクリックして**OK**。

1. **オブジェクト Id**ボックスで、 **ID_ANIMATION_STARTBACKWARD**、し、**メッセージ**ボックスで、**コマンド**します。 クリックして**ハンドラーを追加**します。

1. **メンバー関数を追加**ダイアログ ボックスで、をクリックして**OK**。

1. **オブジェクト Id**ボックスで、 **ID_ANIMATION_STOP**、し、**メッセージ**ボックスで、**コマンド**します。 クリックして**ハンドラーの追加**順にクリックします**OK**します。

1. **メンバー関数を追加**ダイアログ ボックスで、をクリックして**OK**。

1. **MFC クラス ウィザード**、 をクリックして**OK**します。

1. 保存 MFCAnimationWalkthroughView.cpp、エディターで開いているが、それを閉じないでください。

### <a name="to-add-an-animated-object-to-the-project"></a>アニメーション化するオブジェクトをプロジェクトに追加するには

1. **ソリューション エクスプ ローラー**変更用に開きます MFCAnimationWalkthroughView.h をダブルクリックします。 定義の直前に、`CMFCAnimationWalkthroughView`クラスでのアニメーション オブジェクトとスケジュールの競合を処理するカスタム アニメーション コント ローラーを作成するには、次のコードを追加します。

    ```cpp
    class CCustomAnimationController : public CAnimationController
    {
    public:
        CCustomAnimationController()
        {
        }

        virtual BOOL OnHasPriorityTrim(CAnimationGroup* pGroupScheduled,
            CAnimationGroup* pGroupNew,
            UI_ANIMATION_PRIORITY_EFFECT priorityEffect)
        {
            return TRUE;
        }
    };
    ```

1. 最後に、`CMFCAnimationWalkthroughView`クラスで、次のコードを追加します。

    ```cpp
    CCustomAnimationController m_animationController;
    CAnimationColor m_animationColor;
    CAnimationRect m_animationRect;
    ```

1. 後に、`DECLARE_MESSAGE_MAP()`行に、次のコードを追加します。

    ```cpp
    void Animate(BOOL bDirection);
    ```

1. ファイルを保存して閉じます。

1. 後のファイルの上部にある、MFCAnimationWalkthroughView.cpp で、`#include`ステートメントがいずれかのクラスのメソッドでは、前に、次のコードを追加します。

    ```cpp
    static int nAnimationGroup = 0;
    static int nInfoAreaHeight = 40;
    ```

1. コンス トラクターの末尾に`CMFCAnimationWalkthroughView`、次のコードを追加します。

    ```cpp
    m_animationController.EnableAnimationTimerEventHandler();
    m_animationController.EnablePriorityComparisonHandler(UI_ANIMATION_PHT_TRIM);
    m_animationColor = RGB(255, 255, 255);
    m_animationRect = CRect(0, 0, 0, 0);
    m_animationColor.SetID(-1, nAnimationGroup);
    m_animationRect.SetID(-1, nAnimationGroup);
    m_animationController.AddAnimationObject(&m_animationColor);
    m_animationController.AddAnimationObject(&m_animationRect);
    ```

1. 検索、`CAnimationWalthroughView::PreCreateWindow`メソッドと、次のコードに置き換えます。

    ```cpp
    BOOL CMFCAnimationWalkthroughView::PreCreateWindow(CREATESTRUCT& cs)
    {
        // TODO: Modify the Window class or styles here by modifying
        //       the CREATESTRUCT cs
        m_animationController.SetRelatedWnd(this);

        return CView::PreCreateWindow(cs);
    }
    ```

1. 検索、`CAnimationWalkthroughView::OnDraw`メソッドと、次のコードに置き換えます。

    ```cpp
    void CMFCAnimationWalkthroughView::OnDraw(CDC* pDC)
    {
        CMFCAnimationWalkthroughDoc* pDoc = GetDocument();
        ASSERT_VALID(pDoc);
        if (!pDoc)
            return;

        // TODO: add draw code for native data here
        CMemDC dcMem(*pDC, this);
        CDC& dc = dcMem.GetDC();
        CRect rect;
        GetClientRect(rect);

        dc.FillSolidRect(rect, GetSysColor(COLOR_WINDOW));

        CString strRGB;
        strRGB.Format(_T("Fill Color is: %d; %d; %d"),
            GetRValue(m_animationColor),
            GetGValue(m_animationColor),
            GetBValue(m_animationColor));

        dc.DrawText(strRGB, rect, DT_CENTER);
        rect.top += nInfoAreaHeight;

        CBrush br;
        br.CreateSolidBrush(m_animationColor);
        CBrush* pBrushOld = dc.SelectObject(&br);

        dc.Rectangle((CRect)m_animationRect);

        dc.SelectObject(pBrushOld);
    }
    ```

1. ファイルの末尾には、次のコードを追加します。

    ```cpp
    void CMFCAnimationWalkthroughView::Animate(BOOL bDirection)
    {
        static UI_ANIMATION_SECONDS duration = 3;
        static DOUBLE dblSpeed = 35.;
        static BYTE nStartColor = 50;
        static BYTE nEndColor = 255;

        BYTE nRedColorFinal = bDirection ? nStartColor : nEndColor;
        BYTE nGreenColorFinal = bDirection ? nStartColor : nEndColor;
        BYTE nBlueColorFinal = bDirection ? nStartColor : nEndColor;

        CLinearTransition* pRedTransition =
            new CLinearTransition(duration, (DOUBLE)nRedColorFinal);

        CSmoothStopTransition* pGreenTransition =
            new CSmoothStopTransition(duration, (DOUBLE)nGreenColorFinal);

        CLinearTransitionFromSpeed* pBlueTransition =
            new CLinearTransitionFromSpeed(dblSpeed, (DOUBLE)nBlueColorFinal);

        m_animationColor.AddTransition(pRedTransition,
            pGreenTransition,
            pBlueTransition);

        CRect rectClient;
        GetClientRect(rectClient);

        rectClient.top += nInfoAreaHeight;

        int nLeftFinal = bDirection ? rectClient.left : rectClient.CenterPoint().x;
        int nTopFinal = bDirection ? rectClient.top : rectClient.CenterPoint().y;
        int nRightFinal = bDirection ? rectClient.right : rectClient.CenterPoint().x;
        int nBottomFinal = bDirection ? rectClient.bottom : rectClient.CenterPoint().y;

        CLinearTransition* pLeftTransition =
            new CLinearTransition(duration, nLeftFinal);

        CLinearTransition* pTopTransition =
            new CLinearTransition(duration, nTopFinal);

        CLinearTransition* pRightTransition =
            new CLinearTransition(duration, nRightFinal);

        CLinearTransition* pBottomTransition =
            new CLinearTransition(duration, nBottomFinal);

        m_animationRect.AddTransition(pLeftTransition,
            pTopTransition,
            pRightTransition,
            pBottomTransition);

        CBaseKeyFrame* pKeyframeStart =
            CAnimationController::GetKeyframeStoryboardStart();
        CKeyFrame* pKeyFrameEnd =
            m_animationController.CreateKeyframe(nAnimationGroup,
                pBlueTransition);

        pLeftTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pTopTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pRightTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);
        pBottomTransition->SetKeyframes(pKeyframeStart, pKeyFrameEnd);

        m_animationController.AnimateGroup(nAnimationGroup);
    }
    ```

1. **プロジェクト** メニューのをクリックして**クラス ウィザード**します。

1. **MFC クラス ウィザード**  **クラス名**、 **CMFCAnimationWalkthroughView**。

1. **メッセージ** タブで、**メッセージ**ボックスで、 **WM_ERASEBKGND**、 をクリックして**ハンドラーの追加**、 をクリックし、 **ok**.

1. MFCAnimationWalkthroughView.cpp での実装を置き換える`OnEraseBkgnd`を次のコードが再描画されるときにアニメーション化されたオブジェクトのちらつきを軽減します。

    ```cpp
    BOOL CMFCAnimationWalkthroughView::OnEraseBkgnd(CDC* /*pDC*/)
    {
        return TRUE;
    }
    ```

1. 実装を置き換える`CMFCAnimationWalkthroughView::OnAnimationStartforward`、 `CMFCAnimationWalkthroughView::OnAnimationStartbackward`、および`CMFCAnimationWalkthroughView::OnAnimationStop`を次のコード。

    ```cpp
    void CMFCAnimationWalkthroughView::OnAnimationStartforward()
    {
        Animate(TRUE);
    }

    void CMFCAnimationWalkthroughView::OnAnimationStartbackward()
    {
        Animate(FALSE);
    }

    void CMFCAnimationWalkthroughView::OnAnimationStop()
    {
        IUIAnimationManager* pManager = m_animationController.GetUIAnimationManager();
        if (pManager != NULL)
        {
            pManager->AbandonAllStoryboards();

        }
    }
    ```

1. ファイルを保存して閉じます。

### <a name="to-center-the-animated-object-in-the-window"></a>ウィンドウのアニメーション化されたオブジェクトを中央に

1. **ソリューション エクスプ ローラー**変更用に開きます MFCAnimationWalkthroughView.h をダブルクリックします。 最後に、`CMFCAnimationWalkthroughView`クラスの定義の直後後`m_animationRect`、次のコードを追加します。

    ```cpp
    BOOL m_bCurrentDirection;
    ```

1. ファイルを保存して閉じます。

1. **プロジェクト** メニューのをクリックして**クラス ウィザード**します。

1. **MFC クラス ウィザード**  **クラス名**、 **CMFCAnimationWalkthroughView**。

1. **メッセージ** タブで、**メッセージ**ボックスで、 **WM_SIZE**、 をクリックして**ハンドラーの追加**、 をクリックし、 **ok**.

1. MFCAnimationWalkthroughView.cpp でのコードに書き換えます`CMFCAnimationWalkthroughView::OnSize`を次のコード。

    ```cpp
    void CMFCAnimationWalkthroughView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);
        CRect rect;
        GetClientRect(rect);

        rect.top += nInfoAreaHeight;

        CRect rectAnim = m_animationRect;
        m_animationRect = CRect(CPoint(rect.CenterPoint().x - rectAnim.Width() / 2,
        rect.CenterPoint().y - rectAnim.Height() / 2),
        rectAnim.Size());

        if (m_animationController.IsAnimationInProgress())
        {
            Animate(m_bCurrentDirection);
        }
    }
    ```

1. コンス トラクターの先頭に`CMFCAnimationWalkthroughView`、次のコードを追加します。

    ```cpp
    m_bCurrentDirection = TRUE;
    ```

1. 先頭に、`CMFCAnimationWalkthroughView::Animate`メソッドでは、次のコードを追加します。

    ```cpp
    m_bCurrentDirection = bDirection;
    ```

1. ファイルを保存して閉じます。

### <a name="to-verify-the-results"></a>結果を確認するには

1. アプリケーションをビルドして実行します。 **アニメーション** メニューのをクリックして**フォワード開始**します。 四角形が表示され、中央の領域を入力する必要があります。 クリックすると**開始旧バージョンと**、アニメーションが反転する必要があります、およびクリックすると**停止**、それを停止する必要があります。 四角形の塗りつぶしの色をアニメーションの進行に合わせて変更する必要があり、アニメーションをウィンドウの上部にある現在の色を表示する必要があります。

## <a name="see-also"></a>関連項目

[チュートリアル](../mfc/walkthroughs-mfc.md)
