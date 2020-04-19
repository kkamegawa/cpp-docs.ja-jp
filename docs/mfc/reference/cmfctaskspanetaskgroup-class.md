---
title: CMFCTasksPaneTaskGroup クラス
ms.date: 11/19/2018
f1_keywords:
- CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsBottom
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsCollapsed
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsSpecial
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_lstTasks
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rect
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rectGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_strName
helpviewer_keywords:
- CMFCTasksPaneTaskGroup [MFC], CMFCTasksPaneTaskGroup
- CMFCTasksPaneTaskGroup [MFC], SetACCData
- CMFCTasksPaneTaskGroup [MFC], m_bIsBottom
- CMFCTasksPaneTaskGroup [MFC], m_bIsCollapsed
- CMFCTasksPaneTaskGroup [MFC], m_bIsSpecial
- CMFCTasksPaneTaskGroup [MFC], m_lstTasks
- CMFCTasksPaneTaskGroup [MFC], m_rect
- CMFCTasksPaneTaskGroup [MFC], m_rectGroup
- CMFCTasksPaneTaskGroup [MFC], m_strName
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
ms.openlocfilehash: a28f00fb732727ec1334946a9e752679307cd3a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222251"
---
# <a name="cmfctaskspanetaskgroup-class"></a>CMFCTasksPaneTaskGroup クラス

`CMFCTasksPaneTaskGroup`クラスで使用されるヘルパー クラス、 [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)コントロール。 `CMFCTasksPaneTaskGroup` 型のオブジェクトは *タスク グループ*を表します。 タスク グループは、閉じるボタンがある独立したボックスにフレームワークによって表示される項目の一覧です。 このボックスには、オプションのキャプション (グループ名) があります。 グループが閉じると、タスクの一覧は表示されません。

## <a name="syntax"></a>構文

```
class CMFCTasksPaneTaskGroup : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup](#cmfctaskspanetaskgroup)|`CMFCTasksPaneTaskGroup` オブジェクトを構築します。|
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::SetACCData](#setaccdata)|現在のタスク グループのユーザー補助データを決定します。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|タスク グループを作業ウィンドウ コントロールの下部に配置されているかどうかを判断します。|
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|タスク グループが折りたたまれているかどうかを判断します。|
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|タスク グループがあるかどうかを判断します*特殊です。* フレームワークには、異なる色で特別なキャプションが表示されます。|
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|タスクの内部一覧に含まれています。|
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|グループ キャプションの外接する四角形を指定します。|
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|グループの外接する四角形を指定します。|
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|グループの名前を指定します。|

## <a name="remarks"></a>Remarks

次の図は、展開されたタスク グループを示しています。

![展開されたタスク グループ](../../mfc/reference/media/nexttaskgrpexpand.png "展開されたタスク グループ")

次の図は、折りたたまれたタスク グループを示しています。

![折りたたまれたタスク グループ](../../mfc/reference/media/nexttaskgrpcollapse.png "折りたたまれたタスク グループ")

次の図は、キャプションのないタスク グループを示しています。

![キャプションのないタスク グループ](../../mfc/reference/media/nexttaskgrpnocapt.png "キャプションのないタスク グループ")

次の図は、2 つのタスク グループを示します。 最初のタスク グループが設定して、特別なマーク、`m_bIsSpecial`フラグを true の場合、2 番目のタスク グループは特別ではありません。 最初のタスク グループのキャプションが 2 番目のタスク グループより暗い方法に注意してください。

![特殊なタスク グループ](../../mfc/reference/media/nexttaskgrpspecial.png "特殊なタスク グループ")

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxTasksPane.h

##  <a name="cmfctaskspanetaskgroup"></a>  CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup

`CMFCTasksPaneTaskGroup` オブジェクトを構築します。

```
CMFCTasksPaneTaskGroup(
    LPCTSTR lpszName,
    BOOL bIsBottom,
    BOOL bIsSpecial=FALSE,
    BOOL bIsCollapsed=FALSE,
    CMFCTasksPanePropertyPage* pPage=NULL,
    HICON hIcon=NULL);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
グループ キャプションの グループの名前を指定します。

*bIsBottom*<br/>
グループを作業ウィンドウ コントロールの下部に配置されているかどうかを指定します。

