---
title: CurrentScheduler クラス
ms.date: 11/04/2016
f1_keywords:
- CurrentScheduler
- CONCRT/concurrency::CurrentScheduler
- CONCRT/concurrency::CurrentScheduler::Create
- CONCRT/concurrency::CurrentScheduler::CreateScheduleGroup
- CONCRT/concurrency::CurrentScheduler::Detach
- CONCRT/concurrency::CurrentScheduler::Get
- CONCRT/concurrency::CurrentScheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::CurrentScheduler::GetPolicy
- CONCRT/concurrency::CurrentScheduler::Id
- CONCRT/concurrency::CurrentScheduler::IsAvailableLocation
- CONCRT/concurrency::CurrentScheduler::RegisterShutdownEvent
- CONCRT/concurrency::CurrentScheduler::ScheduleTask
helpviewer_keywords:
- CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
ms.openlocfilehash: 6bf61af9ff55722553353a045c87501dbd27fad9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143078"
---
# <a name="currentscheduler-class"></a>CurrentScheduler クラス

呼び出し元コンテキストに関連付けられている現在のスケジューラの抽象化を表します。

## <a name="syntax"></a>構文

```cpp
class CurrentScheduler;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[作成](#create)|`_Policy` パラメーターによって記述された動作を持つ新しいスケジューラを作成し、呼び出し元のコンテキストにアタッチします。 新しく作成されたスケジューラは、呼び出し元のコンテキストの現在のスケジューラになります。|
|[CreateScheduleGroup](#createschedulegroup)|オーバーロードされます。 呼び出し元のコンテキストに関連付けられているスケジューラ内に新しいスケジュールグループを作成します。 パラメーター `_Placement` を受け取るバージョンを使用すると、新しく作成されたスケジュールグループ内のタスクが、そのパラメーターで指定された場所で実行されるようにバイアスされます。|
|[デタッチ](#detach)|現在のスケジューラを呼び出し元のコンテキストからデタッチし、以前にアタッチされたスケジューラを現在のスケジューラとして復元します (存在する場合)。 このメソッドから制御が戻った後、呼び出し元のコンテキストは、前に `CurrentScheduler::Create` または `Scheduler::Attach` のいずれかのメソッドを使用してコンテキストにアタッチされたスケジューラによって管理されます。|
|[Get](#get)|呼び出し元のコンテキストに関連付けられているスケジューラへのポインターを返します。これは、現在のスケジューラとも呼ばれます。|
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|呼び出し元のコンテキストに関連付けられているスケジューラの仮想プロセッサの現在の数を返します。|
|[GetPolicy](#getpolicy)|現在のスケジューラが作成されたポリシーのコピーを返します。|
|[ID](#id)|現在のスケジューラの一意の識別子を返します。|
|[IsAvailableLocation](#isavailablelocation)|指定された場所が現在のスケジューラで使用できるかどうかを判断します。|
|[RegisterShutdownEvent](#registershutdownevent)|現在のコンテキストに関連付けられているスケジューラがシャットダウンして自身を破棄するときに、`_ShutdownEvent` パラメーターで渡された Windows イベントハンドルをシグナル状態にします。 イベントがシグナル状態になると、スケジューラに対してスケジュールされていたすべての作業が完了します。 この方法では、複数のシャットダウンイベントを登録できます。|
|[ScheduleTask](#scheduletask)|オーバーロードされます。 呼び出し元のコンテキストに関連付けられているスケジューラ内の軽量タスクをスケジュールします。 軽量タスクは、ランタイムによって決定されるスケジュールグループに配置されます。 パラメーター `_Placement` を受け取るバージョンでは、指定された位置でタスクの実行がバイアスされます。|

## <a name="remarks"></a>解説

呼び出し元のコンテキストに関連付けられているスケジューラ (「 [scheduler](scheduler-class.md)」を参照) が存在しない場合、`CurrentScheduler` クラス内の多くのメソッドによって、プロセスの既定のスケジューラがアタッチされます。 これは、このような呼び出し中にプロセスの既定のスケジューラが作成されることを意味する場合もあります。

## <a name="inheritance-hierarchy"></a>継承階層

`CurrentScheduler`

## <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="create"></a> 作成

`_Policy` パラメーターによって記述された動作を持つ新しいスケジューラを作成し、呼び出し元のコンテキストにアタッチします。 新しく作成されたスケジューラは、呼び出し元のコンテキストの現在のスケジューラになります。

```cpp
static void __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>パラメーター

