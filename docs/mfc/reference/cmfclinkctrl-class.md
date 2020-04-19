---
title: CMFCLinkCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
ms.openlocfilehash: 839448694cee17f5bc1a1e47f7c113026a1a4006
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346207"
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl クラス

`CMFCLinkCtrl`クラス ボタンをハイパーリンクとして表示し、ボタンがクリックされたときに、リンクのターゲットを呼び出します。

## <a name="syntax"></a>構文

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCLinkCtrl::SetURL](#seturl)|ボタンのテキストとして指定された URL が表示されます。|
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|暗黙的なプロトコルを設定します (たとえば、"http:") の URL。|
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|ボタンのテキストまたはビットマップを格納するボタンのサイズを変更します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|ボタンのフォーカスされた四角形が描画される前に、フレームワークによって呼び出されます。|

## <a name="remarks"></a>Remarks

派生したボタンをクリックすると、`CMFCLinkCtrl`クラス、フレームワークのパラメーターとして、ボタンの URL を渡して、`ShellExecute`メソッド。 次に、`ShellExecute`メソッドは、URL のターゲットを開きます。

## <a name="example"></a>例

次の例のサイズを設定する方法を示します、`CMFCLinkCtrl`オブジェクト、および url と、ツールヒントを設定する方法、`CMFCLinkCtrl`オブジェクト。 この例は、[新しいコントロール サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxlinkctrl.h

##  <a name="ondrawfocusrect"></a>  CMFCLinkCtrl::OnDrawFocusRect

ボタンのフォーカスされた四角形が描画される前に、フレームワークによって呼び出されます。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイス コンテキストへのポインター。

*rectClient*<br/>
[in]リンク コントロールの外接する四角形にします。

### <a name="remarks"></a>Remarks

ボタンのフォーカスされた四角形を描画するために、独自のコードを使用する場合に、このメソッドをオーバーライドします。

##  <a name="seturl"></a>  CMFCLinkCtrl::SetURL

ボタンのテキストとして指定された URL が表示されます。

```
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>パラメーター

*lpszURL*<br/>
[in]表示するボタンのテキスト。

### <a name="remarks"></a>Remarks

##  <a name="seturlprefix"></a>  CMFCLinkCtrl::SetURLPrefix

暗黙的なプロトコルを設定します (たとえば、"http:") の URL。

```
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>パラメーター

*lpszPrefix*<br/>
[in]URL のプロトコルのプレフィックス。

### <a name="remarks"></a>Remarks

このメソッドを使用すると、URL プレフィックスを設定できます。 プレフィックスは、ボタンの表面上は表示されませんが、これを使用するには、URL のターゲットを参照します。

##  <a name="sizetocontent"></a>  CMFCLinkCtrl::SizeToContent

ボタンのテキストまたはビットマップを格納するボタンのサイズを変更します。

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>パラメーター

*bVCenter*<br/>
[in]ボタンのテキストと、リンク コントロールの上下の間に垂直方向にビットマップを中央揃えする場合は TRUEそれ以外の場合、FALSE です。 既定値は FALSE です。

*bHCenter*<br/>
[in]ボタンのテキストと、リンク コントロールの左側および右側との間の水平方向にビットマップを中央揃えする場合は TRUEそれ以外の場合、FALSE です。 既定値は FALSE です。

### <a name="return-value"></a>戻り値

A [CSize](../../atl-mfc-shared/reference/csize-class.md)リンク コントロールの新しいサイズを格納しているオブジェクト。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CLinkCtrl クラス](../../mfc/reference/clinkctrl-class.md)<br/>
[CMFCButton クラス](../../mfc/reference/cmfcbutton-class.md)
