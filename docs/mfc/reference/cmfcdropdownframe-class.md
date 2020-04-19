---
title: CMFCDropDownFrame クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::Create
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentMenuBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentPopupMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::RecalcLayout
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::SetAutoDestroy
helpviewer_keywords:
- CMFCDropDownFrame [MFC], Create
- CMFCDropDownFrame [MFC], GetParentMenuBar
- CMFCDropDownFrame [MFC], GetParentPopupMenu
- CMFCDropDownFrame [MFC], RecalcLayout
- CMFCDropDownFrame [MFC], SetAutoDestroy
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
ms.openlocfilehash: 534dc90443371c8440e0cb317540f2cf80f6eacc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78869065"
---
# <a name="cmfcdropdownframe-class"></a>CMFCDropDownFrame クラス

ドロップダウンツールバーとドロップダウンツールバーボタンにドロップダウンのフレームウィンドウ機能を提供します。

## <a name="syntax"></a>構文

```
class CMFCDropDownFrame : public CMiniFrameWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|||
|-|-|
|Name|Description|
|`CMFCDropDownFrame::CMFCDropDownFrame`|既定のコンストラクターです。|
|`CMFCDropDownFrame::~CMFCDropDownFrame`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|Name|Description|
|[CMFCDropDownFrame:: Create](#create)|`CMFCDropDownFrame` オブジェクトを作成します。|
|`CMFCDropDownFrame::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|[CMFCDropDownFrame:: GetParentMenuBar](#getparentmenubar)|ドロップダウンフレームの親メニューバーを取得します。|
|[CMFCDropDownFrame:: GetParentPopupMenu](#getparentpopupmenu)|ドロップダウンフレームの親ポップアップメニューを取得します。|
|`CMFCDropDownFrame::GetThisClass`|このクラス型に関連付けられている[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|[CMFCDropDownFrame:: RecalcLayout](#recalclayout)|ドロップダウンフレームを移動します。|
|[CMFCDropDownFrame:: SetAutoDestroy](#setautodestroy)|子のドロップダウンツールバーウィンドウを自動的に破棄するかどうかを設定します。|

### <a name="remarks"></a>解説

このクラスは、コードで直接使用するためのものではありません。

フレームワークは、このクラスを使用して、`CMFCDropDownToolbar` クラスと `CMFCDropDownToolbarButton` クラスにフレーム動作を提供します。 これらのクラスの詳細については、「 [Cmfcdropdowntoolbar クラス](../../mfc/reference/cmfcdropdowntoolbar-class.md)および[CMFCDropDownToolbarButton クラス](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)」を参照してください。

## <a name="example"></a>例

次の例は、`CFrameWnd` クラスから `CMFCDropDownFrame` オブジェクトへのポインターを取得する方法と、子のドロップダウンツールバーウィンドウを自動的に破棄するように設定する方法を示しています。

[!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[から派生しているのではない](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)

[CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdropdowntoolbar.h

##  <a name="create"></a>CMFCDropDownFrame:: Create

`CMFCDropDownFrame` オブジェクトを作成します。

```
virtual BOOL Create(
    CWnd* pWndParent,
    int x,
    int y,
    CMFCDropDownToolBar* pWndOriginToolbar);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|Description|
|*pWndParent*|からドロップダウンフレームの親ウィンドウ。|
|*x*|からダウンフレームの位置を表示する水平方向の画面座標。|
|*y*|から下方向のフレームの位置を表示する垂直方向の画面座標。|
|*pWndOriginToolbar*|からこのメソッドが新しいドロップダウンフレームオブジェクトを設定するために使用するドロップダウンボタンを持つツールバー。|

### <a name="return-value"></a>戻り値

ドロップダウンフレームが正常に作成された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

このメソッドは、base [CMiniFrameWnd:: CreateEx](../../mfc/reference/cminiframewnd-class.md#createex)メソッドを呼び出して、WS_POPUP スタイルのドロップダウンフレームウィンドウを作成します。 ドロップダウンフレームウィンドウは、指定した画面座標で表示されます。 [CMiniFrameWnd:: CreateEx](../../mfc/reference/cminiframewnd-class.md#createex)メソッドが FALSE を返す場合、このメソッドは失敗します。

`CMFCDropDownFrame` クラスは、指定された `CMFCDropDownToolBar` パラメーターのコピーを作成します。 このメソッドは、ボタンのイメージとボタンの状態を `pWndOriginToolbar` パラメーターから `m_pWndOriginToolbar` データメンバーにコピーします。

##  <a name="getparentmenubar"></a>CMFCDropDownFrame:: GetParentMenuBar

ドロップダウンフレームの親メニューバーを取得します。

```
CMFCMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>戻り値

ドロップダウンフレームの親メニューバーへのポインター。フレームに親がない場合は NULL。

### <a name="remarks"></a>解説

このメソッドは、親のメニューバーを親ボタンから取得します。 このメソッドは、ドロップダウンフレームに親ボタンがない場合、または親ボタンに親メニューバーがない場合に NULL を返します。

##  <a name="getparentpopupmenu"></a>CMFCDropDownFrame:: GetParentPopupMenu

ドロップダウンフレームの親ポップアップメニューを取得します。

```
CMFCDropDownFrame* GetParentPopupMenu() const;
```

### <a name="return-value"></a>戻り値

ドロップダウンフレームの親ドロップダウンメニューへのポインター。フレームに親がない場合は NULL。

### <a name="remarks"></a>解説

このメソッドは、親メニューを親ボタンから取得します。 ドロップダウンフレームに親ボタンがない場合、または親ボタンに親メニューがない場合、このメソッドは NULL を返します。

##  <a name="recalclayout"></a>CMFCDropDownFrame:: RecalcLayout

ドロップダウンフレームを移動します。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|Description|
|*bNotify*|から未使用.|

### <a name="remarks"></a>解説

このメソッドは、ドロップダウンフレームが作成されたとき、または親ウィンドウのサイズが変更されたときに、フレームワークによって呼び出されます。 このメソッドは、親ウィンドウの位置とサイズを使用して、ドロップダウンフレームの位置とサイズを計算します。

##  <a name="setautodestroy"></a>CMFCDropDownFrame:: SetAutoDestroy

子のドロップダウンツールバーウィンドウを自動的に破棄するかどうかを設定します。

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>パラメーター

*bAutoDestroy*<br/>
から関連付けられているドロップダウンツールバーウィンドウを自動的に破棄する場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

*Bautodestroy*が TRUE の場合、`CMFCDropDownFrame` デストラクターは、関連付けられているドロップダウンツールバーウィンドウを破棄します。 既定値は TRUE です。

## <a name="see-also"></a>参照

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar クラス](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCDropDownToolbarButton クラス](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
