---
title: CMFCTasksPaneTask クラス
ms.date: 11/19/2018
f1_keywords:
- CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTask::m_bAutoDestroyWindow
- AFXTASKSPANE/CMFCTasksPaneTask::m_bIsBold
- AFXTASKSPANE/CMFCTasksPaneTask::m_dwUserData
- AFXTASKSPANE/CMFCTasksPaneTask::m_hwndTask
- AFXTASKSPANE/CMFCTasksPaneTask::m_nIcon
- AFXTASKSPANE/CMFCTasksPaneTask::m_nWindowHeight
- AFXTASKSPANE/CMFCTasksPaneTask::m_pGroup
- AFXTASKSPANE/CMFCTasksPaneTask::m_rect
- AFXTASKSPANE/CMFCTasksPaneTask::m_strName
- AFXTASKSPANE/CMFCTasksPaneTask::m_uiCommandID
helpviewer_keywords:
- CMFCTasksPaneTask [MFC], CMFCTasksPaneTask
- CMFCTasksPaneTask [MFC], SetACCData
- CMFCTasksPaneTask [MFC], m_bAutoDestroyWindow
- CMFCTasksPaneTask [MFC], m_bIsBold
- CMFCTasksPaneTask [MFC], m_dwUserData
- CMFCTasksPaneTask [MFC], m_hwndTask
- CMFCTasksPaneTask [MFC], m_nIcon
- CMFCTasksPaneTask [MFC], m_nWindowHeight
- CMFCTasksPaneTask [MFC], m_pGroup
- CMFCTasksPaneTask [MFC], m_rect
- CMFCTasksPaneTask [MFC], m_strName
- CMFCTasksPaneTask [MFC], m_uiCommandID
ms.assetid: c5a7513b-cd8f-4e2e-b16f-650e1fe30954
ms.openlocfilehash: 95a2e4f2a1f2e3344936af33fb2258b496b1be93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218709"
---
# <a name="cmfctaskspanetask-class"></a>CMFCTasksPaneTask クラス

`CMFCTasksPaneTask`クラスは、作業ウィンドウ コントロールのタスクを表すヘルパー クラス ( [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md))。 タスク オブジェクトは、タスク グループ内の項目を表します ( [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md))。 各タスクには、ユーザーがタスク名の左側に表示されるタスクやアイコンをクリックしたときにフレームワークが実行するコマンドを設定できます。

## <a name="syntax"></a>構文

```
class CMFCTasksPaneTask : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCTasksPaneTask::CMFCTasksPaneTask](#cmfctaskspanetask)|作成し、初期化、`CMFCTasksPaneTask`オブジェクト。|
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCTasksPaneTask::SetACCData](#setaccdata)|ユーザー補助データを現在のタスクを決定します。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CMFCTasksPaneTask::m_bAutoDestroyWindow](#m_bautodestroywindow)|タスク ウィンドウが自動的に破棄されるかどうかを判断します。|
|[CMFCTasksPaneTask::m_bIsBold](#m_bisbold)|フレームワークは太字でタスクのラベルを描画するかどうかを判断します。|
|[CMFCTasksPaneTask::m_dwUserData](#m_dwuserdata)|フレームワークは、タスクに関連付けるユーザー定義のデータが含まれています。 タスクに関連付けられているデータがあるない場合は、0 に設定します。|
|[CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)|タスク ウィンドウのハンドル。|
|[CMFCTasksPaneTask::m_nIcon](#m_nicon)|フレームワークは、タスクの横に表示するイメージのイメージ リスト内のインデックス。|
|[CMFCTasksPaneTask::m_nWindowHeight](#m_nwindowheight)|タスク ウィンドウの高さ。 タスク ウィンドウのタスクがない場合は、この値は 0 です。|
|[CMFCTasksPaneTask::m_pGroup](#m_pgroup)|ポインター、`CMFCTasksPaneTaskGroup`にこのタスクが属しています。|
|[CMFCTasksPaneTask::m_rect](#m_rect)|タスクの外接する四角形を指定します。|
|[CMFCTasksPaneTask::m_strName](#m_strname)|タスクの名前。|
|[CMFCTasksPaneTask::m_uiCommandID](#m_uicommandid)|ユーザーがタスクをクリックしたときにフレームワークが実行されるコマンドのコマンド ID を指定します。 この値が有効なコマンド ID でない場合は、タスクが単純なラベルとして扱われます。|

## <a name="remarks"></a>Remarks

次の図は、次の 3 つのタスクが含まれているタスク グループを示しています。

![展開されたタスク グループ](../../mfc/reference/media/nexttaskgrpexpand.png "展開されたタスク グループ")

> [!NOTE]
> タスクが有効なコマンド ID を持たない場合は、単純なラベルとして扱われます。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxTasksPane.h

##  <a name="cmfctaskspanetask"></a>  CMFCTasksPaneTask::CMFCTasksPaneTask

作成し、初期化、`CMFCTasksPaneTask`オブジェクト。

```
CMFCTasksPaneTask(
    CMFCTasksPaneTaskGroup* pGroup,
    LPCTSTR lpszName,
    int nIcon,
    UINT uiCommandID,
    DWORD dwUserData = 0,
    HWND hwndTask = NULL,
    BOOL bAutoDestroyWindow = FALSE,
    int nWindowHeight = 0);
