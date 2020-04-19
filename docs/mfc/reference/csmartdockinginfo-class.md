---
title: CSmartDockingInfo クラス
ms.date: 11/19/2018
f1_keywords:
- CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo::CopyTo
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_bUseThemeColorInShading
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrBaseBackground
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneDest
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneSrc
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrTransparent
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_nCentralGroupOffset
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_sizeTotal
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerBmpResID
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerLightBmpResID
helpviewer_keywords:
- CSmartDockingInfo [MFC], CopyTo
- CSmartDockingInfo [MFC], m_bUseThemeColorInShading
- CSmartDockingInfo [MFC], m_clrBaseBackground
- CSmartDockingInfo [MFC], m_clrToneDest
- CSmartDockingInfo [MFC], m_clrToneSrc
- CSmartDockingInfo [MFC], m_clrTransparent
- CSmartDockingInfo [MFC], m_nCentralGroupOffset
- CSmartDockingInfo [MFC], m_sizeTotal
- CSmartDockingInfo [MFC], m_uiMarkerBmpResID
- CSmartDockingInfo [MFC], m_uiMarkerLightBmpResID
ms.assetid: cab04f38-4bc1-4378-9337-c56fc87fbd68
ms.openlocfilehash: d5f918b591e1db9ff67288a8761f7554698fa761
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324006"
---
# <a name="csmartdockinginfo-class"></a>CSmartDockingInfo クラス

スマート ドッキング マーカーの外観を定義します。

## <a name="syntax"></a>構文

