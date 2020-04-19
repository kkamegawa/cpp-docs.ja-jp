---
title: CTreeView クラス
ms.date: 11/04/2016
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
ms.openlocfilehash: fec8379a3944d981672754274f50dd4e60f71b61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323597"
---
# <a name="ctreeview-class"></a>CTreeView クラス

簡単に使用およびツリー コントロールの[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)MFC のドキュメント/ビュー アーキテクチャのツリー コントロールの機能をカプセル化するクラス。

## <a name="syntax"></a>構文

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CTreeView::CTreeView](#ctreeview)|`CTreeView` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CTreeView::GetTreeCtrl](#gettreectrl)|ビューに関連付けられているツリーのコントロールを返します。|

## <a name="remarks"></a>Remarks

このアーキテクチャの詳細については、「の概要、 [CView](../../mfc/reference/cview-class.md)クラスとクロス リファレンスがあります。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcview.h

##  <a name="ctreeview"></a>  CTreeView::CTreeView

`CTreeView` オブジェクトを構築します。

```
CTreeView();
```

##  <a name="gettreectrl"></a>  CTreeView::GetTreeCtrl

ビューに関連付けられているツリーのコントロールへの参照を返します。

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>関連項目

[CCtrlView クラス](../../mfc/reference/cctrlview-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CView クラス](../../mfc/reference/cview-class.md)<br/>
[CCtrlView クラス](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl クラス](../../mfc/reference/ctreectrl-class.md)
