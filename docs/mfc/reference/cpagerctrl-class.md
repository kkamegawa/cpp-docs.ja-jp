---
title: CPagerCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CPagerCtrl
- AFXCMN/CPagerCtrl
- AFXCMN/CPagerCtrl::CPagerCtrl
- AFXCMN/CPagerCtrl::Create
- AFXCMN/CPagerCtrl::CreateEx
- AFXCMN/CPagerCtrl::ForwardMouse
- AFXCMN/CPagerCtrl::GetBkColor
- AFXCMN/CPagerCtrl::GetBorder
- AFXCMN/CPagerCtrl::GetButtonSize
- AFXCMN/CPagerCtrl::GetButtonState
- AFXCMN/CPagerCtrl::GetDropTarget
- AFXCMN/CPagerCtrl::GetScrollPos
- AFXCMN/CPagerCtrl::IsButtonDepressed
- AFXCMN/CPagerCtrl::IsButtonGrayed
- AFXCMN/CPagerCtrl::IsButtonHot
- AFXCMN/CPagerCtrl::IsButtonInvisible
- AFXCMN/CPagerCtrl::IsButtonNormal
- AFXCMN/CPagerCtrl::RecalcSize
- AFXCMN/CPagerCtrl::SetBkColor
- AFXCMN/CPagerCtrl::SetBorder
- AFXCMN/CPagerCtrl::SetButtonSize
- AFXCMN/CPagerCtrl::SetChild
- AFXCMN/CPagerCtrl::SetScrollPos
helpviewer_keywords:
- CPagerCtrl [MFC], CPagerCtrl
- CPagerCtrl [MFC], Create
- CPagerCtrl [MFC], CreateEx
- CPagerCtrl [MFC], ForwardMouse
- CPagerCtrl [MFC], GetBkColor
- CPagerCtrl [MFC], GetBorder
- CPagerCtrl [MFC], GetButtonSize
- CPagerCtrl [MFC], GetButtonState
- CPagerCtrl [MFC], GetDropTarget
- CPagerCtrl [MFC], GetScrollPos
- CPagerCtrl [MFC], IsButtonDepressed
- CPagerCtrl [MFC], IsButtonGrayed
- CPagerCtrl [MFC], IsButtonHot
- CPagerCtrl [MFC], IsButtonInvisible
- CPagerCtrl [MFC], IsButtonNormal
- CPagerCtrl [MFC], RecalcSize
- CPagerCtrl [MFC], SetBkColor
- CPagerCtrl [MFC], SetBorder
- CPagerCtrl [MFC], SetButtonSize
- CPagerCtrl [MFC], SetChild
- CPagerCtrl [MFC], SetScrollPos
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
ms.openlocfilehash: 519a376bdecc488a94eab65973e33d960ca50c8d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503029"
---
# <a name="cpagerctrl-class"></a>CPagerCtrl クラス

`CPagerCtrl` クラスは、Windows のページャー コントロールをラップします。ページャー コントロールには、外側のウィンドウに収まらない内側のウィンドウをスクロールによって表示する機能があります。

## <a name="syntax"></a>構文

