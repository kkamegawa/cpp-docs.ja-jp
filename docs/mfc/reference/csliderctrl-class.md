---
title: Csliderctrl 使い方クラス
ms.date: 11/04/2016
f1_keywords:
- CSliderCtrl
- AFXCMN/CSliderCtrl
- AFXCMN/CSliderCtrl::CSliderCtrl
- AFXCMN/CSliderCtrl::ClearSel
- AFXCMN/CSliderCtrl::ClearTics
- AFXCMN/CSliderCtrl::Create
- AFXCMN/CSliderCtrl::CreateEx
- AFXCMN/CSliderCtrl::GetBuddy
- AFXCMN/CSliderCtrl::GetChannelRect
- AFXCMN/CSliderCtrl::GetLineSize
- AFXCMN/CSliderCtrl::GetNumTics
- AFXCMN/CSliderCtrl::GetPageSize
- AFXCMN/CSliderCtrl::GetPos
- AFXCMN/CSliderCtrl::GetRange
- AFXCMN/CSliderCtrl::GetRangeMax
- AFXCMN/CSliderCtrl::GetRangeMin
- AFXCMN/CSliderCtrl::GetSelection
- AFXCMN/CSliderCtrl::GetThumbLength
- AFXCMN/CSliderCtrl::GetThumbRect
- AFXCMN/CSliderCtrl::GetTic
- AFXCMN/CSliderCtrl::GetTicArray
- AFXCMN/CSliderCtrl::GetTicPos
- AFXCMN/CSliderCtrl::GetToolTips
- AFXCMN/CSliderCtrl::SetBuddy
- AFXCMN/CSliderCtrl::SetLineSize
- AFXCMN/CSliderCtrl::SetPageSize
- AFXCMN/CSliderCtrl::SetPos
- AFXCMN/CSliderCtrl::SetRange
- AFXCMN/CSliderCtrl::SetRangeMax
- AFXCMN/CSliderCtrl::SetRangeMin
- AFXCMN/CSliderCtrl::SetSelection
- AFXCMN/CSliderCtrl::SetThumbLength
- AFXCMN/CSliderCtrl::SetTic
- AFXCMN/CSliderCtrl::SetTicFreq
- AFXCMN/CSliderCtrl::SetTipSide
- AFXCMN/CSliderCtrl::SetToolTips
helpviewer_keywords:
- CSliderCtrl [MFC], CSliderCtrl
- CSliderCtrl [MFC], ClearSel
- CSliderCtrl [MFC], ClearTics
- CSliderCtrl [MFC], Create
- CSliderCtrl [MFC], CreateEx
- CSliderCtrl [MFC], GetBuddy
- CSliderCtrl [MFC], GetChannelRect
- CSliderCtrl [MFC], GetLineSize
- CSliderCtrl [MFC], GetNumTics
- CSliderCtrl [MFC], GetPageSize
- CSliderCtrl [MFC], GetPos
- CSliderCtrl [MFC], GetRange
- CSliderCtrl [MFC], GetRangeMax
- CSliderCtrl [MFC], GetRangeMin
- CSliderCtrl [MFC], GetSelection
- CSliderCtrl [MFC], GetThumbLength
- CSliderCtrl [MFC], GetThumbRect
- CSliderCtrl [MFC], GetTic
- CSliderCtrl [MFC], GetTicArray
- CSliderCtrl [MFC], GetTicPos
- CSliderCtrl [MFC], GetToolTips
- CSliderCtrl [MFC], SetBuddy
- CSliderCtrl [MFC], SetLineSize
- CSliderCtrl [MFC], SetPageSize
- CSliderCtrl [MFC], SetPos
- CSliderCtrl [MFC], SetRange
- CSliderCtrl [MFC], SetRangeMax
- CSliderCtrl [MFC], SetRangeMin
- CSliderCtrl [MFC], SetSelection
- CSliderCtrl [MFC], SetThumbLength
- CSliderCtrl [MFC], SetTic
- CSliderCtrl [MFC], SetTicFreq
- CSliderCtrl [MFC], SetTipSide
- CSliderCtrl [MFC], SetToolTips
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
ms.openlocfilehash: 8fffdfc002b25fdcd72dcbbf53e7e6c321f55296
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502517"
---
# <a name="csliderctrl-class"></a>Csliderctrl 使い方クラス

