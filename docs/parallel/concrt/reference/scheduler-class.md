---
title: Scheduler クラス
ms.date: 11/04/2016
f1_keywords:
- Scheduler
- CONCRT/concurrency::Scheduler
- CONCRT/concurrency::Scheduler::Scheduler
- CONCRT/concurrency::Scheduler::Attach
- CONCRT/concurrency::Scheduler::Create
- CONCRT/concurrency::Scheduler::CreateScheduleGroup
- CONCRT/concurrency::Scheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::Scheduler::GetPolicy
- CONCRT/concurrency::Scheduler::Id
- CONCRT/concurrency::Scheduler::IsAvailableLocation
- CONCRT/concurrency::Scheduler::Reference
- CONCRT/concurrency::Scheduler::RegisterShutdownEvent
- CONCRT/concurrency::Scheduler::Release
- CONCRT/concurrency::Scheduler::ResetDefaultSchedulerPolicy
- CONCRT/concurrency::Scheduler::ScheduleTask
- CONCRT/concurrency::Scheduler::SetDefaultSchedulerPolicy
helpviewer_keywords:
- Scheduler class
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
ms.openlocfilehash: 77ad876b8352ab1ae86fde622b05712ec5f2cea9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142007"
---
# <a name="scheduler-class"></a>Scheduler クラス

コンカレンシー ランタイム スケジューラの抽象化を表します。

## <a name="syntax"></a>構文

```cpp
class Scheduler;
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|Name|説明|
|----------|-----------------|
|[Scheduler](#ctor)|`Scheduler` クラスのオブジェクトは、ファクトリメソッドを使用して、または暗黙的に作成することができます。|
|[~ Scheduler デストラクター](#dtor)|`Scheduler` クラスのオブジェクトは、すべての外部参照が存在しなくなると、暗黙的に破棄されます。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[Attach](#attach)|スケジューラを呼び出し元のコンテキストにアタッチします。 このメソッドから制御が戻った後、呼び出し元のコンテキストはスケジューラによって管理され、スケジューラは現在のスケジューラになります。|
|[作成](#create)|`_Policy` パラメーターによって記述された動作を持つ新しいスケジューラを作成し、スケジューラに初期参照を配置し、そのスケジューラへのポインターを返します。|
|[CreateScheduleGroup](#createschedulegroup)|オーバーロードされます。 スケジューラ内に新しいスケジュールグループを作成します。 パラメーター `_Placement` を受け取るバージョンを使用すると、新しく作成されたスケジュールグループ内のタスクが、そのパラメーターで指定された場所で実行されるようにバイアスされます。|
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|スケジューラの現在の仮想プロセッサ数を返します。|
|[GetPolicy](#getpolicy)|スケジューラが作成されたポリシーのコピーを返します。|
|[ID](#id)|スケジューラの一意の識別子を返します。|
|[IsAvailableLocation](#isavailablelocation)|指定された場所がスケジューラで使用できるかどうかを判断します。|
|[リファレンス](#reference)|スケジューラの参照カウントをインクリメントします。|
|[RegisterShutdownEvent](#registershutdownevent)|スケジューラがシャットダウンして自身を破棄するときに、`_Event` パラメーターで渡された Windows イベントハンドルをシグナル状態にします。 イベントがシグナル状態になると、スケジューラに対してスケジュールされていたすべての作業が完了します。 この方法では、複数のシャットダウンイベントを登録できます。|
|[Release](#release)|スケジューラの参照カウントをデクリメントします。|
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|既定のスケジューラポリシーをランタイムの既定値にリセットします。 次に既定のスケジューラが作成されるときに、ランタイムの既定のポリシー設定が使用されます。|
|[ScheduleTask](#scheduletask)|オーバーロードされます。 スケジューラ内の軽量タスクをスケジュールします。 軽量タスクは、ランタイムによって決定されるスケジュールグループに配置されます。 パラメーター `_Placement` を受け取るバージョンでは、指定された位置でタスクの実行がバイアスされます。|
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|既定のスケジューラを作成するためにユーザー定義のポリシーを使用できるようにします。 このメソッドは、プロセス内に既定のスケジューラが存在しない場合にのみ呼び出すことができます。 既定のポリシーが設定されると、`SetDefaultSchedulerPolicy` または[Resetdefaultスケジューラポリシー](#resetdefaultschedulerpolicy)メソッドへの次の有効な呼び出しまで有効になります。|

## <a name="remarks"></a>解説

同時実行ランタイム scheduler は、アプリケーションによってキューに置かれた作業を実行するために、スレッドなどのオペレーティングシステムの実行コンテキストにマップされる実行コンテキストを使用します。 スケジューラの同時実行レベルは、リソースマネージャーによって付与された仮想プロセッサの数と同じになります。 仮想プロセッサとは、処理リソースを抽象化したものであり、基になるシステムのハードウェア スレッドに対応しています。 指定された時点に 1 つの仮想プロセッサで実行できるスケジューラ コンテキストは 1 つのみです。

同時実行ランタイムは、並列処理を実行するプロセスごとに既定のスケジューラを作成します。 さらに、独自の scheduler インスタンスを作成して、このクラスを使用して操作することもできます。

## <a name="inheritance-hierarchy"></a>継承階層

`Scheduler`

## <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="attach"></a>外付け

スケジューラを呼び出し元のコンテキストにアタッチします。 このメソッドから制御が戻った後、呼び出し元のコンテキストはスケジューラによって管理され、スケジューラは現在のスケジューラになります。

```cpp
virtual void Attach() = 0;
```

### <a name="remarks"></a>解説

スケジューラをアタッチすると、スケジューラに参照が暗黙的に配置されます。

将来のある時点で、スケジューラをシャットダウンできるようにするために、 [Currentscheduler::D etach](currentscheduler-class.md#detach)メソッドを呼び出す必要があります。

このメソッドが既に別のスケジューラにアタッチされているコンテキストから呼び出された場合、既存のスケジューラは以前のスケジューラとして記憶され、新しく作成されたスケジューラは現在のスケジューラになります。 後で `CurrentScheduler::Detach` メソッドを呼び出すと、前のスケジューラが現在のスケジューラとして復元されます。

このスケジューラが呼び出しコンテキストの現在のスケジューラである場合、このメソッドは[improper_scheduler_attach](improper-scheduler-attach-class.md)例外をスローします。

## <a name="create"></a> 作成

`_Policy` パラメーターによって記述された動作を持つ新しいスケジューラを作成し、スケジューラに初期参照を配置し、そのスケジューラへのポインターを返します。

```cpp
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>パラメーター

