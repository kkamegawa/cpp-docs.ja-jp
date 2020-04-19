---
title: CControlBar Class
ms.date: 11/04/2016
f1_keywords:
- CControlBar
- AFXEXT/CControlBar
- AFXEXT/CControlBar::CControlBar
- AFXEXT/CControlBar::CalcDynamicLayout
- AFXEXT/CControlBar::CalcFixedLayout
- AFXEXT/CControlBar::CalcInsideRect
- AFXEXT/CControlBar::DoPaint
- AFXEXT/CControlBar::DrawBorders
- AFXEXT/CControlBar::DrawGripper
- AFXEXT/CControlBar::EnableDocking
- AFXEXT/CControlBar::GetBarStyle
- AFXEXT/CControlBar::GetBorders
- AFXEXT/CControlBar::GetCount
- AFXEXT/CControlBar::GetDockingFrame
- AFXEXT/CControlBar::IsFloating
- AFXEXT/CControlBar::OnUpdateCmdUI
- AFXEXT/CControlBar::SetBarStyle
- AFXEXT/CControlBar::SetBorders
- AFXEXT/CControlBar::SetInPlaceOwner
- AFXEXT/CControlBar::m_bAutoDelete
- AFXEXT/CControlBar::m_pInPlaceOwner
helpviewer_keywords:
- CControlBar [MFC], CControlBar
- CControlBar [MFC], CalcDynamicLayout
- CControlBar [MFC], CalcFixedLayout
- CControlBar [MFC], CalcInsideRect
- CControlBar [MFC], DoPaint
- CControlBar [MFC], DrawBorders
- CControlBar [MFC], DrawGripper
- CControlBar [MFC], EnableDocking
- CControlBar [MFC], GetBarStyle
- CControlBar [MFC], GetBorders
- CControlBar [MFC], GetCount
- CControlBar [MFC], GetDockingFrame
- CControlBar [MFC], IsFloating
- CControlBar [MFC], OnUpdateCmdUI
- CControlBar [MFC], SetBarStyle
- CControlBar [MFC], SetBorders
- CControlBar [MFC], SetInPlaceOwner
- CControlBar [MFC], m_bAutoDelete
- CControlBar [MFC], m_pInPlaceOwner
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
ms.openlocfilehash: 41e40b3da7b4a294fe396a9d93f7c6a93593ff95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345826"
---
# <a name="ccontrolbar-class"></a>CControlBar Class

コントロール バー クラスの基本クラス[CStatusBar](../../mfc/reference/cstatusbar-class.md)、 [CToolBar](../../mfc/reference/ctoolbar-class.md)、 [CDialogBar](../../mfc/reference/cdialogbar-class.md)、 [CReBar](../../mfc/reference/crebar-class.md)、および[COleResizeBar](../../mfc/reference/coleresizebar-class.md)します。

## <a name="syntax"></a>構文