Windows コモン スライダー コントロールの機能を提供します。

## <a name="syntax"></a>構文

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[Csliderctrl 使い方:: Csliderctrl 使い方](#csliderctrl)|`CSliderCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[Csliderctrl 使い方:: ClearSel](#clearsel)|スライダーコントロールの現在の選択範囲をクリアします。|
|[Csliderctrl 使い方:: ClearTics](#cleartics)|スライダーコントロールから現在の目盛りを削除します。|
|[Csliderctrl 使い方:: Create](#create)|スライダーコントロールを作成し、 `CSliderCtrl`オブジェクトにアタッチします。|
|[Csliderctrl 使い方:: CreateEx](#createex)|指定した Windows 拡張スタイルを使用してスライダーコントロールを作成し`CSliderCtrl` 、オブジェクトにアタッチします。|
|[Csliderctrl 使い方:: GetBuddy](#getbuddy)|指定した位置にあるスライダーコントロールの関連ウィンドウへのハンドルを取得します。|
|[Csliderctrl 使い方:: GetChannelRect](#getchannelrect)|スライダーコントロールのチャネルのサイズを取得します。|
|[Csliderctrl 使い方:: GetLineSize](#getlinesize)|スライダーコントロールの行のサイズを取得します。|
|[CSliderCtrl::GetNumTics](#getnumtics)|スライダーコントロールの目盛りの数を取得します。|
|[Csliderctrl 使い方:: GetPageSize](#getpagesize)|スライダーコントロールのページサイズを取得します。|
|[Csliderctrl 使い方:: GetPos](#getpos)|スライダーの現在位置を取得します。|
|[CSliderCtrl::GetRange](#getrange)|スライダーの位置の最小値と最大値を取得します。|
|[CSliderCtrl::GetRangeMax](#getrangemax)|スライダーの最大位置を取得します。|
|[CSliderCtrl::GetRangeMin](#getrangemin)|スライダーの最小位置を取得します。|
|[Csliderctrl 使い方:: GetSelection](#getselection)|現在の選択範囲を取得します。|
|[CSliderCtrl::GetThumbLength](#getthumblength)|現在の trackbar コントロールのスライダーの長さを取得します。|
|[Csliderctrl 使い方:: GetThumbRect](#getthumbrect)|スライダーコントロールのつまみのサイズを取得します。|
|[Csliderctrl 使い方:: GetTic](#gettic)|指定した目盛りの位置を取得します。|
|[Csliderctrl 使い方:: Getの配列](#getticarray)|スライダーコントロールの目盛りの位置の配列を取得します。|
|[Csliderctrl 使い方:: Get、Pos](#getticpos)|指定した目盛りの位置をクライアント座標で取得します。|
|[Csliderctrl 使い方:: GetToolTips ヒント](#gettooltips)|スライダーコントロールに割り当てられているツールヒントコントロール (存在する場合) へのハンドルを取得します。|
|[Csliderctrl 使い方:: SetBuddy](#setbuddy)|スライダーコントロールの関連ウィンドウとしてウィンドウを割り当てます。|
|[Csliderctrl 使い方:: SetLineSize](#setlinesize)|スライダーコントロールの線のサイズを設定します。|
|[Csliderctrl 使い方:: SetPageSize](#setpagesize)|スライダーコントロールのページサイズを設定します。|
|[Csliderctrl 使い方:: SetPos](#setpos)|スライダーの現在位置を設定します。|
|[CSliderCtrl::SetRange](#setrange)|スライダーの位置の最小値と最大値を設定します。|
|[CSliderCtrl::SetRangeMax](#setrangemax)|スライダーの最大位置を設定します。|
|[CSliderCtrl::SetRangeMin](#setrangemin)|スライダーの最小位置を設定します。|
|[Csliderctrl 使い方:: SetSelection](#setselection)|現在の選択範囲を設定します。|
|[Csliderctrl 使い方:: SetThumbLength](#setthumblength)|現在の trackbar コントロールのスライダーの長さを設定します。|
|[Csliderctrl 使い方:: SetTic](#settic)|指定した目盛りの位置を設定します。|
|[CSliderCtrl::SetTicFreq](#setticfreq)|スライダーコントロールごとの目盛りの間隔を設定します。|
|[Csliderctrl 使い方:: Setヒント側](#settipside)|Trackbar コントロールによって使用されるツールヒントコントロールを配置します。|
|[Csliderctrl 使い方:: SetToolTips ヒント](#settooltips)|ツールヒントコントロールをスライダーコントロールに割り当てます。|

## <a name="remarks"></a>Remarks

"スライダーコントロール" (トラックバーとも呼ばれます) は、スライダーと省略可能な目盛りを含むウィンドウです。 ユーザーがマウスまたは方向キーを使用してスライダーを移動すると、コントロールは通知メッセージを送信して変更を示します。

スライダーコントロールは、ユーザーが範囲内の不連続値または連続する値のセットを選択する場合に便利です。 たとえば、スライダーコントロールを使用して、ユーザーがスライダーを所定の目盛りに動かして、キーボードの繰り返し速度を設定できるようにすることができます。

このコントロール (および`CSliderCtrl`クラス) は、windows 95/98 および windows NT バージョン3.51 以降で実行されているプログラムに対してのみ使用できます。

スライダーは、作成時に指定した増分で移動します。 たとえば、スライダーの範囲を5にするように指定した場合、スライダーは、スライダーコントロールの左側の位置と範囲内のインクリメントごとに1つの位置の6つの位置のみを占めることができます。 通常、これらの各位置は目盛りによって識別されます。

スライダーを作成するには、の`Create` `CSliderCtrl`コンストラクターとメンバー関数を使用します。 スライダーコントロールを作成した後は、のメンバー関数`CSliderCtrl`を使用して、そのプロパティの多くを変更できます。 加えられる変更には、スライダーの最小位置と最大位置の設定、目盛りの描画、選択範囲の設定、およびスライダーの位置変更が含まれます。

の使用方法`CSliderCtrl`の詳細については、「 [Controls](../../mfc/controls-mfc.md) and [using csliderctrl 使い方](../../mfc/using-csliderctrl.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcmn.h

##  <a name="clearsel"></a>Csliderctrl 使い方:: ClearSel

スライダーコントロールの現在の選択範囲をクリアします。

```
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>パラメーター

*より描画*<br/>
再描画フラグ。 このパラメーターが TRUE の場合、選択がクリアされた後にスライダーが再描画されます。それ以外の場合、スライダーは再描画されません。

##  <a name="cleartics"></a>Csliderctrl 使い方:: ClearTics

スライダーコントロールから現在の目盛りを削除します。

```
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>パラメーター

*より描画*<br/>
再描画フラグ。 このパラメーターが TRUE の場合、目盛りがクリアされた後にスライダーが再描画されます。それ以外の場合、スライダーは再描画されません。

##  <a name="create"></a>  CSliderCtrl::Create

スライダーコントロールを作成し、 `CSliderCtrl`オブジェクトにアタッチします。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
スライダーコントロールのスタイルを指定します。 Windows SDK で説明されている[スライダーコントロールスタイル](/windows/win32/Controls/trackbar-control-styles)の任意の組み合わせをコントロールに適用します。

*rect*<br/>
スライダーコントロールのサイズと位置を指定します。 これは、 [CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトまたは[RECT](/previous-versions/dd162897\(v=vs.85\))構造体のいずれかになります。

*pParentWnd*<br/>
スライダーコントロールの親ウィンドウ (通常は`CDialog`) を指定します。 NULL にすることはできません。

*nID*<br/>
スライダーコントロールの ID を指定します。

### <a name="return-value"></a>戻り値

初期化が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

を作成する`CSliderCtrl`には、2つの手順を実行します。 まず、コンストラクターを呼び出し、次にを`Create`呼び出します。これにより、スライダーコントロールが作成`CSliderCtrl`され、オブジェクトにアタッチされます。

*DwStyle*に設定されている値に応じて、スライダーコントロールは垂直方向または水平方向のどちらかを持つことができます。 両端に目盛りを設定するか、どちらか一方または両方に目盛りを付けることができます。 また、連続する値の範囲を指定するために使用することもできます。

拡張ウィンドウスタイルをスライダーコントロールに適用するには、では`Create`なく [CreateEx](#createex) を呼び出します。

##  <a name="createex"></a>  CSliderCtrl::CreateEx

コントロール (子ウィンドウ) を作成し、 `CSliderCtrl`オブジェクトに関連付けます。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwExStyle*<br/>
作成するコントロールの拡張スタイルを指定します。 拡張 Windows スタイルの一覧については、Windows SDK の[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)の*dwexstyle*パラメーターを参照してください。

*dwStyle*<br/>
スライダーコントロールのスタイルを指定します。 Windows SDK で説明されている[スライダーコントロールスタイル](/windows/win32/Controls/trackbar-control-styles)の任意の組み合わせをコントロールに適用します。

*rect*<br/>
*PParentWnd*のクライアント座標で、作成されるウィンドウのサイズと位置を記述する[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。

*pParentWnd*<br/>
コントロールの親であるウィンドウへのポインター。

*nID*<br/>
コントロールの子ウィンドウ ID。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

Windows `CreateEx`拡張スタイルの先頭**WS_EX_** によって指定された拡張 windows スタイルを適用するには、[[作成](#create)] ではなくを使用します。

##  <a name="csliderctrl"></a>Csliderctrl 使い方:: Csliderctrl 使い方

`CSliderCtrl` オブジェクトを構築します。

```
CSliderCtrl();
```

##  <a name="getbuddy"></a>  CSliderCtrl::GetBuddy

指定した位置にあるスライダーコントロールの関連ウィンドウへのハンドルを取得します。

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>パラメーター

*fLocation*<br/>
2つの関連ウィンドウハンドルのうち、どれを取得するかを示すブール値。 次のいずれかの値になります。

- TRUE は、スライダーの左にあるメンバーを対象とするハンドルを取得します。 スライダーコントロールで TBS_VERT スタイルが使用されている場合、メッセージは、スライダーの上にある関連するを取得します。

- FALSE は、スライダーの右側にあるメンバーへのハンドルを取得します。 スライダーコントロールで TBS_VERT スタイルが使用されている場合、メッセージは、スライダーの下にある友人を取得します。

### <a name="return-value"></a>戻り値

*Flocation*によって指定された場所にある関連ウィンドウである[CWnd](../../mfc/reference/cwnd-class.md)オブジェクトへのポインター。その場所に関連ウィンドウが存在しない場合は NULL。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy)の動作を実装します。 スライダーコントロールスタイルの説明については、Windows SDK の「 [Trackbar コントロールスタイル](/windows/win32/Controls/trackbar-control-styles)」を参照してください。

##  <a name="getchannelrect"></a>  CSliderCtrl::GetChannelRect

スライダーコントロールのチャネルの外接する四角形のサイズと位置を取得します。

```
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>パラメーター

*lprc*<br/>
関数がを返したときのチャネルの外接する四角形のサイズと位置を格納している、 [CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

チャネルは、スライダーが移動する領域であり、範囲が選択されている場合は強調表示を含みます。

##  <a name="getlinesize"></a>  CSliderCtrl::GetLineSize

スライダーコントロールの線のサイズを取得します。

```
int GetLineSize() const;
```

### <a name="return-value"></a>戻り値

スライダーコントロールの線のサイズ。

### <a name="remarks"></a>Remarks

線のサイズは、TB_LINEUP および TB_LINEDOWN 通知のスライダーの移動量に影響します。 行サイズの既定の設定は1です。

##  <a name="getnumtics"></a>  CSliderCtrl::GetNumTics

スライダーコントロールの目盛りの数を取得します。

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>戻り値

スライダーコントロールの目盛りの数。

##  <a name="getpagesize"></a>  CSliderCtrl::GetPageSize

スライダーコントロールのページのサイズを取得します。

```
int GetPageSize() const;
```

### <a name="return-value"></a>戻り値

スライダーコントロールのページのサイズ。

### <a name="remarks"></a>Remarks

ページサイズは、TB_PAGEUP および TB_PAGEDOWN 通知のスライダーの移動量に影響します。

##  <a name="getpos"></a>  CSliderCtrl::GetPos

スライダーコントロールのスライダーの現在位置を取得します。

```
int GetPos() const;
```

### <a name="return-value"></a>戻り値

現在位置を返します。

##  <a name="getrange"></a>  CSliderCtrl::GetRange

スライダーコントロールのスライダーの最大位置と最小位置を取得します。

```
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>パラメーター

*N1 日*<br/>
最小位置を受け取る整数への参照。

*N1 日*<br/>
最大位置を受け取る整数への参照。

### <a name="remarks"></a>Remarks

この関数は、 *Nmin*および*n1 日*によって参照される整数に値をコピーします。

##  <a name="getrangemax"></a>  CSliderCtrl::GetRangeMax

スライダーコントロールのスライダーの最大位置を取得します。

```
int GetRangeMax() const;
```

### <a name="return-value"></a>戻り値

コントロールの最大位置。

##  <a name="getrangemin"></a>  CSliderCtrl::GetRangeMin

スライダーコントロールのスライダーの最小位置を取得します。

```
int GetRangeMin() const;
```

### <a name="return-value"></a>戻り値

コントロールの最小位置。

##  <a name="getselection"></a>Csliderctrl 使い方:: GetSelection

スライダーコントロール内の現在の選択範囲の開始位置と終了位置を取得します。

```
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>パラメーター

*N1 日*<br/>
現在の選択範囲の開始位置を受け取る整数への参照。

*N1 日*<br/>
現在の選択範囲の終了位置を受け取る整数への参照。

##  <a name="getthumblength"></a>  CSliderCtrl::GetThumbLength

現在の trackbar コントロールのスライダーの長さを取得します。

```
int GetThumbLength() const;
```

### <a name="return-value"></a>戻り値

スライダーの長さ (ピクセル単位)。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[TBM_GETTHUMBLENGTH](/windows/win32/Controls/tbm-getthumblength)メッセージを送信します。

##  <a name="getthumbrect"></a>Csliderctrl 使い方:: GetThumbRect

スライダーコントロールのスライダー (つまみ) の外接する四角形のサイズと位置を取得します。

```
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>パラメーター

*lprc*<br/>
関数が戻るとき`CRect`に、スライダーの外接する四角形を格納しているオブジェクトへのポインター。

##  <a name="gettic"></a>  CSliderCtrl::GetTic

スライダーコントロールの目盛りの位置を取得します。

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>パラメーター

*nTic*<br/>
目盛りを識別する0から始まるインデックス。

### <a name="return-value"></a>戻り値

指定された目盛りの位置。 *Ntic*で有効なインデックスが指定されていない場合は-1。

##  <a name="getticarray"></a>  CSliderCtrl::GetTicArray

スライダーコントロールの目盛りの位置を格納している配列のアドレスを取得します。

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>戻り値

スライダーコントロールの目盛りの位置を格納している配列のアドレス。

##  <a name="getticpos"></a>Csliderctrl 使い方:: Get、Pos

スライダーコントロールの目盛りの現在の物理的な位置を取得します。

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>パラメーター

*nTic*<br/>
目盛りを識別する0から始まるインデックス。

### <a name="return-value"></a>戻り値

指定したティックの物理的な位置 (クライアント座標)。 *Ntic*が有効なインデックスを指定しない場合は-1。

##  <a name="gettooltips"></a>Csliderctrl 使い方:: GetToolTips ヒント

スライダーコントロールに割り当てられているツールヒントコントロール (存在する場合) へのハンドルを取得します。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>戻り値

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)オブジェクトへのポインター。ツールヒントが使用されていない場合は NULL。 スライダーコントロールで TBS_TOOLTIPS スタイルが使用されていない場合、戻り値は NULL になります。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips)の動作を実装します。 このメンバー関数は、コントロールへ`CToolTipCtrl`のハンドルではなく、オブジェクトを返すことに注意してください。

スライダーコントロールスタイルの説明については、Windows SDK の「 [Trackbar コントロールスタイル](/windows/win32/Controls/trackbar-control-styles)」を参照してください。

##  <a name="setbuddy"></a>  CSliderCtrl::SetBuddy

スライダーコントロールの関連ウィンドウとしてウィンドウを割り当てます。

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>パラメーター

*pWndBuddy*<br/>
スライダーコントロールのメンバー `CWnd`として設定されるオブジェクトへのポインター。

*fLocation*<br/>
関連ウィンドウを表示する場所を指定する値。 この値には、次のいずれかを指定できます。

- TRUE を指定すると、trackbar コントロールで TBS_HORZ スタイルが使用されている場合、トラックバーの左側に buddy が表示されます。 Trackbar が TBS_VERT スタイルを使用している場合は、トラックバーコントロールの上に関連が表示されます。

- FALSE trackbar コントロールで TBS_HORZ スタイルが使用されている場合、このメンバーは trackbar の右側に表示されます。 Trackbar で TBS_VERT スタイルを使用している場合は、トラックバーコントロールの下に関連が表示されます。

### <a name="return-value"></a>戻り値

以前にその位置にあるスライダーコントロールに割り当てられた[CWnd](../../mfc/reference/cwnd-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy)の動作を実装します。 このメンバー関数は、戻り値と`CWnd`パラメーターの両方のウィンドウハンドルではなく、オブジェクトへのポインターを使用することに注意してください。

スライダーコントロールスタイルの説明については、Windows SDK の「 [Trackbar コントロールスタイル](/windows/win32/Controls/trackbar-control-styles)」を参照してください。

##  <a name="setlinesize"></a>  CSliderCtrl::SetLineSize

スライダーコントロールの線のサイズを設定します。

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>パラメーター

*nSize*<br/>
スライダーコントロールの新しい行サイズ。

### <a name="return-value"></a>戻り値

前の行のサイズ。

### <a name="remarks"></a>Remarks

線のサイズは、TB_LINEUP および TB_LINEDOWN 通知のスライダーの移動量に影響します。

##  <a name="setpagesize"></a>  CSliderCtrl::SetPageSize

スライダーコントロールのページのサイズを設定します。

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>パラメーター

*nSize*<br/>
スライダーコントロールの新しいページサイズ。

### <a name="return-value"></a>戻り値

前のページのサイズ。

### <a name="remarks"></a>Remarks

ページサイズは、TB_PAGEUP および TB_PAGEDOWN 通知のスライダーの移動量に影響します。

##  <a name="setpos"></a>  CSliderCtrl::SetPos

スライダーコントロールのスライダーの現在位置を設定します。

```
void SetPos(int nPos);
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
新しいスライダーの位置を指定します。

##  <a name="setrange"></a>  CSliderCtrl::SetRange

スライダーコントロールのスライダーの範囲 (最小値と最大位置) を設定します。

```
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>パラメーター

*N1 日*<br/>
スライダーの最小位置。

*N1 日*<br/>
スライダーの最大位置。

*より描画*<br/>
再描画フラグ。 このパラメーターが TRUE の場合、範囲が設定された後にスライダーが再描画されます。それ以外の場合、スライダーは再描画されません。

##  <a name="setrangemax"></a>  CSliderCtrl::SetRangeMax

スライダーコントロールのスライダーの最大範囲を設定します。

```
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>パラメーター

*N1 日*<br/>
スライダーの最大位置。

*より描画*<br/>
再描画フラグ。 このパラメーターが TRUE の場合、範囲が設定された後にスライダーが再描画されます。それ以外の場合、スライダーは再描画されません。

##  <a name="setrangemin"></a>  CSliderCtrl::SetRangeMin

スライダーコントロールのスライダーの最小範囲を設定します。

```
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>パラメーター

*N1 日*<br/>
スライダーの最小位置。

*より描画*<br/>
再描画フラグ。 このパラメーターが TRUE の場合、範囲が設定された後にスライダーが再描画されます。それ以外の場合、スライダーは再描画されません。

##  <a name="setselection"></a>Csliderctrl 使い方:: SetSelection

スライダーコントロールの現在の選択範囲の開始位置と終了位置を設定します。

```
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>パラメーター

*N1 日*<br/>
スライダーの開始位置。

*N1 日*<br/>
スライダーの終了位置。

##  <a name="setthumblength"></a>Csliderctrl 使い方:: SetThumbLength

現在の trackbar コントロールのスライダーの長さを設定します。

```
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*nLength*|からスライダーの長さ (ピクセル単位)。|

### <a name="remarks"></a>Remarks

このメソッドでは、trackbar コントロールを[TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles) style に設定する必要があります。

このメソッドは、Windows SDK で説明されている[TBM_SETTHUMBLENGTH](/windows/win32/Controls/tbm-setthumblength)メッセージを送信します。

### <a name="example"></a>例

現在の trackbar コントロールにアクセスするため`m_sliderCtrl`に使用される変数を定義するコード例を次に示します。 この例では、trackbar コントロール`thumbLength`の thumb コンポーネントの既定の長さを格納するために使用される変数も定義します。 次の例では、これらの変数を使用します。

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>例

次のコード例では、trackbar コントロールの thumb コンポーネントを既定の長さの2倍に設定します。

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

##  <a name="settic"></a>  CSliderCtrl::SetTic

スライダーコントロールの目盛りの位置を設定します。

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>パラメーター

*nTic*<br/>
目盛りの位置。 このパラメーターには正の値を指定する必要があります。

### <a name="return-value"></a>戻り値

目盛りが設定されている場合は0以外の。それ以外の場合は0です。

##  <a name="setticfreq"></a>  CSliderCtrl::SetTicFreq

スライダーに目盛りを表示する頻度を設定します。

```
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>パラメーター

*nFreq*<br/>
目盛りの頻度。

### <a name="remarks"></a>Remarks

たとえば、frequency が2に設定されている場合、スライダーの範囲内の他のすべての増分に対して目盛りが表示されます。 頻度の既定の設定は1です (つまり、範囲内のすべての増分が目盛りに関連付けられています)。

この関数を使用するには、TBS_AUTOTICKS スタイルを使用してコントロールを作成する必要があります。 詳細については、「 [csliderctrl 使い方:: Create](#create)」を参照してください。

##  <a name="settipside"></a>Csliderctrl 使い方:: Setヒント側

Trackbar コントロールによって使用されるツールヒントコントロールを配置します。

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>パラメーター

*nLocation*<br/>
ツールヒントコントロールを表示する位置を表す値。 使用可能な値の一覧については、「Windows SDK」で説明されている Win32 message [TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside)を参照してください。

### <a name="return-value"></a>戻り値

ツールヒントコントロールの前の位置を表す値。 戻り値は、 *Nlocation*に指定できる値の1つになります。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message TBM_SETTIPSIDE の動作を実装します。 TBS_TOOLTIPS スタイルを使用するスライダーコントロールは、ツールヒントを表示します。 スライダーコントロールスタイルの説明については、Windows SDK の「 [Trackbar コントロールスタイル](/windows/win32/Controls/trackbar-control-styles)」を参照してください。

##  <a name="settooltips"></a>Csliderctrl 使い方:: SetToolTips ヒント

ツールヒントコントロールをスライダーコントロールに割り当てます。

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>パラメーター

*pWndTip*<br/>
スライダーコントロールで使用するツールヒントを格納している[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips)の動作を実装します。 TBS_TOOLTIPS スタイルを使用してスライダーコントロールを作成すると、スライダーの横に表示される既定のツールヒントコントロールが作成され、スライダーの現在位置が表示されます。 スライダーコントロールスタイルの説明については、Windows SDK の「 [Trackbar コントロールスタイル](/windows/win32/Controls/trackbar-control-styles)」を参照してください。

## <a name="see-also"></a>関連項目

[MFC のサンプル CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl クラス](../../mfc/reference/cprogressctrl-class.md)
