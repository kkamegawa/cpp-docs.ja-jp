---
title: CAnimationController クラス
ms.date: 03/27/2019
f1_keywords:
- CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::AddAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::AddKeyframeToGroup
- AFXANIMATIONCONTROLLER/CAnimationController::AnimateGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CleanUpGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CreateKeyframe
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationManagerEvent
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnablePriorityComparisonHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnableStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::GetKeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionLibrary
- AFXANIMATIONCONTROLLER/CAnimationController::IsAnimationInProgress
- AFXANIMATIONCONTROLLER/CAnimationController::IsValid
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnBeforeAnimationStart
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCancel
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCompress
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityConclude
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityTrim
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAllAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationController::ScheduleGroup
- AFXANIMATIONCONTROLLER/CAnimationController::SetRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::UpdateAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::OnAfterSchedule
- AFXANIMATIONCONTROLLER/CAnimationController::gkeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::m_bIsValid
- AFXANIMATIONCONTROLLER/CAnimationController::m_lstAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::m_pRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionLibrary
helpviewer_keywords:
- CAnimationController [MFC], CAnimationController
- CAnimationController [MFC], AddAnimationObject
- CAnimationController [MFC], AddKeyframeToGroup
- CAnimationController [MFC], AnimateGroup
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], CreateKeyframe
- CAnimationController [MFC], EnableAnimationManagerEvent
- CAnimationController [MFC], EnableAnimationTimerEventHandler
- CAnimationController [MFC], EnablePriorityComparisonHandler
- CAnimationController [MFC], EnableStoryboardEventHandler
- CAnimationController [MFC], FindAnimationGroup
- CAnimationController [MFC], FindAnimationObject
- CAnimationController [MFC], GetKeyframeStoryboardStart
- CAnimationController [MFC], GetUIAnimationManager
- CAnimationController [MFC], GetUIAnimationTimer
- CAnimationController [MFC], GetUITransitionFactory
- CAnimationController [MFC], GetUITransitionLibrary
- CAnimationController [MFC], IsAnimationInProgress
- CAnimationController [MFC], IsValid
- CAnimationController [MFC], OnAnimationIntegerValueChanged
- CAnimationController [MFC], OnAnimationManagerStatusChanged
- CAnimationController [MFC], OnAnimationTimerPostUpdate
- CAnimationController [MFC], OnAnimationTimerPreUpdate
- CAnimationController [MFC], OnAnimationTimerRenderingTooSlow
- CAnimationController [MFC], OnAnimationValueChanged
- CAnimationController [MFC], OnBeforeAnimationStart
- CAnimationController [MFC], OnHasPriorityCancel
- CAnimationController [MFC], OnHasPriorityCompress
- CAnimationController [MFC], OnHasPriorityConclude
- CAnimationController [MFC], OnHasPriorityTrim
- CAnimationController [MFC], OnStoryboardStatusChanged
- CAnimationController [MFC], OnStoryboardUpdated
- CAnimationController [MFC], RemoveAllAnimationGroups
- CAnimationController [MFC], RemoveAnimationGroup
- CAnimationController [MFC], RemoveAnimationObject
- CAnimationController [MFC], RemoveTransitions
- CAnimationController [MFC], ScheduleGroup
- CAnimationController [MFC], SetRelatedWnd
- CAnimationController [MFC], UpdateAnimationManager
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], OnAfterSchedule
- CAnimationController [MFC], gkeyframeStoryboardStart
- CAnimationController [MFC], m_bIsValid
- CAnimationController [MFC], m_lstAnimationGroups
- CAnimationController [MFC], m_pAnimationManager
- CAnimationController [MFC], m_pAnimationTimer
- CAnimationController [MFC], m_pRelatedWnd
- CAnimationController [MFC], m_pTransitionFactory
- CAnimationController [MFC], m_pTransitionLibrary
ms.assetid: ed294c98-695e-40a6-b940-33ef1d40aa6b
ms.openlocfilehash: 9039d44d9ef36a47c11b3ecaddf232ad427727c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507652"
---
# <a name="canimationcontroller-class"></a>CAnimationController クラス

アニメーションを作成および管理するための中心的なインターフェイスを提供する、アニメーション コントローラーを実装します。

## <a name="syntax"></a>構文

