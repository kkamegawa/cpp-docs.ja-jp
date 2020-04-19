---
title: CMFCToolBarEditBoxButton クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CanBeStretched
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::CopyFrom
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetByCmd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContentsAll
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetEditBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetHwnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::GetInvalidateRect
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::HaveHotBorder
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::IsFlatMode
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::NotifyCommand
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnAddToCustomizePage
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnChangeParentWnd
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnClick
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnCtlColor
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnGlobalFontsChanged
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnMove
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnShow
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnSize
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::OnUpdateToolTip
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetContextMenuID
- AFXTOOLBAREDITBOXBUTTON/CMFCToolBarEditBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarEditBoxButton [MFC], CMFCToolBarEditBoxButton
- CMFCToolBarEditBoxButton [MFC], CanBeStretched
- CMFCToolBarEditBoxButton [MFC], CopyFrom
- CMFCToolBarEditBoxButton [MFC], GetByCmd
- CMFCToolBarEditBoxButton [MFC], GetContentsAll
- CMFCToolBarEditBoxButton [MFC], GetContextMenuID
- CMFCToolBarEditBoxButton [MFC], GetEditBorder
- CMFCToolBarEditBoxButton [MFC], GetHwnd
- CMFCToolBarEditBoxButton [MFC], GetInvalidateRect
- CMFCToolBarEditBoxButton [MFC], HaveHotBorder
- CMFCToolBarEditBoxButton [MFC], IsFlatMode
- CMFCToolBarEditBoxButton [MFC], NotifyCommand
- CMFCToolBarEditBoxButton [MFC], OnAddToCustomizePage
- CMFCToolBarEditBoxButton [MFC], OnChangeParentWnd
- CMFCToolBarEditBoxButton [MFC], OnClick
- CMFCToolBarEditBoxButton [MFC], OnCtlColor
- CMFCToolBarEditBoxButton [MFC], OnGlobalFontsChanged
- CMFCToolBarEditBoxButton [MFC], OnMove
- CMFCToolBarEditBoxButton [MFC], OnShow
- CMFCToolBarEditBoxButton [MFC], OnSize
- CMFCToolBarEditBoxButton [MFC], OnUpdateToolTip
- CMFCToolBarEditBoxButton [MFC], SetContextMenuID
- CMFCToolBarEditBoxButton [MFC], SetFlatMode
ms.assetid: b21d9b67-6bf7-4ca9-bd62-b237756e0ab3
ms.openlocfilehash: 3e988d789ca6a038ce41bca829850f6509fd9df1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504731"
---
# <a name="cmfctoolbareditboxbutton-class"></a>CMFCToolBarEditBoxButton クラス

エディットコントロール ( [CEdit クラス](../../mfc/reference/cedit-class.md)) を含むツールバーボタン。

## <a name="syntax"></a>構文

