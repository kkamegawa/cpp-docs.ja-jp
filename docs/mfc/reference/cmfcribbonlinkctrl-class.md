---
title: CMFCRibbonLinkCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CopyFrom
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetCompactSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetRegularSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetToolTipText
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::IsDrawTooltipImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDraw
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDrawMenuImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnMouseMove
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnSetIcon
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OpenLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::SetLink
helpviewer_keywords:
- CMFCRibbonLinkCtrl [MFC], CMFCRibbonLinkCtrl
- CMFCRibbonLinkCtrl [MFC], CopyFrom
- CMFCRibbonLinkCtrl [MFC], GetCompactSize
- CMFCRibbonLinkCtrl [MFC], GetLink
- CMFCRibbonLinkCtrl [MFC], GetRegularSize
- CMFCRibbonLinkCtrl [MFC], GetToolTipText
- CMFCRibbonLinkCtrl [MFC], IsDrawTooltipImage
- CMFCRibbonLinkCtrl [MFC], OnDraw
- CMFCRibbonLinkCtrl [MFC], OnDrawMenuImage
- CMFCRibbonLinkCtrl [MFC], OnMouseMove
- CMFCRibbonLinkCtrl [MFC], OnSetIcon
- CMFCRibbonLinkCtrl [MFC], OpenLink
- CMFCRibbonLinkCtrl [MFC], SetLink
ms.assetid: 77ae1941-e0ab-4a9d-911e-1752d34c079b
ms.openlocfilehash: 12a83e45176f7fc6020da1f0d0ee5923ef0f466c
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866154"
---
# <a name="cmfcribbonlinkctrl-class"></a>CMFCRibbonLinkCtrl クラス

リボン上に配置するハイパーリンクを実装します。 ハイパーリンクをクリックすると、Web ページが表示されます。
詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。

## <a name="syntax"></a>構文

```
class CMFCRibbonLinkCtrl : public CMFCRibbonButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|`CMFCRibbonLinkCtrl` オブジェクトを構築して初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|( `CMFCRibbonButton::CopyFrom`をオーバーライドします)。|
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|( [CMFCRibbonButton:: GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize)をオーバーライドします。)|
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|ハイパーリンクの値を返します。|
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|( [CMFCRibbonButton:: GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize)をオーバーライドします。)|
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|( [CMFCRibbonButton:: GetToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext)をオーバーライドします。)|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|( `CMFCRibbonButton::IsDrawTooltipImage`をオーバーライドします)。|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|( [CMFCRibbonButton:: OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw)をオーバーライドします)。|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|( [CMFCRibbonBaseElement:: OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)をオーバーライドします。)|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|( `CMFCRibbonButton::OnMouseMove`をオーバーライドします)。|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|ハイパーリンクで指定されている Web ページを開きます。|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|ハイパーリンクの値を設定します。|

## <a name="remarks"></a>Remarks

ハイパーリンクを作成したら、 [CMFCRibbonPanel:: add](../../mfc/reference/cmfcribbonpanel-class.md#add)を呼び出してパネルに追加します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxRibbonLinkCtrl

##  <a name="cmfcribbonlinkctrl"></a>  CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl

[CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)オブジェクトを構築し、初期化します。

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
からリンクコントロールがクリックされたときに実行されるコマンドのコマンド ID を指定します。

*lpszText*<br/>
からリンクコントロールに表示するラベルを指定します。

*lpszLink*<br/>
からリンクコントロールに関連付けられているハイパーリンクを指定します。

### <a name="example"></a>例

`CMFCRibbonLinkCtrl`クラスのコンストラクターを使用する方法を次の例に示します。 このコードスニペットは、リボンの[ガジェットサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCRibbonLinkCtrl::CopyFrom

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>パラメーター

から*src*<br/>

### <a name="remarks"></a>Remarks

##  <a name="getcompactsize"></a>  CMFCRibbonLinkCtrl::GetCompactSize

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

から*pDC*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getlink"></a>  CMFCRibbonLinkCtrl::GetLink

ハイパーリンクの値を返します。

```
LPCTSTR GetLink() const;
```

### <a name="return-value"></a>戻り値

ハイパーリンクの現在の値。

### <a name="remarks"></a>Remarks

##  <a name="getregularsize"></a>  CMFCRibbonLinkCtrl::GetRegularSize

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

から*pDC*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="gettooltiptext"></a>  CMFCRibbonLinkCtrl::GetToolTipText

```
virtual CString GetToolTipText() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="ondrawmenuimage"></a>  CMFCRibbonLinkCtrl::OnDrawMenuImage

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>パラメーター

から*CDC&#42;*<br/>
から*CRect*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="isdrawtooltipimage"></a>CMFCRibbonLinkCtrl::IsDrawTooltipImage

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="ondraw"></a>  CMFCRibbonLinkCtrl::OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

から*pDC*<br/>

### <a name="remarks"></a>Remarks

##  <a name="onmousemove"></a>  CMFCRibbonLinkCtrl::OnMouseMove

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>パラメーター

から*ポイント*<br/>

### <a name="remarks"></a>Remarks

##  <a name="onseticon"></a>  CMFCRibbonLinkCtrl::OnSetIcon

```
virtual void OnSetIcon();
```

### <a name="remarks"></a>Remarks

##  <a name="openlink"></a>  CMFCRibbonLinkCtrl::OpenLink

ハイパーリンクで指定されている Web ページを開きます。

```
BOOL OpenLink();
```

### <a name="return-value"></a>戻り値

関連付けられた web ページが正常に開かれた場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

`CMFCRibbonLinkCtrl`オブジェクトに関連付けられているハイパーリンクを使用して、web ページを開きます。

##  <a name="setlink"></a>  CMFCRibbonLinkCtrl::SetLink

ハイパーリンクの値を設定します。

```
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>パラメーター

*lpszLink*<br/>
からハイパーリンクのテキストを指定します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton クラス](../../mfc/reference/cmfcribbonbutton-class.md)
