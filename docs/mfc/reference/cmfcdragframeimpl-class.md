---
title: CMFCDragFrameImpl クラス
ms.date: 10/18/2018
f1_keywords:
- CMFCDragFrameImpl
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
ms.openlocfilehash: 05b4426da6bee0443a407cff583f47bee60262e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348615"
---
# <a name="cmfcdragframeimpl-class"></a>CMFCDragFrameImpl クラス

`CMFCDragFrameImpl`クラスは、ユーザーが標準ドッキング モードのペインをドラッグしたときに表示されるドラッグ四角形を描画します。
詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

## <a name="syntax"></a>構文

```
class CMFCDragFrameImpl
```

## <a name="remarks"></a>Remarks

このクラスのオブジェクトがそれぞれに埋め込まれた[CPane クラス](../../mfc/reference/cpane-class.md)オブジェクト。 使用してそのため、各ペイン、`CanFloat`メソッドが、ユーザーがドラッグしたときに、ドラッグ四角形を表示します。

使用してドラッグ四角形の幅を制御する[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat)と[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdragframeimpl.h

##  <a name="enddrawdragframe"></a>  CMFCDragFrameImpl::EndDrawDragFrame

```
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```

### <a name="parameters"></a>パラメーター

[in]*bClearInternalRects*<br/>

### <a name="remarks"></a>Remarks

##  <a name="init"></a>  CMFCDragFrameImpl::Init

```
void Init(CWnd* pDraggedWnd);
```

### <a name="parameters"></a>パラメーター

[in]*pDraggedWnd*<br/>

### <a name="remarks"></a>Remarks

##  <a name="movedragframe"></a>  CMFCDragFrameImpl::MoveDragFrame

```
void MoveDragFrame(BOOL bForceMove = FALSE);
```

### <a name="parameters"></a>パラメーター

[in] *bForceMove*<br/>

### <a name="remarks"></a>Remarks

##  <a name="placetabpredocking"></a>  CMFCDragFrameImpl::PlaceTabPreDocking

```
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,
    BOOL bFirstTime);

void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```

### <a name="parameters"></a>パラメーター

[in] *pTabbedBar*<br/>

[in]*bFirstTime*<br/>

[in]*pCBarToPlaceOn*<br/>

### <a name="remarks"></a>Remarks

##  <a name="removetabpredocking"></a>  CMFCDragFrameImpl::RemoveTabPreDocking

```
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```

### <a name="parameters"></a>パラメーター

[in]*pOldTargetBar*<br/>

### <a name="remarks"></a>Remarks

##  <a name="resetstate"></a>  CMFCDragFrameImpl::ResetState

```
void ResetState();
```

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CPane クラス](../../mfc/reference/cpane-class.md)