```
class CSmartDockingInfo : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CSmartDockingInfo::CSmartDockingInfo`|既定のコンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSmartDockingInfo::CopyTo](#copyto)|現在のスマート ドッキング情報パラメーターに指定されたコピー [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)オブジェクト。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CSmartDockingInfo::m_bUseThemeColorInShading](#m_busethemecolorinshading)|フレームワークはスマート ドッキング マーカーを表示するときに、現在のテーマの色を使用するかどうかを指定します。|
|[CSmartDockingInfo::m_clrBaseBackground](#m_clrbasebackground)|スマート ドッキング マーカーの基本の背景色を指定します。|
|[CSmartDockingInfo::m_clrToneDest](#m_clrtonedest)|置換する色を指定します`m_clrToneSrc`スマート ドッキング マーカー ビットマップにします。|
|[CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)|スマート ドッキング マーカー ビットマップの色を指定します。|
|[CSmartDockingInfo::m_clrTransparent](#m_clrtransparent)|透過的な場合は、スマート ドッキング マーカー ビットマップの色を指定します。|
|[CSmartDockingInfo::m_nCentralGroupOffset](#m_ncentralgroupoffset)|サーバーの全体のグループの四角形の境界からスマート ドッキング マーカーの中央のグループのオフセットを指定します。|
|[CSmartDockingInfo::m_sizeTotal](#m_sizetotal)|グループ内のすべてのスマート ドッキング マーカーの合計サイズを指定します。|
|[CSmartDockingInfo::m_uiMarkerBmpResID](#m_uimarkerbmpresid)|フレームワークが強調表示されていないスマート ドッキング マーカーに使用されるビットマップのリソース Id を定義します。|
|[CSmartDockingInfo::m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|フレームワークが強調表示されているスマート ドッキング マーカーに使用されるビットマップのリソース Id を定義します。|

## <a name="remarks"></a>Remarks

内部的には、framework ハンドルでスマート ドッキング マーカー。 次の図は、標準のスマート ドッキング マーカーを示しています。

![スマート ドッキングの標準的なマーカー](../../mfc/reference/media/nextsdmarkers.png "スマート ドッキングの標準マーカー")

この図では、左側のイメージは、有効になっているタブへのドッキングを持たないサーバーの全体のグループのスマート ドッキング マーカーを示します。 中央のイメージは、右端のスマート ドッキング マーカーを示しています。 右側のイメージは、有効になっているタブへのドッキングが中央のグループのスマート ドッキング マーカーを示します。 サーバーの全体のグループのスマート ドッキング マーカーはメインのビットマップを備え、5 つのスマート ドッキング マーカー ビットマップ。

スマート ドッキング マーカーの次のパラメーターをカスタマイズすることができます。

- 色 たとえば、すべてのユーザー定義の色で、図のマーカーの青の色を置き換えることができます。

- 透明色。

- 外接する四角形の枠線から中央のグループ内のスマート ドッキング マーカーのオフセットします。

- サーバーの全体のグループを表すメインのビットマップ。

- 正規表現と強調表示されたスマート ドッキング マーカーを表すビットマップ。

次の図は、カスタマイズされたスマート ドッキング マーカーの例を示します。

![スマート ドッキング カスタム マーカー](../../mfc/reference/media/nextsdmarkerscustom.png "スマート ドッキング カスタム マーカー")

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxDockingManager.h

##  <a name="copyto"></a>  CSmartDockingInfo::CopyTo

現在のスマート ドッキングのパラメーターに指定されたコピー [CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)オブジェクト。

```
void CopyTo(CSmartDockingInfo& params);
```

### <a name="parameters"></a>パラメーター

*params*<br/>
[out]型のオブジェクト`CSmartDockingInfo`スマート ドッキングの現在のパラメーターに設定されます。

##  <a name="m_busethemecolorinshading"></a>  CSmartDockingInfo::m_bUseThemeColorInShading

フレームワークはスマート ドッキング マーカーを表示するときに、現在のテーマの色を使用するかどうかを指定します。

```
BOOL m_bUseThemeColorInShading;
```

### <a name="remarks"></a>Remarks

現在のテーマの色を使用して、マーカーを描画する場合は TRUE、それ以外の場合、マーカーは、薄い青色で描画されます。

既定値は FALSE です。

##  <a name="m_clrbasebackground"></a>  CSmartDockingInfo::m_clrBaseBackground

スマート ドッキング マーカーの基本の背景色を指定します。

```
COLORREF m_clrBaseBackground;
```

##  <a name="m_clrtonedest"></a>  CSmartDockingInfo::m_clrToneDest

置き換える色を指定します`m_clrToneSrc`スマート ドッキング マーカー ビットマップにします。

```
COLORREF m_clrToneDest;
```

### <a name="remarks"></a>Remarks

プログラムでマーカー ビットマップの色を変更するには、この値を設定します。 たとえば、フレームワークで提供される標準的なマーカーの色を変更する場合は、この値を目的の色に設定します。 既定では、 [CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc) RGB (61、123、241) に設定されている (青み色)。

カスタム マーカーの色を変更する、両方を指定する必要があります`m_clrToneDest`と`m_clrToneSrc`します。

##  <a name="m_clrtonesrc"></a>  CSmartDockingInfo::m_clrToneSrc

スマート ドッキング マーカー ビットマップの色を指定します。

```
COLORREF m_clrToneSrc;
```

### <a name="remarks"></a>Remarks

別の色でカスタムのビットマップの色を置換する場合にのみ、この値を設定します。 標準 (フレームワークが提供) の色を変更する場合は、この値を設定する必要はありませんマーカー。

使用`(COLORREF)-1`スマート ドッキングのグループのメンバーは空のままにします。

##  <a name="m_clrtransparent"></a>  CSmartDockingInfo::m_clrTransparent

透過的な場合は、スマート ドッキング マーカー ビットマップの色を指定します。

```
COLORREF m_clrTransparent;
```

### <a name="remarks"></a>Remarks

ドッキングのグループにカスタム マーカーとカスタムのビットマップを表示する場合は、この値を設定する必要があります。

##  <a name="m_ncentralgroupoffset"></a>  CSmartDockingInfo::m_nCentralGroupOffset

スマート ドッキング マーカーの中央のグループとサーバーの全体のグループの四角形の境界間のオフセットを指定します。

```
int m_nCentralGroupOffset;
```

### <a name="remarks"></a>Remarks

カスタム マーカーとスマート ドッキング マーカーの中央のグループの境界間の既定オフセットを変更したい場合は、この値を指定します。 既定のオフセットは、5 ピクセルです。

##  <a name="m_sizetotal"></a>  CSmartDockingInfo::m_sizeTotal

中央のグループ内のすべてのスマート ドッキング マーカーを囲む外接する四角形の合計サイズを指定します。

```
CSize m_sizeTotal;
```

### <a name="remarks"></a>Remarks

設定`m_sizeTotal`外接する四角形の中心グループ マーカーのサイズにします。 マーカーのカスタム ビットマップを使用している場合は、この値を指定することが必要です。

##  <a name="m_uimarkerbmpresid"></a>  CSmartDockingInfo::m_uiMarkerBmpResID

強調表示されている非カスタム スマート ドッキング マーカーに使用されるビットマップのリソース Id を定義します。

```
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Remarks

スマート ドッキング マーカーを表すビットマップのリソース Id をこの配列に格納します。 現在、AFX_SD_MARKERS_NUM は 5 として定義されています。 次のように配列に格納します。

```cpp
params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;
params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;
params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;
params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;
params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;
```

##  <a name="m_uimarkerlightbmpresid"></a>  CSmartDockingInfo::m_uiMarkerLightBmpResID

強調表示されているカスタム スマート ドッキング マーカーに使用されるビットマップのリソース Id を定義します。

```
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>Remarks

強調表示されたスマート ドッキング マーカーを表すビットマップのリソース Id をこの配列に格納します。 現在、AFX_SD_MARKERS_NUM は 5 として定義されています。 次のように配列に格納します。

```cpp
params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;
params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;
params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;
params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;
params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;
```

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)
