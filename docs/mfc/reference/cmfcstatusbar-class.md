---
title: CMFCStatusBar クラス
ms.date: 11/19/2018
f1_keywords:
- CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar::CalcFixedLayout
- AFXSTATUSBAR/CMFCStatusBar::CommandToIndex
- AFXSTATUSBAR/CMFCStatusBar::Create
- AFXSTATUSBAR/CMFCStatusBar::CreateEx
- AFXSTATUSBAR/CMFCStatusBar::DoesAllowDynInsertBefore
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneDoubleClick
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneProgressBar
- AFXSTATUSBAR/CMFCStatusBar::GetCount
- AFXSTATUSBAR/CMFCStatusBar::GetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetItemID
- AFXSTATUSBAR/CMFCStatusBar::GetItemRect
- AFXSTATUSBAR/CMFCStatusBar::GetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::GetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::GetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::GetPaneText
- AFXSTATUSBAR/CMFCStatusBar::GetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::GetTipText
- AFXSTATUSBAR/CMFCStatusBar::InvalidatePaneContent
- AFXSTATUSBAR/CMFCStatusBar::PreCreateWindow
- AFXSTATUSBAR/CMFCStatusBar::SetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::SetIndicators
- AFXSTATUSBAR/CMFCStatusBar::SetPaneAnimation
- AFXSTATUSBAR/CMFCStatusBar::SetPaneBackgroundColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneIcon
- AFXSTATUSBAR/CMFCStatusBar::SetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::SetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::SetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::SetPaneText
- AFXSTATUSBAR/CMFCStatusBar::SetPaneTextColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::SetTipText
- AFXSTATUSBAR/CMFCStatusBar::OnDrawPane
helpviewer_keywords:
- CMFCStatusBar [MFC], CalcFixedLayout
- CMFCStatusBar [MFC], CommandToIndex
- CMFCStatusBar [MFC], Create
- CMFCStatusBar [MFC], CreateEx
- CMFCStatusBar [MFC], DoesAllowDynInsertBefore
- CMFCStatusBar [MFC], EnablePaneDoubleClick
- CMFCStatusBar [MFC], EnablePaneProgressBar
- CMFCStatusBar [MFC], GetCount
- CMFCStatusBar [MFC], GetDrawExtendedArea
- CMFCStatusBar [MFC], GetExtendedArea
- CMFCStatusBar [MFC], GetItemID
- CMFCStatusBar [MFC], GetItemRect
- CMFCStatusBar [MFC], GetPaneInfo
- CMFCStatusBar [MFC], GetPaneProgress
- CMFCStatusBar [MFC], GetPaneStyle
- CMFCStatusBar [MFC], GetPaneText
- CMFCStatusBar [MFC], GetPaneWidth
- CMFCStatusBar [MFC], GetTipText
- CMFCStatusBar [MFC], InvalidatePaneContent
- CMFCStatusBar [MFC], PreCreateWindow
- CMFCStatusBar [MFC], SetDrawExtendedArea
- CMFCStatusBar [MFC], SetIndicators
- CMFCStatusBar [MFC], SetPaneAnimation
- CMFCStatusBar [MFC], SetPaneBackgroundColor
- CMFCStatusBar [MFC], SetPaneIcon
- CMFCStatusBar [MFC], SetPaneInfo
- CMFCStatusBar [MFC], SetPaneProgress
- CMFCStatusBar [MFC], SetPaneStyle
- CMFCStatusBar [MFC], SetPaneText
- CMFCStatusBar [MFC], SetPaneTextColor
- CMFCStatusBar [MFC], SetPaneWidth
- CMFCStatusBar [MFC], SetTipText
- CMFCStatusBar [MFC], OnDrawPane
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
ms.openlocfilehash: 87f75769e2f400a7721a8c9089d6c5596c31a4e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388371"
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar クラス

`CMFCStatusBar`クラスに似たステータス バー、`CStatusBar`クラス。 ただし、`CMFCStatusBar` クラスには、イメージ、アニメーション、およびプログレス バーを表示する機能や、マウスのダブルクリックに応答する機能など、`CStatusBar` クラスでは提供されない機能が含まれています。

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

