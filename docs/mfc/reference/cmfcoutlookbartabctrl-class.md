---
title: CMFCOutlookBarTabCtrl Class
ms.date: 10/18/2018
f1_keywords:
- CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::AddControl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::Create
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableInPlaceEdit
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableScrollButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetVisiblePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsMode2003
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowOptions
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetActiveTab
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetToolbarImageList
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetVisiblePageButtons
helpviewer_keywords:
- CMFCOutlookBarTabCtrl [MFC], AddControl
- CMFCOutlookBarTabCtrl [MFC], CanShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], CanShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], Create
- CMFCOutlookBarTabCtrl [MFC], EnableAnimation
- CMFCOutlookBarTabCtrl [MFC], EnableInPlaceEdit
- CMFCOutlookBarTabCtrl [MFC], EnableScrollButtons
- CMFCOutlookBarTabCtrl [MFC], GetBorderSize
- CMFCOutlookBarTabCtrl [MFC], GetVisiblePageButtons
- CMFCOutlookBarTabCtrl [MFC], IsAnimation
- CMFCOutlookBarTabCtrl [MFC], IsMode2003
- CMFCOutlookBarTabCtrl [MFC], OnShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowOptions
- CMFCOutlookBarTabCtrl [MFC], SetActiveTab
- CMFCOutlookBarTabCtrl [MFC], SetBorderSize
- CMFCOutlookBarTabCtrl [MFC], SetPageButtonTextAlign
- CMFCOutlookBarTabCtrl [MFC], SetToolbarImageList
- CMFCOutlookBarTabCtrl [MFC], SetVisiblePageButtons
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
ms.openlocfilehash: c791f3988c7257ed7d188917394e74a6dbeca98b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374039"
---
# <a name="cmfcoutlookbartabctrl-class"></a>CMFCOutlookBarTabCtrl Class

Microsoft Outlook の **ナビゲーション ウィンドウ** と同じ外観を持つタブ コントロールです。
詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。
## <a name="syntax"></a>構文

