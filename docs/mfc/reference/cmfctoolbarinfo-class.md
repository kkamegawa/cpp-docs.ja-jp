---
title: CMFCToolBarInfo クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo::m_uiColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuResID
helpviewer_keywords:
- CMFCToolBarInfo [MFC], m_uiColdResID
- CMFCToolBarInfo [MFC], m_uiDisabledResID
- CMFCToolBarInfo [MFC], m_uiHotResID
- CMFCToolBarInfo [MFC], m_uiLargeColdResID
- CMFCToolBarInfo [MFC], m_uiLargeDisabledResID
- CMFCToolBarInfo [MFC], m_uiLargeHotResID
- CMFCToolBarInfo [MFC], m_uiMenuDisabledResID
- CMFCToolBarInfo [MFC], m_uiMenuResID
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
ms.openlocfilehash: b2f8af439a2534f24cdba9b0ccdb12b150db6d0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62217809"
---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo クラス

さまざまな状態のツール バー イメージのリソース ID を含みます。 `CMFCToolBarInfo` パラメーターとして使用されるヘルパー クラスには、 [cmfctoolbar::loadtoolbarex](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex)メソッド。

## <a name="syntax"></a>構文

```
class CMFCToolBarInfo
```

## <a name="members"></a>メンバー

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|(コールド) 標準のツール バー イメージを含むツールバーのビットマップのリソース ID。|
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|ツールバーの無効イメージを含むツールバーのビットマップのリソース ID。|
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|選択されている (ホット) ツール バー イメージを含むツールバーのビットマップのリソース ID。|
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|通常、大規模なツール バー イメージを含むツールバーのビットマップのリソース ID。|
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|含む大規模な場合は、ツールバーのビットマップのリソース ID には、ツール バー イメージが無効になります。|
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|ツールバーの大規模で選択したイメージを含むツールバーのビットマップのリソース ID。|
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|メニューの無効イメージを含むツールバーのビットマップのリソース ID。|
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|メニュー イメージを含むツールバーのビットマップのリソース ID。|

## <a name="remarks"></a>Remarks

完全なツールバーのビットマップは、固定サイズの小さいツール バー イメージ (ボタン) で構成されます。 格納されているそれぞれのリソース ID、`CMFCToolBarInfo`オブジェクトが 1 つの状態 (例では、選択されている、無効な場合、大規模なまたはメニュー イメージ) 用のツール バー イメージの完全なセットを含むビットマップ。

## <a name="inheritance-hierarchy"></a>継承階層

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtoolbar.h

##  <a name="m_uicoldresid"></a>  CMFCToolBarInfo::m_uiColdResID

ツールバーのすべての標準ボタン イメージのリソース ID を指定します。

```
UINT m_uiColdResID;
```

##  <a name="m_uidisabledresid"></a>  CMFCToolBarInfo::m_uiDisabledResID

ツールバーのボタンにアクセスできないイメージのリソース ID を指定します。

```
UINT m_uiDisabledResID;
```

##  <a name="m_uihotresid"></a>  CMFCToolBarInfo::m_uiHotResID

ツールバーのボタンが強調表示されているイメージをすべてのリソース ID を指定します。

```
UINT m_uiHotResID
```

##  <a name="m_uilargecoldresid"></a>  CMFCToolBarInfo::m_uiLargeColdResID

ツールバーのすべての大きな標準ボタン イメージのリソース ID を指定します。

```
UINT m_uiLargeColdResID
```

##  <a name="m_uilargedisabledresid"></a>  CMFCToolBarInfo::m_uiLargeDisabledResID

ツールバーのすべての大きな無効にされたボタン イメージのリソース ID を指定します。

```
UINT m_uiLargeDisabledResID;
```

##  <a name="m_uilargehotresid"></a>  CMFCToolBarInfo::m_uiLargeHotResID

ツールバーの大規模な強調表示されているイメージがすべてのリソース ID を指定します。

```
UINT m_uiLargeHotResID;
```

##  <a name="m_uimenudisabledresid"></a>  CMFCToolBarInfo::m_uiMenuDisabledResID

ツールバーのコマンドにアクセスできないイメージのリソース ID を指定します。

```
UINT m_uiMenuDisabledResID;
```

##  <a name="m_uimenuresid"></a>  CMFCToolBarInfo::m_uiMenuResID

ツールバーのすべての標準のメニュー項目のイメージのリソース ID を指定します。

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar クラス](../../mfc/reference/cmfctoolbar-class.md)
