---
title: CMFCAutoHideButton クラス
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::BringToTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Create
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAlignment
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAutoHideWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetParentToolBar
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetRect
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetTextSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::HighlightButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsActive
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHighlighted
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHorizontal
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsVisible
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Move
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDraw
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDrawBorder
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnFillBackground
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ReplacePane
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowAttachedWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::UnSetAutoHideMode
helpviewer_keywords:
- CMFCAutoHideButton [MFC], BringToTop
- CMFCAutoHideButton [MFC], Create
- CMFCAutoHideButton [MFC], GetAlignment
- CMFCAutoHideButton [MFC], GetAutoHideWindow
- CMFCAutoHideButton [MFC], GetParentToolBar
- CMFCAutoHideButton [MFC], GetRect
- CMFCAutoHideButton [MFC], GetSize
- CMFCAutoHideButton [MFC], GetTextSize
- CMFCAutoHideButton [MFC], HighlightButton
- CMFCAutoHideButton [MFC], IsActive
- CMFCAutoHideButton [MFC], IsHighlighted
- CMFCAutoHideButton [MFC], IsHorizontal
- CMFCAutoHideButton [MFC], IsTop
- CMFCAutoHideButton [MFC], IsVisible
- CMFCAutoHideButton [MFC], Move
- CMFCAutoHideButton [MFC], OnDraw
- CMFCAutoHideButton [MFC], OnDrawBorder
- CMFCAutoHideButton [MFC], OnFillBackground
- CMFCAutoHideButton [MFC], ReplacePane
- CMFCAutoHideButton [MFC], ShowAttachedWindow
- CMFCAutoHideButton [MFC], ShowButton
- CMFCAutoHideButton [MFC], UnSetAutoHideMode
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
ms.openlocfilehash: 15b449b4b9f9074966ac269787b1b3ca6f977f48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403889"
---
# <a name="cmfcautohidebutton-class"></a>CMFCAutoHideButton クラス

非表示になるように構成されている [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) を表示または非表示にするボタンです。

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

## <a name="syntax"></a>構文

```
class CMFCAutoHideButton : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCAutoHideButton::BringToTop](#bringtotop)||
|[CMFCAutoHideButton::Create](#create)|自動的に隠すボタンを作成して初期化します。|
|[CMFCAutoHideButton::GetAlignment](#getalignment)|自動的に隠すボタンの配置を取得します。|
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|返します、 [CDockablePane](../../mfc/reference/cdockablepane-class.md)自動的に隠すボタンに関連付けられているオブジェクト。|
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||
|[CMFCAutoHideButton::GetRect](#getrect)||
|[CMFCAutoHideButton::GetSize](#getsize)|自動的に隠すボタンのサイズを調べます。|
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|自動的に隠すボタンのテキスト ラベルのサイズを返します。|
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|自動的に隠すボタンを強調表示します。|
|[CMFCAutoHideButton::IsActive](#isactive)|自動的に隠すボタンがアクティブかどうかを示します。|
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|自動的に隠すボタンの強調表示状態を返します。|
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|自動的に隠すボタンの表示方向が水平と垂直のどちらであるかを判断します。|
|[CMFCAutoHideButton::IsTop](#istop)||
|[CMFCAutoHideButton::IsVisible](#isvisible)|ボタンが表示されるかどうかを示します。|
|[CMFCAutoHideButton::Move](#move)||
|[CMFCAutoHideButton::OnDraw](#ondraw)|フレームワークは、自動的に隠すボタンを描画するときにこのメソッドを呼び出します。|
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|フレームワークは、自動的に隠すボタンの境界線を描画するときにこのメソッドを呼び出します。|
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|フレームワークは、自動的に隠すボタンの背景を塗りつぶすときにこのメソッドを呼び出します。|
|[CMFCAutoHideButton::ReplacePane](#replacepane)||
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|表示と関連付けられている非表示[CDockablePane クラス](../../mfc/reference/cdockablepane-class.md)します。|
|[CMFCAutoHideButton::ShowButton](#showbutton)|自動的に隠すボタンの表示と非表示を切り替えます。|
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||

## <a name="remarks"></a>Remarks

作成、`CMFCAutoHideButton`オブジェクトにアタッチされて、 [CDockablePane クラス](../../mfc/reference/cdockablepane-class.md)します。 ユーザーが `CMFCAutoHideButton` オブジェクトと対話操作を行うと、`CDockablePane` オブジェクトの非表示と表示が切り替えられます。

既定では、ユーザーが自動非表示をオンにすると、フレームワークが自動的に `CMFCAutoHideButton` を作成します。 フレームワークは、`CMFCAutoHideButton` クラスではなく、カスタム UI クラスの要素を作成できます。 フレームワークが使用するカスタム UI クラスを指定するには、静的メンバー変数 `CMFCAutoHideBar::m_pAutoHideButtonRTS` をカスタム UI クラスと等しくなるように設定します。 既定では、この変数は `CMFCAutoHideButton` に設定されます。

## <a name="example"></a>例

`CMFCAutoHideButton` オブジェクトを構築して `CMFCAutoHideButton` クラスのさまざまなメソッドを使用する方法を次の例に示します。 この例では、`Create` メソッドを使用して `CMFCAutoHideButton` オブジェクトを初期化する方法、関連付けられている `CDockablePane` クラスを表示する方法、および自動非表示ボタンを表示する方法を示しています。

[!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAutoHideButton`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxautohidebutton.h