```
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|既定のコンストラクターです。|
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCOutlookBarTabCtrl::AddControl](#addcontrol)|Outlook バーの新しいタブとしては、Windows コントロールを追加します。|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|フレームワークによって呼び出されるとき、ユーザーに表示される編集ボックスのサイズを決定する名前を変更しますタブ。( `CMFCBaseTabCtrl::CalcRectEdit`をオーバーライドします)。|
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|現在表示されているよりも少ない Outlook バー タブ ページのボタンを表示できる場合を判断するサイズ変更操作中に、フレームワークによって呼び出されます。|
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](#canshowmorepagebuttons)|現在表示されているよりも、複数の Outlook バー タブのページ ボタンを表示できる場合を判断するサイズ変更操作中に、フレームワークによって呼び出されます。|
|[CMFCOutlookBarTabCtrl::Create](#create)|Outlook バーのタブ コントロールを作成します。|
|`CMFCOutlookBarTabCtrl::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)|アクティブなタブの切り替え中に発生するアニメーションが有効になっているかどうかを指定します。|
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|ユーザーが Outlook バーのタブ ボタンのテキスト ラベルを変更できるかどうかを指定します。 (上書き[CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit))。|
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](#enablescrollbuttons)|ユーザーが Outlook バー ペイン上のボタン間をスクロールできるボタンを有効にするためにフレームワークによって呼び出されます。|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|指定したポイントを含むウィンドウを識別します。 (上書き[CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd))。|
|[CMFCOutlookBarTabCtrl::GetBorderSize](#getbordersize)|Outlook のタブ コントロールの境界線のサイズを返します。|
|`CMFCOutlookBarTabCtrl::GetTabArea`|タブ コントロールのタブ領域の位置とサイズを取得します。 (上書き[CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea))。|
|`CMFCOutlookBarTabCtrl::GetThisClass`|ポインターを取得する、framework によって使用される、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)このクラス型に関連付けられているオブジェクト。|
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabCtrl::IsAnimation](#isanimation)|アクティブなタブの切り替え中に発生するアニメーションが有効になっているかどうかを判断します。|
|[CMFCOutlookBarTabCtrl::IsMode2003](#ismode2003)|かどうか、Outlook バーのタブ コントロールが Microsoft Outlook 2003 をエミュレートするモードを決定します。|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|タブ領域の内部ポイントであるかどうかを判断します。 (上書き[CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea))。|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|タブが切り離し可能かどうかを判断します。 (上書き[CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable))。|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|タブを挿入または削除されたときに、フレームワークによって呼び出されます。 ( `CMFCBaseTabCtrl::OnChangeTabs`をオーバーライドします)。|
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](#onshowfewerpagebuttons)|表示されているタブ ページのボタンの数を減らすために、フレームワークによって呼び出されます。|
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](#onshowmorepagebuttons)|表示されているタブ ページのボタンの数を増やすために、フレームワークによって呼び出されます。|
|[CMFCOutlookBarTabCtrl::OnShowOptions](#onshowoptions)|表示、**ナビゲーション ペイン オプション**ダイアログ。|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|タブ コントロールの内部レイアウトを再計算します。 (上書き[CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout))。|
|[CMFCOutlookBarTabCtrl::SetActiveTab](#setactivetab)|アクティブなタブを設定します。(上書き[CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab))。|
|[CMFCOutlookBarTabCtrl::SetBorderSize](#setbordersize)|Outlook のタブ コントロールの境界線のサイズを設定します。|
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](#setpagebuttontextalign)|Outlook バーのタブ ボタンのテキスト ラベルの配置を設定します。|
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|Outlook 2003 モードで Outlook バーの下部に表示されるアイコンを含むビットマップを設定 (を参照してください[CMFCOutlookBar クラス](../../mfc/reference/cmfcoutlookbar-class.md))。|
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](#setvisiblepagebuttons)||

## <a name="remarks"></a>Remarks

ドッキングのサポートのある Outlook バーを作成するには、使用、 `CMFCOutlookBar` Outlook バーのタブ コントロールをホストするオブジェクト。 詳細については、次を参照してください。 [CMFCOutlookBar クラス](../../mfc/reference/cmfcoutlookbar-class.md)します。

## <a name="example"></a>例

次の例では、初期化する方法、`CMFCOutlookBarTabCtrl`オブジェクトをさまざまなメソッドを使用して、`CMFCOutlookBarTabCtrl`クラス。 例では、Outlook バーのタブ ページのボタンのテキスト ラベルのインプレース編集を有効にする、アニメーションを有効にする、ユーザーが Outlook バー ペイン上のボタンをスクロールして、Outlook タブの続きの境界線のサイズの設定を有効にするスクロール ハンドルを有効にする方法を示しています。ロール、および Outlook バーのタブ ボタンのテキスト ラベルの配置を設定します。 このコード スニペットの一部、 [Outlook デモ サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[から派生しているのではない](../../mfc/reference/cwnd-class.md)

[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)

[CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxoutlookbartabctrl.h

##  <a name="addcontrol"></a>  CMFCOutlookBarTabCtrl::AddControl

Outlook バーの新しいタブとしては、Windows コントロールを追加します。

```
void AddControl(
    CWnd* pWndCtrl,
    LPCTSTR lpszName,
    int nImageID=-1,
    BOOL bDetachable=TRUE,
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```

### <a name="parameters"></a>パラメーター

*pWndCtrl*<br/>
[in]追加するコントロールへのポインター。

*lpszName*<br/>
[in]タブの名前を指定します。

*bDetachable*<br/>
[in]TRUE の場合、ページが作成されます、取り外し可能です。

*nImageID*<br/>
[in]新しいタブに表示されるイメージの内部のイメージ リストのイメージのインデックス。

*dwControlBarStyle*<br/>
[in]ラップされたドッキング ペインの AFX_ cbrs _ * スタイルを指定します。

### <a name="remarks"></a>Remarks

Outlook バーの新しいページにコントロールを追加するのにには、この関数を使用します。

この関数で内部的に呼び出します[::addtab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)します。

設定した場合*bDetachable*を TRUE に`AddControl`内部的に作成、`CDockablePaneAdapter`オブジェクトし、追加したコントロールをラップします。 ランタイム クラスに、タブ付きウィンドウのランタイム クラスが自動的に設定`CMFCOutlookBar`とフローティング フレームのランタイム クラス`CMultiPaneFrameWnd`します。

### <a name="example"></a>例

次の例では、使用する方法、`AddControl`メソッドで、`CMFCOutlookBarTabCtrl`クラス。 このコード スニペットの一部、 [Outlook デモ サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

##  <a name="canshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowFewerPageButtons

現在表示されているよりも少ない Outlook バー タブ ページのボタンを表示できるかどうかを判断する操作をサイズ変更時にフレームワークによって呼び出されます。

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>戻り値

複数のボタンがある場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

Outlook バーのタブ コントロールは、動的に追加またはタブによって、どのくらいの領域が使用可能な表示から削除します。 このメソッドは、そのプロセスを支援するためにフレームワークによって使用されます。

##  <a name="canshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowMorePageButtons

現在表示されているよりも多く Outlook バー タブ ページのボタンを表示できるかどうかを判断する操作をサイズ変更時にフレームワークによって呼び出されます。

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>戻り値

ボタンが現在表示されている; がある場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

Outlook バーのタブ コントロールは動的に追加またはタブによって、どのくらいの領域が使用可能な表示から削除します。 このメソッドは、そのプロセスを支援するためにフレームワークによって使用されます。

##  <a name="create"></a>  CMFCOutlookBarTabCtrl::Create

Outlook バーのタブ コントロールを作成します。

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
[in]初期サイズと位置をピクセル単位で指定します。

*pParentWnd*<br/>
[in]親ウィンドウへのポインター。 NULL は指定できません。

*nID*<br/>
[in]コントロールの id。

### <a name="return-value"></a>戻り値

コントロールが正常に作成されている場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

通常、outlook バーのタブ コントロールが作成[CMFCOutlookBar クラス](../../mfc/reference/cmfcoutlookbar-class.md)プロセスの WM_CREATE メッセージを制御します。

##  <a name="enableanimation"></a>  CMFCOutlookBarTabCtrl::EnableAnimation

アクティブなタブの切り替え中に発生するアニメーションが有効になっているかどうかを指定します。

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
[in]アニメーションを有効または無効になっているかどうかを指定します。

### <a name="remarks"></a>Remarks

アニメーションを無効にするには、この関数を呼び出します。 タブ ページを開くと、ページのキャプションはアニメーションが有効になっている場合にアップまたはスケール ダウンをスライドします。 アニメーションが無効になっている場合は、ページがすぐにアクティブなになります。

既定では、アニメーションが有効にします。

##  <a name="enableinplaceedit"></a>  CMFCOutlookBarTabCtrl::EnableInPlaceEdit

ユーザーが Outlook バーのタブ ページのボタンのテキスト ラベルを変更できるかどうかを指定します。

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
TRUE の場合は、テキスト ラベルのインプレース編集を有効にします。 FALSE の場合は、インプレース編集を無効にします。

### <a name="remarks"></a>Remarks

有効または無効のタブ ページのボタンのテキスト ラベルのインプレース編集には、この関数を呼び出します。 既定では、インプレース編集が無効になります。

##  <a name="enablescrollbuttons"></a>  CMFCOutlookBarTabCtrl::EnableScrollButtons

ユーザーが Outlook バー ペイン上のボタン間をスクロールできるスクロール ハンドルを有効にするためにフレームワークによって呼び出されます。

```
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
[in]スクロール ボタンを表示するかどうかを判断します。

*bIsUp*<br/>
[in]上部のスクロール バーが表示されるかどうかを判断します。

*bIsDown*<br/>
[in]下部のスクロール バーが表示されるかどうかを判断します。

### <a name="remarks"></a>Remarks

スクロール ボタンの表示を有効にします。 スクロール ボタンを復元するアクティブなタブが変更されたときに、このメソッドは、フレームワークによって呼び出されます。

##  <a name="getbordersize"></a>  CMFCOutlookBarTabCtrl::GetBorderSize

Outlook のタブ コントロールの境界線のサイズを返します。

```
int GetBorderSize() const;
```

### <a name="return-value"></a>戻り値

境界線のサイズ (ピクセル単位)。

##  <a name="getvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::GetVisiblePageButtons

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="isanimation"></a>  CMFCOutlookBarTabCtrl::IsAnimation

アクティブなタブの切り替え中に発生するアニメーションが有効になっているかどうかを指定します。

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>戻り値

0 以外の場合は、アニメーションが有効な場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

呼び出す、 [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)を有効にまたはアニメーションを無効にします。

##  <a name="ismode2003"></a>  CMFCOutlookBarTabCtrl::IsMode2003

Outlook バーのタブ コントロールが Microsoft Outlook 2003 をエミュレートするモードであるかどうかを判断します。

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>戻り値

Outlook のタブ コントロール バーが Outlook 2003 モードでは、TRUE を返します。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

この値によって設定されます[CMFCOutlookBar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003)します。

##  <a name="onshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowFewerPageButtons

表示されているタブ ページのボタンの数を減らすために、フレームワークによって呼び出されます。

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>Remarks

このメソッドは、コントロールがサイズ変更時にページ表示 タブのボタンの数を調整します。

##  <a name="onshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowMorePageButtons

表示されているタブ ページのボタンの数を増やすために、フレームワークによって呼び出されます。

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>Remarks

このメソッドは、コントロールがサイズ変更時に表示されているタブ ページのボタンの数を調整します。

##  <a name="onshowoptions"></a>  CMFCOutlookBarTabCtrl::OnShowOptions

表示、**ナビゲーション ペイン オプション** ダイアログ ボックス。

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>Remarks

**ナビゲーション ペイン オプション**ダイアログ ボックスで、ユーザーをタブ ページのボタンが、表示するかを選択し、順序が表示されます。

ユーザーが選択すると、このメソッドが、フレームワークによって呼び出されます、**ナビゲーション ペイン オプション**コントロールのカスタマイズ メニューからメニュー項目。

##  <a name="setactivetab"></a>  CMFCOutlookBarTabCtrl::SetActiveTab

アクティブなタブを設定します。アクティブなタブが表示される内容と、開いています。

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>パラメーター

*iTab*<br/>
[in]開くタブの 0 から始まるインデックス。

### <a name="return-value"></a>戻り値

指定したタブが正常に開かれた場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

アクティブなタブの設定の視覚効果は、アニメーションを有効にするかどうかによって異なります。 詳細については、次を参照してください。 [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)します。

##  <a name="setbordersize"></a>  CMFCOutlookBarTabCtrl::SetBorderSize

Outlook のタブ コントロールの境界線のサイズを設定します。

```
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>パラメーター

*nBorderSize*<br/>
[in]新しい境界線のサイズをピクセル単位で指定します。

### <a name="remarks"></a>Remarks

新しい境界線のサイズを設定し、outlook のウィンドウ レイアウトを再計算します。

##  <a name="setpagebuttontextalign"></a>  CMFCOutlookBarTabCtrl::SetPageButtonTextAlign

Outlook バーのタブ ボタンのテキスト ラベルの配置を設定します。

```
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>パラメーター

*uiAlign*<br/>
[in]テキストの配置を指定します。

*bRedraw*<br/>
[in]TRUE の場合は、outlook のウィンドウが再描画されます。

### <a name="remarks"></a>Remarks

この関数を使用すると、ページのボタンのテキストの配置を変更できます。

*uiAlign*値は次のいずれかを指定できます。

|定数|説明|
|--------------|-------------|
|TA_LEFT|左揃え|
|TA_CENTER|中央揃え|
|TA_RIGHT|右揃え|

既定値は、TA_CENTER です。

##  <a name="settoolbarimagelist"></a>  CMFCOutlookBarTabCtrl::SetToolbarImageList

Outlook 2003 モードで Outlook バーの下部に表示されるアイコンを含むビットマップを設定します。

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>パラメーター

*uiID*<br/>
[in]読み込むイメージのリソース ID を指定します。

*cx*<br/>
[in]イメージの幅 (ピクセル単位)、イメージ リストを指定します。

*clrTransp*<br/>
[in]透明色を指定する RGB 値。

### <a name="return-value"></a>戻り値

成功した場合、TRUE を返しますそれ以外の場合、FALSE を返します。

### <a name="remarks"></a>Remarks

Microsoft Office 2003 モードでツール バー ボタンに表示されるイメージがイメージ リストをアタッチするのにには、この関数を使用します。 イメージのインデックスは、ページのインデックスに対応する必要があります。

このメソッドは、Microsoft Office 2003 モードではない場合は呼び出されませんする必要があります。 詳細については、次を参照してください。 [CMFCOutlookBar クラス](../../mfc/reference/cmfcoutlookbar-class.md)します。

##  <a name="setvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::SetVisiblePageButtons

```
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>パラメーター

[in] *nVisiblePageButtons*<br/>

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCBaseTabCtrl クラス](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[CMFCOutlookBar クラス](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarPane クラス](../../mfc/reference/cmfcoutlookbarpane-class.md)