*bIsSpecial*<br/>
として、グループが指定されているかどうかを指定します。*特別な*異なる色でグループのキャプションが塗りつぶされたかどうかにそのため、と。

*bIsCollapsed*<br/>
グループが折りたたまれているかどうかを指定します。

*pPage*<br/>
このタスク グループが属するプロパティ ページを指定します。

*hIcon*<br/>
グループ キャプションに表示されるアイコンを指定します。

### <a name="remarks"></a>Remarks

##  <a name="m_bisbottom"></a>  CMFCTasksPaneTaskGroup::m_bIsBottom

タスク グループを作業ウィンドウ コントロールの下部に配置されているかどうかを判断します。

```
BOOL m_bIsBottom;
```

### <a name="remarks"></a>Remarks

1 つのグループは、作業ウィンドウ コントロールの下部に配置できます。 このタスク グループが最後に追加する必要があります。 詳細については、次を参照してください。 [cmfctaskspane::addgroup](../../mfc/reference/cmfctaskspane-class.md#addgroup)します。

##  <a name="m_biscollapsed"></a>  CMFCTasksPaneTaskGroup::m_bIsCollapsed

タスク グループが折りたたまれているかどうかを判断します。

```
BOOL m_bIsCollapsed;
```

### <a name="remarks"></a>Remarks

有効にするかを呼び出すことによって、タスク ウィンドウでグループを折りたたむ機能を無効にする[:enablegroupcollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse)します。

##  <a name="m_bisspecial"></a>  CMFCTasksPaneTaskGroup::m_bIsSpecial

タスク グループがあるかどうかを判断します*特殊*特殊なタスク グループのキャプションを異なる色で識別する必要があるかどうか。

```
BOOL m_bIsSpecial;
```

### <a name="remarks"></a>Remarks

アプリケーションが Windows XP ビジュアル テーマを使用していると`m_bIsSpecial`false、フレームワークによって`DrawThemeBackground`EBP_NORMALGROUPBACKGROUND フラグを使用します。 場合`m_bIsSpecial`が true の場合、フレームワークによって`DrawThemeBackground`EBP_SPECIALGROUPBACKGROUND フラグを使用します。

##  <a name="m_lsttasks"></a>  CMFCTasksPaneTaskGroup::m_lstTasks

タスクの内部一覧に含まれています。

```
CObList m_lstTasks;
```

### <a name="remarks"></a>Remarks

この一覧に、呼び出す[::addtask](../../mfc/reference/cmfctaskspane-class.md#addtask)します。

##  <a name="m_rect"></a>  CMFCTasksPaneTaskGroup::m_rect

グループ キャプションの外接する四角形を指定します。

```
CRect m_rect;
```

### <a name="remarks"></a>Remarks

この値は、フレームワークによって自動的に計算されます。

##  <a name="m_rectgroup"></a>  CMFCTasksPaneTaskGroup::m_rectGroup

グループの外接する四角形を指定します。

```
CRect m_rectGroup;
```

### <a name="remarks"></a>Remarks

この値は、フレームワークによって自動的に計算されます。

##  <a name="m_strname"></a>  CMFCTasksPaneTaskGroup::m_strName

グループの名前を指定します。

```
CString m_strName;
```

### <a name="remarks"></a>Remarks

この値が空の場合は、グループ キャプションが表示されないと、グループを折りたたむことができません。

##  <a name="setaccdata"></a>  CMFCTasksPaneTaskGroup::SetACCData

現在のタスク グループのユーザー補助データを決定します。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>パラメーター

*pParent*<br/>
[in]現在のタスク グループの親ウィンドウを表します。

*data*<br/>
[out]型のオブジェクト`CAccessibilityData`の現在のタスク グループのユーザー補助データに設定されます。

### <a name="return-value"></a>戻り値

TRUE の場合、*データ*パラメーターが正常に現在のタスク グループのユーザー補助データと共に設定されている場合は FALSE。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTasksPane クラス](../../mfc/reference/cmfctaskspane-class.md)<br/>
[CMFCTasksPaneTask クラス](../../mfc/reference/cmfctaskspanetask-class.md)<br/>
[CMFCOutlookBar クラス](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)