```

### <a name="parameters"></a>パラメーター

*pGroup*<br/>
指定します、 [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)タスクが属しています。

*lpszName*<br/>
タスクの名前を指定します。

*nIcon*<br/>
イメージ リストで、タスクのイメージのインデックスを指定します。

*uiCommandID*<br/>
タスクがクリックされたときに実行されるコマンドのコマンド ID を指定します。

*dwUserData*<br/>
ユーザー定義データ。

*hwndTask*<br/>
タスク ウィンドウを識別するハンドルを指定します。

*bAutoDestroyWindow*<br/>
TRUE の場合、タスク ウィンドウを自動的に破棄されます。

*nWindowHeight*<br/>
タスク ウィンドウの高さを指定します。

### <a name="remarks"></a>Remarks

##  <a name="m_bautodestroywindow"></a>  CMFCTasksPaneTask::m_bAutoDestroyWindow

タスク ウィンドウが自動的に破棄されるかどうかを判断します。

```
BOOL m_bAutoDestroyWindow;
```

### <a name="remarks"></a>Remarks

タスク ウィンドウをことを指定する場合は TRUE に設定 ( [CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)) に自動的に。 それ以外の場合、FALSE に破棄する必要があります。

##  <a name="m_bisbold"></a>  CMFCTasksPaneTask::m_bIsBold

タスクのラベルが太字のテキストで描画されるかどうかを判断します。

```
BOOL m_bIsBold;
```

### <a name="remarks"></a>Remarks

このメンバーを表示する場合は true、タスクのラベルのテキストを太字に設定します。

##  <a name="m_dwuserdata"></a>  CMFCTasksPaneTask::m_dwUserData

タスクに関連付けられているユーザー定義のデータが含まれています。 データが、タスクに関連付けられていない場合は、0 に設定します。

```
DWORD m_dwUserData;
```

### <a name="remarks"></a>Remarks

##  <a name="m_hwndtask"></a>  CMFCTasksPaneTask::m_hwndTask

タスク ウィンドウのハンドル。

```
HWND m_hwndTask;
```

### <a name="remarks"></a>Remarks

タスク ウィンドウを追加するには、呼び出す[CMFCTasksPane::AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow)します。

##  <a name="m_nicon"></a>  CMFCTasksPaneTask::m_nIcon

指定したタスクの横に表示されるイメージを識別するイメージ リスト内のインデックス位置。

```
int m_nIcon;
```

### <a name="remarks"></a>Remarks

イメージ リストの設定[CMFCTasksPane::SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist)します。

設定`m_nIcon`に画像がない場合、タスクを表示したい場合は-1。

##  <a name="m_nwindowheight"></a>  CMFCTasksPaneTask::m_nWindowHeight

タスク ウィンドウの高さ。 タスク ウィンドウのタスクがない場合は、この値は 0 です。

```
int m_nWindowHeight;
```

### <a name="remarks"></a>Remarks

##  <a name="m_pgroup"></a>  CMFCTasksPaneTask::m_pGroup

ポインター、 [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)このタスクが属しています。

```
CMFCTasksPaneTaskGroup* m_pGroup;
```

### <a name="remarks"></a>Remarks

親グループのすべてのタスクが必要です。 呼び出すことによって、タスク ペインにグループを追加する[cmfctaskspane::addgroup](../../mfc/reference/cmfctaskspane-class.md#addgroup)します。

##  <a name="m_rect"></a>  CMFCTasksPaneTask::m_rect

タスクの外接する四角形を指定します。

```
CRect m_rect;
```

### <a name="remarks"></a>Remarks

この値は、タスクが描画されるときにフレームワークによって計算されます。

##  <a name="m_strname"></a>  CMFCTasksPaneTask::m_strName

タスクの名前。

```
CString m_strName;
```

### <a name="remarks"></a>Remarks

##  <a name="m_uicommandid"></a>  CMFCTasksPaneTask::m_uiCommandID

ユーザーがタスクをクリックしたときに実行されるコマンドのコマンド ID を指定します。 この値が有効なコマンド ID でない場合は、タスクが単純なラベルとして扱われます。

```
UINT m_uiCommandID;
```

### <a name="remarks"></a>Remarks

##  <a name="setaccdata"></a>  CMFCTasksPaneTask::SetACCData

ユーザー補助データを現在のタスクを決定します。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>パラメーター

*pParent*<br/>
[in]現在のタスクの親ウィンドウを表します。

*data*<br/>
[out]型のオブジェクト`CAccessibilityData`現在のタスクのユーザー補助データに設定されます。

### <a name="return-value"></a>戻り値

TRUE の場合、*データ*パラメーターが正常に現在のタスクのユーザー補助データと共に設定されている場合は FALSE。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)
