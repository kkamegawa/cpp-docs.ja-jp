---
title: CMFCImageEditorPaletteBar クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::GetRowHeight
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable
helpviewer_keywords:
- CMFCImageEditorPaletteBar [MFC], GetRowHeight
- CMFCImageEditorPaletteBar [MFC], IsButtonExtraSizeAvailable
ms.assetid: 3fb7ba8e-f254-4d56-b913-9941b4ed8138
ms.openlocfilehash: 6812f3f425186484ef892d7f5c626c0dfce0f863
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378103"
---
# <a name="cmfcimageeditorpalettebar-class"></a>CMFCImageEditorPaletteBar クラス

イメージ エディター ダイアログ ボックスにパレット バー機能を提供します。

## <a name="syntax"></a>構文

```
class CMFCImageEditorPaletteBar : public CMFCToolBar
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|名前|説明|
|[CMFCImageEditorPaletteBar::GetRowHeight](#getrowheight)|ツール バー ボタンの高さを返します。 (上書き[CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight))。|
|[CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|罫線を拡張するボタンがツールバーに表示できるかどうかを判断します。 (上書き[CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable))。|

### <a name="remarks"></a>Remarks

このクラスは、コードから直接使用するものではありません。

フレームワークでは、このクラスを使用して、イメージ エディター ダイアログ ボックスでパレット バーを表示します。 イメージ エディターのダイアログ ボックスの詳細については、次を参照してください。 [CMFCImageEditorDialog クラス](../../mfc/reference/cmfcimageeditordialog-class.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCImageEditorPaletteBar](../../mfc/reference/cmfcimageeditorpalettebar-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afximageeditordialog.h

##  <a name="getrowheight"></a>  CMFCImageEditorPaletteBar::GetRowHeight

ツール バー ボタンの高さを返します。

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>戻り値

ツールバーの各ボタンの高さ。

##  <a name="isbuttonextrasizeavailable"></a>  CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable

罫線を拡張するボタンがツールバーに表示できるかどうかを判断します。

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>戻り値

このメソッドは、FALSE を返します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog クラス](../../mfc/reference/cmfcimageeditordialog-class.md)