*_Policy*<br/>
新しく作成されたスケジューラの動作を記述するスケジューラポリシー。

### <a name="return-value"></a>戻り値

新しく作成されたスケジューラへのポインター。 この `Scheduler` オブジェクトには、最初の参照カウントが配置されています。

### <a name="remarks"></a>解説

`Create` メソッドを使用してスケジューラを作成した後、最初の参照カウントを削除し、スケジューラのシャットダウンを許可するために、将来のある時点で `Release` メソッドを呼び出す必要があります。

このメソッドで作成されたスケジューラは、呼び出し元のコンテキストにアタッチされていません。 [Attach](#attach)メソッドを使用してコンテキストにアタッチすることができます。

このメソッドは、 [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)や[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)など、さまざまな例外をスローする場合があります。

## <a name="createschedulegroup"></a>CreateScheduleGroup

スケジューラ内に新しいスケジュールグループを作成します。 パラメーター `_Placement` を受け取るバージョンを使用すると、新しく作成されたスケジュールグループ内のタスクが、そのパラメーターで指定された場所で実行されるようにバイアスされます。

```cpp
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```

### <a name="parameters"></a>パラメーター

*_Placement*<br/>
スケジュールグループ内のタスクがでの実行に対してバイアスをかける場所への参照。

### <a name="return-value"></a>戻り値

新しく作成されたスケジュールグループへのポインター。 この `ScheduleGroup` オブジェクトには、最初の参照カウントが配置されています。

### <a name="remarks"></a>解説

スケジュールグループに対する作業のスケジュールが完了したら、 [Release](schedulegroup-class.md#release)メソッドを呼び出す必要があります。 スケジューラがキューに登録されているすべての作業が完了すると、スケジューラはスケジュールグループを破棄します。

このスケジューラを明示的に作成した場合は、スケジューラで参照を解放する前に、その中のスケジュールグループへのすべての参照を解放する必要があることに注意してください。

## <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors

スケジューラの現在の仮想プロセッサ数を返します。

```cpp
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```

### <a name="return-value"></a>戻り値

スケジューラの現在の仮想プロセッサの数。

## <a name="getpolicy"></a>GetPolicy

スケジューラが作成されたポリシーのコピーを返します。

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>戻り値

スケジューラが作成されたポリシーのコピー。

## <a name="id"></a>番号

スケジューラの一意の識別子を返します。

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>戻り値

スケジューラの一意の識別子。

## <a name="isavailablelocation"></a>IsAvailableLocation

指定された場所がスケジューラで使用できるかどうかを判断します。

```cpp
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```

### <a name="parameters"></a>パラメーター

*_Placement*<br/>
スケジューラの照会先の場所への参照。

### <a name="return-value"></a>戻り値

`_Placement` 引数で指定された場所がスケジューラで使用できるかどうかを示します。

### <a name="remarks"></a>解説

戻り値は、指定された場所が使用可能かどうかを瞬間的にサンプリングすることに注意してください。 複数のスケジューラが存在する場合、動的リソース管理によって、任意の時点でスケジューラからリソースを追加または取得できます。 このような状況が発生した場合、特定の場所で可用性を変更できます。

## <a name="reference"></a>「

スケジューラの参照カウントをインクリメントします。

```cpp
virtual unsigned int Reference() = 0 ;
```

### <a name="return-value"></a>戻り値

新しくインクリメントされた参照カウント。

### <a name="remarks"></a>解説

これは通常、合成のためにスケジューラの有効期間を管理するために使用されます。 スケジューラの参照カウントが0になると、スケジューラのすべての処理が完了した後に、スケジューラがシャットダウンして破棄されます。

メソッドは、`Reference` メソッドを呼び出す前の参照カウントが0で、スケジューラによって所有されていないコンテキストから呼び出しが行われた場合に、 [improper_scheduler_reference](improper-scheduler-reference-class.md)例外をスローします。

## <a name="registershutdownevent"></a>RegisterShutdownEvent

スケジューラがシャットダウンして自身を破棄するときに、`_Event` パラメーターで渡された Windows イベントハンドルをシグナル状態にします。 イベントがシグナル状態になると、スケジューラに対してスケジュールされていたすべての作業が完了します。 この方法では、複数のシャットダウンイベントを登録できます。

```cpp
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```

### <a name="parameters"></a>パラメーター

*_Event*<br/>
スケジューラがシャットダウンして自身を破棄したときにランタイムによって通知される Windows イベントオブジェクトへのハンドル。

## <a name="release"></a>解除

スケジューラの参照カウントをデクリメントします。

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>戻り値

新しくデクリメントされた参照カウント。

### <a name="remarks"></a>解説

これは通常、合成のためにスケジューラの有効期間を管理するために使用されます。 スケジューラの参照カウントが0になると、スケジューラのすべての処理が完了した後に、スケジューラがシャットダウンして破棄されます。

## <a name="resetdefaultschedulerpolicy"></a>ResetDefaultSchedulerPolicy

既定のスケジューラポリシーをランタイムの既定値にリセットします。 次に既定のスケジューラが作成されるときに、ランタイムの既定のポリシー設定が使用されます。

```cpp
static void __cdecl ResetDefaultSchedulerPolicy();
```

### <a name="remarks"></a>解説

このメソッドは、既定のスケジューラがプロセス内に存在する間に呼び出すことができます。 既存の既定のスケジューラのポリシーには影響しません。 ただし、既定のスケジューラがシャットダウンされ、新しい既定値が後で作成された場合、新しいスケジューラはランタイムの既定のポリシー設定を使用します。

## <a name="ctor"></a>組む

`Scheduler` クラスのオブジェクトは、ファクトリメソッドを使用して、または暗黙的に作成することができます。

```cpp
Scheduler();
```

### <a name="remarks"></a>解説

スケジューラを呼び出し元のコンテキストにアタッチする必要があるランタイム関数の多くを使用すると、プロセスの既定のスケジューラが暗黙的に作成されます。 `CurrentScheduler` クラス内のメソッドと PPL およびエージェントレイヤーの機能は、通常、暗黙的な添付ファイルを実行します。

また、`CurrentScheduler::Create` メソッドまたは `Scheduler::Create` メソッドのいずれかを使用して、スケジューラを明示的に作成することもできます。

## <a name="dtor"></a>~ Scheduler

`Scheduler` クラスのオブジェクトは、すべての外部参照が存在しなくなると、暗黙的に破棄されます。

```cpp
virtual ~Scheduler();
```

## <a name="scheduletask"></a>ScheduleTask

スケジューラ内の軽量タスクをスケジュールします。 軽量タスクは、ランタイムによって決定されるスケジュールグループに配置されます。 パラメーター `_Placement` を受け取るバージョンでは、指定された位置でタスクの実行がバイアスされます。

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;

virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement) = 0;
```

### <a name="parameters"></a>パラメーター

*_Proc*<br/>
ライトウェイトタスクの本体を実行するために実行する関数へのポインター。

*_Data*<br/>
タスクの本体にパラメーターとして渡されるデータへの void ポインター。

*_Placement*<br/>
ライトウェイトタスクがで実行されるようにバイアスされる場所への参照。

## <a name="setdefaultschedulerpolicy"></a>SetDefaultSchedulerPolicy

既定のスケジューラを作成するためにユーザー定義のポリシーを使用できるようにします。 このメソッドは、プロセス内に既定のスケジューラが存在しない場合にのみ呼び出すことができます。 既定のポリシーが設定されると、`SetDefaultSchedulerPolicy` または[Resetdefaultスケジューラポリシー](#resetdefaultschedulerpolicy)メソッドへの次の有効な呼び出しまで有効になります。

```cpp
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>パラメーター

*_Policy*<br/>
既定のスケジューラポリシーとして設定するポリシー。

### <a name="remarks"></a>解説

プロセス内に既定のスケジューラが既に存在するときに `SetDefaultSchedulerPolicy` メソッドが呼び出されると、ランタイムは[default_scheduler_exists](default-scheduler-exists-class.md)例外をスローします。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[Scheduler クラス](scheduler-class.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[タスク スケジューラ](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