```
class CAnimationController : public CObject;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAnimationController:: CAnimationController](#canimationcontroller)|アニメーションコントローラーを構築します。|
|[CAnimationController:: ~ CAnimationController](#_dtorcanimationcontroller)|デストラクターです。 アニメーションコントローラーオブジェクトが破棄されているときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationController::AddAnimationObject](#addanimationobject)|アニメーションコントローラーに属するグループにアニメーションオブジェクトを追加します。|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|グループにキーフレームを追加します。|
|[CAnimationController:: AnimateGroup](#animategroup)|アニメーションを実行するグループを準備し、必要に応じてスケジュールをスケジュールします。|
|[CAnimationController:: CleanUpGroup](#cleanupgroup)|オーバーロードされます。 アニメーションがスケジュールされているときにグループをクリーンアップするために、フレームワークによって呼び出されます。|
|[CAnimationController::CreateKeyframe](#createkeyframe)|オーバーロードされます。 遷移に依存するキーフレームを作成し、指定したグループに追加します。|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|アニメーションマネージャーの状態が変化したときに呼び出すハンドラーを設定または解放します。|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|タイミングイベントのハンドラーとタイミングの更新のハンドラーを設定または解放します。|
|[CAnimationController:: EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|スケジュールされたストーリーボードをキャンセル、終了、トリミング、または圧縮できるかどうかを判断するために呼び出す優先順位比較ハンドラーを設定または解放します。|
|[CAnimationController:: EnableStoryboardEventHandler](#enablestoryboardeventhandler)|ストーリーボードの状態イベントと更新イベントのハンドラーを設定または解放します。|
|[CAnimationController:: Findをグループ化します。](#findanimationgroup)|オーバーロードされます。 ストーリーボードによってアニメーショングループを検索します。|
|[CAnimationController:: Findアニメーションオブジェクト](#findanimationobject)|指定されたアニメーション変数を含むアニメーションオブジェクトを検索します。|
|[CAnimationController:: GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|ストーリーボードの開始を識別するキーフレームを返します。|
|[CAnimationController:: GetUIAnimationManager](#getuianimationmanager)|カプセル化された Iui' Manager オブジェクトへのアクセスを提供します。|
|[CAnimationController:: GetUIAnimationTimer](#getuianimationtimer)|カプセル化された Iuiアニメーションタイマーオブジェクトへのアクセスを提供します。|
|[CAnimationController:: GetUITransitionFactory](#getuitransitionfactory)|Iui、遷移ライブラリの作成に失敗した場合は、Iui' の遷移のファクトリインターフェイスまたは NULL へのポインター。|
|[CAnimationController:: GetUITransitionLibrary](#getuitransitionlibrary)|カプセル化された Iui' オブジェクトへのアクセスを提供します。|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|少なくとも1つのグループがアニメーションを再生しているかどうかを示します。|
|[CAnimationController:: IsValid](#isvalid)|アニメーションコントローラーが有効かどうかを示します。|
|[CAnimationController:: OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|アニメーション変数の整数値が変更されたときにフレームワークによって呼び出されます。|
|[CAnimationController:: Onアニメーションマネージャー Statuschanged](#onanimationmanagerstatuschanged)|アニメーションマネージャーからの StatusChanged イベントに応答して、フレームワークによって呼び出されます。|
|[CAnimationController:: Onアニメーション Timerpostupdate](#onanimationtimerpostupdate)|アニメーションの更新が完了した後にフレームワークによって呼び出されます。|
|[CAnimationController:: Onアニメーション Timerpreupdate](#onanimationtimerpreupdate)|アニメーションの更新が開始される前にフレームワークによって呼び出されます。|
|[CAnimationController:: OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|アニメーションのレンダリングフレームレートが望ましいフレームレートの最小値を下回ると、フレームワークによって呼び出されます。|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|アニメーション変数の値が変更されたときにフレームワークによって呼び出されます。|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|アニメーションがスケジュールされる直前に、フレームワークによって呼び出されます。|
|[CAnimationController:: Onhas優先順位の取り消し](#onhasprioritycancel)|スケジュールの競合を解決するために、フレームワークによって呼び出されます。|
|[CAnimationController:: Onhasの圧縮](#onhasprioritycompress)|スケジュールの競合を解決するために、フレームワークによって呼び出されます。|
|[CAnimationController:: Onhas優先順位の結論](#onhaspriorityconclude)|スケジュールの競合を解決するために、フレームワークによって呼び出されます。|
|[CAnimationController:: Onhas優先順位 Trim](#onhasprioritytrim)|スケジュールの競合を解決するために、フレームワークによって呼び出されます。|
|[CAnimationController:: OnStoryboardStatusChanged](#onstoryboardstatuschanged)|ストーリーボードの状態が変化したときにフレームワークによって呼び出されます。|
|[CAnimationController:: OnStoryboardUpdated](#onstoryboardupdated)|ストーリーボードが更新されたときにフレームワークによって呼び出されます。|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|アニメーションコントローラーからすべてのアニメーショングループを削除します。|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|アニメーションコントローラーから、指定された ID を持つアニメーショングループを削除します。|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|アニメーションコントローラーからアニメーションオブジェクトを削除します。|
|[CAnimationController::RemoveTransitions](#removetransitions)|指定したグループに属するアニメーションオブジェクトからの切り替え効果を削除します。|
|[CAnimationController:: ScheduleGroup](#schedulegroup)|アニメーションをスケジュールします。|
|[CAnimationController:: SetRelatedWnd](#setrelatedwnd)|アニメーションコントローラーとウィンドウの間のリレーションシップを確立します。|
|[CAnimationController:: Updateアニメーションマネージャー](#updateanimationmanager)|アニメーションマネージャーに対して、すべてのアニメーション変数の値を更新するように指示します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationController:: CleanUpGroup](#cleanupgroup)|オーバーロードされます。 グループをクリーンアップするヘルパー。|
|[CAnimationController:: OnAfterSchedule](#onafterschedule)|指定したグループのアニメーションがスケジュールされた直後に、フレームワークによって呼び出されます。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CAnimationController:: gkeyframeStoryboardStart](#g_keyframestoryboardstart)|ストーリーボードの開始を表すキーフレーム。|
|[CAnimationController:: m_bIsValid](#m_bisvalid)|アニメーションコントローラーが有効かどうかを指定します。 現在の OS が Windows アニメーション API をサポートしていない場合、このメンバーは FALSE に設定されます。|
|[CAnimationController:: m_lstAnimationGroups](#m_lstanimationgroups)|このアニメーションコントローラーに属するアニメーショングループのリスト。|
|[CAnimationController:: m_pAnimationManager](#m_panimationmanager)|アニメーションマネージャー COM オブジェクトへのポインターを格納します。|
|[CAnimationController:: m_pAnimationTimer](#m_panimationtimer)|アニメーションタイマー COM オブジェクトへのポインターを格納します。|
|[CAnimationController:: m_pRelatedWnd](#m_prelatedwnd)|アニメーションマネージャーの状態が変更されたとき、または更新後のイベントが発生したときに自動的に再描画できる、関連する CWnd オブジェクトへのポインター。 NULL を指定できます。|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|遷移ファクトリ COM オブジェクトへのポインターを格納します。|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|遷移ライブラリ COM オブジェクトへのポインターを格納します。|

## <a name="remarks"></a>Remarks

CAnimationController クラスは、アニメーションを管理するキークラスです。 アプリケーションでアニメーションコントローラーのインスタンスを1つ以上作成し、必要に応じて、CAnimationController:: SetRelatedWnd を使用して、アニメーションコントローラーのインスタンスを CWnd オブジェクトに接続することもできます。 この接続は、アニメーションマネージャーの状態が変化したとき、またはアニメーションタイマーが更新されたときに、関連ウィンドウに WM_PAINT メッセージを自動的に送信するために必要です。 この関係を有効にしない場合は、アニメーションを手動で表示するウィンドウを再描画する必要があります。 このため、CAnimationController からクラスを派生させ、OnAnimationManagerStatusChanged および/または Onanimationmanagerstatuschanged をオーバーライドし、必要に応じて1つ以上のウィンドウを無効にすることができます。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="_dtorcanimationcontroller"></a>CAnimationController:: ~ CAnimationController

デストラクターです。 アニメーションコントローラーオブジェクトが破棄されているときに呼び出されます。

```
virtual ~CAnimationController(void);
```

##  <a name="addanimationobject"></a>CAnimationController:: Addアニメーションオブジェクト

アニメーションコントローラーに属するグループにアニメーションオブジェクトを追加します。

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>パラメーター

*pObject*<br/>
アニメーションオブジェクトへのポインター。

### <a name="return-value"></a>戻り値

関数が成功した場合に pObject が追加された既存のまたは新しいアニメーショングループへのポインター。PObject が、別のアニメーションコントローラーに属しているグループに既に追加されている場合は NULL です。

### <a name="remarks"></a>Remarks

アニメーションオブジェクトをアニメーションコントローラーに追加するには、このメソッドを呼び出します。 オブジェクトは、オブジェクトの GroupID に従ってグループに追加されます (「CAnimationBaseObject:: SetID」を参照してください)。 アニメーションコントローラーは、指定された GroupID を使用して追加される最初のオブジェクトである場合、新しいグループを作成します。 アニメーションオブジェクトは、1つのアニメーションコントローラーにのみ追加できます。 オブジェクトを別のコントローラーに追加する必要がある場合は、まず Removeのオブジェクトを呼び出します。 既にグループに追加されているオブジェクトに対して新しい GroupID を使用して SetID を呼び出した場合、オブジェクトは古いグループから削除され、指定された ID を持つ別のグループに追加されます。

##  <a name="addkeyframetogroup"></a>  CAnimationController::AddKeyframeToGroup

グループにキーフレームを追加します。

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
グループ ID を指定します。

*pKeyframe*<br/>
キーフレームへのポインター。

### <a name="return-value"></a>戻り値

関数が成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

通常は、このメソッドを呼び出す必要はありません。代わりに、CAnimationController:: CreateKeyframe フレームを使用します。これにより、作成されたキーフレームが作成され、グループに自動的に追加されます。

##  <a name="animategroup"></a>  CAnimationController::AnimateGroup

アニメーションを実行するグループを準備し、必要に応じてスケジュールをスケジュールします。

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
GroupID を指定します。

*bScheduleNow*<br/>
アニメーションをすぐに実行するかどうかを指定します。

### <a name="return-value"></a>戻り値

アニメーションが正常にスケジュールされて実行された場合は TRUE。

### <a name="remarks"></a>Remarks

このメソッドは、ストーリーボードを作成し、アニメーション変数を追加し、切り替え効果を適用し、キーフレームを設定する実際の作業を行います。 BScheduleNow を FALSE に設定すると、スケジュールの遅延が発生する可能性があります。 この場合、指定したグループには、アニメーション用に設定されたストーリーボードが保持されます。 その時点で、ストーリーボード変数とアニメーション変数のイベントを設定できます。 実際にアニメーションを実行する必要がある場合は、CAnimationController:: ScheduleGroup を呼び出します。

##  <a name="canimationcontroller"></a>CAnimationController:: CAnimationController

アニメーションコントローラーを構築します。

```
CAnimationController(void);
```

##  <a name="cleanupgroup"></a>CAnimationController:: CleanUpGroup

アニメーションがスケジュールされているときにグループをクリーンアップするために、フレームワークによって呼び出されます。

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
GroupID を指定します。

*pGroup*<br/>
消去するアニメーショングループへのポインター。

### <a name="remarks"></a>Remarks

このメソッドは、指定されたグループからすべての遷移とキーフレームを削除します。これは、アニメーションがスケジュールされた後は関係がないためです。

##  <a name="createkeyframe"></a>  CAnimationController::CreateKeyframe

遷移に依存するキーフレームを作成し、指定したグループに追加します。

```
CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseTransition* pTransition);

CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
キーフレームを作成する対象グループの ID を指定します。

*pTransition*<br/>
遷移へのポインター。 この移行の完了後に、ストーリーボードにキーフレームが挿入されます。

*pKeyframe*<br/>
このキーフレームの基準キーフレームへのポインター。

*オフセット*<br/>
pKeyframe で指定した基準キーフレームからのオフセット (秒単位)。

### <a name="return-value"></a>戻り値

関数が正常に終了した場合は、新しく作成されたキーフレームへのポインター。

### <a name="remarks"></a>Remarks

返されたポインターを格納して、新しく作成されたキーフレームを他のキーフレームの基準にすることができます (2 番目のオーバーロードを参照)。 キーフレームで遷移を開始することもできます。CBaseTransition::SetKeyframes をご覧ください。 このようにして作成したキーフレームを削除する必要はありません。アニメーション グループによって自動的に削除されます。 キーフレームを他のキーフレームや遷移に基づいて作成する場合は注意し、循環参照が発生しないようにしてください。

##  <a name="enableanimationmanagerevent"></a>  CAnimationController::EnableAnimationManagerEvent

アニメーションマネージャーの状態が変化したときに呼び出すハンドラーを設定または解放します。

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
ハンドラーを設定するか、解放するかを指定します。

### <a name="return-value"></a>戻り値

