---
title: CMFCPropertyGridToolTipCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
ms.openlocfilehash: f1b6f626b5f9844c73cd2225a7d6311f5b2f7d4f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505090"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl クラス

[Cmfcpropertygridctrl クラス](../../mfc/reference/cmfcpropertygridctrl-class.md)がツールヒントを表示するために使用するツールヒントコントロールを実装します。

## <a name="syntax"></a>構文

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|||
|-|-|
|名前|説明|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|`CMFCPropertyGridToolTipCtrl` オブジェクトを構築します。|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|名前|説明|
|[CMFCPropertyGridToolTipCtrl:: Create](#create)|ツールヒントコントロールのウィンドウを作成します。|
|[CMFCPropertyGridToolTipCtrl::D eactivate](#deactivate)|ツールヒントコントロールを非アクティブにして非表示にします。|
|[CMFCPropertyGridToolTipCtrl:: GetLastRect](#getlastrect)|ツールヒントコントロールの最後の位置の座標を返します。|
|[CMFCPropertyGridToolTipCtrl:: Hide](#hide)|ツールヒントコントロールを非表示にします。|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|[TranslateMessage](../../mfc/reference/cwinapp-class.md) および [DispatchMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) の各 Windows 関数にディスパッチされる前に、ウィンドウ メッセージを変換するためにクラス [CWinApp](/windows/win32/api/winuser/nf-winuser-dispatchmessage) で使用されます。 ( [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)をオーバーライドします)。|
|[CMFCPropertyGridToolTipCtrl:: SetTextMargin](#settextmargin)|ツールヒントのテキストと、ツールヒントウィンドウの境界線との間隔を設定します。|
|[CMFCPropertyGridToolTipCtrl:: Track](#track)|ツールヒントコントロールを表示します。|

## <a name="remarks"></a>Remarks

ポインターをプロパティ名の上に置くと、ツールヒントが表示されます。 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)クラスは、ユーザーが簡単に読めるようにツールヒントを表示します。 通常、ツールヒントの位置は、ポインターの位置によって決まります。 このクラスを使用すると、プロパティ名の上にツールヒントが表示され、プロパティ名が完全に表示されます。

MFC は、このコントロールを自動的に作成し、 [Cmfcpropertygridctrl クラス](../../mfc/reference/cmfcpropertygridctrl-class.md)で使用します。

## <a name="example"></a>例

`CMFCPropertyGridToolTipCtrl`クラスのオブジェクトを構築する方法と、ツールヒントコントロールを表示する方法を次の例に示します。

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxpropertygridtooltipctrl

##  <a name="cmfcpropertygridtooltipctrl"></a>CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

`CMFCPropertyGridToolTipCtrl` オブジェクトを構築します。

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

##  <a name="create"></a>CMFCPropertyGridToolTipCtrl:: Create

ツールヒントコントロールのウィンドウを作成します。

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
から親ウィンドウへのポインター。

### <a name="return-value"></a>戻り値

ウィンドウが正常に作成された場合は TRUE。それ以外の場合は FALSE。

##  <a name="deactivate"></a>CMFCPropertyGridToolTipCtrl::D eactivate

ツールヒントコントロールを非アクティブにして非表示にします。

```
void Deactivate();
```

### <a name="remarks"></a>Remarks

このメソッドは、最後の位置とテキストを空の値に設定します。これにより、 [CMFCPropertyGridToolTipCtrl:: Track](#track)の後続の呼び出しでツールヒントが表示されます。

##  <a name="getlastrect"></a>CMFCPropertyGridToolTipCtrl:: GetLastRect

ツールヒントコントロールの最後の位置の座標を返します。

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
入出力ツールヒントコントロールの最後の位置を格納します。

##  <a name="hide"></a>CMFCPropertyGridToolTipCtrl:: Hide

ツールヒントコントロールを非表示にします。

```
void Hide();
```

##  <a name="settextmargin"></a>CMFCPropertyGridToolTipCtrl:: SetTextMargin

ツールヒントのテキストと、ツールヒントウィンドウの境界線との間隔を設定します。

```
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>パラメーター

*nTextMargin*<br/>
からツールヒントコントロールのテキストと、ツールヒントウィンドウの境界線との間隔を指定します。 既定値は10ピクセルです。

##  <a name="track"></a>CMFCPropertyGridToolTipCtrl:: Track

ツールヒントコントロールを表示します。

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
からツールヒントコントロールの位置とサイズを指定します。

*strText*<br/>
からツールヒントに表示されるテキストを指定します。

### <a name="remarks"></a>Remarks

このメソッドは、 *rect*によって指定された位置とサイズにツールヒントコントロールを表示します。 このメソッドが最後に呼び出されてから位置、サイズ、およびテキストが変更されていない場合、このメソッドは無効です。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)
