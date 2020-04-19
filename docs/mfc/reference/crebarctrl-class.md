---
title: CReBarCtrl クラス
ms.date: 11/19/2018
f1_keywords:
- CReBarCtrl
- AFXCMN/CReBarCtrl
- AFXCMN/CReBarCtrl::CReBarCtrl
- AFXCMN/CReBarCtrl::BeginDrag
- AFXCMN/CReBarCtrl::Create
- AFXCMN/CReBarCtrl::CreateEx
- AFXCMN/CReBarCtrl::DeleteBand
- AFXCMN/CReBarCtrl::DragMove
- AFXCMN/CReBarCtrl::EndDrag
- AFXCMN/CReBarCtrl::GetBandBorders
- AFXCMN/CReBarCtrl::GetBandCount
- AFXCMN/CReBarCtrl::GetBandInfo
- AFXCMN/CReBarCtrl::GetBandMargins
- AFXCMN/CReBarCtrl::GetBarHeight
- AFXCMN/CReBarCtrl::GetBarInfo
- AFXCMN/CReBarCtrl::GetBkColor
- AFXCMN/CReBarCtrl::GetColorScheme
- AFXCMN/CReBarCtrl::GetDropTarget
- AFXCMN/CReBarCtrl::GetExtendedStyle
- AFXCMN/CReBarCtrl::GetImageList
- AFXCMN/CReBarCtrl::GetPalette
- AFXCMN/CReBarCtrl::GetRect
- AFXCMN/CReBarCtrl::GetRowCount
- AFXCMN/CReBarCtrl::GetRowHeight
- AFXCMN/CReBarCtrl::GetTextColor
- AFXCMN/CReBarCtrl::GetToolTips
- AFXCMN/CReBarCtrl::HitTest
- AFXCMN/CReBarCtrl::IDToIndex
- AFXCMN/CReBarCtrl::InsertBand
- AFXCMN/CReBarCtrl::MaximizeBand
- AFXCMN/CReBarCtrl::MinimizeBand
- AFXCMN/CReBarCtrl::MoveBand
- AFXCMN/CReBarCtrl::PushChevron
- AFXCMN/CReBarCtrl::RestoreBand
- AFXCMN/CReBarCtrl::SetBandInfo
- AFXCMN/CReBarCtrl::SetBandWidth
- AFXCMN/CReBarCtrl::SetBarInfo
- AFXCMN/CReBarCtrl::SetBkColor
- AFXCMN/CReBarCtrl::SetColorScheme
- AFXCMN/CReBarCtrl::SetExtendedStyle
- AFXCMN/CReBarCtrl::SetImageList
- AFXCMN/CReBarCtrl::SetOwner
- AFXCMN/CReBarCtrl::SetPalette
- AFXCMN/CReBarCtrl::SetTextColor
- AFXCMN/CReBarCtrl::SetToolTips
- AFXCMN/CReBarCtrl::SetWindowTheme
- AFXCMN/CReBarCtrl::ShowBand
- AFXCMN/CReBarCtrl::SizeToRect
helpviewer_keywords:
- CReBarCtrl [MFC], CReBarCtrl
- CReBarCtrl [MFC], BeginDrag
- CReBarCtrl [MFC], Create
- CReBarCtrl [MFC], CreateEx
- CReBarCtrl [MFC], DeleteBand
- CReBarCtrl [MFC], DragMove
- CReBarCtrl [MFC], EndDrag
- CReBarCtrl [MFC], GetBandBorders
- CReBarCtrl [MFC], GetBandCount
- CReBarCtrl [MFC], GetBandInfo
- CReBarCtrl [MFC], GetBandMargins
- CReBarCtrl [MFC], GetBarHeight
- CReBarCtrl [MFC], GetBarInfo
- CReBarCtrl [MFC], GetBkColor
- CReBarCtrl [MFC], GetColorScheme
- CReBarCtrl [MFC], GetDropTarget
- CReBarCtrl [MFC], GetExtendedStyle
- CReBarCtrl [MFC], GetImageList
- CReBarCtrl [MFC], GetPalette
- CReBarCtrl [MFC], GetRect
- CReBarCtrl [MFC], GetRowCount
- CReBarCtrl [MFC], GetRowHeight
- CReBarCtrl [MFC], GetTextColor
- CReBarCtrl [MFC], GetToolTips
- CReBarCtrl [MFC], HitTest
- CReBarCtrl [MFC], IDToIndex
- CReBarCtrl [MFC], InsertBand
- CReBarCtrl [MFC], MaximizeBand
- CReBarCtrl [MFC], MinimizeBand
- CReBarCtrl [MFC], MoveBand
- CReBarCtrl [MFC], PushChevron
- CReBarCtrl [MFC], RestoreBand
- CReBarCtrl [MFC], SetBandInfo
- CReBarCtrl [MFC], SetBandWidth
- CReBarCtrl [MFC], SetBarInfo
- CReBarCtrl [MFC], SetBkColor
- CReBarCtrl [MFC], SetColorScheme
- CReBarCtrl [MFC], SetExtendedStyle
- CReBarCtrl [MFC], SetImageList
- CReBarCtrl [MFC], SetOwner
- CReBarCtrl [MFC], SetPalette
- CReBarCtrl [MFC], SetTextColor
- CReBarCtrl [MFC], SetToolTips
- CReBarCtrl [MFC], SetWindowTheme
- CReBarCtrl [MFC], ShowBand
- CReBarCtrl [MFC], SizeToRect
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
ms.openlocfilehash: 14befb819a30238abb5780b1bdcc6d74402e8976
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741190"
---
# <a name="crebarctrl-class"></a>CReBarCtrl クラス