##  <a name="bringtotop"></a>  CMFCAutoHideButton::BringToTop

```
void BringToTop();
```

### <a name="remarks"></a>Remarks

##  <a name="create"></a>  CMFCAutoHideButton::Create

作成し、自動的に隠す ボタンを初期化します。

```
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>パラメーター

*pParentBar*<br/>
[in]親ツールバーへのポインター。

*pAutoHideWnd*<br/>
[in]ポインターを[CDockablePane](../../mfc/reference/cdockablepane-class.md)オブジェクト。 この自動的に隠すボタンが非表示になり、ことを示しています`CDockablePane`します。

*dwAlignment*<br/>
[in]メイン フレーム ウィンドウのボタンの配置を指定する値。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

作成するときに、`CMFCAutoHideButton`オブジェクト、特定の自動的に隠す ボタンを関連付ける必要があります`CDockablePane`します。 ユーザーは、自動的に隠す ボタンを使用して、非表示にし、表示、関連付けられている`CDockablePane`します。

*場合*パラメーターは、アプリケーションでは、自動的に隠す ボタンが存在する場所を示します。 このパラメーターは次のいずれかの値に設定できます。

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

##  <a name="getalignment"></a>  CMFCAutoHideButton::GetAlignment

自動的に隠すボタンの配置を取得します。

```
DWORD GetAlignment() const;
```

### <a name="return-value"></a>戻り値

自動的に隠すボタンの現在の配置を含む DWORD 値を指定します。

### <a name="remarks"></a>Remarks

自動的に隠すボタンの配置では、アプリケーションでは、ボタンが存在する場所を示します。 次の値のいずれかを指定できます。

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CRBS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

##  <a name="getautohidewindow"></a>  CMFCAutoHideButton::GetAutoHideWindow

返します、 [CDockablePane](../../mfc/reference/cdockablepane-class.md)自動的に隠すボタンに関連付けられているオブジェクト。

```
CDockablePane* GetAutoHideWindow() const;
```

### <a name="return-value"></a>戻り値

関連付けられているへのポインター`CDockablePane`オブジェクト。

### <a name="remarks"></a>Remarks

関連付けると、自動的に隠す ボタンを`CDockablePane`、渡す、`CDockablePane`へのパラメーターとして、 [CMFCAutoHideButton::Create](#create)メソッド。

##  <a name="getparenttoolbar"></a>  CMFCAutoHideButton::GetParentToolBar

```
CMFCAutoHideBar* GetParentToolBar();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getrect"></a>  CMFCAutoHideButton::GetRect

```
CRect GetRect() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getsize"></a>  CMFCAutoHideButton::GetSize

自動的に隠すボタンのサイズを調べます。

```
CSize GetSize() const;
```

### <a name="return-value"></a>戻り値

A`CSize`ボタンのサイズを格納しているオブジェクト。

### <a name="remarks"></a>Remarks

計算されたサイズには、自動的に隠すボタンの境界線のサイズが含まれています。

##  <a name="gettextsize"></a>  CMFCAutoHideButton::GetTextSize

自動的に隠すボタンのテキスト ラベルのサイズを返します。

```
virtual CSize GetTextSize() const;
```

### <a name="return-value"></a>戻り値

A [CSize](../../atl-mfc-shared/reference/csize-class.md)自動的に隠すボタンのテキストのサイズを格納しているオブジェクト。

##  <a name="isactive"></a>  CMFCAutoHideButton::IsActive

自動的に隠すボタンがアクティブかどうかを示します。

```
BOOL IsActive() const;
```

### <a name="return-value"></a>戻り値

自動的に隠す ボタンがアクティブである場合は TRUEFALSE それ以外の場合。

### <a name="remarks"></a>Remarks

自動的に隠す ボタンが有効な場合、関連付けられている[CDockablePane クラス](../../mfc/reference/cdockablepane-class.md)ウィンドウが表示されます。

##  <a name="ishorizontal"></a>  CMFCAutoHideButton::IsHorizontal

自動的に隠すボタンの表示方向が水平と垂直のどちらであるかを判断します。

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>戻り値

ボタンが水平の場合、0 以外の場合それ以外の場合は 0 です。

### <a name="remarks"></a>Remarks

向きを設定するために、フレームワーク、 [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md)オブジェクトの作成時にします。  使用して方向を制御することができます、*場合*パラメーター、 [CMFCAutoHideButton::Create](#create)メソッド。

##  <a name="istop"></a>  CMFCAutoHideButton::IsTop

```
BOOL IsTop() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="isvisible"></a>  CMFCAutoHideButton::IsVisible