```
class CControlBar : public CWnd
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CControlBar::CControlBar](#ccontrolbar)|`CControlBar` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|としてダイナミック コントロール バーのサイズを返します、 [CSize](../../atl-mfc-shared/reference/csize-class.md)オブジェクト。|
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|としてコントロール バーのサイズを返します、 [CSize](../../atl-mfc-shared/reference/csize-class.md)オブジェクト。|
|[CControlBar::CalcInsideRect](#calcinsiderect)|境界線を含むコントロール バー領域の現在のディメンションを返します。|
|[CControlBar::DoPaint](#dopaint)|コントロール バーの境界線およびグリップをレンダリングします。|
|[CControlBar::DrawBorders](#drawborders)|コントロール バーの境界線をレンダリングします。|
|[CControlBar::DrawGripper](#drawgripper)|コントロール バーのグリップをレンダリングします。|
|[CControlBar::EnableDocking](#enabledocking)|コントロール バーをドッキングまたはフローティングできるようにします。|
|[したとき](#getbarstyle)|コントロール バーのスタイル設定を取得します。|
|[CControlBar::GetBorders](#getborders)|コントロール バーの境界線の値を取得します。|
|[CControlBar::GetCount](#getcount)|コントロール バーの HWND 以外の要素の数を返します。|
|[CControlBar::GetDockingFrame](#getdockingframe)|コントロール バーがドッキングされるフレームへのポインターを返します。|
|[CControlBar::IsFloating](#isfloating)|対象のコントロール バーがフローティング コントロール バーである場合に、ゼロ以外の値を返します。|
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|コマンド UI ハンドラーを呼び出します。|
|[CControlBar::SetBarStyle](#setbarstyle)|コントロール バーのスタイル設定を変更します。|
|[CControlBar::SetBorders](#setborders)|コントロール バーの境界線の値を設定します。|
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|コントロール バーのインプレース所有者を変更します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CControlBar::m_bAutoDelete](#m_bautodelete)|ゼロ以外の場合は、Windows のコントロール バーが破棄されると、`CControlBar` オブジェクトが削除されます。|
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|コントロール バーのインプレース所有者です。|

## <a name="remarks"></a>Remarks

通常、コントロール バーは、フレーム ウィンドウの左側または右側にアラインされるウィンドウです。 いずれかの Windows メッセージに応答を生成する windows には、HWND ベースのコントロールや windows でないし、アプリケーション コードまたはフレームワーク コードによって管理されている非 HWND ベースの項目が子項目に含めることができます。 リスト ボックスやエディット コントロール、HWND ベースのコントロールの例ステータス バー ペインやビットマップ ボタンは、HWND ベースのコントロールの例を示します。

通常、コントロール バーのウィンドウは親フレーム ウィンドウの子ウィンドウであり、通常はクライアント ビューまたはフレーム ウィンドウの MDI クライアントの兄弟です。 `CControlBar` オブジェクトは、親ウィンドウのクライアント領域の四角形に関する情報を使用して、それ自体を配置します。 次に、親ウィンドウのクライアント領域においてどの程度の未割り当て領域が残っているかについて、親ウィンドウに通知します。

`CControlBar` の詳細については、次を参照してください。

- [コントロール バー](../../mfc/control-bars.md)

- [テクニカル ノート 31:コントロール バー](../../mfc/tn031-control-bars.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxext.h

##  <a name="calcdynamiclayout"></a>  CControlBar::CalcDynamicLayout

フレームワークは、動的なツールバーのサイズを計算するには、このメンバー関数を呼び出します。

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>パラメーター

*nLength*<br/>
コントロール バー、水平方向または垂直方向に応じてのいずれかの要求されたディメンション*寸法*します。

*nMode*<br/>
次の定義済みフラグを使用して、ダイナミック コントロール バーの幅と高さを決定します。 ビットごとの OR を使用して (&#124;) フラグを結合する演算子。

|レイアウト モードのフラグ|その意味|
|-----------------------|-------------------|
|LM_STRETCH|コントロール バーをフレームのサイズに引き伸ばすかどうかを示します。 バーがドッキング バー (ドッキングの使用不可) ではない場合に設定します。 設定されていない、バーがドッキングまたはフローティング (ドッキングの使用可能)。 設定すると、LM_STRETCH 無視*されて*いる状態に基づいたディメンションを返します。 LM_STRETCH 動作と同様に、 *bStretch*で使用されるパラメーター [CalcFixedLayout](#calcfixedlayout); 伸縮と印刷の向きの関係の詳細については、メンバー関数を参照してください。|
|いる|バーが水平方向または垂直方向であることを示します。 場合は、バーが水平方向と垂直方向の場合は設定されませんを設定します。 いる動作と同様に、 *bHorz*で使用されるパラメーター [CalcFixedLayout](#calcfixedlayout); 伸縮と印刷の向きの関係の詳細については、メンバー関数を参照してください。|
|LM_MRUWIDTH|動的な幅を最近使用します。 無視*されて*パラメーターとは、記憶された最近の幅を使用します。|
|LM_HORZDOCK|ディメンションを水平にドッキングします。 無視*されて*パラメーターを最大の幅の動的なサイズを返します。|
|LM_VERTDOCK|ディメンションを垂直方向にドッキングします。 無視*されて*パラメーターを最大の高さを持つ動的なサイズを返します。|
|LM_LENGTHY|場合設定*されて*幅ではなく、高さ (Y 方向) を示します。|
|LM_COMMIT|LM_MRUWIDTH をフローティング コントロール バーの現在の幅にリセットします。|

### <a name="return-value"></a>戻り値

コントロール バー (ピクセル単位) のサイズ、 [CSize](../../atl-mfc-shared/reference/csize-class.md)オブジェクト。

### <a name="remarks"></a>Remarks

派生したクラスで独自の動的レイアウトを提供するには、このメンバー関数をオーバーライド`CControlBar`します。 派生した MFC クラス`CControlBar`など[CToolbar](../../mfc/reference/ctoolbar-class.md)このメンバー関数をオーバーライドし、独自の実装を提供します。

##  <a name="calcfixedlayout"></a>  CControlBar::CalcFixedLayout

コントロール バーの水平方向のサイズを計算するには、このメンバー関数を呼び出します。

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>パラメーター

*bStretch*<br/>
バーをフレームのサイズに引き伸ばすかどうかを示します。 *BStretch*バーのドッキング バー (ドッキングの使用不可) ではないと (ドッキングの使用可能) をドッキングまたはフローティングがある場合に 0 をパラメーターが 0 以外の場合は。

*bHorz*<br/>
バーが水平方向または垂直方向であることを示します。 *BHorz*バーが水平方向および垂直方向にある場合は 0 の場合は、パラメーターが 0 以外の場合。

### <a name="return-value"></a>戻り値

コントロール バー (ピクセル単位) のサイズ、`CSize`オブジェクト。

### <a name="remarks"></a>Remarks

ツールバーなどのコントロール バーが水平方向に拡張できます。 または垂直方向にボタンに合わせて、コントロール バーに含まれています。

場合*bStretch*が true の場合、拡張によって提供される方向に沿ってディメンション*bHorz*します。 つまり場合、 *bHorz* false で、コントロール バーが垂直方向に拡大されます。 場合*bStretch* FALSE は、stretch は行われません。 次の表は、の組み合わせ、および結果として得られるコントロール バー スタイルを示しています。 *bStretch*と*bHorz*します。

|bStretch|bHorz|拡大|[方向]|ドッキングかどうかのドッキング|
|--------------|-----------|----------------|-----------------|--------------------------|
|true|true|水平方向の拡大|横方向に配置|ドッキングしません。|
|true|false|垂直方向の拡大|垂直方向|ドッキングしません。|
|false|true|伸縮しません。|横方向に配置|ドッキング|
|false|false|伸縮しません。|垂直方向|ドッキング|

##  <a name="calcinsiderect"></a>  CControlBar::CalcInsideRect

フレームワークは、コントロール バーのクライアント領域を計算するには、この関数を呼び出します。

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
コントロール バーの現在のディメンションが含まれています境界線を含むです。

*bHorz*<br/>
バーが水平方向または垂直方向であることを示します。 *BHorz*バーが水平方向および垂直方向にある場合は 0 の場合は、パラメーターが 0 以外の場合。

### <a name="remarks"></a>Remarks

コントロール バーが描画される前に、この関数が呼び出されます。

コントロール バーのグリップ バー、罫線の描画をカスタマイズするには、この関数をオーバーライドします。

##  <a name="ccontrolbar"></a>  CControlBar::CControlBar

`CControlBar` オブジェクトを構築します。

```
CControlBar();
```

##  <a name="dopaint"></a>  CControlBar::DoPaint

枠線とコントロール バーのグリップ バーを表示するためにフレームワークによって呼び出されます。

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
境界線およびコントロール バーのグリップをレンダリングするために使用するデバイス コンテキストへのポインター。

### <a name="remarks"></a>Remarks

コントロール バーの描画動作をカスタマイズするには、この関数をオーバーライドします。

もう 1 つのカスタマイズの方法は、オーバーライドする、`DrawBorders`と`DrawGripper`関数し、境界線およびグリップ用のカスタムの描画コードを追加します。 既定では、これらのメソッドが呼び出されるため`DoPaint`メソッドは、のオーバーライドを`DoPaint`は必要ありません。

##  <a name="drawborders"></a>  CControlBar::DrawBorders

コントロール バーの境界線を表示するためにフレームワークによって呼び出されます。

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
コントロール バーの境界線の描画に使用するデバイス コンテキストへのポインター。

*rect*<br/>
A`CRect`コントロール バーのサイズを格納しているオブジェクト。

### <a name="remarks"></a>Remarks

コントロール バーの境界線の外観をカスタマイズするには、この関数をオーバーライドします。

##  <a name="drawgripper"></a>  CControlBar::DrawGripper

コントロール バーのグリップを表示するためにフレームワークによって呼び出されます。

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
コントロール バーのグリップをレンダリングするために使用するデバイス コンテキストへのポインター。

*rect*<br/>
A`CRect`コントロール バーのグリップの大きさを格納しているオブジェクト。

### <a name="remarks"></a>Remarks

コントロール バーのグリップの外観をカスタマイズするには、この関数をオーバーライドします。

##  <a name="enabledocking"></a>  CControlBar::EnableDocking

ドッキング コントロール バーを有効にするには、この関数を呼び出します。

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>パラメーター

*dwDockStyle*<br/>
サポートされている場合は、コントロール バーがドッキングをサポートするかどうかとするコントロール バーをドッキングできる、親ウィンドウの辺を指定します。 次の 1 つ以上を指定できます。

- CBRS_ALIGN_TOP は、クライアント領域の上部にドッキングできます。

- CBRS_ALIGN_BOTTOM は、クライアント領域の下部にドッキングできます。

- CBRS_ALIGN_LEFT は、クライアント領域の左側にドッキングできます。

- CBRS_ALIGN_RIGHT は、クライアント領域の右側にドッキングできます。

- CBRS_ALIGN_ANY は、クライアント領域の任意の辺にドッキングできます。

- CBRS_FLOAT_MULTI は、1 つのミニフレーム ウィンドウにフローティングする複数のコントロール バーを使用できます。

0 の場合 (つまり、いないことを示すフラグ)、コントロール バーがドッキングされます。

### <a name="remarks"></a>Remarks

指定した辺は、移行先フレーム ウィンドウのドッキングの辺のいずれかに一致する必要がありますか、そのフレーム ウィンドウにコントロール バーをドッキングすることはできません。

##  <a name="getbarstyle"></a>  CControlBar::GetBarStyle

判断するためには、この関数を呼び出す**cbrs _** (コントロール バーのスタイル) の設定は、コントロール バーに現在設定されています。

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>戻り値

現在**cbrs _** コントロール バーの設定 (コントロール バーのスタイル)。 参照してください[CControlBar::SetBarStyle](#setbarstyle)使用可能なスタイルの完全な一覧についてはします。

### <a name="remarks"></a>Remarks

処理しない**ws _** (ウィンドウ スタイル) スタイル。

##  <a name="getborders"></a>  CControlBar::GetBorders

コントロール バーの境界線の現在の値を返します。

```
CRect GetBorders() const;
```

### <a name="return-value"></a>戻り値

A`CRect`コントロール バー オブジェクトの各辺のピクセル単位で、現在の幅を格納しているオブジェクト。 値など、*左*、メンバーの[CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクト、左の境界線の幅です。

##  <a name="getcount"></a>  CControlBar::GetCount

HWND ではない項目の数を返します、`CControlBar`オブジェクト。

```
int GetCount() const;
```

### <a name="return-value"></a>戻り値

HWND 以外のアイテムの数、`CControlBar`オブジェクト。 この関数の場合は 0 を返します、 [CDialogBar](../../mfc/reference/cdialogbar-class.md)オブジェクト。

### <a name="remarks"></a>Remarks

派生のオブジェクトに依存する項目の種類: ペイン[CStatusBar](../../mfc/reference/cstatusbar-class.md)オブジェクトおよびボタンとの区切り記号[CToolBar](../../mfc/reference/ctoolbar-class.md)オブジェクト。

##  <a name="getdockingframe"></a>  CControlBar::GetDockingFrame

コントロール バーがドッキングされている現在のフレーム ウィンドウへのポインターを取得するには、このメンバー関数を呼び出します。

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>戻り値

成功した場合は、フレーム ウィンドウへのポインターそれ以外の場合は NULL です。

場合 (つまり、コントロール バーがフローティング) 場合に、コントロール バーは、フレーム ウィンドウにドッキングされていない、この関数は、その親にポインターを返します[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)します。

### <a name="remarks"></a>Remarks

ドッキング可能なコントロール バーの詳細については、次を参照してください。 [CControlBar::EnableDocking](#enabledocking)と[CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar)します。

##  <a name="isfloating"></a>  CControlBar::IsFloating

コントロール バーがフローティングかドッキングかどうかを判断するには、このメンバー関数を呼び出します。

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>戻り値

コントロール バーが固定されていない場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

ドッキング コントロール バーの状態を変更するには、呼び出して[切り離すには](../../mfc/reference/cframewnd-class.md#floatcontrolbar)します。

##  <a name="m_bautodelete"></a>  CControlBar::m_bAutoDelete

ゼロ以外の場合は、Windows のコントロール バーが破棄されると、`CControlBar` オブジェクトが削除されます。

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Remarks

*m_bAutoDelete* BOOL 型のパブリック変数です。

コントロール バー オブジェクトは通常、フレーム ウィンドウ オブジェクトに埋め込まれます。 この場合、 *m_bAutoDelete* 0 は、フレーム ウィンドウが破棄されるときに、埋め込まれたコントロール バー オブジェクトが破棄されるためです。

割り当てる場合、この変数を 0 以外の値に設定、`CControlBar`を呼び出すと、ヒープ上のオブジェクトが行わない**削除**します。

##  <a name="m_pinplaceowner"></a>  CControlBar::m_pInPlaceOwner

コントロール バーのインプレース所有者です。

```
CWnd* m_pInPlaceOwner;
```

##  <a name="onupdatecmdui"></a>  CControlBar::OnUpdateCmdUI

このメンバー関数は、ツールバーまたはステータス バーの状態を更新するためにフレームワークによって呼び出されます。

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>パラメーター

*pTarget*<br/>
アプリケーションのメイン フレーム ウィンドウへのポインター。 このポインターは、更新メッセージをルーティングするために使用されます。

*持たず*<br/>
更新ハンドラーがないコントロールが無効と自動的に表示されるかどうかを示すフラグ。

### <a name="remarks"></a>Remarks

各ボタンまたはウィンドウを更新するのにには、更新ハンドラーを適切に設定するのに、メッセージ マップに ON_UPDATE_COMMAND_UI マクロを使用します。 参照してください[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)詳細については、このマクロを使用します。

`OnUpdateCmdUI` アプリケーションがアイドル状態のときに、フレームワークによって呼び出されます。 フレーム ウィンドウを更新する必要がありますいないを子ウィンドウを直接には少なくとも表示されるフレーム ウィンドウの。 `OnUpdateCmdUI` 高度なは、オーバーライド可能な。

##  <a name="setbarstyle"></a>  CControlBar::SetBarStyle

必要な設定するには、この関数を呼び出す**cbrs _** コントロール バーのスタイル。

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
コントロール バーに必要なスタイル。 次の 1 つ以上を指定できます。

- CBRS_ALIGN_TOP は、フレーム ウィンドウのクライアント領域の上部にドッキング コントロール バーを使用できます。

- CBRS_ALIGN_BOTTOM は、フレーム ウィンドウのクライアント領域の下部にドッキング コントロール バーを使用できます。

- CBRS_ALIGN_LEFT は、フレーム ウィンドウのクライアント領域の左側にドッキング コントロール バーを使用できます。

- CBRS_ALIGN_RIGHT は、フレーム ウィンドウのクライアント領域の右側にドッキング コントロール バーを使用できます。

- CBRS_ALIGN_ANY は、フレーム ウィンドウのクライアント領域の任意の辺にドッキング コントロール バーを使用できます。

- CBRS_BORDER_TOP により、境界線を表示されるときにバー コントロールの上端に描画します。

- CBRS_BORDER_BOTTOM により、境界線を表示されるときにバー コントロールの下端に描画します。

- CBRS_BORDER_LEFT により、境界線を表示されるときにバー コントロールの左端に描画します。

- CBRS_BORDER_RIGHT により、境界線を表示されるときにバー コントロールの右端に描画します。

- CBRS_FLOAT_MULTI は、1 つのミニフレーム ウィンドウにフローティングする複数のコントロール バーを使用できます。

- CBRS_TOOLTIPS とツール ヒント コントロール バーに表示されます。

- CBRS_FLYBY によりメッセージのテキスト ツール ヒントとして同時に更新します。

- CBRS_GRIPPER によりグリッパー、バンドをで使用されるような`CReBar`オブジェクトは、いずれかの描画される`CControlBar`-クラスを派生します。

### <a name="remarks"></a>Remarks

影響しません、 **ws _** (ウィンドウ スタイル) 設定します。

##  <a name="setborders"></a>  CControlBar::SetBorders

コントロール バーの境界線のサイズを設定するには、この関数を呼び出します。

```
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*cxLeft*<br/>
コントロール バーの左罫線の幅をピクセル単位で。

*cyTop*<br/>
コントロール バーの上枠線の高さをピクセル単位で。

*cxRight*<br/>
コントロール バーの右罫線の幅をピクセル単位で。

*cyBottom*<br/>
コントロール バーの下の境界線の高さをピクセル単位で。

*lpRect*<br/>
ポインターを[CRect](../../atl-mfc-shared/reference/crect-class.md)コントロール バー オブジェクトの各境界のピクセル単位で、現在の幅を格納しているオブジェクト。

### <a name="example"></a>例

次のコード例では、5 (ピクセル単位) をコントロール バーの上端と下端の枠線と左および右の境界線を 2 ピクセルに設定します。

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

##  <a name="setinplaceowner"></a>  CControlBar::SetInPlaceOwner

コントロール バーのインプレース所有者を変更します。

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*我が物*<br/>
`CWnd` オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[MFC サンプル CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CToolBar クラス](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar クラス](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar クラス](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar クラス](../../mfc/reference/crebar-class.md)