ハンドラーが正常に設定または解放された場合は TRUE。

### <a name="remarks"></a>Remarks

ハンドラーが設定されている (有効になっている) 場合、アニメーションマネージャーの状態が変化したときに Onanimation Managerstatuschanged が呼び出されます。

##  <a name="enableanimationtimereventhandler"></a>  CAnimationController::EnableAnimationTimerEventHandler

タイミングイベントのハンドラーとタイミングの更新のハンドラーを設定または解放します。

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
ハンドラーを設定または解放するかどうかを指定します。

*idleBehavior*<br/>
タイマー更新ハンドラーのアイドル動作を指定します。

### <a name="return-value"></a>戻り値

ハンドラーが正常に設定または解放された場合は TRUE。このメソッドが、最初にハンドラーを解放せずに2回呼び出された場合、または他のエラーが発生した場合は FALSE。

### <a name="remarks"></a>Remarks

ハンドラーが設定されている (有効になっている) 場合、Windows アニメーション API は Onanimation Timerpreupdate、Onanimation Timerpostupdate、OnRenderingTooSlow メソッドを呼び出します。 Windows アニメーション API 更新ストーリーボードを許可するには、アニメーションタイマーを有効にする必要があります。 それ以外の場合は、すべてのアニメーション変数の値を更新するようにアニメーションマネージャーに指示するために、CAnimationController:: Updateanimation Manager を呼び出す必要があります。

##  <a name="enableprioritycomparisonhandler"></a>CAnimationController:: EnablePriorityComparisonHandler

スケジュールされたストーリーボードをキャンセル、終了、トリミング、または圧縮できるかどうかを判断するために呼び出す優先順位比較ハンドラーを設定または解放します。

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>パラメーター

*dwHandlerType*<br/>
設定または解放するハンドラーを指定する UI_ANIMATION_PHT_ フラグ (「解説」を参照) の組み合わせ。

### <a name="return-value"></a>戻り値

ハンドラーが正常に設定または解放された場合は TRUE。

### <a name="remarks"></a>Remarks

ハンドラーが設定されている (有効になっている) 場合、dwHandlerType に応じて、次の仮想メソッドが呼び出されます。Onhas優先順位、onhas優先順位、onhas優先度トリム、Onhas優先順位圧縮。 dwHandler は、次のフラグを組み合わせることができます。UI_ANIMATION_PHT_NONE すべてのハンドラー UI_ANIMATION_PHT_CANCEL-set Cancel comparison handler UI_ANIMATION_PHT_CONCLUDE-set 結論比較ハンドラ UI_ANIMATION_PHT_COMPRESS-set Compress comparison handler UI_ANIMATION_PHT_TRIMTrim 比較ハンドラー UI_ANIMATION_PHT_CANCEL_REMOVE-削除の取り消し比較ハンドラー UI_ANIMATION_PHT_CONCLUDE_REMOVE-削除の比較ハンドラー UI_ANIMATION_PHT_COMPRESS_REMOVE-削除の比較ハンドラー UI_ANIMATION_PHT_TRIM_REMOVE Trim 比較ハンドラーを削除します。

##  <a name="enablestoryboardeventhandler"></a>CAnimationController:: EnableStoryboardEventHandler

ストーリーボードの状態イベントと更新イベントのハンドラーを設定または解放します。

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
グループ ID を指定します。

*bEnable*<br/>
ハンドラーを設定するか、解放するかを指定します。

### <a name="return-value"></a>戻り値

ハンドラーが正常に設定または解放された場合は TRUE。指定されたアニメーショングループが見つかった場合、または指定したグループのアニメーションが開始されておらず、内部ストーリーボードが NULL の場合は FALSE。

### <a name="remarks"></a>Remarks

