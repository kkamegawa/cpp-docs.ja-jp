---
title: CAutoHideDockSite クラス
ms.date: 11/04/2016
f1_keywords:
- CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::CanAcceptPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::DockPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::GetAlignRect
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::RepositionPanes
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetLeft
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetRight
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::UnSetAutoHideMode
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::m_nExtraSpace
helpviewer_keywords:
- CAutoHideDockSite [MFC], CanAcceptPane
- CAutoHideDockSite [MFC], DockPane
- CAutoHideDockSite [MFC], GetAlignRect
- CAutoHideDockSite [MFC], RepositionPanes
- CAutoHideDockSite [MFC], SetOffsetLeft
- CAutoHideDockSite [MFC], SetOffsetRight
- CAutoHideDockSite [MFC], UnSetAutoHideMode
- CAutoHideDockSite [MFC], m_nExtraSpace
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
ms.openlocfilehash: f24827e2dc1f4d1131f5b63aebeb0e2b09bc2281
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388476"
---
# <a name="cautohidedocksite-class"></a>CAutoHideDockSite クラス

`CAutoHideDockSite`拡張、 [CDockSite クラス](../../mfc/reference/cdocksite-class.md)自動非表示のドッキング ペインを実装します。

## <a name="syntax"></a>構文

```
class CAutoHideDockSite : public CDockSite
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|||
|-|-|
|名前|説明|
|`CAutoHideDockSite::CAutoHideDockSite`|`CAutoHideDockSite` オブジェクトを構築します。|
|`CAutoHideDockSite::~CAutoHideDockSite`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|名前|説明|
|`CAutoHideDockSite::AllowShowOnPaneMenu`|示すかどうか、`CAutoHideDockSite`ウィンドウのメニューが表示されます。|
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|基本ウィンドウ オブジェクトがから派生したかどうかを決定する、 [CMFCAutoHideBar クラス](../../mfc/reference/cmfcautohidebar-class.md)します。|
|[CAutoHideDockSite::DockPane](#dockpane)|このペインをドッキング`CAuotHideDockSite`オブジェクト。|
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|画面座標でドッキング サイトのサイズを取得します。|
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|上のウィンドウを再描画、`CAutoHideDockSite`グローバル余白とボタン間のスペースを使用します。|
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|ドッキング バーの左側にある余白を設定します。|
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|ドッキング バーの右側にある余白を設定します。|
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|呼び出し[CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode)上のオブジェクトに対して、`CAutoHideDockSite`します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|名前|説明|
|[CAutoHideDockSite::m_nExtraSpace](#m_nextraspace)|ツールバーとドッキング バーの端との間隔のサイズを定義します。 この領域は左端または上端から、ドッキング領域の配置に応じてのいずれかから測定されます。|

## <a name="remarks"></a>Remarks

呼び出すと[CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes)、フレームワークによって自動的に作成、`CAutoHideDockSite`オブジェクト。 ほとんどの場合、インスタンス化、またはこのクラスを直接使用する必要はありません。

ドッキング バーがドッキング ペインの左側にあるとの左側にある間のギャップ、 [CMFCAutoHideButton クラス](../../mfc/reference/cmfcautohidebutton-class.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="example"></a>例

次の例は、取得する方法を示します、`CAutoHideDockSite`オブジェクトから、`CMFCAutoHideBar`オブジェクト、およびドッキング バーの左と右の余白を設定する方法。

[!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]

## <a name="requirements"></a>必要条件

**ヘッダー:** afxautohidedocksite.h

##  <a name="canacceptpane"></a>  CAutoHideDockSite::CanAcceptPane

基本のペインがかどうかを[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)オブジェクトまたはから派生した`CMFCAutoHideBar`。

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pBar*|[in]フレームワークがテストする基本ウィンドウ。|

### <a name="return-value"></a>戻り値

TRUE の場合*pBar*から派生`CMFCAutoHideBar`;FALSE それ以外の場合。

### <a name="remarks"></a>Remarks

基本ウィンドウ オブジェクトがから派生している場合`CMFCAutoHideBar`を含めることができます、`CAutoHideDockSite`します。

##  <a name="dockpane"></a>  CAutoHideDockSite::DockPane

このペインをドッキング[CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)オブジェクト。

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*我が物*|[in]フレームワークがドッキングするウィンドウです。|
|*dockMethod*|[in]ウィンドウのオプションをドッキングします。|
|*lpRect*|[in]ドッキング ウィンドウの境界を指定する四角形。|

### <a name="remarks"></a>Remarks

既定の実装は、パラメーターを使用しない*dockMethod*、将来使用するために提供されています。

場合*lpRect*が null の場合、フレームワークは、ドッキング サイトの既定の場所に、ウィンドウを格納します。 ドッキング サイトが水平方向の場合は、既定の場所は、ドッキング サイトの左端にあるは。 それ以外の場合、既定の場所は、ドッキング サイトの上部には。

##  <a name="getalignrect"></a>  CAutoHideDockSite::GetAlignRect

画面座標でドッキング サイトのサイズを取得します。

```
void GetAlignRect(CRect& rect) const;
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*rect*|[in]四角形への参照。 メソッドは、この四角形にドッキング サイトのサイズを格納します。|

