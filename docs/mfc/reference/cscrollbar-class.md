---
title: CScrollBar クラス
ms.date: 11/04/2016
f1_keywords:
- CScrollBar
- AFXWIN/CScrollBar
- AFXWIN/CScrollBar::CScrollBar
- AFXWIN/CScrollBar::Create
- AFXWIN/CScrollBar::EnableScrollBar
- AFXWIN/CScrollBar::GetScrollBarInfo
- AFXWIN/CScrollBar::GetScrollInfo
- AFXWIN/CScrollBar::GetScrollLimit
- AFXWIN/CScrollBar::GetScrollPos
- AFXWIN/CScrollBar::GetScrollRange
- AFXWIN/CScrollBar::SetScrollInfo
- AFXWIN/CScrollBar::SetScrollPos
- AFXWIN/CScrollBar::SetScrollRange
- AFXWIN/CScrollBar::ShowScrollBar
helpviewer_keywords:
- CScrollBar [MFC], CScrollBar
- CScrollBar [MFC], Create
- CScrollBar [MFC], EnableScrollBar
- CScrollBar [MFC], GetScrollBarInfo
- CScrollBar [MFC], GetScrollInfo
- CScrollBar [MFC], GetScrollLimit
- CScrollBar [MFC], GetScrollPos
- CScrollBar [MFC], GetScrollRange
- CScrollBar [MFC], SetScrollInfo
- CScrollBar [MFC], SetScrollPos
- CScrollBar [MFC], SetScrollRange
- CScrollBar [MFC], ShowScrollBar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
ms.openlocfilehash: cd0c1ed85969d50548cf6b2be1d5677ed62110bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502565"
---
# <a name="cscrollbar-class"></a>CScrollBar クラス

Windows のスクロール バー コントロールの機能を提供します。

## <a name="syntax"></a>構文