ハンドラーが設定されている (有効になっている) 場合、Windows アニメーション API は OnStoryboardStatusChanges と OnStoryboardUpdated の仮想メソッドを呼び出します。 ハンドラーは、指定されたアニメーショングループに対して CAnimationController:: Animate が呼び出された後に設定する必要があります。これは、カプセル化された Iuianimation Storyboard オブジェクトを作成するためです。

##  <a name="findanimationgroup"></a>  CAnimationController::FindAnimationGroup

グループ ID を使ってアニメーショングループを検索します。

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
GroupID を指定します。

*pStoryboard*<br/>
ストーリーボードへのポインター。

### <a name="return-value"></a>戻り値

アニメーショングループへのポインター。指定した ID を持つグループが見つからない場合は NULL。

### <a name="remarks"></a>Remarks

実行時にアニメーショングループを検索するには、このメソッドを使用します。 特定の GroupID を持つ最初のアニメーションオブジェクトがアニメーションコントローラーに追加されるときに、グループが作成され、アニメーショングループの内部リストに追加されます。

##  <a name="findanimationobject"></a>CAnimationController:: Findアニメーションオブジェクト

指定されたアニメーション変数を含むアニメーションオブジェクトを検索します。

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>パラメーター

*pVariable*<br/>
アニメーション変数へのポインター。

*ppObject*<br/>
Output. アニメーションオブジェクトまたは NULL へのポインターが含まれています。

*ppGroup*<br/>
Output. アニメーションオブジェクトを保持するアニメーショングループへのポインター、または NULL を格納します。

### <a name="return-value"></a>戻り値

オブジェクトが見つかった場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

受信アニメーション変数からアニメーションオブジェクトを検索する必要がある場合に、イベントハンドラーから呼び出されます。

##  <a name="g_keyframestoryboardstart"></a>CAnimationController:: gkeyframeStoryboardStart

ストーリーボードの開始を表すキーフレーム。

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

##  <a name="getkeyframestoryboardstart"></a>CAnimationController:: GetKeyframeStoryboardStart

ストーリーボードの開始を識別するキーフレームを返します。

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>戻り値

ストーリーボードの開始を識別する、基本キーフレームへのポインター。

### <a name="remarks"></a>Remarks

このキーフレームを取得して、ストーリーボードの開始時点の他のキーフレームまたは遷移のベースにします。

##  <a name="getuianimationmanager"></a>CAnimationController:: GetUIAnimationManager

カプセル化された Iui' Manager オブジェクトへのアクセスを提供します。

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>戻り値

Iuianimation Manager インターフェイスへのポインター。または、アニメーションマネージャーの作成に失敗した場合は NULL。

### <a name="remarks"></a>Remarks

現在の OS が Windows アニメーション API をサポートしていない場合、このメソッドは NULL を返し、それ以降の CAnimationController:: IsValid のすべての呼び出しで FALSE が返されます。 Iuianimation Manager にアクセスして、アニメーションコントローラーでラップされていないインターフェイスメソッドを呼び出す必要がある場合があります。

##  <a name="getuianimationtimer"></a>CAnimationController:: GetUIAnimationTimer

カプセル化された Iuiアニメーションタイマーオブジェクトへのアクセスを提供します。

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>戻り値

Iuianimation Timer インターフェイスへのポインター。アニメーションタイマーの作成に失敗した場合は NULL。

### <a name="remarks"></a>Remarks

現在の OS が Windows アニメーション API をサポートしていない場合、このメソッドは NULL を返し、それ以降の CAnimationController:: IsValid のすべての呼び出しで FALSE が返されます。

##  <a name="getuitransitionfactory"></a>CAnimationController:: GetUITransitionFactory

Iui、遷移ライブラリの作成に失敗した場合は、Iui' の遷移のファクトリインターフェイスまたは NULL へのポインター。

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>戻り値

遷移ファクトリの作成に失敗した場合は、Iui' 遷移 Tionfactory または NULL へのポインター。

### <a name="remarks"></a>Remarks

現在の OS が Windows アニメーション API をサポートしていない場合、このメソッドは NULL を返し、それ以降の CAnimationController:: IsValid のすべての呼び出しで FALSE が返されます。

##  <a name="getuitransitionlibrary"></a>CAnimationController:: GetUITransitionLibrary

カプセル化された Iui' オブジェクトへのアクセスを提供します。

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>戻り値

Iuiによって、移行ライブラリの作成に失敗した場合は、Iuiによって、そのインターフェイスまたは NULL を指すポインターです。

### <a name="remarks"></a>Remarks

現在の OS が Windows アニメーション API をサポートしていない場合、このメソッドは NULL を返し、それ以降の CAnimationController:: IsValid のすべての呼び出しで FALSE が返されます。

##  <a name="isanimationinprogress"></a>  CAnimationController::IsAnimationInProgress

少なくとも1つのグループがアニメーションを再生しているかどうかを示します。

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>戻り値

このアニメーションコントローラーでアニメーションが進行中の場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

アニメーションマネージャーの状態を確認し、状態が UI_ANIMATION_MANAGER_BUSY の場合は TRUE を返します。

##  <a name="isvalid"></a>CAnimationController:: IsValid

アニメーションコントローラーが有効かどうかを示します。

```
BOOL IsValid() const;
```

### <a name="return-value"></a>戻り値

