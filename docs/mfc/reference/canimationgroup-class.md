---
title: CAnimationGroup クラス
ms.date: 03/27/2019
f1_keywords:
- CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::Animate
- AFXANIMATIONCONTROLLER/CAnimationGroup::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationGroup::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::Schedule
- AFXANIMATIONCONTROLLER/CAnimationGroup::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutoclearTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstKeyFrames
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pStoryboard
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pParentController
helpviewer_keywords:
- CAnimationGroup [MFC], CAnimationGroup
- CAnimationGroup [MFC], Animate
- CAnimationGroup [MFC], ApplyTransitions
- CAnimationGroup [MFC], FindAnimationObject
- CAnimationGroup [MFC], GetGroupID
- CAnimationGroup [MFC], RemoveKeyframes
- CAnimationGroup [MFC], RemoveTransitions
- CAnimationGroup [MFC], Schedule
- CAnimationGroup [MFC], SetAutodestroyTransitions
- CAnimationGroup [MFC], AddKeyframes
- CAnimationGroup [MFC], AddTransitions
- CAnimationGroup [MFC], CreateTransitions
- CAnimationGroup [MFC], m_bAutoclearTransitions
- CAnimationGroup [MFC], m_bAutodestroyAnimationObjects
- CAnimationGroup [MFC], m_bAutodestroyKeyframes
- CAnimationGroup [MFC], m_lstAnimationObjects
- CAnimationGroup [MFC], m_lstKeyFrames
- CAnimationGroup [MFC], m_pStoryboard
- CAnimationGroup [MFC], m_nGroupID
- CAnimationGroup [MFC], m_pParentController
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
ms.openlocfilehash: 32b2adfee2a36139a11caa12fa98bd240b0732dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152076"
---
# <a name="canimationgroup-class"></a>CAnimationGroup クラス

アニメーション ストーリー ボードをアニメーション オブジェクト、および遷移アニメーションを定義するアニメーション グループを実装しています。

## <a name="syntax"></a>構文

```
class CAnimationGroup;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|アニメーションのグループを作成します。|
|[CAnimationGroup:: ~ CAnimationGroup](#_dtorcanimationgroup)|デストラクターです。 アニメーションのグループが破棄されるときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationGroup::Animate](#animate)|グループをアニメーション化します。|
|[CAnimationGroup::ApplyTransitions](#applytransitions)|アニメーション オブジェクトへの遷移を適用します。|
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|指定したアニメーション変数を含むアニメーション オブジェクトを検索します。|
|[CAnimationGroup::GetGroupID](#getgroupid)|GroupID を返します。|
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|削除し、必要に応じて、アニメーションのグループに属しているすべてのキーフレームを破棄します。|
|[CAnimationGroup::RemoveTransitions](#removetransitions)|アニメーションのグループに属するアニメーション オブジェクトからの遷移を削除します。|
|[CAnimationGroup::Schedule](#schedule)|指定された時刻にアニメーションをスケジュールします。|
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|自動的にグループ化に属するすべてのアニメーション オブジェクトの遷移を破棄するように指示します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationGroup::AddKeyframes](#addkeyframes)|ストーリー ボードにキーフレームを追加するためのヘルパーです。|
|[CAnimationGroup::AddTransitions](#addtransitions)|ストーリー ボードへの遷移を追加するためのヘルパーです。|
|[CAnimationGroup::CreateTransitions](#createtransitions)|遷移の COM オブジェクトを作成するためのヘルパーです。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|グループに属するアニメーション オブジェクトからの遷移をクリアする方法を指定します。 このメンバーが TRUE の場合、アニメーションがスケジュールされているときに、遷移に自動的に削除されます。 それ以外の場合は、遷移を手動で削除する必要があります。|
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|アニメーション オブジェクトを破棄する方法を指定します。 このパラメーターが TRUE の場合、グループが破棄されるときに、アニメーション オブジェクトが自動的に破棄されます。 それ以外の場合のアニメーション オブジェクトを手動で破壊する必要があります。 既定値は FALSE です。 新しい演算子をグループに属しているすべてのアニメーション オブジェクトが動的に割り当てられる場合にのみ、この値を TRUE に設定します。|
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|キーフレームを破棄する方法を指定します。 すべてのキーフレームが削除され、破棄されます。 この値が TRUE の場合それ以外の場合のみが一覧から削除されます。 既定値は TRUE です。|
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|アニメーション オブジェクトの一覧が含まれています。|
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|キーフレームの一覧が含まれています。|
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|アニメーションのストーリー ボードへのポインター。 このポインターは、アニメーションでの呼び出し後にのみ有効です。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|アニメーションのグループの一意の識別子。|
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|このグループに属しているアニメーション コント ローラーへのポインター。|

## <a name="remarks"></a>Remarks

アニメーション グループは、CAnimationController::AddAnimationObject を使用してアニメーション オブジェクトを追加するときにも、アニメーション コント ローラー (CAnimationController) によって自動的に作成されます。 アニメーション、グループは、GroupID で、通常は、アニメーション グループ操作をパラメーターとして扱われますによって識別されます。 GroupID は、新しいアニメーション グループに追加する最初のアニメーション オブジェクトから取得されます。 CAnimationController::AnimateGroup を呼び出すし、パブリック メンバー m_pStoryboard を介してアクセスできるようにカプセル化されたアニメーション ストーリー ボードが作成されます。

## <a name="inheritance-hierarchy"></a>継承階層

`CAnimationGroup`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="_dtorcanimationgroup"></a>  CAnimationGroup::~CAnimationGroup

デストラクターです。 アニメーションのグループが破棄されるときに呼び出されます。

```
~CAnimationGroup();
```

##  <a name="addkeyframes"></a>  CAnimationGroup::AddKeyframes

ストーリー ボードにキーフレームを追加するためのヘルパーです。

```
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>パラメーター