*_Policy*<br/>
新しく作成されたスケジューラの動作を説明するスケジューラポリシー。

### <a name="remarks"></a>解説

スケジューラが呼び出し元のコンテキストにアタッチされると、スケジューラに参照カウントが暗黙的に配置されます。

`Create` メソッドを使用してスケジューラを作成した後、スケジューラをシャットダウンできるようにするために、将来のある時点で[Currentscheduler::D etach](#detach)メソッドを呼び出す必要があります。

このメソッドが既に別のスケジューラにアタッチされているコンテキストから呼び出された場合、既存のスケジューラは以前のスケジューラとして記憶され、新しく作成されたスケジューラは現在のスケジューラになります。 後で `CurrentScheduler::Detach` メソッドを呼び出すと、前のスケジューラが現在のスケジューラとして復元されます。

このメソッドは、 [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)や[invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)など、さまざまな例外をスローする場合があります。

## <a name="createschedulegroup"></a>CreateScheduleGroup

呼び出し元のコンテキストに関連付けられているスケジューラ内に新しいスケジュールグループを作成します。 パラメーター `_Placement` を受け取るバージョンを使用すると、新しく作成されたスケジュールグループ内のタスクが、そのパラメーターで指定された場所で実行されるようにバイアスされます。

```cpp
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```

### <a name="parameters"></a>パラメーター

*_Placement*<br/>
スケジュールグループ内のタスクがで実行されるようにバイアスされる場所への参照。

### <a name="return-value"></a>戻り値

新しく作成されたスケジュールグループへのポインター。 この `ScheduleGroup` オブジェクトには、最初の参照カウントが配置されています。

### <a name="remarks"></a>解説

呼び出し元のコンテキストにスケジューラが現在関連付けられていない場合、このメソッドを呼び出すと、プロセスの既定のスケジューラが作成されるか、または呼び出し元コンテキストにアタッチされます。

スケジュールグループに対する作業のスケジュールが完了したら、 [Release](schedulegroup-class.md#release)メソッドを呼び出す必要があります。 スケジューラがキューに登録されているすべての作業が完了すると、スケジューラはスケジュールグループを破棄します。

このスケジューラを明示的に作成した場合は、現在のコンテキストをデタッチすることによって、スケジューラで参照を解放する前に、その中にあるスケジュールグループへのすべての参照を解放する必要があることに注意してください。

## <a name="detach"></a>分離

現在のスケジューラを呼び出し元のコンテキストからデタッチし、以前にアタッチされたスケジューラを現在のスケジューラとして復元します (存在する場合)。 このメソッドから制御が戻った後、呼び出し元のコンテキストは、前に `CurrentScheduler::Create` または `Scheduler::Attach` のいずれかのメソッドを使用してコンテキストにアタッチされたスケジューラによって管理されます。

```cpp
static void __cdecl Detach();
```

### <a name="remarks"></a>解説

`Detach` メソッドは、スケジューラから参照カウントを暗黙的に削除します。

呼び出し元のコンテキストにスケジューラがアタッチされていない場合は、このメソッドを呼び出すと[scheduler_not_attached](scheduler-not-attached-class.md)例外がスローされます。

スケジューラによって内部および管理されているコンテキスト、または[scheduler:: Attach](scheduler-class.md#attach)メソッドまたは[Currentscheduler:: Create](#create)メソッド以外のメソッドを使用してアタッチされたコンテキストからこのメソッドを呼び出すと、 [improper_scheduler_detach](improper-scheduler-detach-class.md)例外がスローされます。

## <a name="get"></a>取得

呼び出し元のコンテキストに関連付けられているスケジューラへのポインターを返します。これは、現在のスケジューラとも呼ばれます。

```cpp
static Scheduler* __cdecl Get();
```

### <a name="return-value"></a>戻り値

呼び出し元のコンテキスト (現在のスケジューラ) に関連付けられているスケジューラへのポインター。

### <a name="remarks"></a>解説

呼び出し元のコンテキストにスケジューラが現在関連付けられていない場合、このメソッドを呼び出すと、プロセスの既定のスケジューラが作成されるか、または呼び出し元コンテキストにアタッチされます。 このメソッドによって返される `Scheduler` オブジェクトには、追加の参照は配置されません。

## <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors

呼び出し元のコンテキストに関連付けられているスケジューラの仮想プロセッサの現在の数を返します。

```cpp
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```

### <a name="return-value"></a>戻り値

スケジューラが呼び出し元のコンテキストに関連付けられている場合、そのスケジューラの仮想プロセッサの現在の数。それ以外の場合は、`-1`値です。

### <a name="remarks"></a>解説

呼び出し元のコンテキストがまだスケジューラに関連付けられていない場合、このメソッドはスケジューラの添付ファイルにはなりません。

このメソッドからの戻り値は、呼び出し元のコンテキストに関連付けられているスケジューラの仮想プロセッサの数を瞬間的にサンプリングしたものです。 この値は、返される瞬間に古くなる可能性があります。

## <a name="getpolicy"></a>GetPolicy

現在のスケジューラが作成されたポリシーのコピーを返します。

```cpp
static SchedulerPolicy __cdecl GetPolicy();
```

### <a name="return-value"></a>戻り値

現在のスケジューラが作成されたポリシーのコピー。

### <a name="remarks"></a>解説

呼び出し元のコンテキストにスケジューラが現在関連付けられていない場合、このメソッドを呼び出すと、プロセスの既定のスケジューラが作成されるか、または呼び出し元コンテキストにアタッチされます。

## <a name="id"></a>番号

現在のスケジューラの一意の識別子を返します。

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>戻り値

スケジューラが呼び出し元のコンテキストに関連付けられている場合は、そのスケジューラの一意の識別子。それ以外の場合は、`-1`値です。

### <a name="remarks"></a>解説

呼び出し元のコンテキストがまだスケジューラに関連付けられていない場合、このメソッドはスケジューラの添付ファイルにはなりません。

## <a name="isavailablelocation"></a>IsAvailableLocation

指定された場所が現在のスケジューラで使用できるかどうかを判断します。

```cpp
static bool __cdecl IsAvailableLocation(const location& _Placement);
```

### <a name="parameters"></a>パラメーター

*_Placement*<br/>
現在のスケジューラに対してクエリを実行する場所への参照。

### <a name="return-value"></a>戻り値

`_Placement` 引数によって指定された場所が現在のスケジューラで使用できるかどうかを示す値。

### <a name="remarks"></a>解説

呼び出し元のコンテキストがまだスケジューラに関連付けられていない場合、このメソッドはスケジューラの添付ファイルにはなりません。

戻り値は、指定された場所が使用可能かどうかを瞬間的にサンプリングすることに注意してください。 複数のスケジューラが存在する場合、動的リソース管理によって、任意の時点でスケジューラからリソースを追加または取得できます。 このような状況が発生した場合、特定の場所で可用性を変更できます。

## <a name="registershutdownevent"></a>RegisterShutdownEvent

現在のコンテキストに関連付けられているスケジューラがシャットダウンして自身を破棄するときに、`_ShutdownEvent` パラメーターで渡された Windows イベントハンドルをシグナル状態にします。 イベントがシグナル状態になると、スケジューラに対してスケジュールされていたすべての作業が完了します。 この方法では、複数のシャットダウンイベントを登録できます。

```cpp
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```

### <a name="parameters"></a>パラメーター

*_ShutdownEvent*<br/>
現在のコンテキストに関連付けられているスケジューラがシャットダウンして自身を破棄したときにランタイムによって通知される Windows イベントオブジェクトへのハンドル。

### <a name="remarks"></a>解説

呼び出し元のコンテキストにスケジューラがアタッチされていない場合は、このメソッドを呼び出すと[scheduler_not_attached](scheduler-not-attached-class.md)例外がスローされます。

## <a name="scheduletask"></a>ScheduleTask

呼び出し元のコンテキストに関連付けられているスケジューラ内の軽量タスクをスケジュールします。 軽量タスクは、ランタイムによって決定されるスケジュールグループに配置されます。 パラメーター `_Placement` を受け取るバージョンでは、指定された位置でタスクの実行がバイアスされます。

```cpp
static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data);

static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement);
```

### <a name="parameters"></a>パラメーター

*_Proc*<br/>
ライトウェイトタスクの本体を実行するために実行する関数へのポインター。

*_Data*<br/>
タスクの本体にパラメーターとして渡されるデータへの void ポインター。

*_Placement*<br/>
ライトウェイトタスクがで実行されるようにバイアスされる場所への参照。

### <a name="remarks"></a>解説

呼び出し元のコンテキストにスケジューラが現在関連付けられていない場合、このメソッドを呼び出すと、プロセスの既定のスケジューラが作成されるか、または呼び出し元コンテキストにアタッチされます。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[Scheduler クラス](scheduler-class.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[タスク スケジューラ](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