```
class CScrollBar : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CScrollBar:: CScrollBar](#cscrollbar)|`CScrollBar` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CScrollBar:: Create](#create)|Windows のスクロールバーを作成し、 `CScrollBar`オブジェクトにアタッチします。|
|[CScrollBar:: EnableScrollBar](#enablescrollbar)|スクロール バーの矢印の一方または両方を有効または無効にします。|
|[CScrollBar:: GetScrollBarInfo](#getscrollbarinfo)|`SCROLLBARINFO`構造体を使用して、スクロールバーに関する情報を取得します。|
|[CScrollBar:: GetScrollInfo](#getscrollinfo)|スクロールバーに関する情報を取得します。|
|[CScrollBar:: GetScrollLimit](#getscrolllimit)|スクロールバーの制限を取得します。|
|[CScrollBar:: GetScrollPos](#getscrollpos)|スクロール ボックスの現在位置を取得します。|
|[CScrollBar::GetScrollRange](#getscrollrange)|指定されたスクロールバーの現在の最小および最大のスクロールバーの位置を取得します。|
|[CScrollBar:: SetScrollInfo](#setscrollinfo)|スクロール バーの情報を設定します。|
|[CScrollBar:: SetScrollPos](#setscrollpos)|スクロールボックスの現在位置を設定します。|
|[CScrollBar::SetScrollRange](#setscrollrange)|指定されたスクロール バーの最小位置と最大位置の値を設定します。|
|[CScrollBar:: ShowScrollBar](#showscrollbar)|スクロールバーの表示と非表示を切り替えます。|

## <a name="remarks"></a>Remarks

スクロールバーコントロールを作成するには、2つの手順を実行します。 まず`CScrollBar` 、コンストラクター `CScrollBar`を呼び出してオブジェクトを作成した後、 [create](#create) member 関数を呼び出して、Windows のスクロール`CScrollBar`バーコントロールを作成し、オブジェクトにアタッチします。

ダイアログボックス内で`CScrollBar` (ダイアログリソースを使用して) `CScrollBar`オブジェクトを作成すると、ユーザーがダイアログボックスを閉じたときにが自動的に破棄されます。

ウィンドウ内に`CScrollBar`オブジェクトを作成する場合は、そのオブジェクトを破棄することも必要になることがあります。

スタックに`CScrollBar`オブジェクトを作成すると、そのオブジェクトは自動的に破棄されます。 新しい関数を使用`CScrollBar`してヒープにオブジェクトを作成する場合は、ユーザーが Windows スクロールバーを終了したときにオブジェクトを破棄するために、オブジェクトに対して**delete**を呼び出す必要があります。

`CScrollBar`オブジェクトにメモリを割り当てる場合は、 `CScrollBar`デストラクターをオーバーライドして割り当てを破棄します。

の使用`CScrollBar`に関する関連情報については、「[コントロール](../../mfc/controls-mfc.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="create"></a>  CScrollBar::Create

Windows のスクロールバーを作成し、 `CScrollBar`オブジェクトにアタッチします。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
スクロールバーのスタイルを指定します。 スクロールバー[スタイル](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)の任意の組み合わせをスクロールバーに適用します。

*rect*<br/>
スクロールバーのサイズと位置を指定します。 に`RECT`は、構造体`CRect`またはオブジェクトを指定できます。

*pParentWnd*<br/>
スクロールバーの親ウィンドウ (通常`CDialog`はオブジェクト) を指定します。 NULL にすることはできません。

*nID*<br/>
スクロールバーのコントロール ID。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

オブジェクトを構築`CScrollBar`するには、2つの手順を実行します。 最初に、 `CScrollBar`オブジェクトを構築するコンストラクターを呼び出します。次`Create`に、を呼び出します。これにより、関連付けられた`CScrollBar` Windows スクロールバーが作成および初期化され、オブジェクトにアタッチされます。

次の[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)をスクロールバーに適用します。

- 常に WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED はまれ

- グループコントロールに WS_GROUP

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

##  <a name="cscrollbar"></a>CScrollBar:: CScrollBar

`CScrollBar` オブジェクトを構築します。

```
CScrollBar();
```

### <a name="remarks"></a>Remarks

オブジェクトを構築した後、 `Create`メンバー関数を呼び出して、Windows のスクロールバーを作成して初期化します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

##  <a name="enablescrollbar"></a>  CScrollBar::EnableScrollBar

スクロール バーの矢印の一方または両方を有効または無効にします。

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>パラメーター

*nArrowFlags*<br/>
スクロール矢印を有効または無効にするかどうか、および有効または無効にする矢印を指定します。 このパラメーターには、次のいずれかの値を指定できます。

- ESB_ENABLE_BOTH を使用すると、スクロールバーの両方の矢印が有効になります。

- ESB_DISABLE_LTUP は、水平スクロールバーまたは垂直スクロールバーの上矢印の左矢印を無効にします。

- ESB_DISABLE_RTDN は、水平スクロールバーまたは垂直スクロールバーの下矢印の右矢印を無効にします。

- ESB_DISABLE_BOTH は、スクロールバーの両方の矢印を無効にします。

### <a name="return-value"></a>戻り値

指定に従って矢印が有効または無効になっている場合は0以外の。それ以外の場合は0。矢印が既に要求された状態であるか、またはエラーが発生したことを示します。

### <a name="example"></a>例

  [Cscrollbar:: SetScrollRange](#setscrollrange)の例を参照してください。

##  <a name="getscrollbarinfo"></a>CScrollBar:: GetScrollBarInfo

 `SCROLLBARINFO` 構造体がスクロール バーについて保持している情報を取得します。

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>パラメーター

*pScrollInfo*<br/>
[SCROLLBARINFO](/windows/win32/api/winuser/ns-winuser-scrollbarinfo)構造体へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [SBM_SCROLLBARINFO](/windows/win32/Controls/sbm-getscrollbarinfo)メッセージの機能をエミュレートします。

##  <a name="getscrollinfo"></a>  CScrollBar::GetScrollInfo

 `SCROLLINFO` 構造体がスクロール バーについて保持している情報を取得します。

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>パラメーター

*lpScrollInfo*<br/>
[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)構造体へのポインター。 この構造体の詳細については、Windows SDK を参照してください。

*nMask*<br/>
取得するスクロールバーのパラメーターを指定します。 一般的な使用法である SIF_ALL は、SIF_PAGE、SIF_POS、SIF_TRACKPOS、および SIF_RANGE の組み合わせを指定します。 Nmask 値の詳細については、「」を参照してください`SCROLLINFO` 。

### <a name="return-value"></a>戻り値

メッセージが値を取得した場合、戻り値は TRUE になります。 それ以外の場合は FALSE になります。

### <a name="remarks"></a>Remarks

`GetScrollInfo`アプリケーションで32ビットのスクロール位置を使用できるようにします。

[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)構造体には、スクロールバーの最小値と最大値、ページサイズ、スクロールボックスの位置 (つまみ) などの情報が含まれています。 構造体の既定値の変更の詳細については、Windows SDK の構造に関するトピックを参照してください。`SCROLLINFO`

スクロールバーの位置を示す MFC Windows メッセージハンドラー ([CWnd:: OnHScroll] と [ [cwnd:: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)]) では、位置データの16ビットのみが提供されます。 `GetScrollInfo`と`SetScrollInfo`は、32ビットのスクロールバーの位置データを提供します。 したがって、アプリケーションは、 `GetScrollInfo`または`CWnd::OnVScroll`の`CWnd::OnHScroll`いずれかを処理中にを呼び出して、32ビットのスクロールバーの位置データを取得できます。

### <a name="example"></a>例

  [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)の例を参照してください。

##  <a name="getscrolllimit"></a>  CScrollBar::GetScrollLimit

スクロールバーのスクロールの最大位置を取得します。

```
int GetScrollLimit();
```

### <a name="return-value"></a>戻り値

成功した場合のスクロールバーの最大位置を指定します。それ以外の場合は0です。

### <a name="example"></a>例

  [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)の例を参照してください。

##  <a name="getscrollpos"></a>CScrollBar:: GetScrollPos

スクロール ボックスの現在位置を取得します。

```
int GetScrollPos() const;
```

### <a name="return-value"></a>戻り値

成功した場合のスクロールボックスの現在位置を指定します。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

現在の位置は、現在のスクロール範囲に依存する相対値です。 たとえば、スクロールの範囲が100から200で、スクロールボックスがバーの中央にある場合、現在の位置は150になります。

### <a name="example"></a>例

  [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)の例を参照してください。

##  <a name="getscrollrange"></a>  CScrollBar::GetScrollRange

指定されたスクロールバーの現在の最小および最大のスクロールバーの位置を、 *Lpminpos*および*lpminpos*によって指定された場所にコピーします。

```
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>パラメーター

