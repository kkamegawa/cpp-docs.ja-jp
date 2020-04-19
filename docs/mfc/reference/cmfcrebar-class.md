---
title: CMFCReBar クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCReBar
- AFXREBAR/CMFCReBar
- AFXREBAR/CMFCReBar::AddBar
- AFXREBAR/CMFCReBar::CalcFixedLayout
- AFXREBAR/CMFCReBar::CanFloat
- AFXREBAR/CMFCReBar::Create
- AFXREBAR/CMFCReBar::EnableDocking
- AFXREBAR/CMFCReBar::GetReBarBandInfoSize
- AFXREBAR/CMFCReBar::GetReBarCtrl
- AFXREBAR/CMFCReBar::OnShowControlBarMenu
- AFXREBAR/CMFCReBar::OnToolHitTest
- AFXREBAR/CMFCReBar::OnUpdateCmdUI
- AFXREBAR/CMFCReBar::SetPaneAlignment
helpviewer_keywords:
- CMFCReBar [MFC], AddBar
- CMFCReBar [MFC], CalcFixedLayout
- CMFCReBar [MFC], CanFloat
- CMFCReBar [MFC], Create
- CMFCReBar [MFC], EnableDocking
- CMFCReBar [MFC], GetReBarBandInfoSize
- CMFCReBar [MFC], GetReBarCtrl
- CMFCReBar [MFC], OnShowControlBarMenu
- CMFCReBar [MFC], OnToolHitTest
- CMFCReBar [MFC], OnUpdateCmdUI
- CMFCReBar [MFC], SetPaneAlignment
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
ms.openlocfilehash: d348cf7aac57ce213e4d3f602501d12cee8e20d8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505442"
---
# <a name="cmfcrebar-class"></a>CMFCReBar クラス

`CMFCReBar`オブジェクトは、rebar コントロールのレイアウト、永続性、および状態に関する情報を提供するコントロールバーです。
詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。
## <a name="syntax"></a>構文

