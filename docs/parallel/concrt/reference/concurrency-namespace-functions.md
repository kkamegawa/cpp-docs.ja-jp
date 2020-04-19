---
title: コンカレンシー名前空間の関数
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::Alloc
- concrt/concurrency::DisableTracing
- concrt/concurrency::EnableTracing
- concrtrm/concurrency::GetExecutionContextId
- concrtrm/concurrency::GetOSVersion
- concrtrm/concurrency::GetProcessorNodeCount
- concrtrm/concurrency::GetSchedulerId
- agents/concurrency::asend
- ppltasks/concurrency::cancel_current_task
- ppltasks/concurrency::create_async
- ppltasks/concurrency::create_task
- concurrent_vector/concurrency::internal_assign_iterators
- ppl/concurrency::interruption_point
- agents/concurrency::make_choice
- agents/concurrency::make_greedy_join
- ppl/concurrency::make_task
- ppl/concurrency::parallel_buffered_sort
- ppl/concurrency::parallel_for_each
- ppl/concurrency::parallel_invoke
- ppl/concurrency::parallel_reduce
- ppl/concurrency::parallel_sort
- agents/concurrency::receive
- ppl/concurrency::run_with_cancellation_token
- pplconcrt/concurrency::set_ambient_scheduler
- concrt/concurrency::set_task_execution_resources
- ppltasks/concurrency::task_from_exception
- ppltasks/concurrency::task_from_result
- concrt/concurrency::wait
- ppltasks/concurrency::when_all
- ppltasks/concurrency::when_any
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
ms.openlocfilehash: 4005ae888511ec987fe83ab3d616aa0fc3675a22
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143256"
---
# <a name="concurrency-namespace-functions"></a>コンカレンシー名前空間の関数