*lpMinPos*<br/>
最小位置を受け取る整数変数を指します。

*lpMaxPos*<br/>
最大位置を受け取る整数変数を指します。

### <a name="remarks"></a>Remarks

スクロールバーコントロールの既定の範囲は空です (両方の値が0です)。

### <a name="example"></a>例

  [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)の例を参照してください。

##  <a name="setscrollinfo"></a>CScrollBar:: SetScrollInfo

構造体が`SCROLLINFO`スクロールバーに関して保持する情報を設定します。

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>パラメーター

*lpScrollInfo*<br/>
[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)構造体へのポインター。

*より描画*<br/>
新しい情報を反映するためにスクロールバーを再描画するかどうかを指定します。 [表示*描画*] が TRUE の場合、スクロールバーが再描画されます。 FALSE の場合は、再描画されません。 既定では、スクロールバーが再描画されます。

### <a name="return-value"></a>戻り値

成功した場合、戻り値は TRUE になります。 それ以外の場合は FALSE になります。

### <a name="remarks"></a>Remarks

フラグの値を含む、構造体`SCROLLINFO`のパラメーターに必要な値を指定する必要があります。

構造`SCROLLINFO`体には、スクロールバーの最小値と最大値、ページサイズ、スクロールボックスの位置 (つまみ) などの情報が含まれます。 構造の既定値の変更の詳細については、Windows SDK の[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) structure のトピックを参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

##  <a name="setscrollpos"></a>CScrollBar:: SetScrollPos

スクロールボックスの現在位置を*nPos*で指定した位置に設定し、指定した場合は、新しい位置を反映するようにスクロールバーを再描画します。

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
スクロールボックスの新しい位置を指定します。 スクロール範囲内である必要があります。

*より描画*<br/>
新しい位置を反映するためにスクロールバーを再描画するかどうかを指定します。 [表示*描画*] が TRUE の場合、スクロールバーが再描画されます。 FALSE の場合は、再描画されません。 既定では、スクロールバーが再描画されます。

### <a name="return-value"></a>戻り値

成功した場合は、スクロールボックスの前の位置を指定します。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

スクロールバーが短い間隔で2回再描画されないようにするために、別の関数の後続の呼び出しによってスクロールバーが再描画されるときは常に、値を FALSE に設定します。

### <a name="example"></a>例

  [Cscrollbar:: SetScrollRange](#setscrollrange)の例を参照してください。

##  <a name="setscrollrange"></a>  CScrollBar::SetScrollRange

指定されたスクロール バーの最小位置と最大位置の値を設定します。

```
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>パラメーター

*nMinPos*<br/>
スクロール位置の最小値を指定します。

*nMaxPos*<br/>
スクロール位置の最大値を指定します。

*より描画*<br/>
変更を反映するためにスクロールバーを再描画するかどうかを指定します。 [表示*描画*] が TRUE の場合、スクロールバーは再描画されます。FALSE の場合、再描画されません。 既定では再描画されます。

### <a name="remarks"></a>Remarks

標準スクロールバーを非表示にするには、 *Nminpos*と*nminpos*を0に設定します。

スクロールバーの通知メッセージの処理中にスクロールバーを非表示にするために、この関数を呼び出さないでください。

の呼び出し`SetScrollRange`がメンバー関数の `SetScrollPos` `SetScrollPos`呼び出しの直後に続く場合は、をに設定して、スクロールバーが2回再描画されないようにします。

*Nminpos*によって指定された値と*nminpos*の違いは、32767を超えることはできません。 スクロールバーコントロールの既定の範囲は空です ( *Nminpos*と*nminpos*の両方が0です)。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

##  <a name="showscrollbar"></a>CScrollBar:: ShowScrollBar

スクロールバーの表示と非表示を切り替えます。

```
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>パラメーター

*bShow*<br/>
スクロールバーを表示するか非表示にするかを指定します。 このパラメーターが TRUE の場合、スクロールバーが表示されます。それ以外の場合は非表示になります。

### <a name="remarks"></a>Remarks

アプリケーションでは、スクロールバーの通知メッセージの処理中にスクロールバーを非表示にするために、この関数を呼び出すことはできません。

### <a name="example"></a>例

  [Cscrollbar:: Create](#create)の例を参照してください。

## <a name="see-also"></a>関連項目

[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[CButton クラス](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox クラス](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit クラス](../../mfc/reference/cedit-class.md)<br/>
[CListBox クラス](../../mfc/reference/clistbox-class.md)<br/>
[CStatic クラス](../../mfc/reference/cstatic-class.md)<br/>
[CDialog クラス](../../mfc/reference/cdialog-class.md)