Rebar コントロールの機能がカプセル化されています。Rebar コントロールは、子ウィンドウを含むコンテナーです。

## <a name="syntax"></a>構文

```
class CReBarCtrl : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CReBarCtrl:: CReBarCtrl](#crebarctrl)|`CReBarCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CReBarCtrl:: BeginDrag](#begindrag)|Rebar コントロールをドラッグアンドドロップモードにします。|
|[CReBarCtrl:: Create](#create)|Rebar コントロールを作成し、 `CReBarCtrl`オブジェクトにアタッチします。|
|[CReBarCtrl:: CreateEx](#createex)|指定された Windows 拡張スタイルを使用して rebar コントロールを作成`CReBarCtrl`し、オブジェクトにアタッチします。|
|[CReBarCtrl::D eleteBand](#deleteband)|Rebar コントロールからバンドを削除します。|
|[CReBarCtrl::D ragMove](#dragmove)|の呼び出し`BeginDrag`後に rebar コントロールのドラッグ位置を更新します。|
|[CReBarCtrl:: EndDrag](#enddrag)|Rebar コントロールのドラッグアンドドロップ操作を終了します。|
|[CReBarCtrl:: Getバンド境界線](#getbandborders)|バンドの境界線を取得します。|
|[CReBarCtrl:: Getバンド数](#getbandcount)|Rebar コントロールに現在含まれているバンドの数を取得します。|
|[CReBarCtrl:: Getバンド情報](#getbandinfo)|Rebar コントロール内の指定されたバンドに関する情報を取得します。|
|[CReBarCtrl:: Getバンド余白](#getbandmargins)|バンドの余白を取得します。|
|[CReBarCtrl:: GetBarHeight](#getbarheight)|Rebar コントロールの高さを取得します。|
|[CReBarCtrl:: GetBarInfo](#getbarinfo)|Rebar コントロールとそれが使用するイメージリストに関する情報を取得します。|
|[CReBarCtrl:: GetBkColor](#getbkcolor)|Rebar コントロールの既定の背景色を取得します。|
|[CReBarCtrl:: GetColorScheme](#getcolorscheme)|Rebar コントロールに関連付けられている[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)構造体を取得します。|
|[CReBarCtrl:: GetDropTarget](#getdroptarget)|Rebar コントロールの`IDropTarget`インターフェイスポインターを取得します。|
|[CReBarCtrl:: GetExtendedStyle](#getextendedstyle)|現在の rebar コントロールの拡張スタイルを取得します。|
|[CReBarCtrl:: GetImageList](#getimagelist)|Rebar コントロールに関連付けられているイメージリストを取得します。|
|[CReBarCtrl:: GetPalette](#getpalette)|Rebar コントロールの現在のパレットを取得します。|
|[CReBarCtrl:: GetRect](#getrect)|Rebar コントロール内の指定されたバンドの外接する四角形を取得します。|
|[CReBarCtrl:: GetRowCount](#getrowcount)|Rebar コントロールのバンド行の数を取得します。|
|[CReBarCtrl:: GetRowHeight](#getrowheight)|Rebar コントロール内の指定された行の高さを取得します。|
|[CReBarCtrl:: GetTextColor](#gettextcolor)|Rebar コントロールの既定のテキストの色を取得します。|
|[CReBarCtrl:: GetToolTips ヒント](#gettooltips)|Rebar コントロールに関連付けられているツールヒントコントロールへのハンドルを取得します。|
|[CReBarCtrl:: System.windows.media.visualtreehelper.hittest](#hittest)|Rebar バンドがその時点に存在する場合、そのポイントにある rebar バンドのどの部分が画面上の特定の位置にあるかを判断します。|
|[CReBarCtrl:: IDToIndex](#idtoindex)|バンド識別子 (ID) を rebar コントロールのバンドインデックスに変換します。|
|[CReBarCtrl:: InsertBand](#insertband)|Rebar コントロールに新しいバンドを挿入します。|
|[CReBarCtrl:: 最大化/バンド](#maximizeband)|Rebar コントロールのバンドを最大サイズに変更します。|
|[CReBarCtrl:: MinimizeBand](#minimizeband)|Rebar コントロールのバンドを最小サイズに変更します。|
|[CReBarCtrl:: MoveBand](#moveband)|あるインデックスから別のインデックスにバンドを移動します。|
|[CReBarCtrl::P によってのシェブロン](#pushchevron)|プログラムによってシェブロンをプッシュします。|
|[CReBarCtrl:: RestoreBand](#restoreband)|Rebar コントロールのバンドのサイズを最適なサイズに変更します。|
|[CReBarCtrl:: Setバンド情報](#setbandinfo)|Rebar コントロールの既存のバンドの特性を設定します。|
|[CReBarCtrl:: SetBandWidth 幅](#setbandwidth)|現在の rebar コントロールにおける、指定したドッキングバンドの幅を設定します。|
|[CReBarCtrl:: SetBarInfo](#setbarinfo)|Rebar コントロールの特性を設定します。|
|[CReBarCtrl:: SetBkColor](#setbkcolor)|Rebar コントロールの既定の背景色を設定します。|
|[CReBarCtrl:: SetColorScheme](#setcolorscheme)|Rebar コントロールのボタンの配色を設定します。|
|[CReBarCtrl:: SetExtendedStyle](#setextendedstyle)|現在の rebar コントロールの拡張スタイルを設定します。|
|[CReBarCtrl:: SetImageList](#setimagelist)|Rebar コントロールのイメージリストを設定します。|
|[CReBarCtrl:: SetOwner](#setowner)|Rebar コントロールのオーナーウィンドウを設定します。|
|[CReBarCtrl:: SetPalette](#setpalette)|Rebar コントロールの現在のパレットを設定します。|
|[CReBarCtrl:: SetTextColor](#settextcolor)|Rebar コントロールの既定のテキストの色を設定します。|
|[CReBarCtrl:: SetToolTips ヒント](#settooltips)|ツールヒントコントロールを rebar コントロールに関連付けます。|
|[CReBarCtrl:: SetWindowTheme](#setwindowtheme)|Rebar コントロールの視覚スタイルを設定します。|
|[CReBarCtrl:: ShowBand](#showband)|Rebar コントロール内の指定されたバンドを表示または非表示にします。|
|[CReBarCtrl:: SizeToRect](#sizetorect)|Rebar コントロールを指定された四角形に合わせます。|

## <a name="remarks"></a>Remarks

Rebar コントロールが存在するアプリケーションは、rebar コントロールに含まれる子ウィンドウを rebar バンドに割り当てます。 子ウィンドウは通常、もう1つの一般的なコントロールです。

Rebar コントロールには、1つまたは複数のバンドが含まれます。 各バンドには、グリップバー、ビットマップ、テキストラベル、および子ウィンドウの組み合わせを含めることができます。 バンドには、これらの項目のうち1つだけを含めることができます。

Rebar コントロールは、指定された背景ビットマップ上に子ウィンドウを表示できます。 RBBS_FIXEDSIZE スタイルを使用する場合を除き、すべての rebar コントロールバンドのサイズを変更できます。 Rebar コントロールバンドの位置を変更したりサイズを変更したりすると、rebar コントロールは、そのバンドに割り当てられている子ウィンドウのサイズと位置を管理します。 コントロール内のバンドのサイズを変更または変更するには、バンドのグリップバーをクリックしてドラッグします。

次の図は、3つのバンドを持つ rebar コントロールを示しています。

- バンド0には、フラットで透明なツールバーコントロールが含まれています。

- バンド1には、透明な標準と透明のドロップダウンボタンの両方が含まれています。

- バンド2には、コンボボックスと4つの標準ボタンが含まれています。

   ![Rebar メニューの例](../../mfc/reference/media/vc4scc1.gif "Rebar メニューの例")

## <a name="rebar-control"></a>Rebar コントロール

Rebar コントロールのサポート:

- イメージリスト。

- メッセージ処理。

- カスタム描画機能。

- 標準ウィンドウスタイルに加えて、さまざまなコントロールスタイルを備えています。 これらのスタイルの一覧については、「Windows SDK の[Rebar コントロールスタイル](/windows/win32/Controls/rebar-control-styles)」を参照してください。

詳細については、「 [CReBarCtrl の使用](../../mfc/using-crebarctrl.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcmn.h

##  <a name="begindrag"></a>CReBarCtrl:: BeginDrag

Windows SDK で説明されているように、Win32 message [RB_BEGINDRAG](/windows/win32/Controls/rb-begindrag)の動作を実装します。

```
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>パラメーター

*uBand*<br/>
ドラッグアンドドロップ操作によって影響を受けるバンドの0から始まるインデックス。

*dwPos*<br/>
開始マウス座標を含む DWORD 値です。 水平座標は LOWORD に含まれ、垂直座標は HIWORD に含まれています。 (DWORD)-1 を渡した場合、rebar コントロールは、コントロールの最後のスレッドがまたは`GetMessage` `PeekMessage`を呼び出したときのマウスの位置を使用します。

##  <a name="create"></a>CReBarCtrl:: Create

Rebar コントロールを作成し、 `CReBarCtrl`オブジェクトにアタッチします。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
コントロールに適用される rebar コントロールスタイルの組み合わせを指定します。 サポートされているスタイルの一覧については、「Windows SDK の[Rebar コントロールスタイル](/windows/win32/Controls/rebar-control-styles)」を参照してください。

*rect*<br/>
Rebar コントロールの位置とサイズである、 [CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトまたは[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。

*pParentWnd*<br/>
Rebar コントロールの親ウィンドウである[CWnd](../../mfc/reference/cwnd-class.md)オブジェクトへのポインター。 NULL にすることはできません。

*nID*<br/>
Rebar コントロールのコントロール ID を指定します。

### <a name="return-value"></a>戻り値

オブジェクトが正常に作成された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

次の2つの手順で rebar コントロールを作成します。

1. オブジェクトを構築するには、 `CReBarCtrl` [crebarctrl](#crebarctrl)を呼び出します。

1. このメンバー関数を呼び出します。これにより、Windows rebar コントロールが作成`CReBarCtrl`され、オブジェクトにアタッチされます。

を呼び出す`Create`と、コモンコントロールが初期化されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

##  <a name="createex"></a>CReBarCtrl:: CreateEx

コントロール (子ウィンドウ) を作成し、 `CReBarCtrl`オブジェクトに関連付けます。

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
コントロールに適用される rebar コントロールスタイルの組み合わせを指定します。 サポートされているスタイルの一覧については、「Windows SDK の[Rebar コントロールスタイル](/windows/win32/Controls/rebar-control-styles)」を参照してください。

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

##  <a name="crebarctrl"></a>CReBarCtrl:: CReBarCtrl

`CReBarCtrl` オブジェクトを作成します。

```
CReBarCtrl();
```

### <a name="example"></a>例

  [Crebarctrl:: Create](#create)の例を参照してください。

##  <a name="deleteband"></a>CReBarCtrl::D eleteBand

Windows SDK で説明されているように、Win32 message [RB_DELETEBAND](/windows/win32/Controls/rb-deleteband)の動作を実装します。

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>パラメーター

*uBand*<br/>
削除するバンドの0から始まるインデックス。

### <a name="return-value"></a>戻り値

バンドが正常に削除された場合は0以外の場合は。それ以外の場合は0。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

##  <a name="dragmove"></a>CReBarCtrl::D ragMove

Windows SDK で説明されているように、Win32 message [RB_DRAGMOVE](/windows/win32/Controls/rb-dragmove)の動作を実装します。

```
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>パラメーター

*dwPos*<br/>
新しいマウス座標を含む DWORD 値です。 水平座標は LOWORD に含まれ、垂直座標は HIWORD に含まれています。 (DWORD)-1 を渡した場合、rebar コントロールは、コントロールの最後のスレッドがまたは`GetMessage` `PeekMessage`を呼び出したときのマウスの位置を使用します。

##  <a name="enddrag"></a>CReBarCtrl:: EndDrag

Windows SDK で説明されているように、Win32 message [RB_ENDDRAG](/windows/win32/Controls/rb-enddrag)の動作を実装します。

```
void EndDrag();
```

##  <a name="getbandborders"></a>CReBarCtrl:: Getバンド境界線

Windows SDK で説明されているように、Win32 message [RB_GETBANDBORDERS](/windows/win32/Controls/rb-getbandborders)の動作を実装します。

```
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>パラメーター

*uBand*<br/>
境界線が取得されるバンドの0から始まるインデックス。

*中国語*<br/>
バンドの境界線を受け取る[RECT](/previous-versions/dd162897\(v=vs.85\))構造体へのポインター。 Rebar コントロールに RBS_BANDBORDERS スタイルが指定されている場合、この構造体の各メンバーは、境界を構成するバンドの対応する側のピクセル数を受け取ります。 Rebar コントロールに RBS_BANDBORDERS スタイルが設定されていない場合、この構造体の左のメンバーだけが有効な情報を受け取ります。 Rebar コントロールスタイルの説明については、「Windows SDK の[Rebar コントロールスタイル](/windows/win32/Controls/rebar-control-styles)」を参照してください。

##  <a name="getbandcount"></a>CReBarCtrl:: Getバンド数

Windows SDK で説明されているように、Win32 message [RB_GETBANDCOUNT](/windows/win32/Controls/rb-getbandcount)の動作を実装します。

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>戻り値

コントロールに割り当てられているバンドの数。

##  <a name="getbandinfo"></a>CReBarCtrl:: Getバンド情報

Windows SDK で説明されているように、Win32 メッセージ[RB_GETBANDINFO](/windows/win32/Controls/rb-getbandinfo)の動作を実装します。

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>パラメーター

*uBand*<br/>
情報を取得するバンドの0から始まるインデックス。

*prbbi*<br/>
バンド情報を受信する[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)構造体へのポインター。 この構造体の`cbSize`メンバーをに`sizeof(REBARBANDINFO)`設定し、このメッセージ`fMask`を送信する前に取得する項目にメンバーを設定する必要があります。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

##  <a name="getbandmargins"></a>  CReBarCtrl::GetBandMargins

バンドの余白を取得します。

```
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>パラメーター

*pMargins*<br/>
情報を受け取る[余白](/windows/win32/api/uxtheme/ns-uxtheme-margins)の構造体へのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [RB_GETBANDMARGINS](/windows/win32/Controls/rb-getbandmargins)メッセージの機能をエミュレートします。

##  <a name="getbarheight"></a>CReBarCtrl:: GetBarHeight

Rebar バーの高さを取得します。

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>戻り値

コントロールの高さ (ピクセル単位) を表す値。

##  <a name="getbarinfo"></a>CReBarCtrl:: GetBarInfo

Windows SDK で説明されているように、Win32 message [RB_GETBARINFO](/windows/win32/Controls/rb-getbarinfo)の動作を実装します。

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>パラメーター

*prbi*<br/>
Rebar コントロール情報を受け取る[REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo)構造体へのポインター。 このメッセージを送信する前に、この構造`sizeof(REBARINFO)`体の cbSize メンバーをに設定する必要があります。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

##  <a name="getbkcolor"></a>CReBarCtrl:: GetBkColor

Windows SDK で説明されているように、Win32 message [RB_GETBKCOLOR](/windows/win32/Controls/rb-getbkcolor)の動作を実装します。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>戻り値

現在の既定の背景色を表す COLORREF 値。

##  <a name="getcolorscheme"></a>CReBarCtrl:: GetColorScheme

Rebar コントロールの[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)構造体を取得します。

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>パラメーター

*lpcs*<br/>
Windows SDK で説明されているように、 [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)構造体へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

構造`COLORSCHEME`体には、ボタンの強調表示色とボタンの影の色が含まれます。

##  <a name="getdroptarget"></a>CReBarCtrl:: GetDropTarget

Windows SDK で説明されているように、Win32 message [RB_GETDROPTARGET](/windows/win32/Controls/rb-getdroptarget)の動作を実装します。

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>戻り値

[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)インターフェイスへのポインター。

##  <a name="getextendedstyle"></a>CReBarCtrl:: GetExtendedStyle

現在の rebar コントロールの拡張スタイルを取得します。

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>戻り値

拡張スタイルを示すフラグのビットごとの組み合わせ (or)。 使用できるフラグは RBS_EX_SPLITTER と RBS_EX_TRANSPARENT です。 詳細については、 [Crebarctrl:: SetExtendedStyle](#setextendedstyle)メソッドの*dwMask*パラメーターを参照してください。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[RB_GETEXTENDEDSTYLE](/windows/win32/Controls/rb-dragmove)メッセージを送信します。

##  <a name="getimagelist"></a>  CReBarCtrl::GetImageList

Rebar コントロールに関連付けられたオブジェクトを取得します。`CImageList`

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>戻り値

[CImageList](../../mfc/reference/cimagelist-class.md)オブジェクトへのポインター。 コントロールにイメージリストが設定されていない場合は NULL を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo)構造体に格納されているサイズとマスクの情報を使用します。

##  <a name="getpalette"></a>  CReBarCtrl::GetPalette

Rebar コントロールの現在のパレットを取得します。

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>戻り値

Rebar コントロールの現在のパレットを指定する[CPalette](../../mfc/reference/cpalette-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、オブジェクトを`CPalette` hpalette ではなく戻り値として使用することに注意してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

##  <a name="getrect"></a>  CReBarCtrl::GetRect

Windows SDK で説明されているように、Win32 message [RB_GETRECT](/windows/win32/Controls/rb-getrect)の動作を実装します。

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>パラメーター

*uBand*<br/>
Rebar コントロールのバンドの0から始まるインデックス。

*中国語*<br/>
Rebar バンドの境界を受け取る[RECT](/previous-versions/dd162897\(v=vs.85\))構造体へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

##  <a name="getrowcount"></a>  CReBarCtrl::GetRowCount

Windows SDK で説明されているように、Win32 message [RB_GETROWCOUNT](/windows/win32/Controls/rb-getrowcount)の動作を実装します。

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>戻り値

コントロール内のバンド行の数を表す UINT 値。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

##  <a name="getrowheight"></a>CReBarCtrl:: GetRowHeight

Windows SDK で説明されているように、Win32 message [RB_GETROWHEIGHT](/windows/win32/Controls/rb-getrowheight)の動作を実装します。

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>パラメーター

*uRow*<br/>
高さを取得するバンドの0から始まるインデックス。

### <a name="return-value"></a>戻り値

行の高さをピクセル単位で表す UINT 値。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

##  <a name="gettextcolor"></a>  CReBarCtrl::GetTextColor

Windows SDK で説明されているように、Win32 message [RB_GETTEXTCOLOR](/windows/win32/Controls/rb-gettextcolor)の動作を実装します。

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>戻り値

現在の既定のテキストの色を表す COLORREF 値。

##  <a name="gettooltips"></a>CReBarCtrl:: GetToolTips ヒント

Windows SDK で説明されているように、Win32 message [RB_GETTOOLTIPS](/windows/win32/Controls/rb-gettooltips)の動作を実装します。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>戻り値

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

の`GetToolTips` MFC 実装では、HWND ではなく、 `CToolTipCtrl`へのポインターが返されることに注意してください。

##  <a name="hittest"></a>  CReBarCtrl::HitTest

Windows SDK で説明されているように、Win32 message [RB_HITTEST](/windows/win32/Controls/rb-hittest)の動作を実装します。

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>パラメーター

*prbht*<br/>
[RBHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-rbhittestinfo)構造体へのポインター。 この構造体のメンバーは`pt` 、メッセージを送信する前に、テストするポイントにクライアント座標で初期化する必要があります。

### <a name="return-value"></a>戻り値

指定したポイントのバンドの0から始まるインデックス番号。 rebar バンドがポイントになかった場合は-1。

##  <a name="idtoindex"></a>CReBarCtrl:: IDToIndex

Windows SDK で説明されているように、Win32 message [RB_IDTOINDEX](/windows/win32/controls/rb-idtoindex)の動作を実装します。

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>パラメーター

*Uno Did*<br/>
バンドが挿入されるときに、 `wID` [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)構造体のメンバーで渡された、指定したバンドのアプリケーション定義識別子。

### <a name="return-value"></a>戻り値

成功した場合は0から始まるバンドインデックス。それ以外の場合は-1。 重複するバンドインデックスが存在する場合は、最初のインデックスが返されます。

##  <a name="insertband"></a>CReBarCtrl:: InsertBand

Windows SDK で説明されているように、Win32 message [RB_INSERTBAND](/windows/win32/Controls/rb-insertband)の動作を実装します。

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>パラメーター

*uIndex*<br/>
バンドが挿入される位置の0から始まるインデックス。 このパラメーターを-1 に設定すると、コントロールは最後の位置に新しいバンドを追加します。

*prbbi*<br/>
挿入するバンドを定義する[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)構造体へのポインター。 この関数を呼び出す前に、この構造体`sizeof(REBARBANDINFO)`の cbSize メンバーをに設定する必要があります。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

##  <a name="maximizeband"></a>CReBarCtrl:: 最大化/バンド

Rebar コントロールのバンドを最大サイズに変更します。

```
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>パラメーター

*uBand*<br/>
最大化するバンドの0から始まるインデックス。

### <a name="remarks"></a>Remarks

Windows SDK で説明されているように、`fIdeal` を 0 に設定して、Win32 メッセージ [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

##  <a name="minimizeband"></a>CReBarCtrl:: MinimizeBand

Rebar コントロールのバンドを最小サイズに変更します。

```
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>パラメーター

*uBand*<br/>
最小化するバンドの0から始まるインデックス。

### <a name="remarks"></a>Remarks

Windows SDK で説明されているように、Win32 message [RB_MINIMIZEBAND](/windows/win32/Controls/rb-minimizeband)の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

##  <a name="moveband"></a>CReBarCtrl:: MoveBand

Windows SDK で説明されているように、Win32 message [RB_MOVEBAND](/windows/win32/Controls/rb-moveband)の動作を実装します。

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>パラメーター

*uFrom*<br/>
移動するバンドの0から始まるインデックス。

*U)*<br/>
新しいバンド位置の0から始まるインデックス。 このパラメーター値は、バンド数から1を引いた数より大きくすることはできません。 バンド数を取得するには、 [Getバンド数](#getbandcount)を呼び出します。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

##  <a name="pushchevron"></a>  CReBarCtrl::PushChevron

Windows SDK で説明されているように、Win32 message [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron)の動作を実装します。

```
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>パラメーター

*uBand*<br/>
シェブロンをプッシュするバンドの0から始まるインデックス。

*lAppValue*<br/>
アプリケーションで32ビット値が定義されています。 Windows SDK の[RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron)の*lAppValue*を参照してください。

##  <a name="restoreband"></a>CReBarCtrl:: RestoreBand

Rebar コントロールのバンドのサイズを最適なサイズに変更します。

```
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>パラメーター

*uBand*<br/>
最大化するバンドの0から始まるインデックス。

### <a name="remarks"></a>Remarks

Windows SDK で説明されているように、`fIdeal` を 1 に設定して、Win32 メッセージ [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

##  <a name="setbandinfo"></a>CReBarCtrl:: Setバンド情報

Windows SDK で説明されているように、Win32 message [RB_SETBANDINFO](/windows/win32/Controls/rb-setbandinfo)の動作を実装します。

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>パラメーター

*uBand*<br/>
新しい設定を受け取るバンドの0から始まるインデックス。

*prbbi*<br/>
挿入するバンドを定義する[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)構造体へのポインター。 このメッセージを送信`cbSize`する前に、この`sizeof(REBARBANDINFO)`構造体のメンバーをに設定する必要があります。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

##  <a name="setbandwidth"></a>CReBarCtrl:: SetBandWidth 幅

現在の rebar コントロールにおける、指定したドッキングバンドの幅を設定します。

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*uBand*|からRebar バンドの0から始まるインデックス。|
|*cxWidth*|からRebar バンドの新しい幅 (ピクセル単位)。|

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[RB_SETBANDWIDTH](/windows/win32/Controls/rb-setbandwidth)メッセージを送信します。

### <a name="example"></a>例

現在の rebar コントロールにアクセスするため`m_rebar`に使用される変数を定義するコード例を次に示します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>例

次のコード例では、各 rebar バンドを同じ幅に設定します。

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

##  <a name="setbarinfo"></a>CReBarCtrl:: SetBarInfo

Windows SDK で説明されているように、Win32 message [RB_SETBARINFO](/windows/win32/Controls/rb-setbarinfo)の動作を実装します。

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>パラメーター

*prbi*<br/>
設定する情報を格納している[REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo)構造体へのポインター。 このメッセージを送信`cbSize`する前に、この`sizeof(REBARINFO)`構造体のメンバーをに設定する必要があります

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

##  <a name="setbkcolor"></a>CReBarCtrl:: SetBkColor

Windows SDK で説明されているように、Win32 message [RB_SETBKCOLOR](/windows/win32/Controls/rb-setbkcolor)の動作を実装します。

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>パラメーター

*/clr*<br/>
新しい既定の背景色を表す COLORREF 値。

### <a name="return-value"></a>戻り値

前の既定の背景色を表す[COLORREF](/windows/win32/gdi/colorref)値。

### <a name="remarks"></a>Remarks

背景色を設定するタイミングと、既定値の設定方法の詳細については、このトピックを参照してください。

##  <a name="setcolorscheme"></a>  CReBarCtrl::SetColorScheme

Rebar コントロールのボタンの配色を設定します。

```
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>パラメーター

*lpcs*<br/>
Windows SDK で説明されているように、 [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)構造体へのポインター。

### <a name="remarks"></a>Remarks

構造`COLORSCHEME`体には、ボタンの強調表示色とボタンの影の色の両方が含まれます。

##  <a name="setextendedstyle"></a>CReBarCtrl:: SetExtendedStyle

現在の rebar コントロールの拡張スタイルを設定します。

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*dwMask*|から*Dwflags ex*パラメーターで適用されるフラグを指定するフラグのビットごとの組み合わせ (or)。 次の値の1つまたは複数を使用します。<br /><br /> RBS_EX_SPLITTER:既定では、分割線は水平モードで下部に表示され、垂直モードでは右側に表示されます。<br /><br /> RBS_EX_TRANSPARENT:[WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)メッセージを親ウィンドウに転送します。|
|*Dwスタイル Ex*|から適用するスタイルを指定するフラグのビットごとの組み合わせ (or)。 スタイルを設定するには、 *dwMask*パラメーターで使用されているのと同じフラグを指定します。 スタイルをリセットするには、[バイナリ 0] を指定します。|

### <a name="return-value"></a>戻り値

前の拡張スタイル。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[RB_SETEXTENDEDSTYLE](/windows/win32/Controls/rb-setextendedstyle)メッセージを送信します。

##  <a name="setimagelist"></a>CReBarCtrl:: SetImageList

イメージリストを rebar コントロールに割り当てます。

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>パラメーター

*pImageList*<br/>
Rebar コントロールに割り当てられるイメージリストを格納している[CImageList](../../mfc/reference/cimagelist-class.md)オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

##  <a name="setowner"></a>  CReBarCtrl::SetOwner

Windows SDK で説明されているように、Win32 message [RB_SETPARENT](/windows/win32/Controls/rb-setparent)の動作を実装します。

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
Rebar コントロールの所有`CWnd`者として設定するオブジェクトへのポインター。

### <a name="return-value"></a>戻り値

Rebar コントロールの現在の所有者である[CWnd](../../mfc/reference/cwnd-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、windows への`CWnd`ハンドルではなく、rebar コントロールの現在の所有者と選択された所有者の両方のオブジェクトへのポインターを使用することに注意してください。

> [!NOTE]
>  このメンバー関数は、コントロールが作成されたときに設定された実際の親を変更しません。代わりに、指定したウィンドウに通知メッセージを送信します。

##  <a name="setpalette"></a>  CReBarCtrl::SetPalette

Windows SDK で説明されているように、Win32 message [RB_SETPALETTE](/windows/win32/Controls/rb-setpalette)の動作を実装します。

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>パラメーター

*hPal*<br/>
Rebar コントロールが使用する新しいパレットを指定する HPALETTE。

### <a name="return-value"></a>戻り値

Rebar コントロールの前のパレットを指定する[CPalette](../../mfc/reference/cpalette-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、オブジェクトを`CPalette` hpalette ではなく戻り値として使用することに注意してください。

##  <a name="settextcolor"></a>CReBarCtrl:: SetTextColor

Windows SDK で説明されているように、Win32 message [RB_SETTEXTCOLOR](/windows/win32/Controls/rb-settextcolor)の動作を実装します。

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>パラメーター

*/clr*<br/>
`CReBarCtrl`オブジェクトの新しいテキストの色を表す COLORREF 値。

### <a name="return-value"></a>戻り値

`CReBarCtrl`オブジェクトに関連付けられた前のテキストの色を表す[COLORREF](/windows/win32/gdi/colorref)値。

### <a name="remarks"></a>Remarks

Rebar コントロールでのテキストの色の柔軟性をサポートするために用意されています。

##  <a name="settooltips"></a>CReBarCtrl:: SetToolTips ヒント

ツールヒントコントロールを rebar コントロールに関連付けます。

```
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>パラメーター

*pToolTip*<br/>
[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)オブジェクトへのポインター

### <a name="remarks"></a>Remarks

操作が完了し`CToolTipCtrl`たら、オブジェクトを破棄する必要があります。

##  <a name="setwindowtheme"></a>CReBarCtrl:: SetWindowTheme

Rebar コントロールの視覚スタイルを設定します。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>パラメーター

*pszSubAppName*<br/>
設定する rebar 視覚スタイルを含む Unicode 文字列へのポインター。

### <a name="return-value"></a>戻り値

戻り値は使用されません。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [RB_SETWINDOWTHEME](/windows/win32/Controls/rb-setwindowtheme)メッセージの機能をエミュレートします。

##  <a name="showband"></a>CReBarCtrl:: ShowBand

Windows SDK で説明されているように、Win32 message [RB_SHOWBAND](/windows/win32/Controls/rb-showband)の動作を実装します。

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>パラメーター

*uBand*<br/>
Rebar コントロールのバンドの0から始まるインデックス。

*fShow*<br/>
バンドを表示するか非表示にするかを示します。 この値が TRUE の場合、バンドが表示されます。 それ以外の場合、バンドは非表示になります。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

##  <a name="sizetorect"></a>CReBarCtrl:: SizeToRect

Windows SDK で説明されているように、Win32 message [RB_SIZETORECT](/windows/win32/Controls/rb-sizetorect)の動作を実装します。

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
Rebar コントロールのサイズ変更の対象となる四角形を指定する、 [CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトへの参照。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、 `CRect` `RECT`構造体ではなく、オブジェクトをパラメーターとして使用することに注意してください。

## <a name="see-also"></a>関連項目

[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
