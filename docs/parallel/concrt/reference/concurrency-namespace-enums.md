---
title: コンカレンシー名前空間を持つ列挙型
ms.date: 11/04/2016
f1_keywords:
- CONCRT/concurrency::Agents_EventType
- CONCRT/concurrency::Concrt_TraceFlags
- CONCRT/concurrency::CriticalRegionType
- CONCRT/concurrency::PolicyElementKey
- CONCRT/concurrency::SchedulerType
- CONCRT/concurrency::SwitchingProxyState
- CONCRT/concurrency::WinRTInitializationType
- CONCRT/concurrency::join_type
- CONCRT/concurrency::message_status Enumeration
ms.assetid: a40e3b2d-ad21-4229-9880-2cfa84f7ab8f
ms.openlocfilehash: 716c2d03e6d1ff67566bd28e5931996ea2d400af
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141315"
---
# <a name="concurrency-namespace-enums"></a>コンカレンシー名前空間を持つ列挙型

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[CriticalRegionType](#criticalregiontype)|[DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)|[PolicyElementKey](#policyelementkey)|
|[SchedulerType](#schedulertype)|[SchedulingProtocolType](#schedulingprotocoltype)|[SwitchingProxyState](#switchingproxystate)|
|[WinRTInitializationType](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

## <a name="agent_status"></a>agent_status 列挙型

`agent` の有効な状態。

```cpp
enum agent_status;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`agent_canceled`|`agent` は取り消されました。|
|`agent_created`|`agent` が作成されましたが、開始されていません。|
|`agent_done`|`agent` は取り消されずに終了しました。|
|`agent_runnable`|`agent` が開始されましたが、`run` メソッドが入力されていません。|
|`agent_started`|`agent` が開始されました。|

### <a name="remarks"></a>解説

詳細については、「[非同期エージェント](../../../parallel/concrt/asynchronous-agents.md)」を参照してください。

### <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

## <a name="agents_eventtype"></a>Agents_EventType 列挙型

エージェント ライブラリによって提供されるトレース機能を使用してトレースできるイベントの種類。

```cpp
enum Agents_EventType;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|オブジェクトの作成を表すイベントの種類です。|
|`AGENTS_EVENT_DESTROY`|オブジェクトの削除を表すイベントの種類です。|
|`AGENTS_EVENT_END`|一部の処理の終了を表すイベントの種類|
|`AGENTS_EVENT_LINK`|メッセージブロックのリンクを表すイベントの種類|
|`AGENTS_EVENT_NAME`|オブジェクトの名前を表すイベントの種類です。|
|`AGENTS_EVENT_SCHEDULE`|プロセスのスケジュールを表すイベントの種類|
|`AGENTS_EVENT_START`|一部の処理の開始を表すイベントの種類|
|`AGENTS_EVENT_UNLINK`|メッセージブロックのリンク解除を表すイベントの種類|

### <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

## <a name="concrt_eventtype"></a>ConcRT_EventType 列挙型

コンカレンシー ランタイムによって提供されるトレース機能を使用してトレースできるイベントの種類。

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|スケジューラにアタッチする操作を表すイベントの種類。|
|`CONCRT_EVENT_BLOCK`|コンテキストブロックの動作を表すイベントの種類。|
|`CONCRT_EVENT_DETACH`|スケジューラからデタッチする操作を表すイベントの種類。|
|`CONCRT_EVENT_END`|開始/終了イベントのペアの開始を示すイベントの種類。|
|`CONCRT_EVENT_GENERIC`|その他のイベントに使用されるイベントの種類。|
|`CONCRT_EVENT_IDLE`|コンテキストがアイドル状態になる操作を表すイベントの種類。|
|`CONCRT_EVENT_START`|開始/終了イベントのペアの開始を示すイベントの種類。|
|`CONCRT_EVENT_UNBLOCK`|コンテキストのブロックを解除する操作を表すイベントの種類。|
|`CONCRT_EVENT_YIELD`|コンテキストを生成する操作を表すイベントの種類。|

### <a name="requirements"></a>［要件］

**ヘッダー:** concrt .H**名前空間:** concurrency

## <a name="concrt_traceflags"></a>Concrt_TraceFlags 列挙型

イベントの種類のトレース フラグ。

```cpp
enum Concrt_TraceFlags;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`AgentEventFlag`||
|`AllEventsFlag`||
|`ContextEventFlag`||
|`PPLEventFlag`||
|`ResourceManagerEventFlag`||
|`SchedulerEventFlag`||
|`VirtualProcessorEventFlag`||

### <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

## <a name="criticalregiontype"></a>CriticalRegionType 列挙型

コンテキストが存在するクリティカル領域の種類。

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`InsideCriticalRegion`|コンテキストがクリティカル領域内にあることを示します。 クリティカルなリージョン内では、非同期保留はスケジューラから見えません。 このような中断が発生した場合、リソースマネージャーはスレッドが実行可能になるのを待機し、スケジューラを再度呼び出す代わりに再開するだけです。 このような領域内で行われたロックは、細心の注意を払って行う必要があります。|
|`InsideHyperCriticalRegion`|コンテキストがハイパークリティカル領域内にあることを示します。 ハイパークリティカルなリージョン内では、同期と非同期の両方の保留がスケジューラに表示されません。 このような中断やブロッキングが発生した場合、リソースマネージャーはスレッドが実行可能になるまで待機し、スケジューラを再度呼び出す代わりに再開するだけです。 このような領域内で行われたロックは、このような領域の外側で実行されているコードと共有しないでください。 これを行うと、予期しないデッドロックが発生します。|
|`OutsideCriticalRegion`|コンテキストが重要な領域の外側にあることを示します。|

### <a name="requirements"></a>［要件］

**ヘッダー:** concrtrm. h

## <a name="dynamicprogressfeedbacktype"></a>Dynamic進捗フィードの Backtype 列挙型

`DynamicProgressFeedback` ポリシーによって使用され、スケジューラのリソースのバランスを再調整する際の判断基準として、スケジューラから収集された統計情報に従うか、または `Activate` インターフェイスの `Deactivate` メソッドおよび `IVirtualProcessorRoot` メソッドの呼び出しによってアイドル状態との間で状態が変化する仮想プロセッサのみに基づくかを示します。 使用できるスケジューラポリシーの詳細については、「 [Policyelementkey](concurrency-namespace-enums.md)」を参照してください。

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`ProgressFeedbackDisabled`|スケジューラは、進行状況に関する情報を収集しません。 再調整は、基になるハードウェアスレッドのサブスクリプションレベルのみに基づいて行われます。 サブスクリプションレベルの詳細については、「 [Iexecutionresource:: CurrentSubscriptionLevel](IExecutionResource-structure.md)」を参照してください。<br /><br /> この値は、ランタイムで使用するために予約されています。|
|`ProgressFeedbackEnabled`|スケジューラは、進行状況に関する情報を収集し、リソースマネージャーに渡します。 リソースマネージャーは、基になるハードウェアスレッドのサブスクリプションレベルに加えて、スケジューラに代わってリソースを再調整するために、この統計情報を使用します。 サブスクリプションレベルの詳細については、「 [Iexecutionresource:: CurrentSubscriptionLevel](IExecutionResource-structure.md)」を参照してください。|

## <a name="join_type"></a>join_type 列挙型

`join` メッセージング ブロックの種類。

```cpp
enum join_type;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`greedy`|最長一致の `join` メッセージングブロックは、伝達時にメッセージをすぐに受け入れます。 これはより効率的ですが、ネットワーク構成によってはライブロックが発生する可能性があります。|
|`non_greedy`|最短一致の `join` メッセージングブロックは、メッセージを延期し、すべてが到着した後でそれらを使用します。 これらは動作することは保証されていますが、低速です。|

### <a name="requirements"></a>［要件］

**ヘッダー:** agents.h

## <a name="message_status"></a>message_status 列挙型

ブロックへの `message` オブジェクトの提供に対する有効な応答。

```cpp
enum message_status;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`accepted`|ターゲットがメッセージを受け入れました。|
|`declined`|ターゲットがメッセージを受け入れませんでした。|
|`missed`|ターゲットがメッセージを受け入れようとしましたが、使用できなくなりました。|
|`postponed`|ターゲットがメッセージを延期しました。|

### <a name="requirements"></a>［要件］

**ヘッダー:** agents.h

## <a name="policyelementkey"></a>PolicyElementKey 列挙型

ポリシー キーは、スケジューラの動作をさまざまな側面から表します。 各ポリシー要素は、キーと値の組み合わせで表現されます。 Scheduler ポリシーとスケジューラへの影響の詳細については、「[タスクスケジューラ](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)」を参照してください。

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`ContextPriority`|スケジューラ内の各コンテキストのオペレーティングシステムスレッドの優先順位。 このキーが値に設定されている場合 `INHERIT_THREAD_PRIORITY` スケジューラ内のコンテキストは、スケジューラを作成したスレッドの優先順位を継承します。<br /><br /> 有効な値: Windows `SetThreadPriority` 関数と特別な値の有効な値 `INHERIT_THREAD_PRIORITY`<br /><br /> 既定値: `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|スケジューラの各コンテキストの予約済みスタックサイズ (kb 単位)。<br /><br /> 有効な値: 正の整数<br /><br /> 既定値: `0`、スタックサイズのプロセスの既定値が使用されることを示します。|
|`DynamicProgressFeedback`|スケジューラから収集された統計情報に従ってスケジューラのリソースを再分配するか、基になるハードウェアスレッドのサブスクリプションレベルに基づいて作成するかを決定します。 詳細については、「 [Dynamicのフィードの Backtype](#dynamicprogressfeedbacktype)」を参照してください。<br /><br /> 有効な値: `DynamicProgressFeedbackType` 列挙型のメンバー `ProgressFeedbackEnabled` またはのいずれか `ProgressFeedbackDisabled`<br /><br /> 既定値: `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|`SchedulingProtocol` ポリシーキーが `EnhanceScheduleGroupLocality`値に設定されている場合、これにより、仮想プロセッサのローカルキューごとにキャッシュできる実行可能なコンテキストの最大数が指定されます。 通常、このようなコンテキストは、実行可能になる原因となった仮想プロセッサの後入れ先出し (LIFO) の順序で実行されます。 `SchedulingProtocol` キーが `EnhanceForwardProgress`値に設定されている場合、このポリシーキーは意味を持たないことに注意してください。<br /><br /> 有効な値: 負でない整数<br /><br /> 既定値: `8`|
|`MaxConcurrency`|スケジューラが必要とする最大同時実行レベル。 リソースマネージャーは、この多くの仮想プロセッサを最初に割り当てようとします。 特別な値の[Maxexecutionresources](concurrency-namespace-constants1.md#maxexecutionresources)は、目的の同時実行レベルがコンピューター上のハードウェアスレッドの数と同じであることを示します。 `MinConcurrency` に指定された値がコンピューター上のハードウェアスレッドの数より大きく、`MaxConcurrency` が `MaxExecutionResources`として指定されている場合、`MaxConcurrency` の値が `MinConcurrency`に設定されている内容と一致するようになります。<br /><br /> 有効な値: 正の整数と特別な値 `MaxExecutionResources`<br /><br /> 既定値: `MaxExecutionResources`|
|`MaxPolicyElementKey`|最大ポリシー要素キー。 有効な要素キーではありません。|
|`MinConcurrency`|リソースマネージャーによってスケジューラに提供される必要がある最小同時実行レベル。 スケジューラに割り当てられた仮想プロセッサの数が最小値を下回ることはありません。 特別な値の[Maxexecutionresources](concurrency-namespace-constants1.md#maxexecutionresources)は、最小同時実行レベルがコンピューター上のハードウェアスレッドの数と同じであることを示します。 `MaxConcurrency` に指定された値がコンピューターのハードウェアスレッド数よりも少なく、`MinConcurrency` が `MaxExecutionResources`として指定されている場合、`MinConcurrency` の値は `MaxConcurrency`に設定されている内容と一致するように減少します。<br /><br /> 有効な値は、負でない整数と `MaxExecutionResources`特殊な値です。 同時実行ランタイムスケジューラの構築に使用される scheduler ポリシーでは、`0` の値が無効であることに注意してください。<br /><br /> 既定値: `1`|
|`SchedulerKind`|スケジューラが基になる実行コンテキストに対して使用するスレッドの種類。 詳細については、「[スケジューラの種類](#schedulertype)」を参照してください。<br /><br /> 有効な値: `SchedulerType` 列挙型のメンバー。たとえば、`ThreadScheduler`<br /><br /> 既定値: `ThreadScheduler`。 これは、すべてのオペレーティングシステム上の Win32 スレッドに変換されます。|
|`SchedulingProtocol`|スケジューラによって使用されるスケジューリングアルゴリズムについて説明します。 詳細については、「 [SchedulingProtocolType](#schedulingprotocoltype)」を参照してください。<br /><br /> 有効な値: `SchedulingProtocolType` 列挙型のメンバー `EnhanceScheduleGroupLocality` またはのいずれか `EnhanceForwardProgress`<br /><br /> 既定値: `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|ハードウェアスレッドあたりの仮想プロセッサの仮の数。 ターゲットオーバーサブスクリプション係数は、必要に応じて、マシン上のハードウェアスレッドとの `MaxConcurrency` を満たすために、リソースマネージャーによって増やすことができます。<br /><br /> 有効な値: 正の整数<br /><br /> 既定値: `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

## <a name="schedulertype"></a>スケジューラの種類の列挙型

基になる実行コンテキスト用にスケジューラが利用するスレッドの種類を示すために、`SchedulerKind` ポリシーにより使用されます。 使用できるスケジューラポリシーの詳細については、「 [Policyelementkey](concurrency-namespace-enums.md)」を参照してください。

```cpp
enum SchedulerType;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`ThreadScheduler`|通常の Win32 スレッドの明示的な要求を示します。|
|`UmsThreadDefault`|ユーザーモードスケジュール可能 (UMS) スレッドは、Visual Studio 2013 の同時実行ランタイムではサポートされていません。 `UmsThreadDefault` ポリシーの値として `SchedulerType` を使用しても、エラーは発生しません。 ただし、そのポリシーで作成されたスケジューラでは、既定で Win32 スレッドが使用されます。|

### <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

## <a name="schedulingprotocoltype"></a>SchedulingProtocolType 列挙型

スケジューラに使用されるスケジューリング アルゴリズムを記述するために、`SchedulingProtocol` ポリシーによって使用されます。 使用できるスケジューラポリシーの詳細については、「 [Policyelementkey](concurrency-namespace-enums.md)」を参照してください。

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`EnhanceForwardProgress`|スケジューラは、各タスクの実行後にスケジュールグループを使用してラウンドロビンを優先します。 ブロックされていないコンテキストは、通常、先入れ先出し (FIFO) 方式でスケジュールされます。 仮想プロセッサは、ブロックされていないコンテキストをキャッシュしません。|
|`EnhanceScheduleGroupLocality`|スケジューラは、別のスケジュールグループに移動する前に、現在のスケジュールグループ内のタスクの作業を続行することを優先します。 ブロックされていないコンテキストは仮想プロセッサごとにキャッシュされ、通常は、そのブロックを解除した仮想プロセッサによって後入れ先出し (LIFO) 形式でスケジュールされます。|

### <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

## <a name="switchingproxystate"></a>SwitchingProxyState 列挙型

あるスレッド プロキシから別のスレッド プロキシへの協調的なコンテキスト切り替えを実行するときに、スレッド プロキシの状態を示すために使用します。

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`Blocking`|呼び出し元のスレッドが協調的にブロックされており、後で再度実行して他のアクションを実行するまで、呼び出し元が排他的に所有する必要があることを示します。|
|`Idle`|呼び出し元のスレッドがスケジューラによって不要になり、リソースマネージャーに返されることを示します。 ディスパッチされていたコンテキストは、リソースマネージャーで利用できなくなりました。|
|`Nesting`|別のスケジューラにアタッチするために、呼び出し元のスレッドが子スケジューラを入れ子にし、呼び出し元が必要とすることを示します。|

### <a name="remarks"></a>解説

`SwitchingProxyState` 型のパラメーターがメソッド `IThreadProxy::SwitchTo` に渡され、呼び出しを行っているスレッドプロキシをリソースマネージャーに処理する方法を指定します。

この型の使用方法の詳細については、「 [Ithreadproxy:: SwitchTo](ithreadproxy-structure.md#switchto)」を参照してください。

## <a name="task_group_status"></a>task_group_status 列挙型

`task_group` オブジェクトまたは `structured_task_group` オブジェクトの実行状態を示します。 この型の値は、タスク グループに対してスケジュールされたタスクが完了するのを待機している多数のメソッドによって返されます。

```cpp
enum task_group_status;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`canceled`|`task_group` オブジェクトまたは `structured_task_group` オブジェクトは取り消されました。 1 つまたは複数のタスクが実行されていない可能性があります。|
|`completed`|`task_group` オブジェクトまたは `structured_task_group` オブジェクトのキューに格納されたタスクは、正常に完了しました。|
|`not_complete`|`task_group` オブジェクトのキューに格納されたタスクは完了していません。 この値は、コンカレンシー ランタイムによって現在返されていないことに注意してください。|

### <a name="requirements"></a>［要件］

**ヘッダー:** pplinterface.h

## <a name="winrtinitializationtype"></a>WinRTInitializationType 列挙型

`WinRTInitialization` ポリシーによって使用され、Windows 8 以上のオペレーティング システムで実行されるアプリケーション用のスケジューラ スレッドで、Windows ランタイムを初期化するかどうか、またどのように初期化するかを表します。 使用できるスケジューラポリシーの詳細については、「 [Policyelementkey](concurrency-namespace-enums.md)」を参照してください。

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`DoNotInitializeWinRT`|アプリケーションが Windows 8 またはそれ以降のバージョンのオペレーティング システムで実行される場合、スケジューラ内のスレッドは、Windows ランタイムを初期化しません。|
|`InitializeWinRTAsMTA`|アプリケーションが Windows 8 またはそれ以降のバージョンのオペレーティング システムで実行される場合、スケジューラ内の各スレッドは、Windows ランタイムを初期化し、マルチスレッド アパートメントの一部であることを宣言します。|

## <a name="requirements"></a>［要件］

**ヘッダー:** concrt .h

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
