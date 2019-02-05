---
title: CAnimationController クラス
ms.date: 11/04/2016
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
ms.openlocfilehash: 93189c5c9301e513cfbdf110cf7753e211420fef
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894134"
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
|[CAnimationController::CAnimationController](#canimationcontroller)|アニメーション コント ローラーを構築します。|
|[CAnimationController::~CAnimationController](#canimationcontroller__~canimationcontroller)|デストラクターです。 アニメーション コント ローラーのオブジェクトが破棄されるときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationController::AddAnimationObject](#addanimationobject)|アニメーション オブジェクトをアニメーション コント ローラーが所属するグループに追加します。|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|グループには、キーフレームを追加します。|
|[CAnimationController::AnimateGroup](#animategroup)|アニメーションを実行するグループを準備し、必要に応じて、スケジュールを設定します。|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|オーバーロードされます。 アニメーションがスケジュールされているときに、グループをクリーンアップするためにフレームワークによって呼び出されます。|
|[CAnimationController::CreateKeyframe](#createkeyframe)|オーバーロードされます。 遷移に依存するキーフレームを作成し、指定したグループに追加します。|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|アニメーション マネージャーの状態が変化したときに呼び出すハンドラーを解放または設定します。|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|リリースのタイミング イベントのハンドラーと更新のタイミングのハンドラーを設定または取得します。|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|呼び出すかどうか、スケジュールされたストーリー ボードが取り消されました、という結論に達しました、トリミングしたりできる圧縮を決定する優先度比較ハンドラーを解放または設定します。|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|ストーリー ボードの状態と更新プログラムのイベントのハンドラーを解放または設定します。|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|オーバーロードされます。 そのストーリー ボード アニメーションのグループを検索します。|
|[CAnimationController::FindAnimationObject](#findanimationobject)|指定したアニメーション変数を含むアニメーション オブジェクトを検索します。|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|ストーリー ボードの先頭を識別するキーフレームを返します。|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|カプセル化された IUIAnimationManager オブジェクトへのアクセスを提供します。|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|カプセル化された IUIAnimationTimer オブジェクトへのアクセスを提供します。|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|IUIAnimationTransitionFactory インターフェイスまたは null の場合、遷移ライブラリの作成に失敗した場合へのポインター。|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|カプセル化された IUIAnimationTransitionLibrary オブジェクトへのアクセスを提供します。|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|少なくとも 1 つのグループがアニメーションを再生するかどうかを指示します。|
|[CAnimationController::IsValid](#isvalid)|アニメーション コント ローラーが有効かどうかを示します。|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|アニメーション変数の整数値が変更されたときに、フレームワークによって呼び出されます。|
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|アニメーション マネージャーからメイル イベントに応答フレームワークによって呼び出されます。|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|アニメーションの更新が完了した後に、フレームワークによって呼び出されます。|
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|アニメーションの更新プログラムを開始する前に、フレームワークによって呼び出されます。|
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|アニメーションのレンダリング フレーム レートが最小の望ましいフレーム レートを下回った場合に、フレームワークによって呼び出されます。|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|アニメーション変数の値が変更されたときに、フレームワークによって呼び出されます。|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|フレームワークによって呼び出されます、適切なアニメーションがスケジュールされる前にします。|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|スケジュールの競合を解決するために、フレームワークによって呼び出されます。|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|スケジュールの競合を解決するために、フレームワークによって呼び出されます。|
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|スケジュールの競合を解決するために、フレームワークによって呼び出されます。|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|スケジュールの競合を解決するために、フレームワークによって呼び出されます。|
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|ストーリー ボードの状態が変更されたときに、フレームワークによって呼び出されます。|
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|ストーリー ボードが更新されたときに、フレームワークによって呼び出されます。|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|アニメーション コント ローラーからアニメーションのすべてのグループを削除します。|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|アニメーション コント ローラーから、指定した ID を持つアニメーション グループを削除します。|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|アニメーション オブジェクトをアニメーション コント ローラーから削除します。|
|[CAnimationController::RemoveTransitions](#removetransitions)|指定したグループに属するアニメーション オブジェクトからの遷移を削除します。|
|[CAnimationController::ScheduleGroup](#schedulegroup)|アニメーションのスケジュールを設定します。|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|アニメーション コント ローラーとウィンドウ間の関係を確立します。|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|すべてのアニメーション変数の値を更新する、アニメーション マネージャーに指示します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|オーバーロードされます。 グループをクリーンアップするためのヘルパーです。|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|指定したグループのアニメーションがスケジュールされているだけときに、フレームワークによって呼び出されます。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|ストーリー ボードの開始を表すキーフレームです。|
|[CAnimationController::m_bIsValid](#m_bisvalid)|アニメーション コント ローラーが有効かどうかを指定します。 このメンバーは、現在の OS が Windows Animation API をサポートしていない場合、FALSE に設定されます。|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|このアニメーション コント ローラーに属するアニメーション グループの一覧。|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|アニメーション マネージャーの COM オブジェクトへのポインターを格納します。|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|アニメーション タイマーの COM オブジェクトへのポインターを格納します。|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|アニメーション マネージャーの状態が変更された、または後の更新イベントが発生したときに自動的に描画できる関連の CWnd オブジェクトへのポインター。 NULL にすることができます。|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|遷移の工場出荷時の COM オブジェクトへのポインターを格納します。|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|遷移ライブラリ COM オブジェクトへのポインターを格納します。|

## <a name="remarks"></a>Remarks

CAnimationController クラスは、アニメーションを管理するキー クラスです。 アプリケーションでアニメーション コント ローラーの 1 つまたは複数のインスタンスを作成して、CAnimationController::SetRelatedWnd を使用して、CWnd オブジェクトにアニメーション コント ローラーのインスタンスを必要に応じて、接続します。 アニメーション マネージャーの状態が変更されたか、アニメーション タイマーが更新されたときに関連するウィンドウに WM_PAINT メッセージを自動的に送信するには、この接続が必要です。 この関係を有効にしない場合、手動でアニメーションを表示するウィンドウが再描画する必要があります。 この目的のため CAnimationController からクラスを派生し、OnAnimationManagerStatusChanged や OnAnimationTimerPostUpdate をオーバーライドして必要な場合に、1 つまたは複数の windows を無効にできます。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="_dtorcanimationcontroller"></a>  CAnimationController:: ~ CAnimationController

デストラクターです。 アニメーション コント ローラーのオブジェクトが破棄されるときに呼び出されます。

```
virtual ~CAnimationController(void);
```

##  <a name="addanimationobject"></a>  CAnimationController::AddAnimationObject

アニメーション オブジェクトをアニメーション コント ローラーが所属するグループに追加します。

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>パラメーター

*pObject*<br/>
アニメーション オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

PObject が追加されている場合、関数が成功した場合、既存または新規のアニメーション グループへのポインターPObject は既に別のアニメーション コント ローラーが所属するグループに追加されている場合は NULL です。

### <a name="remarks"></a>Remarks

アニメーション オブジェクトをアニメーション コント ローラーに追加するには、このメソッドを呼び出します。 オブジェクトはオブジェクトの GroupID に従って、グループに追加する (CAnimationBaseObject::SetID を参照してください)。 指定された GroupID を追加する最初のオブジェクトの場合は、アニメーション コント ローラーは、新しいグループを作成します。 アニメーション オブジェクトは、アニメーションを 1 つのコント ローラーのみを追加できます。 オブジェクトを別のコント ローラーに追加する必要がある場合は、まず RemoveAnimationObject を呼び出します。 オブジェクトが、以前のグループから削除し、指定した ID を持つ別のグループに追加されたグループに既に追加されているオブジェクトの新しい GroupID で SetID を呼び出すと場合、

##  <a name="addkeyframetogroup"></a>  CAnimationController::AddKeyframeToGroup

グループには、キーフレームを追加します。

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
グループ ID を指定します

*pKeyframe*<br/>
キーフレームへのポインター。

### <a name="return-value"></a>戻り値

関数が成功した場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

通常が作成され、グループに作成されたキーフレームを自動的に追加します。 このメソッドを呼び出して、CAnimationController::CreateKeyframe を代わりに、使用する必要はありません。

##  <a name="animategroup"></a>  CAnimationController::AnimateGroup

アニメーションを実行するグループを準備し、必要に応じて、スケジュールを設定します。

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
GroupID を指定します。

*bScheduleNow*<br/>
すぐにアニメーションを実行するかどうかを指定します。

### <a name="return-value"></a>戻り値

アニメーションが正常にスケジュールして実行する場合は TRUE。

### <a name="remarks"></a>Remarks

このメソッドは、実際の作業のストーリー ボードを作成し、アニメーション変数の追加および遷移を適用するキーフレームを設定します。 遅延 bScheduleNow を FALSE に設定した場合のスケジュール設定することになります。 この場合、指定されたグループは、アニメーションが設定されているストーリー ボードを保持します。 その時点で、ストーリー ボードとアニメーション変数のイベントを設定できます。 ときに実際には、CAnimationController::ScheduleGroup アニメーションの呼び出しを実行する必要があります。

##  <a name="canimationcontroller"></a>  CAnimationController::CAnimationController

アニメーション コント ローラーを構築します。

```
CAnimationController(void);
```

##  <a name="cleanupgroup"></a>  CAnimationController::CleanUpGroup

アニメーションがスケジュールされているときに、グループをクリーンアップするためにフレームワークによって呼び出されます。

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
GroupID を指定します。

*pGroup*<br/>
クリーニングするアニメーション グループへのポインター。

### <a name="remarks"></a>Remarks

このメソッドを削除しますすべての遷移とキーフレーム指定されたグループからアニメーションがスケジュールされている後に関連がないためです。

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

アニメーション マネージャーの状態が変化したときに呼び出すハンドラーを解放または設定します。

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
設定またはハンドラーを解除するかどうかを指定します。

### <a name="return-value"></a>戻り値

ハンドラーが正常に設定またはリリースされた場合は TRUE。

### <a name="remarks"></a>Remarks

ハンドラーが (有効) を設定すると、Windows アニメーションは、アニメーション マネージャーのステータスが変わった OnAnimationManagerStatusChanged を呼び出します。

##  <a name="enableanimationtimereventhandler"></a>  CAnimationController::EnableAnimationTimerEventHandler

リリースのタイミング イベントのハンドラーと更新のタイミングのハンドラーを設定または取得します。

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
設定またはハンドラーを解除するかどうかを指定します。

*idleBehavior*<br/>
更新ハンドラーのタイマーのアイドル動作を指定します。

### <a name="return-value"></a>戻り値

ハンドラーが正常に設定または解放された場合は TRUE。エラーが発生した場合、その他のまたはハンドラーが最初に、解放しないままの 2 回 FALSE の場合、このメソッドが呼び出されます。

### <a name="remarks"></a>Remarks

ハンドラーは、設定されている場合 (有効) の Windows Animation API 呼び出し、OnAnimationTimerPreUpdate OnAnimationTimerPostUpdate、OnRenderingTooSlow メソッド。 Windows Animation API の更新プログラムのストーリー ボードを可能にするアニメーション タイマーを有効にする必要があります。 それ以外の場合、アニメーションを送信するためにすべてのアニメーション変数の値を更新するマネージャー CAnimationController::UpdateAnimationManager を呼び出す必要があります。

##  <a name="enableprioritycomparisonhandler"></a>  CAnimationController::EnablePriorityComparisonHandler

呼び出すかどうか、スケジュールされたストーリー ボードが取り消されました、という結論に達しました、トリミングしたりできる圧縮を決定する優先度比較ハンドラーを解放または設定します。

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>パラメーター

*dwHandlerType*<br/>
UI_ANIMATION_PHT_ の組み合わせにフラグを設定または解除するには、どのようなハンドラーを指定します (「解説」を参照してください)。

### <a name="return-value"></a>戻り値

ハンドラーが正常に設定またはリリースされた場合は TRUE。

### <a name="remarks"></a>Remarks

ハンドラーは、(有効) 設定 Windows アニメーション呼び出し dwHandlerType に応じて次の仮想メソッドが場合です。OnHasPriorityCancel、OnHasPriorityConclude、OnHasPriorityTrim、OnHasPriorityCompress します。 dwHandler は、次のフラグの組み合わせになります。UI_ANIMATION_PHT_NONE - リリース UI_ANIMATION_PHT_CANCEL - すべてのハンドラーは、[キャンセル] を設定比較ハンドラー UI_ANIMATION_PHT_CONCLUDE - 設定完結比較ハンドラー UI_ANIMATION_PHT_COMPRESS - 圧縮比較ハンドラー UI_ANIMATION_PHT_TRIM の設定 - 設定トリミング比較ハンドラー UI_ANIMATION_PHT_CANCEL_REMOVE - キャンセル比較ハンドラー UI_ANIMATION_PHT_CONCLUDE_REMOVE-remove 完結比較ハンドラー UI_ANIMATION_PHT_COMPRESS_REMOVE - 削除圧縮比較ハンドラー UI_ANIMATION_PHT の削除_TRIM_REMOVE - Trim の比較にハンドラーを削除

##  <a name="enablestoryboardeventhandler"></a>  CAnimationController::EnableStoryboardEventHandler

ストーリー ボードの状態と更新プログラムのイベントのハンドラーを解放または設定します。

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
グループ ID を指定します

*bEnable*<br/>
設定またはハンドラーを解除するかどうかを指定します。

### <a name="return-value"></a>戻り値

TRUE の場合、ハンドラーが正常に設定または解放指定したアニメーション グループが見つかるようになりましたまたは指定したグループのアニメーションが開始されていないとその内部のストーリー ボードが NULL の場合は FALSE。

### <a name="remarks"></a>Remarks

ハンドラーが設定されている場合 (有効) の Windows Animation API は OnStoryboardStatusChanges と OnStoryboardUpdated 仮想メソッドを呼び出します。 ハンドラーを設定してください、指定したアニメーション グループ CAnimationController::Animate が呼び出された後 IUIAnimationStoryboard のカプセル化されたオブジェクトを作成するため。

##  <a name="findanimationgroup"></a>  CAnimationController::FindAnimationGroup

によって、そのグループの id。 アニメーション グループを検索します

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
GroupID を指定します。

*pStoryboard*<br/>
ストーリー ボードへのポインター。

### <a name="return-value"></a>戻り値

アニメーションのグループまたは指定した ID を持つグループが見つからない場合は NULL へのポインター。

### <a name="remarks"></a>Remarks

このメソッドを使用すると、実行時に、アニメーションのグループを検索できます。 グループが作成され、特定のグループ id の最初のアニメーション オブジェクトをアニメーション コント ローラーに追加されているときにアニメーションのグループの内部一覧に追加します。

##  <a name="findanimationobject"></a>  CAnimationController::FindAnimationObject

指定したアニメーション変数を含むアニメーション オブジェクトを検索します。

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
出力します。 アニメーション オブジェクトまたは NULL へのポインターが含まれています。

*ppGroup*<br/>
出力します。 アニメーション オブジェクト、または NULL を保持するアニメーション グループへのポインターが含まれています。

### <a name="return-value"></a>戻り値

オブジェクトが見つかった場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

受信のアニメーション変数からアニメーション オブジェクトを検索することが必要なときに、イベント ハンドラーから呼び出されます。

##  <a name="g_keyframestoryboardstart"></a>  CAnimationController::gkeyframeStoryboardStart

ストーリー ボードの開始を表すキーフレームです。

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

##  <a name="getkeyframestoryboardstart"></a>  CAnimationController::GetKeyframeStoryboardStart

ストーリー ボードの先頭を識別するキーフレームを返します。

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>戻り値

ストーリー ボードの先頭を識別する、基準キーフレームへのポインター。

### <a name="remarks"></a>Remarks

ストーリー ボードの開始時の時点で、他のキーフレームや遷移の基に、このキーフレームを取得します。

##  <a name="getuianimationmanager"></a>  CAnimationController::GetUIAnimationManager

カプセル化された IUIAnimationManager オブジェクトへのアクセスを提供します。

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>戻り値

IUIAnimationManager インターフェイスまたは null の場合、アニメーション マネージャーの作成に失敗した場合へのポインター。

### <a name="remarks"></a>Remarks

現在の OS が Windows Animation API をサポートしていない場合、このメソッドは NULL を返し、その後 CAnimationController::IsValid 上のすべての後続の呼び出しには、FALSE が返されます。 アニメーション コント ローラーによってラップされていない、そのインターフェイス メソッドを呼び出すために IUIAnimationManager にアクセスする必要があります。

##  <a name="getuianimationtimer"></a>  CAnimationController::GetUIAnimationTimer

カプセル化された IUIAnimationTimer オブジェクトへのアクセスを提供します。

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>戻り値

IUIAnimationTimer インターフェイスまたは null の場合、アニメーション タイマーの作成に失敗した場合へのポインター。

### <a name="remarks"></a>Remarks

現在の OS が Windows Animation API をサポートしていない場合、このメソッドは NULL を返し、その後 CAnimationController::IsValid 上のすべての後続の呼び出しには、FALSE が返されます。

##  <a name="getuitransitionfactory"></a>  CAnimationController::GetUITransitionFactory

IUIAnimationTransitionFactory インターフェイスまたは null の場合、遷移ライブラリの作成に失敗した場合へのポインター。

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>戻り値

IUIAnimationTransitionFactory または null の場合、遷移のファクトリの作成に失敗した場合へのポインター。

### <a name="remarks"></a>Remarks

現在の OS が Windows Animation API をサポートしていない場合、このメソッドは NULL を返し、その後 CAnimationController::IsValid 上のすべての後続の呼び出しには、FALSE が返されます。

##  <a name="getuitransitionlibrary"></a>  CAnimationController::GetUITransitionLibrary

カプセル化された IUIAnimationTransitionLibrary オブジェクトへのアクセスを提供します。

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>戻り値

IUIAnimationTransitionLibrary インターフェイスまたは null の場合、遷移ライブラリの作成に失敗した場合へのポインター。

### <a name="remarks"></a>Remarks

現在の OS が Windows Animation API をサポートしていない場合、このメソッドは NULL を返し、その後 CAnimationController::IsValid 上のすべての後続の呼び出しには、FALSE が返されます。

##  <a name="isanimationinprogress"></a>  CAnimationController::IsAnimationInProgress

少なくとも 1 つのグループがアニメーションを再生するかどうかを指示します。

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>戻り値

このアニメーション コント ローラーに対して進行中のアニメーションがある場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

アニメーション マネージャーの状態をチェックし、状態が UI_ANIMATION_MANAGER_BUSY の場合は TRUE を返します。

##  <a name="isvalid"></a>  CAnimationController::IsValid

アニメーション コント ローラーが有効かどうかを示します。

```
BOOL IsValid() const;
```

### <a name="return-value"></a>戻り値

アニメーション コント ローラーが有効な場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

このメソッドは、Windows Animation API は、現在の OS とアニメーション マネージャーの作成ではサポートされていない場合にのみ FALSE を返します。 は、登録されていないために失敗しました。 このフラグの設定が発生するのには COM ライブラリの初期化の後に 1 回以上 GetUIAnimationManager を呼び出す必要があります。

##  <a name="m_bisvalid"></a>  CAnimationController::m_bIsValid

アニメーション コント ローラーが有効かどうかを指定します。 このメンバーは、現在の OS が Windows Animation API をサポートしていない場合、FALSE に設定されます。

```
BOOL m_bIsValid;
```

##  <a name="m_lstanimationgroups"></a>  CAnimationController::m_lstAnimationGroups

このアニメーション コント ローラーに属するアニメーション グループの一覧。

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

##  <a name="m_panimationmanager"></a>  CAnimationController::m_pAnimationManager

アニメーション マネージャーの COM オブジェクトへのポインターを格納します。

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

##  <a name="m_panimationtimer"></a>  CAnimationController::m_pAnimationTimer

アニメーション タイマーの COM オブジェクトへのポインターを格納します。

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

##  <a name="m_prelatedwnd"></a>  CAnimationController::m_pRelatedWnd

アニメーション マネージャーの状態が変更された、または後の更新イベントが発生したときに自動的に描画できる関連の CWnd オブジェクトへのポインター。 NULL にすることができます。

```
CWnd* m_pRelatedWnd;
```

##  <a name="m_ptransitionfactory"></a>  CAnimationController::m_pTransitionFactory

遷移の工場出荷時の COM オブジェクトへのポインターを格納します。

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

##  <a name="m_ptransitionlibrary"></a>  CAnimationController::m_pTransitionLibrary

遷移ライブラリ COM オブジェクトへのポインターを格納します。

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

##  <a name="onafterschedule"></a>  CAnimationController::OnAfterSchedule

指定したグループのアニメーションがスケジュールされているだけときに、フレームワークによって呼び出されます。

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>パラメーター

*pGroup*<br/>
スケジュールされているアニメーション グループへのポインター。

### <a name="remarks"></a>Remarks

既定の実装では、キーフレームを指定したグループから削除し、指定したグループに属するアニメーション変数から移行します。 アニメーションのスケジュールと追加アクションを実行する派生クラスでオーバーライドできます。

##  <a name="onanimationintegervaluechanged"></a>  CAnimationController::OnAnimationIntegerValueChanged

アニメーション変数の整数値が変更されたときに、フレームワークによって呼び出されます。

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
値を持つアニメーション オブジェクトを保持するアニメーション グループへのポインターが変更されました。

*pObject*<br/>
値が変更されたアニメーション変数を格納しているアニメーション オブジェクトへのポインター。

*variable*<br/>
アニメーション変数へのポインター。

*newValue*<br/>
新しい値を指定します。

*prevValue*<br/>
前の値を指定します。

### <a name="remarks"></a>Remarks

このメソッドは、特定のアニメーション変数またはアニメーション オブジェクトに対して呼び出されて EnableIntegerValueChangedEvent でアニメーション変数のイベントを有効にした場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。

##  <a name="onanimationmanagerstatuschanged"></a>  CAnimationController::OnAnimationManagerStatusChanged

アニメーション マネージャーからメイル イベントに応答フレームワークによって呼び出されます。

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>パラメーター

*newStatus*<br/>
新しいアニメーション マネージャーの状態。

*previousStatus*<br/>
前のアニメーション マネージャーの状態です。

### <a name="remarks"></a>Remarks

EnableAnimationManagerEvent でアニメーション マネージャーのイベントを有効にした場合、このメソッドが呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。 既定の実装が SetRelatedWnd で設定された場合に、関連するウィンドウを更新します。

##  <a name="onanimationtimerpostupdate"></a>  CAnimationController::OnAnimationTimerPostUpdate

アニメーションの更新が完了した後に、フレームワークによって呼び出されます。

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>Remarks

EnableAnimationTimerEventHandler を使用して、タイマー イベント ハンドラーを有効にした場合、このメソッドが呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。

##  <a name="onanimationtimerpreupdate"></a>  CAnimationController::OnAnimationTimerPreUpdate

アニメーションの更新プログラムを開始する前に、フレームワークによって呼び出されます。

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>Remarks

EnableAnimationTimerEventHandler を使用して、タイマー イベント ハンドラーを有効にした場合、このメソッドが呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。

##  <a name="onanimationtimerrenderingtooslow"></a>  CAnimationController::OnAnimationTimerRenderingTooSlow

アニメーションのレンダリング フレーム レートが最小の望ましいフレーム レートを下回った場合に、フレームワークによって呼び出されます。

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>パラメーター

*fps*<br/>
1 秒あたりのフレームで現在のフレーム レート。

### <a name="remarks"></a>Remarks

EnableAnimationTimerEventHandler を使用して、タイマー イベント ハンドラーを有効にした場合、このメソッドが呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。 最小の望ましいフレーム レートは、IUIAnimationTimer::SetFrameRateThreshold を呼び出すことによって指定されます。

##  <a name="onanimationvaluechanged"></a>  CAnimationController::OnAnimationValueChanged

アニメーション変数の値が変更されたときに、フレームワークによって呼び出されます。

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
値を持つアニメーション オブジェクトを保持するアニメーション グループへのポインターが変更されました。

*pObject*<br/>
値が変更されたアニメーション変数を格納しているアニメーション オブジェクトへのポインター。

*variable*<br/>
アニメーション変数へのポインター。

*newValue*<br/>
新しい値を指定します。

*prevValue*<br/>
前の値を指定します。

### <a name="remarks"></a>Remarks

このメソッドは、特定のアニメーション変数またはアニメーション オブジェクトに対して呼び出されて EnableValueChangedEvent でアニメーション変数のイベントを有効にした場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。

##  <a name="onbeforeanimationstart"></a>  CAnimationController::OnBeforeAnimationStart

フレームワークによって呼び出されます、適切なアニメーションがスケジュールされる前にします。

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>パラメーター

*pGroup*<br/>
アニメーションが開始しようとしていますが、アニメーション グループへのポインター。

### <a name="remarks"></a>Remarks

この呼び出しを使用して、関連 CWnd にルーティングは、アニメーションは、指定されたグループを開始する前に、追加の操作を実行する派生クラスでオーバーライドできます。

##  <a name="onhasprioritycancel"></a>  CAnimationController::OnHasPriorityCancel

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

*priorityEffect*<br/>
pGroupScheduled の優先度がより高い場合に予想される pGroupNew への影響。

### <a name="return-value"></a>戻り値

pGroupNew が所有するストーリーボードの優先度が高い場合は TRUE を返します。 pGroupScheduled が所有するストーリーボードの優先度が高い場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメソッドは、CAnimationController::EnablePriorityComparisonHandler を使用して優先度比較イベントを有効にし、UI_ANIMATION_PHT_CANCEL を指定した場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。 詳細については、読み取り Windows Animation API ドキュメント[競合管理](/windows/desktop/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)します。

##  <a name="onhasprioritycompress"></a>  CAnimationController::OnHasPriorityCompress

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

*priorityEffect*<br/>
pGroupScheduled の優先度がより高い場合に予想される pGroupNew への影響。

### <a name="return-value"></a>戻り値

pGroupNew が所有するストーリーボードの優先度が高い場合は TRUE を返します。 pGroupScheduled が所有するストーリーボードの優先度が高い場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメソッドは、CAnimationController::EnablePriorityComparisonHandler を使用して優先度比較イベントを有効にし、UI_ANIMATION_PHT_COMPRESS を指定した場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。 詳細については、読み取り Windows Animation API ドキュメント[競合管理](/windows/desktop/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)します。

##  <a name="onhaspriorityconclude"></a>  CAnimationController::OnHasPriorityConclude

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

*priorityEffect*<br/>
pGroupScheduled の優先度がより高い場合に予想される pGroupNew への影響。

### <a name="return-value"></a>戻り値

pGroupNew が所有するストーリーボードの優先度が高い場合は TRUE を返します。 pGroupScheduled が所有するストーリーボードの優先度が高い場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメソッドは、CAnimationController::EnablePriorityComparisonHandler を使用して優先度比較イベントを有効にし、UI_ANIMATION_PHT_CONCLUDE を指定した場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。 詳細については、読み取り Windows Animation API ドキュメント[競合管理](/windows/desktop/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)します。

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

*priorityEffect*<br/>
pGroupScheduled の優先度がより高い場合に予想される pGroupNew への影響。

### <a name="return-value"></a>戻り値

pGroupNew が所有するストーリーボードの優先度が高い場合は TRUE を返します。 pGroupScheduled が所有するストーリーボードの優先度が高い場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメソッドは、CAnimationController::EnablePriorityComparisonHandler を使用して優先度比較イベントを有効にし、UI_ANIMATION_PHT_TRIM を指定した場合に呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。 詳細については、読み取り Windows Animation API ドキュメント[競合管理](/windows/desktop/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)します。

##  <a name="onstoryboardstatuschanged"></a>  CAnimationController::OnStoryboardStatusChanged

ストーリー ボードの状態が変更されたときに、フレームワークによって呼び出されます。

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>パラメーター

*pGroup*<br/>
状態ストーリー ボードを所有しているアニメーション グループへのポインターが変更されました。

*newStatus*<br/>
新しいステータスを指定します。

*previousStatus*<br/>
以前の状態を指定します。

### <a name="remarks"></a>Remarks

CAnimationController::EnableStoryboardEventHandler を使用してストーリー ボードのイベントを有効にした場合、このメソッドが呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。

##  <a name="onstoryboardupdated"></a>  CAnimationController::OnStoryboardUpdated

ストーリー ボードが更新されたときに、フレームワークによって呼び出されます。

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>パラメーター

*pGroup*<br/>
ストーリー ボードを所有しているグループへのポインター。

### <a name="remarks"></a>Remarks

CAnimationController::EnableStoryboardEventHandler を使用してストーリー ボードのイベントを有効にした場合、このメソッドが呼び出されます。 派生クラスでオーバーライドして、アプリケーション固有のアクションを実行できます。

##  <a name="removeallanimationgroups"></a>  CAnimationController::RemoveAllAnimationGroups

アニメーション コント ローラーからアニメーションのすべてのグループを削除します。

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>Remarks

すべてのグループがある削除すると、そのポインターは、アプリケーション レベルでは、格納されている場合必要があります無効になります。 削除対象のグループの CAnimationGroup::m_bAutodestroyAnimationObjects が TRUE の場合は、そのグループに属しているすべてのアニメーション オブジェクトが削除されます;それ以外の場合親アニメーション コント ローラーへの参照は NULL に設定して、それらを別のコント ローラーを追加することができます。

##  <a name="removeanimationgroup"></a>  CAnimationController::RemoveAnimationGroup

アニメーション コント ローラーから、指定した ID を持つアニメーション グループを削除します。

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
アニメーションのグループ ID を指定します

### <a name="remarks"></a>Remarks

このメソッドは、内部グループの一覧から、アニメーションのグループを削除し、削除、したがってそのアニメーション グループへのポインターが格納されている場合にする必要があります無効になります。 CAnimationGroup::m_bAutodestroyAnimationObjects が TRUE の場合は、そのグループに属しているすべてのアニメーション オブジェクトが削除されます。それ以外の場合親アニメーション コント ローラーへの参照は NULL に設定して、それらを別のコント ローラーを追加することができます。

##  <a name="removeanimationobject"></a>  CAnimationController::RemoveAnimationObject

アニメーション オブジェクトをアニメーション コント ローラーから削除します。

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>パラメーター

*pObject*<br/>
アニメーション オブジェクトへのポインター。

*bNoDelete*<br/>
このパラメーターが TRUE の場合、削除すると、オブジェクトが削除されません。

### <a name="remarks"></a>Remarks

アニメーション オブジェクトをアニメーション コント ローラーとアニメーションのグループから削除します。 特定のオブジェクトがなくなった場合に、アニメーション化されない場合、またはオブジェクトを別のアニメーション コント ローラーに移動する必要がある場合は、この関数を呼び出します。 最後に大文字と小文字の bNoDelete TRUE 必要があります。

##  <a name="removetransitions"></a>  CAnimationController::RemoveTransitions

指定したグループに属するアニメーション オブジェクトからの遷移を削除します。

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
グループ ID を指定します

### <a name="remarks"></a>Remarks

グループは、そのアニメーション オブジェクトをループし、各アニメーション オブジェクトの ClearTransitions(FALSE) を呼び出します。 アニメーションがスケジュールされている後に、このメソッドがフレームワークによって呼び出されます。

##  <a name="schedulegroup"></a>  CAnimationController::ScheduleGroup

アニメーションのスケジュールを設定します。

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
アニメーションのスケジュール設定するグループの ID を指定します。

*time*<br/>
スケジュールする時間を指定します。

### <a name="return-value"></a>戻り値

アニメーションが正常にスケジュールされている場合は TRUE。 ストーリー ボードが作成されていない、またはその他のエラーが発生した場合は FALSE。

### <a name="remarks"></a>Remarks

以前 ScheduleGroup を FALSE に設定するパラメーター bScheduleNow で AnimateGroup を呼び出す必要があります。 IUIAnimationTimer::GetTime から取得した必要なアニメーションの時間を指定できます。 時間パラメーターが 0.0 の場合は、アニメーションが現在の時刻にスケジュールされます。

##  <a name="setrelatedwnd"></a>  CAnimationController::SetRelatedWnd

アニメーション コント ローラーとウィンドウ間の関係を確立します。

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*我が物*<br/>
設定するウィンドウ オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

関連 CWnd オブジェクトを設定すると、アニメーション コント ローラー自動的に更新できますが (WM_PAINT メッセージを送信する) ときにアニメーション マネージャーの状態が変更されたか、タイマーの後の更新イベントが発生しました。

##  <a name="updateanimationmanager"></a>  CAnimationController::UpdateAnimationManager

すべてのアニメーション変数の値を更新する、アニメーション マネージャーに指示します。

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>Remarks

呼び出し元がこのメソッドは、現在の時刻に、アニメーション マネージャーを進めます、必要に応じて、ストーリー ボードの状態を変更して、アニメーション変数を更新する適切な値を補間されます。 内部的にこのメソッドは、IUIAnimationTimer::GetTime(timeNow) と IUIAnimationManager::Update(timeNow) を呼び出します。 この動作をカスタマイズする派生クラスでこのメソッドをオーバーライドします。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