*pStoryboard*<br/>
ストーリー ボード COM オブジェクトへのポインター。

*bAddDeep*<br/>
このメソッドが他のキーフレームに依存しているストーリー ボードのキーフレームを追加する必要があるかどうかを指定します。

##  <a name="addtransitions"></a>  CAnimationGroup::AddTransitions

ストーリー ボードへの遷移を追加するためのヘルパーです。

```
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>パラメーター

*pStoryboard*<br/>
ストーリー ボード COM オブジェクトへのポインター。

*bDependOnKeyframes*

##  <a name="animate"></a>  CAnimationGroup::Animate

グループをアニメーション化します。

```
BOOL Animate(
    IUIAnimationManager* pManager,
    IUIAnimationTimer* pTimer,
    BOOL bScheduleNow);
```

### <a name="parameters"></a>パラメーター

*pManager*<br/>
*pTimer*
*bScheduleNow*

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

このメソッドは、内部のストーリー ボードを作成、作成し、遷移を適用したうえでと bScheduleNow が TRUE の場合、アニメーションのスケジュールを設定します。 BScheduleNow が FALSE の場合は、指定された時刻にアニメーションを開始するスケジュールを呼び出す必要があります。

##  <a name="applytransitions"></a>  CAnimationGroup::ApplyTransitions

アニメーション オブジェクトへの遷移を適用します。

```
void ApplyTransitions();
```

### <a name="remarks"></a>Remarks

このメソッドは、ストーリー ボードが作成されていないかどうかはデバッグ モードでアサートします。 最初に、すべての遷移を作成し、「静的」キーフレーム (オフセットに依存するキーフレーム) を追加します、キーフレームに依存しない遷移を追加します、遷移によってキーフレームと他のキーフレームを追加しますおよびキーフレームに依存する遷移を最後に追加します.

##  <a name="canimationgroup"></a>  CAnimationGroup::CAnimationGroup

アニメーションのグループを作成します。

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>パラメーター

*pParentController*<br/>
グループを作成するアニメーション コント ローラーへのポインター。

*nGroupID*<br/>
GroupID を指定します。

##  <a name="createtransitions"></a>  CAnimationGroup::CreateTransitions

遷移の COM オブジェクトを作成するためのヘルパーです。

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>戻り値

TRUE では、メソッドが成功した場合は FALSE です。

##  <a name="findanimationobject"></a>  CAnimationGroup::FindAnimationObject

指定したアニメーション変数を含むアニメーション オブジェクトを検索します。

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>パラメーター

*pVariable*<br/>
アニメーション変数へのポインター。

### <a name="return-value"></a>戻り値

アニメーション オブジェクト、またはアニメーション オブジェクトが見つからない場合は NULL へのポインター。

##  <a name="getgroupid"></a>  CAnimationGroup::GetGroupID

GroupID を返します。

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>戻り値

グループの識別子です。

##  <a name="m_bautocleartransitions"></a>  CAnimationGroup::m_bAutoclearTransitions

グループに属するアニメーション オブジェクトからの遷移をクリアする方法を指定します。 このメンバーが TRUE の場合、アニメーションがスケジュールされているときに、遷移に自動的に削除されます。 それ以外の場合は、遷移を手動で削除する必要があります。

```
BOOL m_bAutoclearTransitions;
```

##  <a name="m_bautodestroyanimationobjects"></a>  CAnimationGroup::m_bAutodestroyAnimationObjects

アニメーション オブジェクトを破棄する方法を指定します。 このパラメーターが TRUE の場合、グループが破棄されるときに、アニメーション オブジェクトが自動的に破棄されます。 それ以外の場合のアニメーション オブジェクトを手動で破壊する必要があります。 既定値は FALSE です。 新しい演算子をグループに属しているすべてのアニメーション オブジェクトが動的に割り当てられる場合にのみ、この値を TRUE に設定します。

```
BOOL m_bAutodestroyAnimationObjects;
```

##  <a name="m_bautodestroykeyframes"></a>  CAnimationGroup::m_bAutodestroyKeyframes

キーフレームを破棄する方法を指定します。 すべてのキーフレームが削除され、破棄されます。 この値が TRUE の場合それ以外の場合のみが一覧から削除されます。 既定値は TRUE です。

```
BOOL m_bAutodestroyKeyframes;
```

##  <a name="m_lstanimationobjects"></a>  CAnimationGroup::m_lstAnimationObjects

アニメーション オブジェクトの一覧が含まれています。

```
CObList m_lstAnimationObjects;
```

##  <a name="m_lstkeyframes"></a>  CAnimationGroup::m_lstKeyFrames

キーフレームの一覧が含まれています。

```
CObList m_lstKeyFrames;
```

##  <a name="m_ngroupid"></a>  CAnimationGroup::m_nGroupID

アニメーションのグループの一意の識別子。

```
UINT32 m_nGroupID;
```

##  <a name="m_pparentcontroller"></a>  CAnimationGroup::m_pParentController

このグループに属しているアニメーション コント ローラーへのポインター。

```
CAnimationController* m_pParentController;
```

##  <a name="m_pstoryboard"></a>  CAnimationGroup::m_pStoryboard

アニメーションのストーリー ボードへのポインター。 このポインターは、アニメーションでの呼び出し後にのみ有効です。

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

##  <a name="removekeyframes"></a>  CAnimationGroup::RemoveKeyframes

削除し、必要に応じて、アニメーションのグループに属しているすべてのキーフレームを破棄します。

```
void RemoveKeyframes();
```

### <a name="remarks"></a>Remarks

M_bAutodestroyKeyframes メンバーが TRUE の場合のキーフレームが削除され、破棄されると、それ以外の場合、キーフレームをだけキーフレームの内部リストから削除します。

##  <a name="removetransitions"></a>  CAnimationGroup::RemoveTransitions

アニメーションのグループに属するアニメーション オブジェクトからの遷移を削除します。

```
void RemoveTransitions();
```

### <a name="remarks"></a>Remarks

M_bAutoclearTransitions フラグが TRUE に設定されている場合、このメソッドは、グループに属しているすべてのアニメーション オブジェクトをループし、CAnimationObject::ClearTransitions(FALSE) を呼び出します。

##  <a name="schedule"></a>  CAnimationGroup::Schedule

指定された時刻にアニメーションをスケジュールします。

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>パラメーター

*pTimer*<br/>
アニメーション タイマーへのポインター。

*time*<br/>
アニメーションをスケジュールする時間を指定します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。FALSE が、メソッドが失敗した場合、またはアニメーション化する場合は、bScheduleNow を FALSE に設定をしない呼び出されました。

### <a name="remarks"></a>Remarks

指定された時刻にアニメーションをスケジュールするには、この関数を呼び出します。 BScheduleNow を FALSE に設定を最初に、アニメーションを呼び出す必要があります。

##  <a name="setautodestroytransitions"></a>  CAnimationGroup::SetAutodestroyTransitions

自動的にグループ化に属するすべてのアニメーション オブジェクトの遷移を破棄するように指示します。

```
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>パラメーター

*bAutoDestroy*<br/>
遷移を破棄する方法を指定します。

### <a name="remarks"></a>Remarks

この値をスタックに遷移を割り当てた場合にのみ FALSE に設定します。 既定値は TRUE、したがってことが推奨新しい演算子を使用して移行のオブジェクトを割り当てます。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