アニメーションコントローラーが有効な場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows アニメーション API が現在の OS でサポートされておらず、アニメーションマネージャーの作成が登録されていないために失敗した場合にのみ、FALSE を返します。 COM ライブラリを初期化した後、少なくとも1回は GetUIAnimationManager を呼び出して、このフラグの設定を行う必要があります。

##  <a name="m_bisvalid"></a>CAnimationController:: m_bIsValid

アニメーションコントローラーが有効かどうかを指定します。 現在の OS が Windows アニメーション API をサポートしていない場合、このメンバーは FALSE に設定されます。

```
BOOL m_bIsValid;
```

##  <a name="m_lstanimationgroups"></a>CAnimationController:: m_lstAnimationGroups

このアニメーションコントローラーに属するアニメーショングループのリスト。

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

##  <a name="m_panimationmanager"></a>CAnimationController:: m_pAnimationManager

アニメーションマネージャー COM オブジェクトへのポインターを格納します。

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

##  <a name="m_panimationtimer"></a>CAnimationController:: m_pAnimationTimer

アニメーションタイマー COM オブジェクトへのポインターを格納します。

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

##  <a name="m_prelatedwnd"></a>CAnimationController:: m_pRelatedWnd

アニメーションマネージャーの状態が変更されたとき、または更新後のイベントが発生したときに自動的に再描画できる、関連する CWnd オブジェクトへのポインター。 NULL を指定できます。

```
CWnd* m_pRelatedWnd;
```

##  <a name="m_ptransitionfactory"></a>  CAnimationController::m_pTransitionFactory

遷移ファクトリ COM オブジェクトへのポインターを格納します。

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

##  <a name="m_ptransitionlibrary"></a>  CAnimationController::m_pTransitionLibrary

遷移ライブラリ COM オブジェクトへのポインターを格納します。

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

##  <a name="onafterschedule"></a>CAnimationController:: OnAfterSchedule

指定したグループのアニメーションがスケジュールされた直後に、フレームワークによって呼び出されます。

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>パラメーター

*pGroup*<br/>
スケジュールされているアニメーショングループへのポインター。

### <a name="remarks"></a>Remarks

既定の実装では、指定されたグループからキーフレームが削除され、指定したグループに属するアニメーション変数から遷移します。 派生クラスでオーバーライドして、アニメーションのスケジュールに応じて追加のアクションを実行できます。

##  <a name="onanimationintegervaluechanged"></a>CAnimationController:: OnAnimationIntegerValueChanged

アニメーション変数の整数値が変更されたときにフレームワークによって呼び出されます。

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>パラメーター

*pGroup*<br/>
値が変更されたアニメーションオブジェクトを保持するアニメーショングループへのポインター。

*pObject*<br/>
値が変更されたアニメーション変数を格納しているアニメーションオブジェクトへのポインター。

*variable*<br/>
アニメーション変数へのポインター。

*newValue*<br/>
新しい値を指定します。

*prevValue*<br/>
前の値を指定します。

### <a name="remarks"></a>Remarks

このメソッドは、特定のアニメーション変数またはアニメーションオブジェクトに対して EnableIntegerValueChangedEvent が呼び出されたアニメーション変数イベントを有効にした場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。

##  <a name="onanimationmanagerstatuschanged"></a>CAnimationController:: Onアニメーションマネージャー Statuschanged

アニメーションマネージャーからの StatusChanged イベントに応答して、フレームワークによって呼び出されます。

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>パラメーター

*newStatus*<br/>
新しいアニメーションマネージャーの状態。

*前の状態*<br/>
アニメーションマネージャーの以前の状態。

### <a name="remarks"></a>Remarks

このメソッドは、Enableanimation Managerevent で animation manager イベントを有効にした場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。 既定の実装では、SetRelatedWnd で設定されている場合、関連ウィンドウが更新されます。

##  <a name="onanimationtimerpostupdate"></a>CAnimationController:: Onアニメーション Timerpostupdate

アニメーションの更新が完了した後にフレームワークによって呼び出されます。

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>Remarks

このメソッドは、Enable' Timereventhandler を使用してタイマーイベントハンドラーを有効にした場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。

##  <a name="onanimationtimerpreupdate"></a>CAnimationController:: Onアニメーション Timerpreupdate

アニメーションの更新が開始される前にフレームワークによって呼び出されます。

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>Remarks

このメソッドは、Enable' Timereventhandler を使用してタイマーイベントハンドラーを有効にした場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。

##  <a name="onanimationtimerrenderingtooslow"></a>CAnimationController:: OnAnimationTimerRenderingTooSlow

アニメーションのレンダリングフレームレートが望ましいフレームレートの最小値を下回ると、フレームワークによって呼び出されます。

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>パラメーター

*fps*<br/>
現在のフレームレート (1 秒あたりのフレーム数)。

### <a name="remarks"></a>Remarks

このメソッドは、Enable' Timereventhandler を使用してタイマーイベントハンドラーを有効にした場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。 IuiSetFrameRateThreshold Timer:: を呼び出すことで、最小の望ましいフレームレートが指定されます。

##  <a name="onanimationvaluechanged"></a>  CAnimationController::OnAnimationValueChanged

アニメーション変数の値が変更されたときにフレームワークによって呼び出されます。

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>パラメーター

*pGroup*<br/>
値が変更されたアニメーションオブジェクトを保持するアニメーショングループへのポインター。