```
class CMFCToolBarEditBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton](#cmfctoolbareditboxbutton)|`CMFCToolBarEditBoxButton` オブジェクトを構築します。|
|`CMFCToolBarEditBoxButton::~CMFCToolBarEditBoxButton`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCToolBarEditBoxButton:: CanBeStretched](#canbestretched)|カスタマイズ中にユーザーがボタンを引き伸ばすことができるかどうかを指定します。 ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)をオーバーライドします)。|
|[CMFCToolBarEditBoxButton:: CopyFrom](#copyfrom)|別のツールバーボタンのプロパティを現在のボタンにコピーします。 ( [CMFCToolBarButton:: CopyFrom を](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)オーバーライドします)。|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: CreateEdit](#createedit)|ボタンに新しいエディットコントロールを作成します。|
|`CMFCToolBarEditBoxButton::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|[CMFCToolBarEditBoxButton:: GetByCmd](#getbycmd)|指定した`CMFCToolBarEditBoxButton`コマンド ID を持つ、アプリケーション内の最初のオブジェクトを取得します。|
|[CMFCToolBarEditBoxButton:: Getのすべての目次](#getcontentsall)|指定したコマンド ID を持つ最初のエディットボックスツールバーコントロールのテキストを取得します。|
|[CMFCToolBarEditBoxButton:: GetContextMenuID](#getcontextmenuid)|ボタンに関連付けられているショートカットメニューのリソース ID を取得します。|
|[CMFCToolBarEditBoxButton::GetEditBorder](#geteditborder)|エディットボックスボタンの編集部分の外接する四角形を取得します。|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: GetEditBox](#geteditbox)|ボタンに埋め込まれているエディットコントロールへのポインターを返します。|
|[CMFCToolBarEditBoxButton::GetHwnd](#gethwnd)|ツールバーボタンに関連付けられているウィンドウハンドルを取得します。 ( [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)をオーバーライドします。)|
|[CMFCToolBarEditBoxButton::GetInvalidateRect](#getinvalidaterect)|再描画する必要があるボタンのクライアント領域の領域を取得します。 ( [CMFCToolBarButton:: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)をオーバーライドします。)|
|`CMFCToolBarEditBoxButton::GetThisClass`|このクラス型に関連付けられている[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|[CMFCToolBarEditBoxButton:: ホットボーダーを持つ](#havehotborder)|ユーザーがボタンをクリックしたときに、ボタンの境界線を表示するかどうかを決定します。 ( [CMFCToolBarButton:: は、ホットボーダー](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)をオーバーライドします)。|
|[CMFCToolBarEditBoxButton::IsFlatMode](#isflatmode)|エディットボックスのボタンがフラットスタイルであるかどうかを判断します。|
|[CMFCToolBarEditBoxButton:: NotifyCommand](#notifycommand)|ボタンが[WM_COMMAND](/windows/win32/menurc/wm-command)メッセージを処理するかどうかを指定します。 ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)をオーバーライドします)。|
|[CMFCToolBarEditBoxButton:: OnAddToCustomizePage](#onaddtocustomizepage)|ボタンが **[カスタマイズ]** ダイアログボックスに追加されたときにフレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)をオーバーライドします)。|
|`CMFCToolBarEditBoxButton::OnCalculateSize`|指定されたデバイスコンテキストとドッキング状態のボタンのサイズを計算するために、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: On電卓 Atesize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)をオーバーライドします)。|
|[CMFCToolBarEditBoxButton::OnChangeParentWnd](#onchangeparentwnd)|新しいツールバーにボタンが挿入されたときにフレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)をオーバーライドします。)|
|[CMFCToolBarEditBoxButton:: OnClick](#onclick)|ユーザーがマウスボタンをクリックしたときにフレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)をオーバーライドします)。|
|[CMFCToolBarEditBoxButton::OnCtlColor](#onctlcolor)|親ツールバーが WM_CTLCOLOR メッセージを処理するときに、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)をオーバーライドします。)|
|`CMFCToolBarEditBoxButton::OnDraw`|指定されたスタイルとオプションを使用してボタンを描画するために、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)をオーバーライドします)。|
|`CMFCToolBarEditBoxButton::OnDrawOnCustomizeList`|**[カスタマイズ]** ダイアログボックスの **[コマンド]** ウィンドウにボタンを描画するために、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)をオーバーライドします。)|
|[CMFCToolBarEditBoxButton:: Onglobalフォントの変更](#onglobalfontschanged)|グローバルフォントが変更されたときにフレームワークによって呼び出されます。 ( [CMFCToolBarButton:: Onglobalフォントの変更](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)をオーバーライドします)。|
|[CMFCToolBarEditBoxButton::OnMove](#onmove)|親ツールバーが移動したときにフレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)をオーバーライドします。)|
|[CMFCToolBarEditBoxButton:: OnShow](#onshow)|ボタンが表示または非表示になったときにフレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnShow を](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)オーバーライドします)。|
|[CMFCToolBarEditBoxButton:: OnSize](#onsize)|親ツールバーがサイズまたは位置を変更し、この変更によってボタンのサイズが変更されるときに、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)をオーバーライドします。)|
|[CMFCToolBarEditBoxButton:: OnUpdateToolTip](#onupdatetooltip)|親ツールバーがツールヒントテキストを更新するときに、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)をオーバーライドします)。|
|`CMFCToolBarEditBoxButton::Serialize`|アーカイブからこのオブジェクトを読み取るか、アーカイブに書き込みます。 ( [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)をオーバーライドします)。|
|`CMFCToolBarEditBoxButton::SetACCData`|指定され`CAccessibilityData`たオブジェクトに、ツールバーボタンのアクセシビリティデータを設定します。 ( [CMFCToolBarButton:: setのデータ](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata)をオーバーライドします)。|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: SetContents](#setcontents)|ボタンの編集コントロールのテキストを設定します。|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: Setのすべての目次](#setcontentsall)|指定したコマンド ID を持つエディットコントロールボタンを検索し、そのボタンの編集コントロールのテキストを設定します。|
|[CMFCToolBarEditBoxButton:: SetContextMenuID](#setcontextmenuid)|ボタンに関連付けられているショートカットメニューのリソース ID を指定します。|
|[CMFCToolBarEditBoxButton::SetFlatMode](#setflatmode)|アプリケーションのエディットボックスボタンのフラットスタイルの外観を指定します。|
|`CMFCToolBarEditBoxButton::`[CMFCToolBarEditBoxButton:: system.windows.forms.control.setstyle](#setstyle)|ボタンのスタイルを指定します。 ( [CMFCToolBarButton:: system.windows.forms.control.setstyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)をオーバーライドします。)|

## <a name="remarks"></a>Remarks

ツールバーに [エディットボックス] ボタンを追加するには、次の手順を実行します。

1. 親ツール バー リソースでボタンのダミー リソース ID を予約します。

2.   `CMFCToolBarEditBoxButton` オブジェクトを構築します。

3. AFX_WM_RESETTOOLBAR メッセージを処理するメッセージハンドラーで、 [Cmfctoolbar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)を使用して、ダミーボタンを新しいコンボボックスボタンに置き換えます。

詳細については、「[チュートリアル:ツールバー](../../mfc/walkthrough-putting-controls-on-toolbars.md)にコントロールを配置する。

## <a name="example"></a>例

`CMFCToolBarEditBoxButton` クラスのさまざまなメソッドの使用方法を次の例に示します。 この例では、ユーザーがボタンをクリックしたときにボタンの境界線が表示されるように指定する方法、ユーザーがボタンをクリックしたときにボタンの境界線を表示するように指定する方法、テキストボックスコントロールのテキストを設定する方法、エディットボックスボタンのフラットスタイルの外観を指定する方法について説明します。には、ツールバーのエディットボックスコントロールのスタイルを指定します。

[!code-cpp[NVC_MFC_RibbonApp#40](../../mfc/reference/codesnippet/cpp/cmfctoolbareditboxbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

`CMFCToolBarEditBoxButton`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtoolbareditboxbutton

##  <a name="canbestretched"></a>CMFCToolBarEditBoxButton:: CanBeStretched

カスタマイズ中にユーザーがボタンを引き伸ばすことができるかどうかを指定します。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>戻り値

このメソッドは TRUE を返します。

### <a name="remarks"></a>Remarks

既定では、フレームワークでは、カスタマイズ時にツールバーボタンを拡張することをユーザーに許可しません。 このメソッドは、カスタマイズ中にユーザーがエディットボックスのツールバーボタンを伸縮できるようにすることで、基本クラスの実装 ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) を拡張します。

##  <a name="cmfctoolbareditboxbutton"></a>CMFCToolBarEditBoxButton::CMFCToolBarEditBoxButton

[CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)オブジェクトを構築します。

```
CMFCToolBarEditBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=ES_AUTOHSCROLL,
    int iWidth=0);
```

### <a name="parameters"></a>パラメーター

*uiID*<br/>
からコントロール ID を指定します。

*iImage*<br/>
からツールバーイメージの0から始まるインデックスを指定します。 このイメージは、 [Cmfctoolbar クラス](../../mfc/reference/cmfctoolbar-class.md)クラスが保持する[cmfctoolbarimages クラス](../../mfc/reference/cmfctoolbarimages-class.md)オブジェクトに配置されています。

*dwStyle*<br/>
からEdit コントロールスタイルを指定します。

*iWidth*<br/>
からエディットコントロールの幅をピクセル単位で指定します。

### <a name="remarks"></a>Remarks

既定のコンストラクターは、edit コントロールスタイルを次の組み合わせに設定します。

WS_CHILD |WS_VISIBLE |ES_AUTOHSCROLL

コントロールの既定の幅は150ピクセルです。

##  <a name="copyfrom"></a>CMFCToolBarEditBoxButton:: CopyFrom

別のツールバーボタンのプロパティを現在のボタンにコピーします。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
[in]コピー元のソースボタンへの参照。

### <a name="remarks"></a>Remarks

このツールバーボタンに別のツールバーボタンをコピーするには、このメソッドを呼び出します。 *src*の型`CMFCToolBarEditBoxButton`はである必要があります。

##  <a name="createedit"></a>CMFCToolBarEditBoxButton:: CreateEdit

ボタンに新しいエディットコントロールを作成します。

```
virtual CEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
からエディットコントロールの親ウィンドウを指定します。 NULL にすることはできません。

*rect*<br/>
からエディットコントロールのサイズと位置を指定します。

### <a name="return-value"></a>戻り値

新しく作成されたエディットコントロールへのポインター。コントロールの作成と添付ファイルが失敗した場合は NULL になります。

### <a name="remarks"></a>Remarks

オブジェクトを構築`CMFCToolBarEditBoxButton`するには、2つの手順を実行します。 最初にコンストラクターを呼び出し、次に`CreateEdit`を呼び出します。これにより、Windows のエディットコントロール`CMFCToolBarEditBoxButton`が作成され、オブジェクトにアタッチされます。

##  <a name="getbycmd"></a>CMFCToolBarEditBoxButton:: GetByCmd

指定した`CMFCToolBarEditBoxButton`コマンド ID を持つ、アプリケーション内の最初のオブジェクトを取得します。

```
static CMFCToolBarEditBoxButton* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
から取得するボタンのコマンド ID。

### <a name="return-value"></a>戻り値

指定し`CMFCToolBarEditBoxButton`たコマンド ID を持つ、アプリケーション内の最初のオブジェクト。そのようなオブジェクトが存在しない場合は NULL。

### <a name="remarks"></a>Remarks

この共有ユーティリティメソッドは、 [CMFCToolBarEditBoxButton:: SetContentsAll](#setcontentsall)と[CMFCToolBarEditBoxButton:: getcontentsall](#getcontentsall)などのメソッドによって、指定されたコマンド ID を持つ最初のエディットボックスツールバーコントロールのテキストを設定または取得するために使用されます。

##  <a name="getcontentsall"></a>CMFCToolBarEditBoxButton:: Getのすべての目次

指定したコマンド ID を持つ最初のエディットボックスツールバーコントロールのテキストを取得します。

```
static CString __stdcall GetContentsAll(UINT uiCmd);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
からコンテンツの取得元となるボタンのコマンド ID。

### <a name="return-value"></a>戻り値

指定したコマンド ID を持つ最初のエディットボックスツールバーコントロールのテキストを格納しているオブジェクト。`CString`

### <a name="remarks"></a>Remarks

指定されたコマンド ID を持つ`CMFCToolBarEditBoxButton`オブジェクトがない場合、このメソッドは空の文字列を返します。

##  <a name="getcontextmenuid"></a>CMFCToolBarEditBoxButton:: GetContextMenuID

ボタンに関連付けられているショートカットメニューのリソース ID を取得します。

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>戻り値

ボタンに関連付けられているショートカットメニューのリソース ID。ボタンに関連付けられているショートカットメニューがない場合は0。

### <a name="remarks"></a>Remarks

フレームワークは、ユーザーがボタンを右クリックしたときに、リソース ID を使用してショートカットメニューを作成します。

##  <a name="geteditborder"></a>CMFCToolBarEditBoxButton::GetEditBorder

エディットボックスボタンの編集部分の外接する四角形を取得します。

```
virtual void GetEditBorder(CRect& rectBorder);
```

### <a name="parameters"></a>パラメーター

*rectBorder*<br/>
入出力外接する四角形を`CRect`受け取るオブジェクトへの参照。

### <a name="remarks"></a>Remarks

このメソッドは、クライアント座標で編集コントロールの外接する四角形を取得します。 各方向の四角形のサイズを1ピクセルずつ拡大します。

[Cmfcvisualmanager:: OnDrawEditBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondraweditborder)メソッドは、オブジェクトの`CMFCToolBarEditBoxButton`周囲に境界線を描画するときに、このメソッドを呼び出します。

##  <a name="geteditbox"></a>CMFCToolBarEditBoxButton::GetEditBox

ボタンに埋め込まれている[CEdit クラス](../../mfc/reference/cedit-class.md)コントロールへのポインターを返します。

```
CEdit* GetEditBox() const;
```

### <a name="return-value"></a>戻り値

このボタンに含まれる[CEdit クラス](../../mfc/reference/cedit-class.md)コントロールへのポインター。 `CEdit`コントロールがまだ作成されていない場合は NULL になります。

### <a name="remarks"></a>Remarks

コントロールを作成`CEdit`するには、 [CMFCToolBarEditBoxButton:: createedit](#createedit)を呼び出します。

##  <a name="gethwnd"></a>CMFCToolBarEditBoxButton::GetHwnd

ツールバーボタンに関連付けられているウィンドウハンドルを取得します。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>戻り値

ボタンに関連付けられているウィンドウハンドル。

### <a name="remarks"></a>Remarks

このメソッドは、エディットボックスボタンの編集コントロール部分のウィンドウハンドルを返すことによって、 [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)メソッドをオーバーライドします。

##  <a name="getinvalidaterect"></a>CMFCToolBarEditBoxButton::GetInvalidateRect

再描画する必要があるボタンのクライアント領域の領域を取得します。

```
virtual const CRect GetInvalidateRect() const;
```

### <a name="return-value"></a>戻り値

再描画する必要がある領域を指定するオブジェクト。`CRect`

### <a name="remarks"></a>Remarks

このメソッドは、テキストラベルの領域を領域に含めることで、基本クラスの実装である[CMFCToolBarButton:: GetInvalidateRect](../../mfc/reference/cmfctoolbarbutton-class.md#getinvalidaterect)を拡張します。

##  <a name="havehotborder"></a>CMFCToolBarEditBoxButton:: ホットボーダーを持つ

ユーザーがボタンをクリックしたときに、ボタンの境界線を表示するかどうかを決定します。

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>戻り値

選択されたときにボタンの境界線が表示される場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このメソッドは、コントロールが表示されている場合に0以外の値を返すことによって、基底クラスの実装である[CMFCToolBarButton::](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)を拡張します。

##  <a name="isflatmode"></a>CMFCToolBarEditBoxButton::IsFlatMode

エディットボックスのボタンがフラットスタイルであるかどうかを判断します。

```
static BOOL __stdcall IsFlatMode();
```

### <a name="return-value"></a>戻り値

ボタンにフラットスタイルが設定されている場合は0以外の場合は。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

既定では、エディットボックスのボタンにはフラットスタイルが設定されています。 [CMFCToolBarEditBoxButton:: SetFlatMode](#setflatmode)メソッドを使用して、アプリケーションのフラットスタイルの外観を変更します。

##  <a name="notifycommand"></a>CMFCToolBarEditBoxButton:: NotifyCommand

ボタンが[WM_COMMAND](/windows/win32/menurc/wm-command)メッセージを処理するかどうかを指定します。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>パラメーター

*iNotifyCode*<br/>
からコマンドに関連付けられている通知メッセージ。

### <a name="return-value"></a>戻り値

ボタンが WM_COMMAND メッセージを処理する場合は TRUE。親ツールバーでメッセージを処理する必要があることを示す場合は FALSE。

### <a name="remarks"></a>Remarks

フレームワークは、親ウィンドウに[WM_COMMAND](/windows/win32/menurc/wm-command)メッセージを送信しようとしているときに、このメソッドを呼び出します。

このメソッドは、 [EN_UPDATE](/windows/win32/Controls/en-update)通知を処理することによって、基底クラスの実装 ( [CMFCToolBarButton:: notifycommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) を拡張します。 このオブジェクトと同じコマンド ID を持つ各エディットボックスに対して、そのテキストラベルがこのオブジェクトのテキストラベルに設定されます。

##  <a name="onaddtocustomizepage"></a>CMFCToolBarEditBoxButton:: OnAddToCustomizePage

ボタンが **[カスタマイズ]** ダイアログボックスに追加されたときにフレームワークによって呼び出されます。

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Remarks

このメソッドは、このオブジェクトと同じコマンド ID を持つ任意のツールバーのエディットボックスコントロールからプロパティをコピーすることによって、基本クラスの実装 ( [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)) を拡張します。 このメソッドは、このオブジェクトと同じコマンド ID を持つエディットボックスコントロールを持つツールバーがない場合は、何も行いません。

**[ユーザー設定]** ダイアログボックスの詳細については、「 [Cmfctoolbarscustomizedialog クラス](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)」を参照してください。

##  <a name="onchangeparentwnd"></a>CMFCToolBarEditBoxButton::OnChangeParentWnd

新しいツールバーにボタンが挿入されたときにフレームワークによって呼び出されます。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
から新しい親ウィンドウへのポインター。

### <a name="remarks"></a>Remarks

このメソッドは、内部`CEdit`オブジェクトを再作成することによって、基底クラスの実装 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) をオーバーライドします。

##  <a name="onclick"></a>CMFCToolBarEditBoxButton:: OnClick

ユーザーがマウスボタンをクリックしたときにフレームワークによって呼び出されます。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
から未使用.

*bDelay*<br/>
から未使用.

### <a name="return-value"></a>戻り値

ボタンがクリックメッセージを処理する場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このメソッドは、内部`CEdit`オブジェクトが表示されている場合に0以外の値を返すことによって、基底クラスの実装 ( [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)) をオーバーライドします。

##  <a name="onctlcolor"></a>CMFCToolBarEditBoxButton::OnCtlColor

親ツールバーが WM_CTLCOLOR メッセージを処理するときに、フレームワークによって呼び出されます。

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からボタンを表示するデバイスコンテキスト。

*nCtlColor*<br/>
から未使用.

### <a name="return-value"></a>戻り値

グローバルウィンドウブラシへのハンドル。

### <a name="remarks"></a>Remarks

このメソッドは、指定されたデバイスコンテキストのテキストと背景色をそれぞれグローバルテキストと背景色に設定することによって、基底クラスの実装 ( [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)) をオーバーライドします。

アプリケーションで使用できるグローバルオプションの詳細については、「 [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md)」を参照してください。

##  <a name="onglobalfontschanged"></a>CMFCToolBarEditBoxButton:: Onglobalフォントの変更

グローバルフォントが変更されたときにフレームワークによって呼び出されます。

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Remarks

このメソッドは、コントロールのフォントをグローバルフォントのフォントに変更することによって、基本クラスの実装 ( [CMFCToolBarButton:: Onglobalfont-size changed](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) を拡張します。

アプリケーションで使用できるグローバルオプションの詳細については、「 [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md)」を参照してください。

##  <a name="onmove"></a>CMFCToolBarEditBoxButton::OnMove

親ツールバーが移動したときにフレームワークによって呼び出されます。

```
virtual void OnMove();
```

### <a name="remarks"></a>Remarks

このメソッドは、内部`CEdit`オブジェクトの位置を更新することによって、既定のクラス実装 ( [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) をオーバーライドします。

##  <a name="onshow"></a>CMFCToolBarEditBoxButton:: OnShow

ボタンが表示または非表示になったときにフレームワークによって呼び出されます。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>パラメーター

*bShow*<br/>
からボタンを表示するかどうかを指定します。 このパラメーターが TRUE の場合は、ボタンが表示されます。 それ以外の場合、ボタンは表示されません。

### <a name="remarks"></a>Remarks

このメソッドは、 *bShow*が TRUE の場合にボタンを表示することによって、基底クラスの実装 ( [CMFCToolBarButton:: onshow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) を拡張します。 それ以外の場合、このメソッドはボタンを非表示にします。

##  <a name="onsize"></a>CMFCToolBarEditBoxButton:: OnSize

親ツールバーがサイズまたは位置を変更し、この変更によってボタンのサイズが変更されるときに、フレームワークによって呼び出されます。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>パラメーター

*iSize*<br/>
からボタンの新しい幅 (ピクセル単位)。

### <a name="remarks"></a>Remarks

このメソッドは、内部`CEdit`オブジェクトのサイズと位置を更新することによって、既定のクラス実装である[CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)をオーバーライドします。

##  <a name="onupdatetooltip"></a>CMFCToolBarEditBoxButton:: OnUpdateToolTip

親ツールバーがツールヒントテキストを更新するときに、フレームワークによって呼び出されます。

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
から未使用.

*iButtonIndex*<br/>
から未使用.

*wndToolTip*<br/>
からツールヒントのテキストを表示するコントロール。

*str*<br/>
入出力更新されたツールヒントテキストを受け取るオブジェクト。`CString`

### <a name="return-value"></a>戻り値

メソッドがツールヒントテキストを更新する場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンの編集部分に関連付けられているツールヒントテキストを表示することによって、基本クラスの実装 ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) を拡張します。 内部`CEdit`オブジェクトが NULL の場合、または`CEdit`オブジェクトのウィンドウハンドルが既存のウィンドウを識別しない場合、このメソッドは何も実行せず、FALSE を返します。

##  <a name="setcontents"></a>CMFCToolBarEditBoxButton:: SetContents

テキストボックスコントロールのテキストを設定します。

```
virtual void SetContents(const CString& sContents);
```

### <a name="parameters"></a>パラメーター

*sContents*<br/>
から設定する新しいテキストを指定します。

##  <a name="setcontentsall"></a>CMFCToolBarEditBoxButton:: Setのすべての目次

指定されたコマンド ID を持つ[CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md)オブジェクトを検索し、そのテキストボックス内に指定されたテキストを設定します。

```
static BOOL SetContentsAll(
    UINT uiCmd,
    const CString& strContents);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
からテキストを変更するコントロールのコマンド ID を指定します。

*strContents*<br/>
から設定する新しいテキストを指定します。

### <a name="return-value"></a>戻り値

テキストが設定されている場合は0以外の。指定した`CMFCToolBarEditBoxButton`コマンド ID を持つコントロールが存在しない場合は0。

##  <a name="setcontextmenuid"></a>CMFCToolBarEditBoxButton:: SetContextMenuID

ボタンに関連付けられているショートカットメニューのリソース ID を指定します。

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
からショートカットメニューのリソース ID。

### <a name="remarks"></a>Remarks

フレームワークは、ユーザーがツールバーボタンを右クリックしたときに、リソース ID を使用してショートカットメニューを作成します。

##  <a name="setflatmode"></a>CMFCToolBarEditBoxButton::SetFlatMode

アプリケーションのエディットボックスボタンのフラットスタイルの外観を指定します。

```
static void __stdcall SetFlatMode(BOOL bFlat = TRUE);
```

### <a name="parameters"></a>パラメーター

*bFlat*<br/>
からエディットボックスボタンのフラットスタイル。 このパラメーターが TRUE の場合、フラットスタイルの外観は有効です。それ以外の場合、フラットスタイルの外観は無効になります。

### <a name="remarks"></a>Remarks

エディットボックスボタンの既定のフラットスタイルは TRUE です。 [CMFCToolBarEditBoxButton:: IsFlatMode](#isflatmode)メソッドを使用して、アプリケーションのフラットスタイルの外観を取得します。

##  <a name="setstyle"></a>CMFCToolBarEditBoxButton:: System.windows.forms.control.setstyle

ツールバーのエディットボックスコントロールのスタイルを指定します。

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>パラメーター

*nStyle*<br/>
から設定する新しいスタイル。

### <a name="remarks"></a>Remarks

このメソッドは、 [CMFCToolBarButton:: m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle)を*nstyle*に設定します。これにより、アプリケーションがカスタマイズモードのときにテキストボックスが無効になり、アプリケーションがカスタマイズモードになっていないときに有効になります (「 [Cmfctoolbar:: setcustomize emode](../../mfc/reference/cmfctoolbar-class.md#setcustomizemode) 」を参照してください)。[Cmfctoolbar:: Isカスタマイズ emode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode))。 有効なスタイルフラグの一覧については、「 [ToolBar コントロールスタイル](../../mfc/reference/toolbar-control-styles.md)」を参照してください。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton クラス](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CEdit クラス](../../mfc/reference/cedit-class.md)<br/>
[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[チュートリアル: ツール バーへのコントロールの追加](../../mfc/walkthrough-putting-controls-on-toolbars.md)
