---
title: CMFCSpinButtonCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
ms.openlocfilehash: 60808359c11604368493031e1b6f4573b3b2026f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410101"
---
# <a name="cmfcspinbuttonctrl-class"></a>CMFCSpinButtonCtrl クラス

`CMFCSpinButtonCtrl`クラスは、スピン ボタン コントロールを描画するビジュアル マネージャーをサポートしています。

## <a name="syntax"></a>構文

```
class CMFCSpinButtonCtrl : public CSpinButtonCtrl
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|既定のコンストラクターです。|
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|現在のスピン ボタン コントロールを再描画します。|

## <a name="remarks"></a>Remarks

ビジュアル マネージャーを使用して、アプリケーションのスピン ボタン コントロールを描画する、交換のすべてのインスタンス、`CSpinButtonCtrl`クラス、`CMFCSpinButtonCtrl`クラス。

## <a name="example"></a>例

次の例のオブジェクトを作成する方法、`CMFCSpinButtonCtrl`クラスを使用してその`Create`メソッド。

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)

[CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxspinbuttonctrl.h

##  <a name="ondraw"></a>  CMFCSpinButtonCtrl::OnDraw

現在のスピン ボタン コントロールを再描画します。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイス コンテキストへのポインター。

### <a name="remarks"></a>Remarks

フレームワークによって、`CMFCSpinButtonCtrl::OnPaint`を処理するメソッド、 [CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint)メッセージ、および、メソッドを呼び出してこの`CMFCSpinButtonCtrl::OnDraw`メソッド。 スピン ボタン コントロールを描画する方法をカスタマイズするには、このメソッドをオーバーライドします。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager クラス](../../mfc/reference/cmfcvisualmanager-class.md)