## <a name="syntax"></a>構文

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(上書き[cbasepane::calcfixedlayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout))。|
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||
|[CMFCStatusBar::Create](#create)|コントロール バーを作成し、それにアタッチします、 [CPane](../../mfc/reference/cpane-class.md)オブジェクト。 (上書き[cpane::create](../../mfc/reference/cpane-class.md#create))。|
|[CMFCStatusBar::CreateEx](#createex)|コントロール バーを作成し、それにアタッチします、 [CPane](../../mfc/reference/cpane-class.md)オブジェクト。 (上書き[cpane::createex](../../mfc/reference/cpane-class.md#createex))。|
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|このペインと親フレームの間の別のウィンドウを動的に挿入するかどうかを判断します。 (上書き[cbasepane::doesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore))。|
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|有効または無効にステータス バーにマウスの処理をダブルクリックします。|
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|指定したウィンドウで進行状況バーを表示します。|
|[CMFCStatusBar::GetCount](#getcount)|ステータス バー ペインの数を返します。|
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCStatusBar::GetItemID](#getitemid)||
|[CMFCStatusBar::GetItemRect](#getitemrect)||
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|ウィンドウ スタイルを返します。 (上書き[CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle))。|
|[CMFCStatusBar::GetPaneText](#getpanetext)||
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|ステータス バーの指定したウィンドウのピクセル単位の幅を返します。|
|[CMFCStatusBar::GetTipText](#gettiptext)|ステータス バーの指定したウィンドウのツールヒントのテキストを返します。|
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|指定したウィンドウを無効にし、そのコンテンツを再描画します。|
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|これにアタッチされた Windows ウィンドウを作成する前にフレームワークによって呼び出されます`CWnd`オブジェクト。 (上書き[CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow))。|
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||
|[CMFCStatusBar::SetIndicators](#setindicators)||
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|指定したウィンドウには、アニメーションを割り当てます。|
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|ステータス バーの指定したウィンドウの背景色を設定します。|
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|ステータス バーの指定したウィンドウのインジケーター アイコンを設定します。|
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|ステータス バーの指定したウィンドウの進行状況バーの現在の進行状況を設定します。|
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|ウィンドウのスタイルを設定します。 (上書き[CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle))。|
|[CMFCStatusBar::SetPaneText](#setpanetext)||
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|ステータス バーの指定したウィンドウのテキストの色を設定します。|
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|ステータス バーの指定したウィンドウのピクセル単位の幅を設定します。|
|[CMFCStatusBar::SetTipText](#settiptext)|ステータス バーの指定したウィンドウのツールヒントのテキストを設定します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|ステータス バーのウィンドウを再描画するときに、フレームワークによって呼び出されます。|

## <a name="remarks"></a>Remarks

次の図は、図から、ステータス バーの[ステータス バーのデモ サンプル](../../overview/visual-cpp-samples.md)アプリケーション。

![CMFCStatusBar の例](../../mfc/reference/media/cmfcstatusbar.png "CMFCStatusBar の例")

## <a name="example"></a>例

次の例では、アプリケーションがさまざまなメソッドを呼び出すに使用するローカル変数、`CMFCStatusBar`クラス。 これらの変数は、StatusBarDemoView.h で宣言されます。 MainFrm.h でメイン フレームが宣言されているドキュメントが StatusBarDemoDoc.h で宣言されている、StatusBarDemoView.h でビューが宣言されています。 このコード スニペットの一部、[ステータス バーのデモ サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

## <a name="example"></a>例

次の例への参照を取得する方法を示します`CMFCStatusBar`オブジェクトを導入することで、 `GetStatusBar` MainFrm.h しからこのメソッドを呼び出すメソッド、 `GetStatusBar` StatusBarDemoView.h メソッド。 このコード スニペットの一部、[ステータス バーのデモ サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

## <a name="example"></a>例

次の例でさまざまなメソッドを呼び出す方法、 `CMFCStatusBar` StatusBarDemoView.cpp 内のクラス。 定数は、MainFrm.h で宣言されます。 例では、アイコンの設定、ステータス バー ペインのツールヒントのテキストを設定する、指定したウィンドウに進行状況バーを表示、アニメーションを指定したウィンドウに割り当て、テキストと、ステータス バー ペインの幅を設定し、処理中の現在の進行状況インジケーターを設定する方法を示しています。ステータス バー ペインの ess バー。 このコード スニペットの一部、[ステータス バーのデモ サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxstatusbar.h

##  <a name="calcfixedlayout"></a>  CMFCStatusBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>パラメーター

[in]*bStretch*<br/>
[in] *bHorz*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="commandtoindex"></a>  CMFCStatusBar::CommandToIndex

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>パラメーター

[in]*から始まり*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="create"></a>  CMFCStatusBar::Create

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>パラメーター

[in] *pParentWnd*<br/>
[in] *dwStyle*<br/>
[in]*nID*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="createex"></a>  CMFCStatusBar::CreateEx

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>パラメーター

[in] *pParentWnd*<br/>
[in]*ツール バー*<br/>
[in] *dwStyle*<br/>
[in]*nID*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="doesallowdyninsertbefore"></a>  CMFCStatusBar::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="enablepanedoubleclick"></a>  CMFCStatusBar::EnablePaneDoubleClick

有効または無効にステータス バーにマウスの処理をダブルクリックします。

```
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
[in]TRUE の場合は、マウスのダブルクリックの処理を有効にします。 それ以外の場合、マウスのダブルクリックの処理を無効にします。

### <a name="remarks"></a>Remarks

ステータス バーが二重のクリックを処理する有効な場合、Windows は、ステータス バーのステータス バー ペインで、ユーザーがダブルクリックされるたびの所有者にリソース ID と共に WM_COMMAND 通知を送信します。

##  <a name="enablepaneprogressbar"></a>  CMFCStatusBar::EnablePaneProgressBar

指定したウィンドウで進行状況バーを表示します。

```
void EnablePaneProgressBar(
    int nIndex,
    long nTotal=100,
    BOOL bDisplayText=FALSE,
    COLORREF clrBar=-1,
    COLORREF clrBarDest=-1,
    COLORREF clrProgressText=-1);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]ペインのインデックスを有効にするには、ある進行状況バーを指定します。

*nTotal*<br/>
[in]進行状況バーの最大値を指定します。

*bDisplayText*<br/>
[in]進行状況バーが現在の進行状況の値を表示するかどうかを指定します。

*clrBar*<br/>
[in]進行状況バーの背景色を指定します。

*clrBarDest*<br/>
[in]進行状況バーの背景の 2 番目の色を指定します。 異なる値を使用して、 *clrBar*色がグラデーションにブレンドをして入力します。

*clrProgressText*<br/>
[in]進行状況バーのテキストの色を指定します。

### <a name="remarks"></a>Remarks

進行状況バーの呼び出しを無効にしたい場合`EnablePaneProgressBar`で*nTotal*を-1 に設定します。 既定で*nTotal* 100 に設定されます。 そのため、進行状況をパーセンテージとして表示する追加の計算にする必要はありません。

異なる値を渡す必要があります*clrBar*と*clrBarDest*進行状況バーの背景色がグラデーションに適用される色が表示されるようにします。 .

現在の進行状況を設定するには、呼び出し、 [CMFCStatusBar::SetPaneProgress](#setpaneprogress)メソッド。

##  <a name="getcount"></a>  CMFCStatusBar::GetCount

ステータス バー ペインの数を取得します。

```
int GetCount() const;
```

### <a name="return-value"></a>戻り値

ステータス バー ペインの数。

##  <a name="getdrawextendedarea"></a>  CMFCStatusBar::GetDrawExtendedArea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getextendedarea"></a>  CMFCStatusBar::GetExtendedArea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>パラメーター

[in]*rect*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getitemid"></a>  CMFCStatusBar::GetItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

[in] *nIndex*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getitemrect"></a>  CMFCStatusBar::GetItemRect

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>パラメーター

[in] *nIndex*<br/>
[in]*lpRect*<br/>

### <a name="remarks"></a>Remarks

##  <a name="getpaneinfo"></a>  CMFCStatusBar::GetPaneInfo

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>パラメーター

[in] *nIndex*<br/>
[in]*nID*<br/>
[in]*nStyle*<br/>
[in] *cxWidth*<br/>

### <a name="remarks"></a>Remarks

##  <a name="getpaneprogress"></a>  CMFCStatusBar::GetPaneProgress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

[in] *nIndex*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getpanestyle"></a>  CMFCStatusBar::GetPaneStyle

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

[in] *nIndex*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getpanetext"></a>  CMFCStatusBar::GetPaneText

```
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

[in] *nIndex*<br/>
[in]*s*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getpanewidth"></a>  CMFCStatusBar::GetPaneWidth

ステータス バーのウィンドウの幅を取得します。

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]ステータス バー ペインのインデックスを指定します。

### <a name="return-value"></a>戻り値

ステータス バー ペインの幅を*nIndex*を指定します。 それ以外の場合、ステータス バー ペインが存在しない場合は 0。

##  <a name="gettiptext"></a>  CMFCStatusBar::GetTipText

ステータス バーのウィンドウのツールヒントのテキストを取得します。

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]ツールヒントのテキストを取得する対象のウィンドウのインデックスを指定します。

### <a name="return-value"></a>戻り値

ステータス バー ペインのツールヒントのテキストを*nIndex*を指定します。 空の文字列の指定したステータス バー ペインが存在しない場合、それ以外の場合*nIndex*のツールヒント テキストが空の場合またはします。

##  <a name="invalidatepanecontent"></a>  CMFCStatusBar::InvalidatePaneContent

ステータス バー ペインが無効にし、そのコンテンツを再描画します。

```
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]内容が無効にして再描画されるウィンドウのインデックスを指定します。

### <a name="remarks"></a>Remarks

ステータス バーが無効になったときは、再描画のマークされます。 Windows で再描画時に、`UpdateWindow`メソッドに WM_PAINT メッセージを送信、`OnPaint`メソッド。

##  <a name="ondrawpane"></a>  CMFCStatusBar::OnDrawPane

ステータス バーのウィンドウを再描画します。

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]描画のデバイス コンテキストへのポインター。

*pPane*<br/>
[in]ポインター、`CMFCStatusBarPaneInfo`再描画するのには、ウィンドウに関する情報を含む構造体。

### <a name="remarks"></a>Remarks

既定では、`OnDrawPane`デバイス コンテキストを使用して、ウィンドウを再描画*pDC*に従って、ペインのスタイルとコンテンツ。

このメソッドをオーバーライド、 `CMFCStatusBar`-ウィンドウの外観をカスタマイズするクラスを派生します。

##  <a name="precreatewindow"></a>  CMFCStatusBar::PreCreateWindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>パラメーター

[in]*cs*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="setdrawextendedarea"></a>  CMFCStatusBar::SetDrawExtendedArea

```
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>パラメーター

[in]*bSet*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setindicators"></a>  CMFCStatusBar::SetIndicators

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>パラメーター

[in] *lpIDArray*<br/>
[in]*nIDCount*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="setpaneanimation"></a>  CMFCStatusBar::SetPaneAnimation

指定したウィンドウには、アニメーションを割り当てます。

```
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]アニメーションを割り当てるウィンドウのインデックスを指定します。

*hImageList*<br/>
[in]アニメーション フレームを保持するイメージ リストを識別するハンドルを指定します。

*nFrameRate*<br/>
[in]アニメーションのミリ秒単位で、フレーム レートを指定します。

*bUpdate*<br/>
[in]TRUE の場合、直ちにウィンドウの内容を更新します。 それ以外の場合が無効になったときに、ウィンドウのコンテンツが更新されます。

### <a name="remarks"></a>Remarks

現在のアニメーションを無効にする場合は、呼び出す`SetPaneAnimation`で`hImageList`を NULL に設定します。

##  <a name="setpanebackgroundcolor"></a>  CMFCStatusBar::SetPaneBackgroundColor

ステータス バー ペインの背景色を設定します。

```
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]新しい背景色を設定する対象のウィンドウのインデックスを指定します。

*clrBackground*<br/>
[in]新しい背景色を指定します。

*bUpdate*<br/>
[in]TRUE の場合、直ちにウィンドウの内容を更新します。 それ以外の場合は更新されません ウィンドウの内容まで、ウィンドウが別の方法で無効になります。

##  <a name="setpaneicon"></a>  CMFCStatusBar::SetPaneIcon

ステータス バー ペインのアイコンを設定します。

```
void SetPaneIcon(
    int nIndex,
    HICON hIcon,
    BOOL bUpdate=TRUE);

void SetPaneIcon(
    int nIndex,
    HBITMAP hBmp,
    COLORREF clrTransparent=RGB(255, 0, 255),
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]イメージを設定する対象のウィンドウのインデックスを指定します。

*hIcon*<br/>
[in]ウィンドウの画像として設定するアイコンを識別するハンドルを指定します。

*bUpdate*<br/>
[in]ウィンドウのコンテンツをすぐに更新するかどうかを指定します。

*hBmp*<br/>
[in]ウィンドウの画像として設定するビットマップを識別するハンドルを指定します。

*clrTransparent*<br/>
[in]ビットマップの透明色を指定する、 *hBmp*を示します。

### <a name="remarks"></a>Remarks

透明色ウィンドウのイメージを設定すると共に、HICON または HBITMAP のいずれかを渡すことができます。 不要にイメージを表示しない場合は、イメージ ハンドルとして NULL 値を渡します。

任意の実行中のアニメーションがある場合を[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)が設定すると、アニメーションは停止されます。

##  <a name="setpaneinfo"></a>  CMFCStatusBar::SetPaneInfo

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>パラメーター

[in] *nIndex*<br/>
[in]*nID*<br/>
[in]*nStyle*<br/>
[in] *cxWidth*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setpaneprogress"></a>  CMFCStatusBar::SetPaneProgress

指定したウィンドウの進行状況バーの現在の進行状況インジケーターを設定します。

```
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]進行状況インジケーターを更新するためのウィンドウのインデックスを指定します。

*nCurr*<br/>
[in]進行状況インジケーターの現在の値を指定します。

*bUpdate*<br/>
[in]ウィンドウがすぐに更新する必要があるかどうかを指定します。

### <a name="remarks"></a>Remarks

指定したウィンドウで進行状況バーの進行状況インジケーターを更新するときに、このメソッドを呼び出します。

呼び出す必要がありますを指定したウィンドウのこの関数を使用する[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)最初。

##  <a name="setpanestyle"></a>  CMFCStatusBar::SetPaneStyle

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>パラメーター

[in] *nIndex*<br/>
[in]*nStyle*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setpanetext"></a>  CMFCStatusBar::SetPaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>パラメーター

[in] *nIndex*<br/>
[in] *lpszNewText*<br/>
[in]*b 更新*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="setpanetextcolor"></a>  CMFCStatusBar::SetPaneTextColor

指定したウィンドウのテキストの色を設定します。

```
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]新しいテキストの色を割り当てるウィンドウのインデックスを指定します。

*clrText*<br/>
[in]テキストの色を指定します。

*bUpdate*<br/>
[in]TRUE の場合、直ちにウィンドウの内容を更新します。 それ以外の場合は更新されません ウィンドウの内容まで、ウィンドウが別の方法で無効になります。

##  <a name="setpanewidth"></a>  CMFCStatusBar::SetPaneWidth

ステータス バー ペインの幅を設定します。

```
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]新しい幅を設定する対象のステータス バー ペインのインデックス。

*cx*<br/>
[in]ステータス バー ペインの (ピクセル単位) の新しい幅。

##  <a name="settiptext"></a>  CMFCStatusBar::SetTipText

ステータス バー ペインのツールヒントのテキストを設定します。

```
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]ツールヒント テキストを割り当てるウィンドウのインデックス。

*pszTipText*<br/>
[in]新しいツールヒント テキスト。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CPane クラス](../../mfc/reference/cpane-class.md)<br/>
[CStatusBar クラス](../../mfc/reference/cstatusbar-class.md)