```
class CMFCReBar : public CPane
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCReBar:: AddBar](#addbar)|バンドを rebar に追加します。|
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|( [Cbasepane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)をオーバーライドします)。|
|[CMFCReBar:: CanFloat](#canfloat)|( [Cbasepane:: CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)をオーバーライドします)。|
|[CMFCReBar:: Create](#create)|Rebar コントロールを作成し、 `CMFCReBar`オブジェクトにアタッチします。|
|[CMFCReBar:: EnableDocking](#enabledocking)|( [Cbasepane:: EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)をオーバーライドします)。|
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|基になる[Crebarctrl](../../mfc/reference/crebarctrl-class.md)コモンコントロールへの直接アクセスを提供します。|
|[CMFCReBar:: OnShowControlBarMenu](#onshowcontrolbarmenu)|( [CPane:: OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu)をオーバーライドします)。|
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|( [CWnd:: OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest)をオーバーライドします)。|
|[CMFCReBar:: OnUpdateCmdUI](#onupdatecmdui)|( [Cbasepane:: OnUpdateCmdUI](cbasepane-class.md)をオーバーライドします)。|
|[CMFCReBar:: Set Alignment](#setpanealignment)|( [Cbasepane:: Setpane alignment](../../mfc/reference/cbasepane-class.md#setpanealignment)をオーバーライドします)。|

## <a name="remarks"></a>Remarks

オブジェクト`CMFCReBar`には、さまざまな子ウィンドウを含めることができます。 これには、エディットボックス、ツールバー、およびリストボックスが含まれます。 Rebar のサイズはプログラムで変更することも、ユーザーがグリップバーをドラッグして rebar のサイズを手動で変更することもできます。 Rebar オブジェクトの背景を任意のビットマップに設定することもできます。

Rebar オブジェクトは、toolbar オブジェクトと同様に動作します。 Rebar コントロールには1つ以上のバンドを含めることができ、各バンドにはグリップバー、ビットマップ、テキストラベル、および子ウィンドウを含めることができます。

## <a name="example"></a>例

`CMFCReBar` クラスのさまざまなメソッドの使用方法を次の例に示します。 この例では、rebar コントロールを作成し、バンドを追加する方法を示します。 バンドは内部ツールバーとして機能します。 このコードスニペットは、 [Rebar テストサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[Cbasepane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxRebar

##  <a name="addbar"></a>  CMFCReBar::AddBar

バンドを rebar に追加します。

```
BOOL AddBar(
    CWnd* pBar,
    LPCTSTR pszText = NULL,
    CBitmap* pbmp = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,
    COLORREF clrFore,
    COLORREF clrBack,
    LPCTSTR pszText = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
[入力、出力]Rebar に挿入される子ウィンドウへのポインター。 参照されるオブジェクトには、 **WS_CHILD**ウィンドウスタイルが必要です。

*pszText*<br/>
からRebar に表示するテキストを指定します。 テキストは子ウィンドウの一部ではありません。 代わりに、rebar 自体に表示されます。

*.pbmp*<br/>
[入力、出力]Rebar の背景に表示されるビットマップを指定します。

*dwStyle*<br/>
からバンドに適用するスタイルを格納します。 バンドスタイルの完全な一覧については、Windows SDK `fStyle`のドキュメントの[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)構造にあるの説明を参照してください。

*clrFore*<br/>
からRebar の前景色を表します。

*clrBack*<br/>
からRebar の背景色を表します。

### <a name="return-value"></a>戻り値

バンドが rebar; に正常に追加された場合は TRUE。それ以外の場合は FALSE。

##  <a name="create"></a>CMFCReBar:: Create

Rebar コントロールを作成し、 [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)オブジェクトにアタッチします。

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
[入力、出力]この rebar コントロールの親ウィンドウへのポインター。

*dwCtrlStyle*<br/>
からRebar コントロールのスタイルを指定します。 既定のスタイル値は**RBS_BANDBORDERS**で、rebar コントロールの隣接するバンドを分離するための細い線を表示します。 有効なスタイルの一覧については、Windows SDK ドキュメントの「 [Rebar コントロールスタイル](/windows/win32/Controls/rebar-control-styles)」を参照してください。

*dwStyle*<br/>
からRebar コントロールのウィンドウスタイル。 有効なスタイルの一覧については、「[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)」を参照してください。

*nID*<br/>
からRebar の子ウィンドウ ID。

### <a name="return-value"></a>戻り値

Rebar が正常に作成された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="getrebarctrl"></a>CMFCReBar::GetReBarCtrl

オブジェクトの`CReBarCtrl` `CMFCReBar`基になるコモンコントロールへの直接アクセスを提供します。

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>戻り値

基になる`CReBarCtrl`オブジェクトへの参照。

### <a name="remarks"></a>Remarks

Rebar をカスタマイズするときに、Windows の rebar コモンコントロール機能を利用するには、このメソッドを呼び出します。

##  <a name="calcfixedlayout"></a>CMFCReBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>パラメーター

から*Bstretch*<br/>
から*bHorz*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="canfloat"></a>CMFCReBar:: CanFloat

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="enabledocking"></a>CMFCReBar:: EnableDocking

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>パラメーター

から*dwDockStyle*<br/>

### <a name="remarks"></a>Remarks

##  <a name="getrebarbandinfosize"></a>CMFCReBar::GetReBarBandInfoSize

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="onshowcontrolbarmenu"></a>CMFCReBar:: OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>パラメーター

から*CPoint*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="ontoolhittest"></a>  CMFCReBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>パラメーター

から*ポイント*<br/>
から*pTI*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="onupdatecmdui"></a>CMFCReBar:: OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>パラメーター

から*Ptarget*<br/>
から*Bdisableifnohndler*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setpanealignment"></a>CMFCReBar:: Set Alignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>パラメーター

から*dwAlignment*<br/>

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CReBarCtrl クラス](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane クラス](../../mfc/reference/cpane-class.md)