*pObject*<br/>
値が変更されたアニメーション変数を格納しているアニメーションオブジェクトへのポインター。

*variable*<br/>
アニメーション変数へのポインター。

*newValue*<br/>
新しい値を指定します。

*prevValue*<br/>
前の値を指定します。

### <a name="remarks"></a>Remarks

このメソッドは、特定のアニメーション変数またはアニメーションオブジェクトに対して EnableValueChangedEvent が呼び出されたアニメーション変数イベントを有効にした場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。

##  <a name="onbeforeanimationstart"></a>  CAnimationController::OnBeforeAnimationStart

アニメーションがスケジュールされる直前に、フレームワークによって呼び出されます。

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>パラメーター

*pGroup*<br/>
アニメーションを開始しようとしているアニメーショングループへのポインター。

### <a name="remarks"></a>Remarks

この呼び出しは関連する CWnd にルーティングされ、派生クラスでオーバーライドして、指定されたグループのアニメーションを開始する前に追加のアクションを実行することができます。

##  <a name="onhasprioritycancel"></a>CAnimationController:: Onhas優先順位の取り消し

スケジュールの競合を解決するために、フレームワークによって呼び出されます。

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>パラメーター

*pGroupScheduled*<br/>
現在スケジュールされているストーリーボードを所有しているグループ。

*pGroupNew*<br/>
pGroupScheduled が所有するスケジュール済みのストーリーボードとスケジュールが競合している新しいストーリーボードを所有しているグループ。

*優先順位効果*<br/>
pGroupScheduled の優先度がより高い場合に予想される pGroupNew への影響。

### <a name="return-value"></a>戻り値

pGroupNew が所有するストーリーボードの優先度が高い場合は TRUE を返します。 pGroupScheduled が所有するストーリーボードの優先度が高い場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメソッドは、CAnimationController::EnablePriorityComparisonHandler を使用して優先度比較イベントを有効にし、UI_ANIMATION_PHT_CANCEL を指定した場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。 [競合管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)の詳細については、WINDOWS アニメーション API のドキュメントを参照してください。

##  <a name="onhasprioritycompress"></a>CAnimationController:: Onhasの圧縮

スケジュールの競合を解決するために、フレームワークによって呼び出されます。

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>パラメーター

*pGroupScheduled*<br/>
現在スケジュールされているストーリーボードを所有しているグループ。

*pGroupNew*<br/>
pGroupScheduled が所有するスケジュール済みのストーリーボードとスケジュールが競合している新しいストーリーボードを所有しているグループ。

*優先順位効果*<br/>
pGroupScheduled の優先度がより高い場合に予想される pGroupNew への影響。

### <a name="return-value"></a>戻り値

pGroupNew が所有するストーリーボードの優先度が高い場合は TRUE を返します。 pGroupScheduled が所有するストーリーボードの優先度が高い場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメソッドは、CAnimationController::EnablePriorityComparisonHandler を使用して優先度比較イベントを有効にし、UI_ANIMATION_PHT_COMPRESS を指定した場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。 [競合管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)の詳細については、WINDOWS アニメーション API のドキュメントを参照してください。

##  <a name="onhaspriorityconclude"></a>CAnimationController:: Onhas優先順位の結論

スケジュールの競合を解決するために、フレームワークによって呼び出されます。

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>パラメーター

*pGroupScheduled*<br/>
現在スケジュールされているストーリーボードを所有しているグループ。

*pGroupNew*<br/>
pGroupScheduled が所有するスケジュール済みのストーリーボードとスケジュールが競合している新しいストーリーボードを所有しているグループ。

*優先順位効果*<br/>
pGroupScheduled の優先度がより高い場合に予想される pGroupNew への影響。

### <a name="return-value"></a>戻り値

pGroupNew が所有するストーリーボードの優先度が高い場合は TRUE を返します。 pGroupScheduled が所有するストーリーボードの優先度が高い場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメソッドは、CAnimationController::EnablePriorityComparisonHandler を使用して優先度比較イベントを有効にし、UI_ANIMATION_PHT_CONCLUDE を指定した場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。 [競合管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)の詳細については、WINDOWS アニメーション API のドキュメントを参照してください。

##  <a name="onhasprioritytrim"></a>  CAnimationController::OnHasPriorityTrim

スケジュールの競合を解決するために、フレームワークによって呼び出されます。

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>パラメーター

*pGroupScheduled*<br/>
現在スケジュールされているストーリーボードを所有しているグループ。

*pGroupNew*<br/>
pGroupScheduled が所有するスケジュール済みのストーリーボードとスケジュールが競合している新しいストーリーボードを所有しているグループ。

*優先順位効果*<br/>
pGroupScheduled の優先度がより高い場合に予想される pGroupNew への影響。

### <a name="return-value"></a>戻り値

pGroupNew が所有するストーリーボードの優先度が高い場合は TRUE を返します。 pGroupScheduled が所有するストーリーボードの優先度が高い場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメソッドは、CAnimationController::EnablePriorityComparisonHandler を使用して優先度比較イベントを有効にし、UI_ANIMATION_PHT_TRIM を指定した場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。 [競合管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)の詳細については、WINDOWS アニメーション API のドキュメントを参照してください。

##  <a name="onstoryboardstatuschanged"></a>CAnimationController:: OnStoryboardStatusChanged