### <a name="remarks"></a>Remarks

四角形は、含まれていないようにオフセット余白が調整されます。

##  <a name="m_nextraspace"></a>  CAutoHideDockSite::m_nExtraSpace

端の間隔のサイズ、 [CAutoHideDockSite クラス](../../mfc/reference/cautohidedocksite-class.md)と[CMFCAutoHideBar クラス](../../mfc/reference/cmfcautohidebar-class.md)オブジェクト。

```
static int m_nExtraSpace;
```

### <a name="remarks"></a>Remarks

ときに、`CMFCAutoHideBar`にドッキングした、 `CAutoHideDockSite`、全体のドッキング サイトを占有する必要があります。 このグローバル変数の左端または上端の境界線間の余白を制御する、`CMFCAutoHideBar`と、対応する`CAutoHideDockSite`エッジ。 上または左のエッジを使用するかどうかは、現在の配置によって異なります。

##  <a name="setoffsetleft"></a>  CAutoHideDockSite::SetOffsetLeft

ドッキング バーの左側にある余白を設定します。

```
void SetOffsetLeft(int nOffset);
```

### <a name="parameters"></a>パラメーター

*nOffset*<br/>
[in]新しいオフセット。

### <a name="remarks"></a>Remarks

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)オブジェクトは静的で、配置、`CAutoHideDockSite`オブジェクト。 つまり、ユーザーの場所に手動で変更ことはできません`CMFCAutoHideBar`オブジェクト。 `SetOffsetLeft`メソッドの一番左の左側にある間の間隔を制御する`CMFCAutoHideBar`の左側にあると、`CAutoHideDockSite`します。

##  <a name="setoffsetright"></a>  CAutoHideDockSite::SetOffsetRight

ドッキング バーの右側にある余白を設定します。

```
void SetOffsetRight(int nOffset);
```

### <a name="parameters"></a>パラメーター

*nOffset*<br/>
[in]新しいオフセット。

### <a name="remarks"></a>Remarks

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)オブジェクトは静的で、配置、`CAutoHideDockSite`オブジェクト。 つまり、ユーザーの場所に手動で変更ことはできません、`CMFCAutoHideBar`オブジェクト。 `SetOffsetRight`メソッドの一番右の右側にある間の間隔を制御する`CMFCAutoHideBar`の右側にあると、`CAutoHideDockSite`します。

##  <a name="repositionpanes"></a>  CAutoHideDockSite::RepositionPanes

ウィンドウを再描画、 [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)します。

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*rectNewClientArea*|[in]予約済みの値。|

### <a name="remarks"></a>Remarks

既定の実装が使用しない*rectNewClientArea*します。 [グローバル] ツールバーの余白とボタン間のスペースを使用して、ペインが再描画します。

##  <a name="unsetautohidemode"></a>  CAutoHideDockSite::UnSetAutoHideMode

呼び出し[CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode)ドッキング サイト上のオブジェクト。

```
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pAutoHideToolbar*|[in]ポインターを[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)オブジェクト ペインにあります、`CAutoHideDockSite`します。|

### <a name="remarks"></a>Remarks

このメソッドを含む行を検索*pAutoHideToolbar*します。 呼び出す`CMFCAutoHideBar.UnSetAutoHideMode`すべて、`CMFCAutoHideBar`その行にオブジェクト。 場合*pAutoHideToolbar*が見つからないまたは NULL である、このメソッドを呼び出す`CMFCAutoHideBar.UnSetAutoHideMode`すべて、`CMFCAutoHideBar`でオブジェクトを`CAutoHideDockSite`します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CDockSite クラス](../../mfc/reference/cdocksite-class.md)