||||
|-|-|-|
|[割り当て](#alloc)|[CreateResourceManager](#createresourcemanager)|[DisableTracing](#disabletracing)|
|[EnableTracing](#enabletracing)|[Free](#free)|[GetExecutionContextId](#getexecutioncontextid)|
|[GetOSVersion](#getosversion)|[GetProcessorCount](#getprocessorcount)|[GetProcessorNodeCount](#getprocessornodecount)|
|[GetSchedulerId](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend](#asend)|
|[cancel_current_task](#cancel_current_task)|[オフ](#clear)|[create_async](#create_async)|
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|
|[parallel_buffered_sort](#parallel_buffered_sort)|[parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|
|[parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[受け取れ](#receive)|
|[run_with_cancellation_token](#run_with_cancellation_token)|[send](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|
|[set_task_execution_resources](#set_task_execution_resources)|[swap](#swap)|[task_from_exception](#task_from_exception)|
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[待機](#wait)|
|[when_all](#when_all)|[when_any](#when_any)|

## <a name="alloc"></a>割り当て

コンカレンシー ランタイムのキャッシュ サブアロケータから、指定したサイズのメモリ ブロックを割り当てます。

```cpp
void* __cdecl Alloc(size_t _NumBytes);
```

### <a name="parameters"></a>パラメーター

*_NumBytes*<br/>
割り当てるメモリのバイト数。

### <a name="return-value"></a>戻り値

新しく割り当てられたメモリへのポインター。

### <a name="remarks"></a>解説

アプリケーションでキャッシュサブアロケータを使用することによってメリットが得られるシナリオの詳細については、「[タスクスケジューラ](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)」を参照してください。

## <a name="asend"></a>asend

ターゲット ブロックにデータを反映するタスクをスケジュールする非同期送信操作です。

```cpp
template <class T>
bool asend(
    _Inout_ ITarget<T>* _Trg,
    const T& _Data);

template <class T>
bool asend(
    ITarget<T>& _Trg,
    const T& _Data);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
送信されるデータの型。

*_Trg*<br/>
データが送信されるターゲットへのポインターまたは参照。

*_Data*<br/>
送信されるデータへの参照。

### <a name="return-value"></a>戻り値

メソッドが返される前にメッセージが受け入れられた場合は**true** 、それ以外の場合は**false** 。

### <a name="remarks"></a>解説

詳細については、「[メッセージパッシング関数](../../../parallel/concrt/message-passing-functions.md)」を参照してください。

## <a name="cancel_current_task"></a>cancel_current_task

現在実行中のタスクを取り消します。 この関数は、タスクの実行を中止して `canceled` 状態に遷移させるために、タスクの本体から呼び出すことができます。

`task` の本体以外では、この関数を呼び出すシナリオはサポートされません。 これを行うと、アプリケーションのクラッシュや停止など、定義されていない動作が発生します。

```cpp
inline __declspec(noreturn) void __cdecl cancel_current_task();
```

## <a name="clear"></a>クリア

同時実行キューをクリアし、現在エンキューされている要素を破棄します。 このメソッドはコンカレンシー セーフではありません。

```cpp
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```

### <a name="parameters"></a>パラメーター

*T*<br/>

*_Ax*<br/>

## <a name="create_async"></a>create_async

ユーザーが指定したラムダまたは関数オブジェクトに基づいて Windows ランタイムの非同期構造を作成します。 `create_async` の戻り値の型は、`IAsyncAction^`、`IAsyncActionWithProgress<TProgress>^`、`IAsyncOperation<TResult>^`、`IAsyncOperationWithProgress<TResult, TProgress>^` のいずれかで、メソッドに渡されるラムダのシグネチャに基づいています。

```cpp
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```

### <a name="parameters"></a>パラメーター

*_Function*<br/>
[Type]\(種類\)。

*_Func*<br/>
Windows ランタイムの非同期構造の作成元となるラムダまたは関数オブジェクト。

### <a name="return-value"></a>戻り値

IAsyncAction ^、IAsyncActionWithProgress\<TProgress > ^、IAsyncOperation\<TResult > ^、または IAsyncOperationWithProgress\<TResult、TProgress > ^ によって表される非同期コンストラクト。 返されるインターフェイスは、関数に渡されるラムダのシグネチャによって異なります。

### <a name="remarks"></a>解説

ラムダの戻り値の型によって、構造がアクションであるか操作であるかが判別されます。

ラムダが void を返すと、アクションが作成されます。 ラムダが型 `TResult` の結果を返すと、TResult の操作が作成されます。

ラムダは `task<TResult>` を返すことがあります。この戻り値は、それ自体に非同期操作をカプセル化します。また、非同期操作を表すタスクのチェーンの継続として機能する場合もあります。 この場合、ラムダ自体はインラインで実行されます。これは、タスクが非同期的に実行されたタスクであり、ラムダの戻り値の型がラップ解除され `create_async` によって返される非同期構造を生成するためです。 これは、タスクを返すラムダ\<void > によってアクションが作成されることを意味し、\<TResult > タスクを返すラムダによって、TResult の操作が作成されることを意味します。

ラムダでは、引数を使用しない場合、または 1 つか 2 つの引数を使用する場合があります。 有効な引数は `progress_reporter<TProgress>` と `cancellation_token` です。これらを両方とも使用する場合は、この順序で指定してください。 ラムダで引数を使用しないと、進行状況の報告機能を持たない非同期構造が作成されます。 Progress_reporter\<TProgress > を受け取るラムダでは、`report` オブジェクトの progress_reporter メソッドが呼び出されるたびに、型 TProgress の進行状況を報告する非同期コンストラクトが返さ `create_async` れます。 cancellation_token を使用するラムダでは、そのトークンを利用して取り消しを確認する場合があります。また、作成されるタスクにこのトークンを渡す場合もあります。これにより、非同期構造を取り消すと、それらのタスクも取り消されます。

ラムダまたは関数オブジェクトの本体が結果 (タスク\<TResult >) を返した場合、ランタイムが暗黙的に作成するタスクのコンテキストで、プロセス MTA 内でラムダが非同期的に実行されます。 `IAsyncInfo::Cancel` のメソッドにより、暗黙のタスクが取り消されます。

ラムダの本体がタスクを返す場合、ラムダはインラインで実行されます。また、ラムダが型 `cancellation_token` の引数を使用するように宣言すると、タスクの作成時にこのトークンを渡すことによって、ラムダ内で作成されるタスクの取り消しをトリガーできます。 また、トークンに対して `register_callback` メソッドを使用すると、生成される非同期操作や非同期アクションで `IAsyncInfo::Cancel` を呼び出すときに、ランタイムでコールバックを呼び出すこともできます。

この関数は、Windows ランタイムアプリでのみ使用できます。

## <a name="createresourcemanager"></a>CreateResourceManager

コンカレンシー ランタイムのリソース マネージャーのシングルトン インスタンスを表すインターフェイスを返します。 リソース マネージャーは、相互の連携を必要とするスケジューラにリソースを割り当てます。

```cpp
IResourceManager* __cdecl CreateResourceManager();
```

### <a name="return-value"></a>戻り値

`IResourceManager` インターフェイス。

### <a name="remarks"></a>解説

それ以降、このメソッドを複数回呼び出すと、リソース マネージャーの同じインスタンスが返されます。 メソッドを呼び出すたびに、リソースマネージャーの参照カウントがインクリメントされます。また、スケジューラがリソースマネージャーとの通信を完了したときに、 [Iresourcemanager:: Release](iresourcemanager-structure.md)メソッドの呼び出しと照合する必要があります。

オペレーティングシステムが同時実行ランタイムでサポートされていない場合、 [unsupported_os](unsupported-os-class.md)がスローされます。

## <a name="create_task"></a>create_task

PPL[タスク](task-class.md)オブジェクトを作成します。 `create_task` は、タスク コンストラクターを使用した任意の場所で使用できます。 タスクの作成中に `auto` キーワードが使用できるようになるため、これは参考用として用意されています。

```cpp
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
パラメーターの型。これに基づいてタスクが構築されます。

*_ReturnType*<br/>
[Type]\(種類\)。

*_Param*<br/>
パラメーター。これに基づいてタスクが構築されます。 UWP アプリでタスクを使用している場合は、ラムダまたは関数オブジェクト、`task_completion_event` オブジェクト、別の `task` オブジェクト、または Windows:: Foundation:: IAsyncInfo インターフェイスを指定できます。

*_TaskOptions*<br/>
タスクオプション。

*_Task*<br/>
作成するタスクです。

### <a name="return-value"></a>戻り値

型 `T` の新しいタスク。`_Param` から推論されます。

### <a name="remarks"></a>解説

最初のオーバーロードは、単一のパラメーターを受け取るタスク コンストラクターのように動作します。

2 番目のオーバーロードは、新しく作成されたタスクで指定されたキャンセル トークンを関連付けます。 このオーバーロードを使用すると、最初のパラメーターとして別の `task` オブジェクトを渡すことができません。

返されたタスクの種類は、関数の最初のパラメーターから推測されます。 `_Param` が `task_completion_event<T>`、`task<T>`、または型 `T` か型 `task<T>` を返すファンクタの場合、作成されたタスクの型は `task<T>` です。

UWP アプリで、`_Param` が Windows:: Foundation:: IAsyncOperation\<T > ^ または Windows:: Foundation:: IAsyncOperationWithProgress\<T、P > ^、またはこれらの型のいずれかを返すファンクタの場合、作成されたタスクは `task<T>`型になります。 `_Param` の型が Windows:: Foundation:: IAsyncAction ^ または Windows:: Foundation:: IAsyncActionWithProgress\<P > ^ の場合、または、これらの型のいずれかを返すファンクタの場合、作成されたタスクの型は `task<void>`になります。

## <a name="disabletracing"></a>DisableTracing

コンカレンシー ランタイムでのトレースを無効にします。 この関数は、ETW トレースが既定で未登録であるため非推奨とされます。

```cpp
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```

### <a name="return-value"></a>戻り値

トレースが正しく無効にされている場合は、`S_OK` が返されます。 トレースが以前に開始されていなかった場合は、`E_NOT_STARTED` が返されます。

## <a name="enabletracing"></a>EnableTracing

コンカレンシー ランタイムでトレースを有効にします。 この関数は、ETW トレースが既定でオンであるため非推奨とされます。

```cpp
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```

### <a name="return-value"></a>戻り値

トレースが正常に開始された場合、`S_OK` が返されます。それ以外の場合は `E_NOT_STARTED` が返されます。

## <a name="free"></a>空け

以前に `Alloc` メソッドによってコンカレンシー ランタイムのキャッシュ サブアロケータに割り当てられたメモリ ブロックを解放します。

```cpp
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```

### <a name="parameters"></a>パラメーター

*_PAllocation*<br/>
以前に `Alloc` メソッドによって割り当てられた解放するメモリへのポインター。 `_PAllocation` パラメーターの値が `NULL` に設定されている場合、このメソッドはそれを無視してすぐに制御を戻します。

### <a name="remarks"></a>解説

アプリケーションでキャッシュサブアロケータを使用することによってメリットが得られるシナリオの詳細については、「[タスクスケジューラ](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)」を参照してください。

## <a name="get_ambient_scheduler"></a>get_ambient_scheduler

```cpp
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```

### <a name="return-value"></a>戻り値

## <a name="getexecutioncontextid"></a>GetExecutionContextId

`IExecutionContext` インターフェイスを実装する実行コンテキストに割り当てることのできる一意識別子を返します。

```cpp
unsigned int __cdecl GetExecutionContextId();
```

### <a name="return-value"></a>戻り値

実行コンテキストの一意の識別子。

### <a name="remarks"></a>解説

このメソッドを使用して、リソースマネージャーによって提供されるいずれかのメソッドにパラメーターとして `IExecutionContext` インターフェイスを渡す前に、実行コンテキストの識別子を取得します。

## <a name="getosversion"></a>GetOSVersion

オペレーティング システムのバージョンを返します。

```cpp
IResourceManager::OSVersion __cdecl GetOSVersion();
```

### <a name="return-value"></a>戻り値

オペレーティング システムを表す列挙値。

### <a name="remarks"></a>解説

オペレーティングシステムが同時実行ランタイムでサポートされていない場合、 [unsupported_os](unsupported-os-class.md)がスローされます。

## <a name="getprocessorcount"></a>GetProcessorCount

基になるシステム上のハードウェア スレッドの数を返します。

```cpp
unsigned int __cdecl GetProcessorCount();
```

### <a name="return-value"></a>戻り値

ハードウェア スレッドの数。

### <a name="remarks"></a>解説

オペレーティングシステムが同時実行ランタイムでサポートされていない場合、 [unsupported_os](unsupported-os-class.md)がスローされます。

## <a name="getprocessornodecount"></a>GetProcessorNodeCount

基になるシステム上の NUMA ノードまたはプロセッサ パッケージの数を返します。

```cpp
unsigned int __cdecl GetProcessorNodeCount();
```

### <a name="return-value"></a>戻り値

NUMA ノードまたはプロセッサ パッケージの数。

### <a name="remarks"></a>解説

システムに含まれる NUMA ノードの数がプロセッサ パッケージの数より多い場合は、NUMA ノードの数が返されます。それ以外の場合は、プロセッサ パッケージの数が返されます。

オペレーティングシステムが同時実行ランタイムでサポートされていない場合、 [unsupported_os](unsupported-os-class.md)がスローされます。

## <a name="getschedulerid"></a>GetSchedulerId

`IScheduler` インターフェイスを実装するスケジューラに割り当てることができる一意識別子を返します。

```cpp
unsigned int __cdecl GetSchedulerId();
```

### <a name="return-value"></a>戻り値

スケジューラの一意の識別子。

### <a name="remarks"></a>解説

このメソッドを使用して、リソースマネージャーによって提供されるいずれかのメソッドにパラメーターとして `IScheduler` インターフェイスを渡す前に、スケジューラの識別子を取得します。

## <a name="internal_assign_iterators"></a>internal_assign_iterators

```cpp
template<typename T, class _Ax>
template<class _I>
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```

### <a name="parameters"></a>パラメーター

*T*<br/>

*_Ax*<br/>

*_I*<br/>

*first*<br/>

*last*<br/>

## <a name="interruption_point"></a>interruption_point

取り消しの割り込みポイントを作成します。 この関数が呼び出されるコンテキストで取り消しが進行中の場合、現在実行中の並列処理を中止する内部例外がスローされます。 取り消しが進行中でない場合は、何も実行されません。

```cpp
inline void interruption_point();
```

### <a name="remarks"></a>解説

`interruption_point()` 関数によってスローされた内部キャンセル例外をキャッチすることはできません。 この例外は、ランタイムによってキャッチおよび処理され、プログラムが異常終了する原因となる可能性があります。

## <a name="is_current_task_group_canceling"></a>is_current_task_group_canceling

現在のコンテキストで現在インラインで実行されているタスク グループがアクティブなキャンセル処理中である (または間もなくキャンセル処理が開始される) かどうかを示す値を返します。 現在のコンテキストで現在インラインで実行されているタスク グループが存在しない場合は、`false` が返されます。

```cpp
bool __cdecl is_current_task_group_canceling();
```

### <a name="return-value"></a>戻り値

現在実行中のタスクグループがキャンセルされている場合は**true** 、それ以外の場合は**false** 。

### <a name="remarks"></a>解説

詳細については、「[キャンセル](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)」を参照してください。

## <a name="make_choice"></a>make_choice

オプションの `choice` や `Scheduler`、および 2 つ以上の入力ソースから `ScheduleGroup` メッセージング ブロックを構築します。

```cpp
template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    Scheduler& _PScheduler,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    ScheduleGroup& _PScheduleGroup,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>パラメーター

*T1*<br/>
1 番目のソースのメッセージ ブロックの型。

*T2*<br/>
2 番目のソースのメッセージ ブロックの型。

*_PScheduler*<br/>
その内部で `Scheduler` メッセージング ブロックの反映タスクがスケジュールされる `choice` オブジェクト。

*_Item1*<br/>
1 番目のソース。

*_Item2*<br/>
2 番目のソース。

*_Items*<br/>
その他のソース。

*_PScheduleGroup*<br/>
その内部で `ScheduleGroup` メッセージング ブロックの反映タスクがスケジュールされる `choice` オブジェクト。 使用される `Scheduler` オブジェクトは、スケジュール グループによって暗黙的に指定されます。

### <a name="return-value"></a>戻り値

2 個またはそれ以上の入力ソースを持つ `choice` メッセージ ブロック。

## <a name="make_greedy_join"></a>make_greedy_join

オプションの `greedy multitype_join` や `Scheduler`、および 2 つ以上の入力ソースから `ScheduleGroup` メッセージング ブロックを構築します。

```cpp
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>,greedy> make_greedy_join(
    Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    T1 _Item1,
    T2 _Items,
    Ts... _Items);
```

### <a name="parameters"></a>パラメーター

*T1*<br/>
1 番目のソースのメッセージ ブロックの型。

*T2*<br/>
2 番目のソースのメッセージ ブロックの型。

*_PScheduler*<br/>
その内部で `Scheduler` メッセージング ブロックの反映タスクがスケジュールされる `multitype_join` オブジェクト。

*_Item1*<br/>
1 番目のソース。

*_Item2*<br/>
2 番目のソース。

*_Items*<br/>
その他のソース。

*_PScheduleGroup*<br/>
その内部で `ScheduleGroup` メッセージング ブロックの反映タスクがスケジュールされる `multitype_join` オブジェクト。 使用される `Scheduler` オブジェクトは、スケジュール グループによって暗黙的に指定されます。

### <a name="return-value"></a>戻り値

2 個またはそれ以上の入力ソースを持つ `greedy multitype_join` メッセージ ブロック。

## <a name="make_join"></a>make_join

オプションの `non_greedy multitype_join` や `Scheduler`、および 2 つ以上の入力ソースから `ScheduleGroup` メッセージング ブロックを構築します。

```cpp
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>>
    make_join(
Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>パラメーター

*T1*<br/>
1 番目のソースのメッセージ ブロックの型。

*T2*<br/>
2 番目のソースのメッセージ ブロックの型。

*_PScheduler*<br/>
その内部で `Scheduler` メッセージング ブロックの反映タスクがスケジュールされる `multitype_join` オブジェクト。

*_Item1*<br/>
1 番目のソース。

*_Item2*<br/>
2 番目のソース。

*_Items*<br/>
その他のソース。

*_PScheduleGroup*<br/>
その内部で `ScheduleGroup` メッセージング ブロックの反映タスクがスケジュールされる `multitype_join` オブジェクト。 使用される `Scheduler` オブジェクトは、スケジュール グループによって暗黙的に指定されます。

### <a name="return-value"></a>戻り値

2 個またはそれ以上の入力ソースを持つ `non_greedy multitype_join` メッセージ ブロック。

## <a name="make_task"></a>make_task

`task_handle` オブジェクトを作成するためのファクトリ メソッドです。

```cpp
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```

### <a name="parameters"></a>パラメーター

*_Function*<br/>
`task_handle` オブジェクトによって表される作業を実行するために呼び出される関数オブジェクトの型。

*_Func*<br/>
`task_handle` オブジェクトによって表される作業を実行するために呼び出される関数。 これには、ラムダファンクタ、関数へのポインター、または `void operator()()`シグネチャを持つ関数呼び出し演算子のバージョンをサポートする任意のオブジェクトを指定できます。

### <a name="return-value"></a>戻り値

`task_handle` オブジェクト。

### <a name="remarks"></a>解説

この関数は、ラムダ式を使用して `task_handle` オブジェクトを作成する必要がある場合に便利です。ラムダファンクタの真の型がわからなくてもオブジェクトを作成できるためです。

## <a name="parallel_buffered_sort"></a>parallel_buffered_sort

指定された範囲の要素を、降順以外の順序、または二項述語によって指定された順序の基準に従って並列に配置します。 この関数は、比較ベースで不安定なインプレース並べ替えという点で `std::sort` と意味が同じです。ただし、`O(n)` 追加スペースが必要で、並べ替えている要素を既定で初期化する必要があります。

```cpp
template<typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>パラメーター

*_Random_iterator*<br/>
入力範囲の反復子の型。

*_Allocator*<br/>
C++標準ライブラリ互換メモリアロケーターの型。

*_Function*<br/>
二項比較子の型。

*_Begin*<br/>
並べ替えられる範囲内の最初の要素の位置を示すランダム アクセス反復子。

*_End*<br/>
並べ替えられる範囲内の最後の要素の 1 つ後ろの位置を示すランダム アクセス反復子。

*_Alloc*<br/>
標準ライブラリとC++互換性のあるメモリアロケーターのインスタンス。

*_Func*<br/>
順序の連続する要素によって満たされる比較条件を定義するユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。 この比較子関数は、シーケンスからの要素のペアで厳密弱順序を強制する必要があります。

*_Chunk_size*<br/>
並列実行のために2つに分割されるチャンクの最低限サイズ。

### <a name="remarks"></a>解説

すべてのオーバーロードには `n * sizeof(T)` 追加の領域が必要です。 `n` は並べ替えられる要素の数であり、`T` は要素の型です。 ほとんどの場合 parallel_buffered_sort は[parallel_sort](concurrency-namespace-functions.md)よりもパフォーマンスの向上を示しており、使用可能なメモリがある場合は parallel_sort で使用する必要があります。

バイナリ比較子を指定しない場合は `std::less` が既定値として使用されるため、演算子 `operator<()`を指定するために要素型が必要になります。

アロケーターの型またはインスタンスを指定しない場合はC++ 、標準ライブラリのメモリアロケーター `std::allocator<T>` を使用してバッファーが割り当てられます。

このアルゴリズムでは、入力範囲が2つのチャンクに分割され、各チャンクが連続して2つのサブチャンクに分割され、並列で実行されます。 省略可能な引数 `_Chunk_size` を使用すると、< `_Chunk_size` 直列にサイズのチャンクを処理する必要があることをアルゴリズムに示すことができます。

## <a name="parallel_for"></a>parallel_for

`parallel_for` は、一定の範囲のインデックスを反復処理し、各反復処理で、ユーザーが指定した関数を並列で実行します。

```cpp
template <typename _Index_type, typename _Function, typename _Partitioner>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func,
    _Partitioner&& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const static_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const simple_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    affinity_partitioner& _Part);
```

### <a name="parameters"></a>パラメーター

*_Index_type*<br/>
反復処理に使用されているインデックスの種類。

*_Function*<br/>
各反復処理で実行される関数の型。

*_Partitioner*<br/>
指定された範囲をパーティション分割するために使用されるパーティショナーの型。

*first*<br/>
反復処理に含める最初のインデックス。

*last*<br/>
反復処理に含める最後のインデックスの1つ後ろのインデックス。

*_Step*<br/>
`first` から `last`に反復するときにステップ実行する値。 手順は正の数値である必要があります。 ステップが1未満の場合、 [invalid_argument](../../../standard-library/invalid-argument-class.md)がスローされます。

*_Func*<br/>
各反復処理で実行される関数。 これには、ラムダ式、関数ポインター、またはシグネチャ `void operator()(_Index_type)`を持つ関数呼び出し演算子のバージョンをサポートする任意のオブジェクトを指定できます。

*_Part*<br/>
パーティショナーオブジェクトへの参照。 引数には、`const`[auto_partitioner](auto-partitioner-class.md)`&`のいずれか、`const`[static_partitioner](static-partitioner-class.md)`&`、 [`const`simple_partitioner`&` また](simple-partitioner-class.md)は[affinity_partitioner](affinity-partitioner-class.md)`&`[オブジェクトが](affinity-partitioner-class.md)使用されている場合、その参照は非定数の左辺値参照である必要があります。これにより、アルゴリズムは将来のループの状態を保存して再利用することができます。

### <a name="remarks"></a>解説

詳細については、「[並列アルゴリズム](../../../parallel/concrt/parallel-algorithms.md)」を参照してください。

## <a name="parallel_for_each"></a>parallel_for_each

`parallel_for_each` は、指定された関数を範囲内の各要素に並列で適用します。 意味的には `for_each` 名前空間の `std` 関数と同等ですが、要素に対する反復処理が並列で行われる点、および反復処理の順序が指定されていない点が異なります。 引数 `_Func` は、`operator()(T)` の形式の関数呼び出し演算子をサポートしている必要があります (`T` パラメーターは反復処理するコンテナーの項目の種類を示します)。

```cpp
template <typename _Iterator, typename _Function>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func);

template <typename _Iterator, typename _Function, typename _Partitioner>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func,
    _Partitioner&& _Part);
```

### <a name="parameters"></a>パラメーター

*_Iterator*<br/>
コンテナーを反復処理するために使用される反復子の型。

*_Function*<br/>
範囲内の各要素に適用される関数の型。

*_Partitioner*<br/>
*first*<br/>
並列反復処理に含める最初の要素の位置を示す反復子。

*last*<br/>
並列反復処理に含まれる最後の要素の1つ後ろの位置を示す反復子。

*_Func*<br/>
範囲内の各要素に適用されるユーザー定義関数オブジェクト。

*_Part*<br/>
パーティショナーオブジェクトへの参照。 引数には、`const`[auto_partitioner](auto-partitioner-class.md)`&`のいずれか、`const`[static_partitioner](static-partitioner-class.md)`&`、 [`const`simple_partitioner`&` また](simple-partitioner-class.md)は[affinity_partitioner](affinity-partitioner-class.md)`&`[オブジェクトが](affinity-partitioner-class.md)使用されている場合、その参照は非定数の左辺値参照である必要があります。これにより、アルゴリズムは将来のループの状態を保存して再利用することができます。

### <a name="remarks"></a>解説

[auto_partitioner](auto-partitioner-class.md)は、明示的なパーティショナーなしでオーバーロードに使用されます。

ランダムアクセスをサポートしていない反復子の場合は、 [auto_partitioner](auto-partitioner-class.md)のみがサポートされます。

詳細については、「[並列アルゴリズム](../../../parallel/concrt/parallel-algorithms.md)」を参照してください。

## <a name="parallel_invoke"></a>parallel_invoke

パラメーターとして渡された関数オブジェクトを並列実行し、実行が完了するまでブロックします。 各関数オブジェクトは、ラムダ式、関数へのポインター、またはシグネチャ `void operator()()` を持つ関数呼び出し演算子をサポートするオブジェクトになります。

```cpp
template <typename _Function1, typename _Function2>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2);

template <typename _Function1, typename _Function2, typename _Function3>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9,
    typename _Function10>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9,
    const _Function10& _Func10);
```

### <a name="parameters"></a>パラメーター

*_Function1*<br/>
並列で実行される最初の関数オブジェクトの型。

*_Function2*<br/>
並列で実行される2番目の関数オブジェクトの型。

*_Function3*<br/>
並列で実行される3番目の関数オブジェクトの型。

*_Function4*<br/>
並列で実行される4番目の関数オブジェクトの型。

*_Function5*<br/>
並列で実行される5番目の関数オブジェクトの型。

*_Function6*<br/>
並列で実行される6番目の関数オブジェクトの型。

*_Function7*<br/>
並列で実行される7番目の関数オブジェクトの型。

*_Function8*<br/>
並列で実行される8番目の関数オブジェクトの型。

*_Function9*<br/>
並列で実行される9番目の関数オブジェクトの型。

*_Function10*<br/>
並列で実行される10番目の関数オブジェクトの型。

*_Func1*<br/>
並列で実行される最初の関数オブジェクト。

*_Func2*<br/>
並列で実行される2番目の関数オブジェクト。

*_Func3*<br/>
並列で実行される3番目の関数オブジェクト。

*_Func4*<br/>
並列で実行される4番目の関数オブジェクト。

*_Func5*<br/>
並列で実行される5番目の関数オブジェクト。

*_Func6*<br/>
並列で実行される6番目の関数オブジェクト。

*_Func7*<br/>
並列で実行される7番目の関数オブジェクト。

*_Func8*<br/>
並列で実行される8番目の関数オブジェクト。

*_Func9*<br/>
並列で実行される9番目の関数オブジェクト。

*_Func10*<br/>
並列で実行される10番目の関数オブジェクト。

### <a name="remarks"></a>解説

パラメーターとして指定された1つ以上の関数オブジェクトが、呼び出し元のコンテキストでインラインで実行される場合があることに注意してください。

この関数にパラメーターとして渡された関数オブジェクトの1つまたは複数が例外をスローした場合、ランタイムはその例外を選択し、それを呼び出しから `parallel_invoke`に伝達します。

詳細については、「[並列アルゴリズム](../../../parallel/concrt/parallel-algorithms.md)」を参照してください。

## <a name="parallel_radixsort"></a>parallel_radixsort

基数並べ替えアルゴリズムを使用して、指定された範囲の要素を降順以外の順序で配置します。 これは安定した並べ替え関数で、符号なし整数 (キーなど) に分類されるように要素を投影する投射関数を必要とします。 並べ替えられる要素には既定の初期化が必要です。

```cpp
template<typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator, typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator, typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);
```

### <a name="parameters"></a>パラメーター

*_Random_iterator*<br/>
入力範囲の反復子の型。

*_Allocator*<br/>
C++標準ライブラリ互換メモリアロケーターの型。

*_Function*<br/>
射影関数の型。

*_Begin*<br/>
並べ替えられる範囲内の最初の要素の位置を示すランダム アクセス反復子。

*_End*<br/>
並べ替えられる範囲内の最後の要素の 1 つ後ろの位置を示すランダム アクセス反復子。

*_Alloc*<br/>
標準ライブラリとC++互換性のあるメモリアロケーターのインスタンス。

*_Proj_func*<br/>
要素を整数値に変換するユーザー定義の射影関数オブジェクト。

*_Chunk_size*<br/>
並列実行のために2つに分割されるチャンクの最低限サイズ。

### <a name="remarks"></a>解説

すべてのオーバーロードには `n * sizeof(T)` 追加の領域が必要です。 `n` は並べ替えられる要素の数であり、`T` は要素の型です。 要素が指定されたときにキーを返すには、`I _Proj_func(T)` シグネチャを持つ単項投影ファンクタが必要です。 `T` は要素型で、`I` は符号なし整数型です。

射影関数を指定しない場合は、単に要素を返す既定の射影関数が整数型に使用されます。 射影関数がない場合、要素が整数型でない場合、関数はコンパイルに失敗します。

アロケーターの型またはインスタンスを指定しない場合はC++ 、標準ライブラリのメモリアロケーター `std::allocator<T>` を使用してバッファーが割り当てられます。

このアルゴリズムでは、入力範囲が2つのチャンクに分割され、各チャンクが連続して2つのサブチャンクに分割され、並列で実行されます。 省略可能な引数 `_Chunk_size` を使用すると、< `_Chunk_size` 直列にサイズのチャンクを処理する必要があることをアルゴリズムに示すことができます。

## <a name="parallel_reduce"></a>parallel_reduce

連続する部分的な合計を計算することで、指定された範囲のすべての要素の合計を計算します。または、指定された二項演算を使用して取得した、合計以外の連続する部分的な結果を並列で計算します。 `parallel_reduce` は `std::accumulate` と意味が同じです。ただし、結合のための二項演算と、初期値ではなく ID 値が必要です。

```cpp
template<typename _Forward_iterator>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity);

template<typename _Forward_iterator, typename _Sym_reduce_fun>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity,
    _Sym_reduce_fun _Sym_fun);

template<typename _Reduce_type,
    typename _Forward_iterator,
    typename _Range_reduce_fun,
    typename _Sym_reduce_fun>
inline _Reduce_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const _Reduce_type& _Identity,
    const _Range_reduce_fun& _Range_fun,
    const _Sym_reduce_fun& _Sym_fun);
```

### <a name="parameters"></a>パラメーター

*_Forward_iterator*<br/>
入力範囲の反復子の型。

*_Sym_reduce_fun*<br/>
対称リダクション関数の型。 これは、`_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`シグネチャを持つ関数型である必要があります。 _Reduce_type は、id 型と減少の結果型と同じです。 3番目のオーバーロードでは、これは `_Range_reduce_fun`の出力の種類と一致している必要があります。

*_Reduce_type*<br/>
入力が減少する型。入力要素の型とは異なる場合があります。 戻り値と id 値は、この型になります。

*_Range_reduce_fun*<br/>
範囲リダクション関数の型。 これは、`_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`シグネチャを持つ関数型である必要があります。 _Reduce_type は、id 型および減少の結果型と同じです。

*_Begin*<br/>
縮小する範囲内の最初の要素を示す入力反復子。

*_End*<br/>
縮小する範囲内の最後の要素の1つ後ろの位置にある要素を示す入力反復子。

*_Identity*<br/>
`_Identity` id 値は、リダクションの結果型と同じ型であり、1番目と2番目のオーバーロードの反復子の `value_type` にもなります。 3番目のオーバーロードでは、id 値はリダクションの結果型と同じ型である必要がありますが、反復子の `value_type` とは異なる可能性があります。 この値には、`value_type` 型の1つの要素の範囲に適用されている場合は範囲の縮小演算子 `_Range_fun`、id 値は型 `value_type` から id 型への値の型キャストのように動作するように、適切な値が必要です。

*_Sym_fun*<br/>
リダクションの2番目ので使用される対称関数。 詳細については、「解説」を参照してください。

*_Range_fun*<br/>
リダクションの最初のフェーズで使用される関数。 詳細については、「解説」を参照してください。

### <a name="return-value"></a>戻り値

リダクションの結果。

### <a name="remarks"></a>解説

並列処理を減らすために、関数は、基になるスケジューラで使用可能なワーカーの数に基づいて、範囲をチャンクに分割します。 リダクションは2フェーズで行われます。最初のフェーズは各チャンク内で減少し、2番目のフェーズは各チャンクからの部分的な結果を減らします。

最初のオーバーロードでは、反復子の `value_type`、`T`は、id 値の型と縮小結果の型と同じである必要があります。 要素型 T は、各チャンク内の要素を減らすために `T T::operator + (T)` 演算子を提供する必要があります。 2番目のフェーズでも同じ演算子が使用されます。

2番目のオーバーロードでは、反復子の `value_type` も、id 値の型と、リダクションの結果の型と同じである必要があります。 指定された二項演算子 `_Sym_fun` は両方のリダクションフェーズで使用され、最初のフェーズの初期値として id 値が使用されます。

3番目のオーバーロードでは、id 値の型はリダクションの結果型と同じである必要がありますが、反復子の `value_type` と異なる場合があります。 範囲縮小関数 `_Range_fun` は、初期値として id 値を持つ最初のフェーズで使用され、2番目のフェーズでは、バイナリ関数 `_Sym_reduce_fun` がサブ結果に適用されます。

## <a name="parallel_sort"></a>parallel_sort

指定された範囲の要素を、降順以外の順序、または二項述語によって指定された順序の基準に従って並列に配置します。 この関数は、比較ベースで不安定なインプレース並べ替えという点で `std::sort` と意味が同じです。

```cpp
template<typename _Random_iterator>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,typename _Function>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>パラメーター

*_Random_iterator*<br/>
入力範囲の反復子の型。

*_Function*<br/>
バイナリ比較ファンクタの型。

*_Begin*<br/>
並べ替えられる範囲内の最初の要素の位置を示すランダム アクセス反復子。

*_End*<br/>
並べ替えられる範囲内の最後の要素の 1 つ後ろの位置を示すランダム アクセス反復子。

*_Func*<br/>
順序の連続する要素によって満たされる比較条件を定義するユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。 この比較子関数は、シーケンスからの要素のペアで厳密弱順序を強制する必要があります。

*_Chunk_size*<br/>
並列実行のために2つに分割されるチャンクの最小サイズ。

### <a name="remarks"></a>解説

最初のオーバーロードでは、`std::less`バイナリ比較子を使用します。

2番目のオーバーロードは、指定されたバイナリ `bool _Func(T, T)` 比較子を使用します。ここで、`T` は入力範囲内の要素の型です。

このアルゴリズムでは、入力範囲が2つのチャンクに分割され、各チャンクが連続して2つのサブチャンクに分割され、並列で実行されます。 省略可能な引数 `_Chunk_size` を使用すると、< `_Chunk_size` 直列にサイズのチャンクを処理する必要があることをアルゴリズムに示すことができます。

## <a name="parallel_transform"></a>parallel_transform

指定された関数オブジェクトをソース範囲内の各要素、または 2 つのソース範囲内の要素のペアに適用し、関数オブジェクトの戻り値をコピー先の範囲に並列でコピーします。 この関数は、意味的には `std::transform` と同じです。

```cpp
template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const static_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const simple_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    affinity_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator,
    typename _Partitioner>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op,
    _Partitioner&& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op);
```

### <a name="parameters"></a>パラメーター

*_Input_iterator1*<br/>
最初の入力反復子または唯一の入力反復子の型。

*_Output_iterator*<br/>
出力反復子の型。

*_Unary_operator*<br/>
入力範囲内の各要素に対して実行される単項ファンの種類。

*_Input_iterator2*<br/>
2番目の入力反復子の型。

*_Binary_operator*<br/>
2つのソース範囲の要素で、実行されたバイナリファンクタの型がペアになります。

*_Partitioner*<br/>
*first1*<br/>
操作する最初の範囲または唯一のソース範囲内の最初の要素の位置を示す入力反復子。

*last1*<br/>
操作対象の最初または唯一のソース範囲内の最後の要素の1つ後ろの位置を示す入力反復子。

*_Result*<br/>
ターゲット範囲の最初の要素の位置を示す出力反復子。

*_Unary_op*<br/>
ソース範囲内の各要素に適用されるユーザー定義の単項関数オブジェクト。

*_Part*<br/>
パーティショナーオブジェクトへの参照。 引数には、`const`[auto_partitioner](auto-partitioner-class.md)`&`のいずれか、`const`[static_partitioner](static-partitioner-class.md)`&`、 [`const`simple_partitioner`&` また](simple-partitioner-class.md)は[affinity_partitioner](affinity-partitioner-class.md)`&`[オブジェクトが](affinity-partitioner-class.md)使用されている場合、その参照は非定数の左辺値参照である必要があります。これにより、アルゴリズムは将来のループの状態を保存して再利用することができます。

*first2*<br/>
操作する 2 番目のソース範囲内の最初の要素の位置を示す入力反復子。

*_Binary_op*<br/>
2つのソース範囲にペアワイズで適用されるユーザー定義の二項関数オブジェクト。

### <a name="return-value"></a>戻り値

関数オブジェクトで変換された出力要素を受け取るターゲット範囲の最後の要素の 1 つ後ろの位置を示す出力反復子。

### <a name="remarks"></a>解説

[auto_partitioner](auto-partitioner-class.md)は、明示的なパーティショナー引数を指定せずにオーバーロードに使用されます。

ランダムアクセスをサポートしていない反復子の場合は、 [auto_partitioner](auto-partitioner-class.md)のみがサポートされます。

引数を受け取るオーバーロード `_Unary_op` 入力範囲内の各要素に単項ファンクタを適用することによって、入力範囲を出力範囲に変換します。 `_Unary_op` は、シグネチャ `operator()(T)` の関数呼び出し演算子をサポートする必要があります。 `T` は、反復処理される範囲の値型です。

引数を受け取るオーバーロードは、2つの入力範囲を、最初の入力範囲から1つの要素に、2番目の入力範囲の1つの要素に適用することで、2つの入力範囲を出力範囲に変換 `_Binary_op` ます。 `_Binary_op` は、シグネチャ `operator()(T, U)` を持つ関数呼び出し演算子をサポートする必要があります。ここで、`T`、`U` は2つの入力反復子の値型です。

詳細については、「[並列アルゴリズム](../../../parallel/concrt/parallel-algorithms.md)」を参照してください。

## <a name="receive"></a>受け取れ

receive の一般的な実装です。これにより、コンテキストで 1 つのソースからのデータを待機し、受け取った値をフィルター処理できます。

```cpp
template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
ペイロードの種類。

*_Src*<br/>
データが予期されるソースへのポインターまたは参照。

*_Timeout*<br/>
メソッドがデータを必要とする最大時間 (ミリ秒単位)。

*_Filter_proc*<br/>
メッセージを受け入れるかどうかを決定するフィルター関数。

### <a name="return-value"></a>戻り値

ペイロードの種類のソースからの値。

### <a name="remarks"></a>解説

パラメーター `_Timeout` に定数 `COOPERATIVE_TIMEOUT_INFINITE`以外の値が指定されている場合、メッセージを受信する前に指定した時間が経過すると、例外[operation_timed_out](operation-timed-out-class.md)がスローされます。 長さゼロのタイムアウトを使用する場合は、`0` (ゼロ) のタイムアウトを指定して `receive` を呼び出すのではなく、 [try_receive](concurrency-namespace-functions.md)関数を使用する必要があります。これは、より効率的で、タイムアウト時に例外をスローしないためです。

詳細については、「[メッセージパッシング関数](../../../parallel/concrt/message-passing-functions.md)」を参照してください。

## <a name="run_with_cancellation_token"></a>run_with_cancellation_token

関数オブジェクトを、指定されたキャンセル トークンのコンテキストですばやく同期的に実行します。

```cpp
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```

### <a name="parameters"></a>パラメーター

*_Function*<br/>
呼び出される関数オブジェクトの型。

*_Func*<br/>
実行される関数オブジェクト。 このオブジェクトは、シグネチャが void (void) の関数呼び出し演算子をサポートしている必要があります。

*_Ct*<br/>
関数オブジェクトの暗黙的な取り消しを制御するキャンセルトークン。 親タスクグループからの暗黙のキャンセルがキャンセルされる可能性がない状態で関数を実行する場合は、`cancellation_token::none()` を使用します。

### <a name="remarks"></a>解説

`cancellation_token` がキャンセルされると、関数オブジェクト内の中断ポイントがトリガーされます。 親のトークンが異なる場合、またはトークンがない場合は、明示的なトークン `_Ct` によって、親の取り消しからこの `_Func` が分離されます。

## <a name="send"></a>送信

ターゲットがメッセージを受け入れるか拒否するまで待機する同期送信操作です。

```cpp
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
ペイロードの種類。

*_Trg*<br/>
データが送信されるターゲットへのポインターまたは参照。

*_Data*<br/>
送信されるデータへの参照。

### <a name="return-value"></a>戻り値

メッセージが受け入れられた場合は**true** 、それ以外の場合は**false** 。

### <a name="remarks"></a>解説

詳細については、「[メッセージパッシング関数](../../../parallel/concrt/message-passing-functions.md)」を参照してください。

## <a name="set_ambient_scheduler"></a>set_ambient_scheduler

```cpp
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```

### <a name="parameters"></a>パラメーター

*_Scheduler*<br/>
設定するアンビエントスケジューラ。

## <a name="set_task_execution_resources"></a>set_task_execution_resources

コンカレンシー ランタイムの内部ワーカー スレッドが使用する実行リソースを、指定された関係セットに制限します。

このメソッドの呼び出しは、リソース マネージャーの作成前、または 2 つのリソース マネージャーの有効期間の間のみ有効です。 これは、呼び出し時にリソース マネージャーが存在しない限り複数回呼び出すことができます。 関係の制限が設定されたら、次の有効な `set_task_execution_resources` メソッド呼び出しまで保持されます。

指定された関係マスクは、プロセス関係マスクのサブセットである必要はありません。 プロセス関係は必要に応じて更新されます。

```cpp
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```

### <a name="parameters"></a>パラメーター

*_ProcessAffinityMask*<br/>
同時実行ランタイムワーカースレッドの制限対象となる関係マスク。 このメソッドは、同時実行ランタイムを現在のプロセッサグループのサブセットに制限する場合にのみ、64ハードウェアスレッドを超えるシステムで使用します。 一般に、グループのアフィニティの配列をパラメーターとして受け取るバージョンのメソッドを使用して、64を超えるハードウェアスレッドを持つコンピューターのアフィニティを制限する必要があります。

*count*<br/>
パラメーター `_PGroupAffinity`によって指定された配列内の `GROUP_AFFINITY` エントリの数。

*_PGroupAffinity*<br/>
`GROUP_AFFINITY` エントリの配列。

### <a name="remarks"></a>解説

メソッドは、呼び出し時にリソースマネージャーが存在する場合は[invalid_operation](invalid-operation-class.md)例外をスローし、指定されたアフィニティによってリソースの空のセットが得られる場合は[invalid_argument](../../../standard-library/invalid-argument-class.md)例外をスローします。

グループのアフィニティの配列をパラメーターとして受け取るメソッドのバージョンは、Windows 7 以降のバージョンのオペレーティングシステムでのみ使用してください。 それ以外の場合は、 [invalid_operation](invalid-operation-class.md)例外がスローされます。

このメソッドの呼び出し後にプログラムによってプロセスアフィニティを変更しても、リソースマネージャーが制限されているアフィニティを再評価することはありません。 したがって、このメソッドを呼び出す前に、関係を処理するためのすべての変更を行う必要があります。

## <a name="swap"></a>  swap

2 つの `concurrent_vector` オブジェクトの要素を交換します。

```cpp
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
同時実行ベクターに格納されている要素のデータ型。

*_Ax*<br/>
同時実行ベクターのアロケーター型。

*_A*<br/>
同時実行ベクターの `_B`と交換される要素を持つ同時実行ベクター。

*_B*<br/>
交換する要素を提供する同時実行ベクター、または要素が同時実行ベクター `_A`と交換されるベクター。

### <a name="remarks"></a>解説

このテンプレート関数は、コンテナークラス `concurrent_vector` に特化したアルゴリズムであり、メンバー関数 `_A`を実行します。 [concurrent_vector:: swap](concurrent-vector-class.md#swap)(`_B`)。 これらは、コンパイラによる関数テンプレートの部分的な順序付けのインスタンスです。 テンプレートと関数呼び出しの照合が一意にならないようにテンプレート関数がオーバーロードされた場合、コンパイラは、最も特化したバージョンのテンプレート関数を選択します。 アルゴリズムクラスのテンプレート関数の `template <class T> void swap(T&, T&)`の一般的なバージョンは、代入によって動作し、低速の操作です。 各コンテナー内の特化バージョンのほうが、コンテナー クラスの内部表現で使用できるため大幅に高速になります。

このメソッドはコンカレンシー セーフではありません。 このメソッドを呼び出すときに、他のスレッドがどちらの同時実行ベクターに対しても操作を実行していないことを確認する必要があります。

## <a name="task_from_exception"></a>task_from_exception

```cpp
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>パラメーター

*_TaskType*<br/>

*_ExType*<br/>

*_Exception*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>戻り値

## <a name="task_from_result"></a>task_from_result

```cpp
template<typename T>
task<T> task_from_result(
    T _Param,
    const task_options& _TaskOptions = task_options());

inline task<bool> task_from_result(ool _Param);

inline task<void> task_from_result(
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>パラメーター

*T*<br/>

*_Param*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>戻り値

## <a name="trace_agents_register_name"></a>Trace_agents_register_name

指定された名前を、ETW トレースのメッセージ ブロックまたはエージェントに関連付けます。

```cpp
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
オブジェクトの型。 通常、これはメッセージブロックまたはエージェントです。

*_PObject*<br/>
トレースで名前が付けられているメッセージブロックまたはエージェントへのポインター。

*_Name*<br/>
指定したオブジェクトの名前。

## <a name="try_receive"></a>try_receive

try-receive の一般的な実装です。これにより、コンテキストで 1 つのソースに対してのみデータの検索を実行し、受け取った値をフィルター処理できます。 データの準備ができていない場合、メソッドは**false**を返します。

```cpp
template <class T>
bool try_receive(_Inout_ ISource<T>* _Src, T& _value);

template <class T>
bool try_receive(
    _Inout_ ISource<T>* _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);

template <class T>
bool try_receive(ISource<T>& _Src, T& _value);

template <class T>
bool try_receive(
    ISource<T>& _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
ペイロードの種類

*_Src*<br/>
データが予期されるソースへのポインターまたは参照。

*_value*<br/>
結果が配置される場所への参照。

*_Filter_proc*<br/>
メッセージを受け入れるかどうかを決定するフィルター関数。

### <a name="return-value"></a>戻り値

ペイロードが `_value`に配置されたかどうかを示す `bool` 値。

### <a name="remarks"></a>解説

詳細については、「[メッセージパッシング関数](../../../parallel/concrt/message-passing-functions.md)」を参照してください。

## <a name="wait"></a>待機

指定した時間だけ現在のコンテキストを停止します。

```cpp
void __cdecl wait(unsigned int _Milliseconds);
```

### <a name="parameters"></a>パラメーター

*_Milliseconds*<br/>
現在のコンテキストを一時停止する時間 (ミリ秒単位)。 `_Milliseconds` パラメーターが `0`値に設定されている場合、現在のコンテキストは、続行する前に実行可能な他のコンテキストに実行を生成する必要があります。

### <a name="remarks"></a>解説

このメソッドが同時実行ランタイム scheduler コンテキストで呼び出されると、スケジューラは、基になるリソースで実行する別のコンテキストを検索します。 スケジューラは本質的に協調しているので、指定されたミリ秒数を正確に再開することはできません。 Scheduler がスケジューラに対して協調的に生成されない他のタスクを実行中である場合、待機期間が無期限になる可能性があります。

## <a name="when_all"></a>when_all

引数として指定されたすべてのタスクが正常に完了したときに正常に完了するタスクを作成します。

```cpp
template <typename _Iterator>
auto when_all(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) ->
    decltype (details::_WhenAllImpl<typename std::iterator_traits<_Iterator>::value_type::result_type,
    _Iterator>::_Perform(_TaskOptions, _Begin,  _End));
```

### <a name="parameters"></a>パラメーター

*_Iterator*<br/>
入力反復子の型。

*_Begin*<br/>
結果のタスクに組み込まれる要素範囲内にある最初の要素の位置。

*_End*<br/>
結果のタスクに組み込まれる要素範囲外にある最初の要素の位置。

*_TaskOptions*<br/>
`task_options` オブジェクト。

### <a name="return-value"></a>戻り値

すべての入力タスクが正常に完了したときに正常に完了するタスク。 入力したタスクの種類が `T` である場合、この関数の出力は `task<std::vector<T>>` になります。 入力したタスクの種類が `void` である場合、出力のタスクも `task<void>` になります。

### <a name="remarks"></a>解説

`when_all` は、その結果、`task` を生成する、非ブロッキング関数です。 [Task:: wait](task-class.md#wait)とは異なり、ASTA (アプリケーション STA) スレッドの UWP アプリでこの関数を呼び出すことは安全です。

いずれかのタスクが取り消された場合、または例外がスローされた場合、返されたタスクは早期に完了し、取り消された状態になります。また、そのタスクに対して[task:: get](task-class.md#get)または `task::wait` を呼び出すと、例外がスローされます。

詳細については、「[タスクの並列](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)化」を参照してください。

## <a name="when_any"></a>when_any

引数として指定されたいずれかのタスクが正常に完了したときに正常に完了するタスクを作成します。

```cpp
template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options())
    -> decltype (
        details::_WhenAnyImpl<
            typename std::iterator_traits<_Iterator>::value_type::result_type,
            _Iterator>::_Perform(_TaskOptions, _Begin, _End));

template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    cancellation_token _CancellationToken)
       -> decltype (
           details::_WhenAnyImpl<
               typename std::iterator_traits<_Iterator>::value_type::result_type,
               _Iterator>::_Perform(_CancellationToken._GetImplValue(), _Begin, _End));
```

### <a name="parameters"></a>パラメーター

*_Iterator*<br/>
入力反復子の型。

*_Begin*<br/>
結果のタスクに組み込まれる要素範囲内にある最初の要素の位置。

*_End*<br/>
結果のタスクに組み込まれる要素範囲外にある最初の要素の位置。

*_TaskOptions*<br/>
*_CancellationToken*<br/>
返されたタスクの取り消しを制御するキャンセル トークン。 キャンセル トークンを指定しない場合、結果のタスクは、完了の原因となったタスクのキャンセル トークンを受け取ります。

### <a name="return-value"></a>戻り値

入力したタスクのいずれかが正常に完了したときに正常に完了するタスク。 入力したタスクの種類が `T` である場合、この関数の出力は `task<std::pair<T, size_t>>>` になります。ここでは、pair の最初の要素は完了したタスクの結果であり、2 番目の要素は完了したタスクのインデックスです。 入力したタスクの種類が `void` である場合、出力は `task<size_t>` になります。この場合、結果は完了したタスクのインデックスです。

### <a name="remarks"></a>解説

`when_any` は、その結果、`task` を生成する、非ブロッキング関数です。 [Task:: wait](task-class.md#wait)とは異なり、ASTA (アプリケーション STA) スレッドの UWP アプリでこの関数を呼び出すことは安全です。

詳細については、「[タスクの並列](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)化」を参照してください。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