ストーリーボードの状態が変化したときにフレームワークによって呼び出されます。

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>パラメーター

*pGroup*<br/>
状態が変更されたストーリーボードを所有するアニメーショングループへのポインター。

*newStatus*<br/>
新しいステータスを指定します。

*前の状態*<br/>
以前の状態を指定します。

### <a name="remarks"></a>Remarks

このメソッドは、CAnimationController:: EnableStoryboardEventHandler を使用してストーリーボードイベントを有効にした場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。

##  <a name="onstoryboardupdated"></a>CAnimationController:: OnStoryboardUpdated

ストーリーボードが更新されたときにフレームワークによって呼び出されます。

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>パラメーター

*pGroup*<br/>
ストーリーボードを所有するグループへのポインター。

### <a name="remarks"></a>Remarks

このメソッドは、CAnimationController:: EnableStoryboardEventHandler を使用してストーリーボードイベントを有効にした場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。

##  <a name="removeallanimationgroups"></a>  CAnimationController::RemoveAllAnimationGroups

アニメーションコントローラーからすべてのアニメーショングループを削除します。

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>Remarks

すべてのグループが削除されます。アプリケーションレベルで格納されている場合、そのポインターは無効にする必要があります。 削除しようとしているグループの CAnimationGroup:: m_bAutodestroyAnimationObjects が TRUE の場合、そのグループに属するすべてのアニメーションオブジェクトが削除されます。それ以外の場合、親アニメーションコントローラーへの参照は NULL に設定され、別のコントローラーに追加することができます。

##  <a name="removeanimationgroup"></a>  CAnimationController::RemoveAnimationGroup

アニメーションコントローラーから、指定された ID を持つアニメーショングループを削除します。

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
アニメーショングループ ID を指定します。

### <a name="remarks"></a>Remarks

このメソッドは、グループの内部リストからアニメーショングループを削除し、それを削除します。そのため、そのアニメーショングループへのポインターを格納した場合は、無効にする必要があります。 CAnimationGroup:: m_bAutodestroyAnimationObjects が TRUE の場合、そのグループに属するすべてのアニメーションオブジェクトが削除されます。それ以外の場合、親アニメーションコントローラーへの参照は NULL に設定され、別のコントローラーに追加することができます。

##  <a name="removeanimationobject"></a>  CAnimationController::RemoveAnimationObject

アニメーションコントローラーからアニメーションオブジェクトを削除します。

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>パラメーター

*pObject*<br/>
アニメーションオブジェクトへのポインター。

*bNoDelete*<br/>
このパラメーターが TRUE の場合、オブジェクトは削除時に削除されません。

### <a name="remarks"></a>Remarks

アニメーションコントローラーとアニメーショングループからアニメーションオブジェクトを削除します。 特定のオブジェクトをアニメーション化しない場合、または別のアニメーションコントローラーにオブジェクトを移動する必要がある場合は、この関数を呼び出します。 最後の例では、bNoDelete が TRUE である必要があります。

##  <a name="removetransitions"></a>  CAnimationController::RemoveTransitions

指定したグループに属するアニメーションオブジェクトからの切り替え効果を削除します。

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
グループ ID を指定します。

### <a name="remarks"></a>Remarks

グループはアニメーションオブジェクトをループし、各アニメーションオブジェクトに対して ClearTransitions (FALSE) を呼び出します。 このメソッドは、アニメーションがスケジュールされた後にフレームワークによって呼び出されます。

##  <a name="schedulegroup"></a>CAnimationController:: ScheduleGroup

アニメーションをスケジュールします。

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
スケジュールするアニメーショングループ ID を指定します。

*time*<br/>
スケジュールする時刻を指定します。

### <a name="return-value"></a>戻り値

アニメーションが正常にスケジュールされた場合は TRUE。 ストーリーボードが作成されていない場合、またはその他のエラーが発生した場合は FALSE。

### <a name="remarks"></a>Remarks

パラメーター bScheduleNow を FALSE に設定して AnimateGroup を呼び出す必要があります。 Iuianimation Timer:: GetTime から取得した、必要なアニメーション時間を指定できます。 時間パラメーターが0.0 の場合、アニメーションは現在の時刻に対してスケジュールされます。

##  <a name="setrelatedwnd"></a>CAnimationController:: SetRelatedWnd

アニメーションコントローラーとウィンドウの間のリレーションシップを確立します。

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
設定するウィンドウオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

関連する CWnd オブジェクトが設定されている場合、アニメーションコントローラーは、アニメーションマネージャーの状態が変更されたとき、またはタイマー後に更新イベントが発生したときに、そのオブジェクトを自動的に更新する (WM_PAINT メッセージを送信する) ことができます。

##  <a name="updateanimationmanager"></a>CAnimationController:: Updateアニメーションマネージャー

アニメーションマネージャーに対して、すべてのアニメーション変数の値を更新するように指示します。

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>Remarks

このメソッドを呼び出すと、アニメーションマネージャーが現在の時刻に進められ、必要に応じてストーリーボードの状態が変化し、任意のアニメーション変数が適切な挿入値に更新されます。 内部的には、このメソッドは IuiGetTime Timer:: (timeNow) と Iui Manager:: Update (timeNow) を呼び出します。 この動作をカスタマイズするには、派生クラスでこのメソッドをオーバーライドします。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