```
class CPagerCtrl : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CPagerCtrl:: CPagerCtrl](#cpagerctrl)|`CPagerCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CPagerCtrl:: Create](#create)|指定されたスタイルを使用してページャーコントロールを作成`CPagerCtrl`し、現在のオブジェクトに添付します。|
|[CPagerCtrl:: CreateEx](#createex)|指定した拡張スタイルを使用してページャーコントロールを作成し`CPagerCtrl` 、現在のオブジェクトに添付します。|
|[CPagerCtrl:: ForwardMouse](#forwardmouse)|現在のページャーコントロールに含まれているウィンドウへの[WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove)メッセージの転送を有効または無効にします。|
|[CPagerCtrl:: GetBkColor](#getbkcolor)|現在のページャーコントロールの背景色を取得します。|
|[CPagerCtrl::GetBorder](#getborder)|現在のページャーコントロールの境界線のサイズを取得します。|
|[CPagerCtrl:: GetButtonSize](#getbuttonsize)|現在のページャーコントロールのボタンのサイズを取得します。|
|[CPagerCtrl:: GetButtonState](#getbuttonstate)|現在のページャーコントロール内の指定されたボタンの状態を取得します。|
|[CPagerCtrl:: GetDropTarget](#getdroptarget)|現在のページャーコントロールの[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)インターフェイスを取得します。|
|[CPagerCtrl:: GetScrollPos](#getscrollpos)|現在のページャーコントロールのスクロール位置を取得します。|
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|現在のページャーコントロールの指定されたボタンが状態`pressed`であるかどうかを示します。|
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|現在のページャーコントロールの指定されたボタンが状態`grayed`であるかどうかを示します。|
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|現在のページャーコントロールの指定されたボタンが状態`hot`であるかどうかを示します。|
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|現在のページャーコントロールの指定されたボタンが状態`invisible`であるかどうかを示します。|
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|現在のページャーコントロールの指定されたボタンが状態`normal`であるかどうかを示します。|
|[CPagerCtrl::RecalcSize](#recalcsize)|現在のページャーコントロールが、格納されているウィンドウのサイズを再計算します。|
|[CPagerCtrl:: SetBkColor](#setbkcolor)|現在のページャーコントロールの背景色を設定します。|
|[CPagerCtrl::SetBorder](#setborder)|現在のページャーコントロールの境界線のサイズを設定します。|
|[CPagerCtrl:: SetButtonSize](#setbuttonsize)|現在のページャーコントロールのボタンのサイズを設定します。|
|[CPagerCtrl:: SetChild](#setchild)|現在のページャーコントロールに含まれるウィンドウを設定します。|
|[CPagerCtrl:: SetScrollPos](#setscrollpos)|現在のページャーコントロールのスクロール位置を設定します。|

## <a name="remarks"></a>Remarks

ページャーコントロールとは、ウィンドウを含んでいるウィンドウのことです。このウィンドウには、ウィンドウの上にあるウィンドウをドラッグしたときに、ウィンドウをスクロールして表示することができます。 ページャーコントロールは、含まれているウィンドウが最も遠い範囲にスクロールされたときに自動的に非表示になる2つのスクロールボタンを表示し、それ以外の場合は再表示します。 水平方向または垂直方向にスクロールするページャーコントロールを作成できます。

たとえば、アプリケーションのすべてのアイテムを表示するのに十分な幅ではないツールバーがある場合は、ツールバーをページャーコントロールに割り当てると、ユーザーはツールバーを左または右にスクロールしてすべてのアイテムにアクセスできるようになります。 Microsoft Internet Explorer バージョン 4.0 (commctrl .dll バージョン 4.71) では、ページャーコントロールが導入されています。

クラスは、[CWnd](../../mfc/reference/cwnd-class.md) クラスから派生します。`CPagerCtrl` ページャーコントロールの詳細と図については、「[ページャーコントロール](/windows/win32/Controls/pager-controls)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcmn.h

##  <a name="cpagerctrl"></a>CPagerCtrl:: CPagerCtrl

`CPagerCtrl` オブジェクトを構築します。

```
CPagerCtrl();
```

### <a name="remarks"></a>Remarks

[Cpagerctrl:: Create](#create)メソッドまたは[cpagerctrl:: CreateEx](#createex)メソッドを使用して、ページャーコントロールを作成し`CPagerCtrl` 、オブジェクトにアタッチします。

##  <a name="create"></a>  CPagerCtrl::Create

指定されたスタイルを使用してページャーコントロールを作成`CPagerCtrl`し、現在のオブジェクトに添付します。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*dwStyle*|からコントロールに適用される[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)および[ページャーコントロールスタイル](/windows/win32/Controls/pager-control-styles)のビットごとの組み合わせ (または)。|
|*rect*|からクライアント座標でのコントロールの位置とサイズを格納している[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。|
|*pParentWnd*|からコントロールの親ウィンドウである[CWnd](../../mfc/reference/cwnd-class.md)オブジェクトへのポインター。 このパラメーターを NULL にすることはできません。|
|*nID*|からコントロールの ID。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ページャーコントロールを作成するには、 `CPagerCtrl`変数を宣言し、その変数に対して[cpagerctrl:: create](#create)メソッドまたは[cpagerctrl:: CreateEx](#createex)メソッドを呼び出します。

### <a name="example"></a>例

次の例では、ページャーコントロールを作成し、 [Cpagerctrl:: SetChild](#setchild)メソッドを使用して、非常に長いボタンコントロールをページャーコントロールに関連付けます。 この例では、 [Cpagerctrl:: SetButtonSize](#setbuttonsize)メソッドを使用して、ページャーコントロールの高さを20ピクセルに設定し、 [Cpagerctrl:: setborder](#setborder)メソッドを使用して境界線の太さを1ピクセルに設定しています。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="createex"></a>CPagerCtrl:: CreateEx

指定した拡張スタイルを使用してページャーコントロールを作成し`CPagerCtrl` 、現在のオブジェクトに添付します。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*dwExStyle*|からコントロールに適用される拡張スタイルのビットごとの組み合わせ。 詳細については、 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)関数の*dwexstyle*パラメーターを参照してください。|
|*dwStyle*|からコントロールに適用される[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)および[ページャーコントロールスタイル](/windows/win32/Controls/pager-control-styles)のビットごとの組み合わせ (または)。|
|*rect*|からクライアント座標でのコントロールの位置とサイズを格納している[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。|
|*pParentWnd*|からコントロールの親ウィンドウである[CWnd](../../mfc/reference/cwnd-class.md)オブジェクトへのポインター。 このパラメーターを NULL にすることはできません。|
|*nID*|からコントロールの ID。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ページャーコントロールを作成するには、 `CPagerCtrl`変数を宣言し、その変数に対して[cpagerctrl:: create](#create)メソッドまたは[cpagerctrl:: CreateEx](#createex)メソッドを呼び出します。

##  <a name="forwardmouse"></a>CPagerCtrl:: ForwardMouse

現在のページャーコントロールに含まれているウィンドウへの[WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove)メッセージの転送を有効または無効にします。

```
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*bForward*|からマウスメッセージを転送する場合は TRUE、マウスメッセージを転送しない場合は FALSE。|

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_FORWARDMOUSE](/windows/win32/Controls/pgm-forwardmouse)メッセージを送信します。

##  <a name="getborder"></a>  CPagerCtrl::GetBorder

現在のページャーコントロールの境界線のサイズを取得します。

```
int GetBorder() const;
```

### <a name="return-value"></a>戻り値

現在の境界線のサイズ (ピクセル単位)。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_GETBORDER](/windows/win32/Controls/pgm-getborder)メッセージを送信します。

### <a name="example"></a>例

次の例では、 [Cpagerctrl:: GetBorder](#getborder)メソッドを使用して、ページャーコントロールの境界線の太さを取得します。

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

##  <a name="getbkcolor"></a>CPagerCtrl:: GetBkColor

現在のページャーコントロールの背景色を取得します。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>戻り値

ページャーコントロールの現在の背景色を格納している[COLORREF](/windows/win32/gdi/colorref)値。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_GETBKCOLOR](/windows/win32/Controls/pgm-getbkcolor)メッセージを送信します。

### <a name="example"></a>例

次の例では、 [Cpagerctrl:: SetBkColor](#setbkcolor)メソッドを使用して、ページャーコントロールの背景色を赤に設定し、 [Cpagerctrl:: GetBkColor](#getbkcolor)メソッドを使用して変更が行われたことを確認します。

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="getbuttonsize"></a>CPagerCtrl:: GetButtonSize

現在のページャーコントロールのボタンのサイズを取得します。

```
int GetButtonSize() const;
```

### <a name="return-value"></a>戻り値

現在のボタンのサイズ (ピクセル単位)。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_GETBUTTONSIZE](/windows/win32/Controls/pgm-getbuttonsize)メッセージを送信します。

ページャーコントロールに PGS_HORZ スタイルが設定されている場合、ボタンのサイズによってページャーボタンの幅が決まります。ページャーコントロールに PGS_VERT スタイルが設定されている場合は、ボタンのサイズによってページャーボタンの高さが決まります。 詳細については、「[ページャーコントロールスタイル](/windows/win32/Controls/pager-control-styles)」を参照してください。

##  <a name="getbuttonstate"></a>  CPagerCtrl::GetButtonState

現在のページャーコントロールの指定されたスクロールボタンの状態を取得します。

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*iButton*|から状態を取得するボタンを示します。 ページャーコントロールスタイルが PGS_HORZ の場合は、左側のボタンに PGB_TOPORLEFT を、右のボタンに PGB_BOTTOMORRIGHT を指定します。 ページャーコントロールスタイルが PGS_VERT の場合は、一番上のボタンに PGB_TOPORLEFT を、下部ボタンに PGB_BOTTOMORRIGHT を指定します。 詳細については、「[ページャーコントロールスタイル](/windows/win32/Controls/pager-control-styles)」を参照してください。|

### <a name="return-value"></a>戻り値

*Ibutton*パラメーターによって指定されたボタンの状態。 状態は、PGF_INVISIBLE、PGF_NORMAL、PGF_GRAYED、PGF_DEPRESSED、または PGF_HOT のいずれかです。 詳細については、 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)メッセージの「戻り値」セクションを参照してください。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)メッセージを送信します。

##  <a name="getdroptarget"></a>CPagerCtrl:: GetDropTarget

現在のページャーコントロールの[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)インターフェイスを取得します。

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>戻り値

現在のページャーコントロール`IDropTarget`のインターフェイスへのポインター。

### <a name="remarks"></a>Remarks

`IDropTarget`は、アプリケーションでドラッグアンドドロップ操作をサポートするために実装するインターフェイスの1つです。

このメソッドは、Windows SDK で説明されている[PGM_GETDROPTARGET](/windows/win32/Controls/pgm-getdroptarget)メッセージを送信します。 このメソッドの呼び出し元は、インターフェイスが不要`Release`になったときに、 [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)インターフェイスのメンバーを呼び出す必要があります。

##  <a name="getscrollpos"></a>CPagerCtrl:: GetScrollPos

現在のページャーコントロールのスクロール位置を取得します。

```
int GetScrollPos() const;
```

### <a name="return-value"></a>戻り値

現在のスクロール位置 (ピクセル単位)。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_GETPOS](/windows/win32/Controls/pgm-getpos)メッセージを送信します。

### <a name="example"></a>例

次の例では、 [Cpagerctrl:: GetScrollPos](#getscrollpos)メソッドを使用して、ページャーコントロールの現在のスクロール位置を取得します。 ページャーコントロールが、左端の位置からまだ0にスクロールしていない場合、この例では、 [Cpagerctrl:: SetScrollPos](#setscrollpos)メソッドを使用して、スクロール位置を0に設定しています。

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

##  <a name="isbuttondepressed"></a>  CPagerCtrl::IsButtonDepressed

現在のページャーコントロールの指定されたスクロールボタンが押された状態かどうかを示します。

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*iButton*|から状態を取得するボタンを示します。 ページャーコントロールスタイルが PGS_HORZ の場合は、左側のボタンに PGB_TOPORLEFT を、右のボタンに PGB_BOTTOMORRIGHT を指定します。 ページャーコントロールスタイルが PGS_VERT の場合は、一番上のボタンに PGB_TOPORLEFT を、下部ボタンに PGB_BOTTOMORRIGHT を指定します。 詳細については、「[ページャーコントロールスタイル](/windows/win32/Controls/pager-control-styles)」を参照してください。|

### <a name="return-value"></a>戻り値

指定したボタンが押された状態の場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)メッセージを送信します。 次に、返される状態が PGF_DEPRESSED であるかどうかをテストします。 詳細については、 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)メッセージの「戻り値」セクションを参照してください。

##  <a name="isbuttongrayed"></a>  CPagerCtrl::IsButtonGrayed

現在のページャーコントロールの指定されたスクロールボタンが淡色表示になっているかどうかを示します。

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*iButton*|から状態を取得するボタンを示します。 ページャーコントロールスタイルが PGS_HORZ の場合は、左側のボタンに PGB_TOPORLEFT を、右のボタンに PGB_BOTTOMORRIGHT を指定します。 ページャーコントロールスタイルが PGS_VERT の場合は、一番上のボタンに PGB_TOPORLEFT を、下部ボタンに PGB_BOTTOMORRIGHT を指定します。 詳細については、「[ページャーコントロールスタイル](/windows/win32/Controls/pager-control-styles)」を参照してください。|

### <a name="return-value"></a>戻り値

指定されたボタンがグレーで表示されている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)メッセージを送信します。 次に、返される状態が PGF_GRAYED であるかどうかをテストします。 詳細については、 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)メッセージの「戻り値」セクションを参照してください。

##  <a name="isbuttonhot"></a>  CPagerCtrl::IsButtonHot

現在のページャーコントロールの指定されたスクロールボタンがホットな状態であるかどうかを示します。

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*iButton*|から状態を取得するボタンを示します。 ページャーコントロールスタイルが PGS_HORZ の場合は、左側のボタンに PGB_TOPORLEFT を、右のボタンに PGB_BOTTOMORRIGHT を指定します。 ページャーコントロールスタイルが PGS_VERT の場合は、一番上のボタンに PGB_TOPORLEFT を、下部ボタンに PGB_BOTTOMORRIGHT を指定します。 詳細については、「[ページャーコントロールスタイル](/windows/win32/Controls/pager-control-styles)」を参照してください。|

### <a name="return-value"></a>戻り値

指定されたボタンがホットな状態である場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)メッセージを送信します。 次に、返される状態が PGF_HOT であるかどうかをテストします。 詳細については、 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)メッセージの「戻り値」セクションを参照してください。

##  <a name="isbuttoninvisible"></a>  CPagerCtrl::IsButtonInvisible

現在のページャーコントロールの指定されたスクロールボタンが非表示状態であるかどうかを示します。

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*iButton*|から状態を取得するボタンを示します。 ページャーコントロールスタイルが PGS_HORZ の場合は、左側のボタンに PGB_TOPORLEFT を、右のボタンに PGB_BOTTOMORRIGHT を指定します。 ページャーコントロールスタイルが PGS_VERT の場合は、一番上のボタンに PGB_TOPORLEFT を、下部ボタンに PGB_BOTTOMORRIGHT を指定します。 詳細については、「[ページャーコントロールスタイル](/windows/win32/Controls/pager-control-styles)」を参照してください。|

### <a name="return-value"></a>戻り値

指定したボタンが非表示の状態にある場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ウィンドウを使用すると、ウィンドウが一番遠い範囲にスクロールされたときに、スクロールボタンが非表示になります。これは、ボタンをクリックしても、含まれているウィンドウを表示することができないためです。

このメソッドは、Windows SDK で説明されている[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)メッセージを送信します。 次に、返される状態が PGF_INVISIBLE であるかどうかをテストします。 詳細については、 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)メッセージの「戻り値」セクションを参照してください。

### <a name="example"></a>例

次の例では、 [Cpagerctrl:: IsButtonInvisible](#isbuttoninvisible)メソッドを使用して、ページャーコントロールの左右のスクロールボタンが表示されるかどうかを確認します。

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

##  <a name="isbuttonnormal"></a>  CPagerCtrl::IsButtonNormal

現在のページャーコントロールの指定されたスクロールボタンが通常の状態であるかどうかを示します。

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*iButton*|から状態を取得するボタンを示します。 ページャーコントロールスタイルが PGS_HORZ の場合は、左側のボタンに PGB_TOPORLEFT を、右のボタンに PGB_BOTTOMORRIGHT を指定します。 ページャーコントロールスタイルが PGS_VERT の場合は、一番上のボタンに PGB_TOPORLEFT を、下部ボタンに PGB_BOTTOMORRIGHT を指定します。 詳細については、「[ページャーコントロールスタイル](/windows/win32/Controls/pager-control-styles)」を参照してください。|

### <a name="return-value"></a>戻り値

指定されたボタンが通常の状態である場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)メッセージを送信します。 次に、返される状態が PGF_NORMAL であるかどうかをテストします。 詳細については、 [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)メッセージの「戻り値」セクションを参照してください。

##  <a name="recalcsize"></a>  CPagerCtrl::RecalcSize

現在のページャーコントロールが、格納されているウィンドウのサイズを再計算します。

```
void RecalcSize();
```

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_RECALCSIZE](/windows/win32/Controls/pgm-recalcsize)メッセージを送信します。 その結果、ページャーコントロールは、 [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize)通知を送信して、含まれているウィンドウのスクロール可能なディメンションを取得します。

### <a name="example"></a>例

次の例では、 [Cpagerctrl:: RecalcSize](#recalcsize)メソッドを使用して、現在のページャーコントロールのサイズを再計算するように要求します。

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>例

次の例では、[メッセージリフレクション](../../mfc/tn062-message-reflection-for-windows-controls.md)を使用して、ページャーコントロールが、計算を実行するためにコントロールの親ダイアログを要求する代わりに、独自のサイズを再計算できるようにします。 この例では`MyPagerCtrl` 、 [cpagerctrl クラス](../../mfc/reference/cpagerctrl-class.md)からクラスを派生させると共に、メッセージ マップを使用し`OnCalcsize`て [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) 通知を通知ハンドラーに関連付けます。 この例では、通知ハンドラーによってページャーコントロールの幅と高さが固定値に設定されています。

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

##  <a name="setbkcolor"></a>CPagerCtrl:: SetBkColor

現在のページャーコントロールの背景色を設定します。

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*clrBk*|からページャーコントロールの新しい背景色を格納している[COLORREF](/windows/win32/gdi/colorref)値。|

### <a name="return-value"></a>戻り値

ページャーコントロールの前の背景色を格納している[COLORREF](/windows/win32/gdi/colorref)値。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_SETBKCOLOR](/windows/win32/Controls/pgm-setbkcolor)メッセージを送信します。

### <a name="example"></a>例

次の例では、 [Cpagerctrl:: SetBkColor](#setbkcolor)メソッドを使用して、ページャーコントロールの背景色を赤に設定し、 [Cpagerctrl:: GetBkColor](#getbkcolor)メソッドを使用して変更が行われたことを確認します。

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="setborder"></a>  CPagerCtrl::SetBorder

現在のページャーコントロールの境界線のサイズを設定します。

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*iBorder*|から新しい境界線のサイズ (ピクセル単位)。 *Iborder*パラメーターが負の値の場合、境界線のサイズは0に設定されます。|

### <a name="return-value"></a>戻り値

前の境界線のサイズ (ピクセル単位)。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_SETBORDER](/windows/win32/Controls/pgm-setborder)メッセージを送信します。

### <a name="example"></a>例

次の例では、ページャーコントロールを作成し、 [Cpagerctrl:: SetChild](#setchild)メソッドを使用して、非常に長いボタンコントロールをページャーコントロールに関連付けます。 この例では、 [Cpagerctrl:: SetButtonSize](#setbuttonsize)メソッドを使用して、ページャーコントロールの高さを20ピクセルに設定し、 [Cpagerctrl:: setborder](#setborder)メソッドを使用して境界線の太さを1ピクセルに設定しています。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setbuttonsize"></a>CPagerCtrl:: SetButtonSize

現在のページャーコントロールのボタンのサイズを設定します。

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*iButtonSize*|から新しいボタンのサイズ (ピクセル単位)。|

### <a name="return-value"></a>戻り値

前のボタンのサイズ (ピクセル単位)。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_SETBUTTONSIZE](/windows/win32/Controls/pgm-setpos)メッセージを送信します。

ページャーコントロールに PGS_HORZ スタイルが設定されている場合、ボタンのサイズによってページャーボタンの幅が決まります。ページャーコントロールに PGS_VERT スタイルが設定されている場合は、ボタンのサイズによってページャーボタンの高さが決まります。 既定のボタンサイズは、スクロールバーの幅の 3 3/4 で、ボタンの最小サイズは12ピクセルです。 詳細については、「[ページャーコントロールスタイル](/windows/win32/Controls/pager-control-styles)」を参照してください。

### <a name="example"></a>例

次の例では、ページャーコントロールを作成し、 [Cpagerctrl:: SetChild](#setchild)メソッドを使用して、非常に長いボタンコントロールをページャーコントロールに関連付けます。 この例では、 [Cpagerctrl:: SetButtonSize](#setbuttonsize)メソッドを使用して、ページャーコントロールの高さを20ピクセルに設定し、 [Cpagerctrl:: setborder](#setborder)メソッドを使用して境界線の太さを1ピクセルに設定しています。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setchild"></a>  CPagerCtrl::SetChild

現在のページャーコントロールに含まれるウィンドウを設定します。

```
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*hwndChild*|から格納されるウィンドウへのハンドル。|

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_SETCHILD](/windows/win32/Controls/pgm-setchild)メッセージを送信します。

このメソッドは、含まれているウィンドウの親を変更しません。ウィンドウハンドルは、スクロール用のページャーコントロールにのみ割り当てられます。 ほとんどの場合、含まれているウィンドウはページャーコントロールの子ウィンドウになります。

### <a name="example"></a>例

次の例では、ページャーコントロールを作成し、 [Cpagerctrl:: SetChild](#setchild)メソッドを使用して、非常に長いボタンコントロールをページャーコントロールに関連付けます。 この例では、 [Cpagerctrl:: SetButtonSize](#setbuttonsize)メソッドを使用して、ページャーコントロールの高さを20ピクセルに設定し、 [Cpagerctrl:: setborder](#setborder)メソッドを使用して境界線の太さを1ピクセルに設定しています。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setscrollpos"></a>CPagerCtrl:: SetScrollPos

現在のページャーコントロールのスクロール位置を設定します。

```
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*iPos*|から新しいスクロール位置 (ピクセル単位)。|

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[PGM_SETPOS](/windows/win32/Controls/pgm-setpos)メッセージを送信します。

## <a name="see-also"></a>関連項目

[CPagerCtrl クラス](../../mfc/reference/cpagerctrl-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[ページャーコントロール](/windows/win32/Controls/pager-controls)
