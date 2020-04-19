---
title: CMFCRibbonLabel クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::CMFCRibbonLabel
- AFXRIBBONLABEL/CMFCRibbonLabel::SetACCData
helpviewer_keywords:
- CMFCRibbonLabel [MFC], CMFCRibbonLabel
- CMFCRibbonLabel [MFC], SetACCData
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
ms.openlocfilehash: b79d6191d2deb0a295e81da1150cc7b38fd81232
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388411"
---
# <a name="cmfcribbonlabel-class"></a>CMFCRibbonLabel クラス

リボンのクリックできないテキスト ラベルを実装します。

## <a name="syntax"></a>構文

```
class CMFCRibbonLabel : public CMFCRibbonButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonLabel::CMFCRibbonLabel](#cmfcribbonlabel)|構築し、初期化、`CMFCRibbonLabel`指定したテキスト文字列を持つオブジェクト。|
|`CMFCRibbonLabel::~CMFCRibbonLabel`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|`CMFCRibbonLabel::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|`CMFCRibbonLabel::GetThisClass`|ポインターを取得する、framework によって使用される、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)このクラス型に関連付けられているオブジェクト。|
|[CMFCRibbonLabel::SetACCData](#setaccdata)|現在のリボンのラベル要素のアクセシビリティ データを決定します。 (上書き[cmfcribbonbutton::setaccdata](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata))。|

### <a name="remarks"></a>Remarks

リボンのラベルを作成した後に追加パネルを呼び出すことによって[cmfcribbonpanel::add](../../mfc/reference/cmfcribbonpanel-class.md#add)します。

クイック アクセス ツールバーには、リボンのラベルを追加することはできません。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxRibbonLabel.h

##  <a name="cmfcribbonlabel"></a>  CMFCRibbonLabel::CMFCRibbonLabel

構築し、初期化、 [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)指定したテキスト文字列を表示するオブジェクト。

```
CMFCRibbonLabel(
    LPCTSTR lpszText,
    BOOL bIsMultiLine = FALSE);
```

### <a name="parameters"></a>パラメーター

*lpszText*<br/>
[in]ラベルに表示されるテキスト。

*bIsMultiLine*<br/>
[in]ラベルが、複数行のラベルであることを指定する場合は TRUEそれ以外の場合、FALSE です。

##  <a name="setaccdata"></a>  CMFCRibbonLabel::SetACCData

現在のリボンのラベル要素のアクセシビリティ データを決定します。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>パラメーター

*pParent*<br/>
[in]現在のリボンのラベルの親ウィンドウを表します。

*data*<br/>
[out]型のオブジェクト`CAccessibilityData`リボンのラベルを現在のユーザー補助データに設定されます。

### <a name="return-value"></a>戻り値

TRUE の場合、*データ*パラメーターが正常にリボンのラベルを現在のユーザー補助データと共に設定されている場合は FALSE。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton クラス](../../mfc/reference/cmfcribbonbutton-class.md)