自動的に隠す ボタンが表示されているかどうかを示します。

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>戻り値

ボタンが表示される場合は TRUE。FALSE それ以外の場合。

##  <a name="ondraw"></a>  CMFCAutoHideButton::OnDraw

フレームワークは、自動的に隠すボタンを描画するときにこのメソッドを呼び出します。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイス コンテキストへのポインター。

### <a name="remarks"></a>Remarks

派生した新しいクラスを作成、アプリケーションで自動的に隠すボタンの外観をカスタマイズする場合は、`CMFCAutoHideButton`します。 派生クラスでは、このメソッドをオーバーライドします。

##  <a name="ondrawborder"></a>  CMFCAutoHideButton::OnDrawBorder

フレームワークは、自動的に隠すボタンの境界線を描画するときにこのメソッドを呼び出します。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイス コンテキストへのポインター。

*rectBounds*<br/>
[in]自動的に隠すボタンの外接する四角形。

*rectBorderSize*<br/>
[in]自動的に隠すボタンの各側の境界線の太さ。

### <a name="remarks"></a>Remarks

派生した新しいクラスを作成、アプリケーションでは、各自動的に隠すボタンの境界線をカスタマイズする場合、`CMFCAutoHideButton`します。 派生クラスでは、このメソッドをオーバーライドします。

##  <a name="onfillbackground"></a>  CMFCAutoHideButton::OnFillBackground

フレームワークは、自動的に隠すボタンの背景を塗りつぶすときにこのメソッドを呼び出します。

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイス コンテキストへのポインター。

*rect*<br/>
[in]自動的に隠すボタンの外接する四角形。

### <a name="remarks"></a>Remarks

派生した新しいクラスを作成、アプリケーションで自動的に隠すボタンの背景をカスタマイズする場合、`CMFCAutoHideButton`します。 派生クラスでは、このメソッドをオーバーライドします。

##  <a name="showattachedwindow"></a>  CMFCAutoHideButton::ShowAttachedWindow

表示と関連付けられている非表示[CDockablePane クラス](../../mfc/reference/cdockablepane-class.md)します。

```
void ShowAttachedWindow(BOOL bShow);
```

### <a name="parameters"></a>パラメーター

*bShow*<br/>
[in]このメソッドを示しています、関連付けられているかどうかを指定するブール値`CDockablePane`します。

##  <a name="showbutton"></a>  CMFCAutoHideButton::ShowButton

自動的に隠すボタンの表示と非表示を切り替えます。

```
virtual void ShowButton(BOOL bShow);
```

### <a name="parameters"></a>パラメーター

*bShow*<br/>
[in]自動的に隠すボタンを表示するかどうかを指定するブール値。

##  <a name="move"></a>  CMFCAutoHideButton::Move

```
void Move(int nOffset);
```

### <a name="parameters"></a>パラメーター

[in]*nOffset*<br/>

### <a name="remarks"></a>Remarks

##  <a name="replacepane"></a>  CMFCAutoHideButton::ReplacePane

```
void ReplacePane(CDockablePane* pNewBar);
```

### <a name="parameters"></a>パラメーター

[in] *pNewBar*<br/>

### <a name="remarks"></a>Remarks

##  <a name="unsetautohidemode"></a>  CMFCAutoHideButton::UnSetAutoHideMode

自動的に隠すモードを無効にします。

```
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```

### <a name="parameters"></a>パラメーター

*pFirstBarInGroup*<br/>
[in]グループ内の最初のバーへのポインター。

### <a name="remarks"></a>Remarks

##  <a name="highlightbutton"></a>  CMFCAutoHideButton::HighlightButton

自動的に隠す ボタンが強調表示されます。

```
virtual void HighlightButton(BOOL bHighlight);
```

### <a name="parameters"></a>パラメーター

*bHighlight*<br/>
新しい自動ボタンの状態を非表示を指定します。 True の場合、ボタンが強調表示されていることを示します、false の場合、ボタンが強調表示されていないことを示します。

### <a name="remarks"></a>Remarks

##  <a name="ishighlighted"></a>  CMFCAutoHideButton::IsHighlighted

自動的に隠す ボタンの強調表示状態を返します。

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>戻り値

自動ボタンを非表示にする場合は TRUE を返しますが強調表示されます。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAutoHideBar クラス](../../mfc/reference/cmfcautohidebar-class.md)<br/>
[CAutoHideDockSite クラス](../../mfc/reference/cautohidedocksite-class.md)
