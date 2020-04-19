---
title: structured_task_group クラス
ms.date: 11/04/2016
f1_keywords:
- structured_task_group
- PPL/concurrency::structured_task_group
- PPL/concurrency::structured_task_group::structured_task_group
- PPL/concurrency::structured_task_group::cancel
- PPL/concurrency::structured_task_group::is_canceling
- PPL/concurrency::structured_task_group::run
- PPL/concurrency::structured_task_group::run_and_wait
- PPL/concurrency::structured_task_group::wait
helpviewer_keywords:
- structured_task_group class
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
ms.openlocfilehash: 93dd79b755f79dcb4857c1b1c4856362b0bd45dd
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142631"
---
# <a name="structured_task_group-class"></a>structured_task_group クラス

`structured_task_group` クラスは、並列処理の高度に構造化されたコレクションを表します。 `structured_task_group` オブジェクトを使用して個々の並列タスクを `task_handle` のキューに配置し、それらのタスクが完了するまで待機するか、実行が完了する前にタスク グループを取り消すことができます。取り消すと、実行が開始されていないタスクはすべて中止されます。

## <a name="syntax"></a>構文

```cpp
class structured_task_group;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[structured_task_group](#ctor)|オーバーロードされます。 新しい `structured_task_group` オブジェクトを構築します。|
|[~ structured_task_group デストラクター](#dtor)|`structured_task_group` オブジェクトを破棄します。 例外が原因でスタックアンワインドの結果としてデストラクターが実行されていない限り、デストラクターを実行する前に、オブジェクトの `wait` または `run_and_wait` メソッドを呼び出す必要があります。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[cancel](#cancel)|では、このタスクグループをルートとする作業のサブツリーをキャンセルすることをお勧めします。 タスクグループにスケジュールされているすべてのタスクは、可能な場合は推移的に取り消されます。|
|[is_canceling](#is_canceling)|タスクグループが現在キャンセル中であるかどうかを呼び出し元に通知します。 これは必ずしも `structured_task_group` オブジェクトで `cancel` メソッドが呼び出されたことを示しているわけではありません (ただし、このメソッドは確かに**true**を返すことになります)。 `structured_task_group` オブジェクトがインラインで実行されていて、作業ツリー内のタスクグループが取り消された場合もあります。 このような場合、ランタイムは、キャンセルがこの `structured_task_group` オブジェクトを流れる前に事前に判断できます。 **true**も返されます。|
|[run](#run)|オーバーロードされます。 `structured_task_group` オブジェクトのタスクをスケジュールします。 呼び出し元は、`_Task_handle` パラメーターで渡された `task_handle` オブジェクトの有効期間を管理します。 パラメーター `_Placement` を受け取るバージョンでは、そのパラメーターによって指定された場所で実行されるようにタスクがバイアスされます。|
|[run_and_wait](#run_and_wait)|オーバーロードされます。 `structured_task_group` オブジェクトを使用して、呼び出し元のコンテキストでインラインで実行されるタスクをスケジュールし、完全なキャンセルをサポートします。 `task_handle` オブジェクトが `run_and_wait`にパラメーターとして渡された場合、呼び出し元は `task_handle` オブジェクトの有効期間を管理します。 次に、関数は、`structured_task_group` オブジェクトのすべての処理が完了するか取り消されるまで待機します。|
|[待機](#wait)|`structured_task_group` のすべての作業が完了するか、取り消されるまで待機します。|

## <a name="remarks"></a>コメント

パフォーマンスを向上させるために、`structured_task_group` オブジェクトの使用にはいくつかの重大な制限が設けられています。

- 1つの `structured_task_group` オブジェクトを複数のスレッドで使用することはできません。 `structured_task_group` オブジェクトのすべての操作は、オブジェクトを作成したスレッドによって実行される必要があります。 この規則の2つの例外は、メンバー関数 `cancel` および `is_canceling`です。 このオブジェクトは、タスクがキャンセル操作のいずれかを使用している場合を除き、ラムダ式のキャプチャリストに含まれておらず、タスク内で使用することができます。

- `structured_task_group` オブジェクトに対してスケジュールされているすべてのタスクは、の有効期間を明示的に管理する必要がある `task_handle` オブジェクトを使用してスケジュールされます。

- 複数のグループは、完全に入れ子になった順序でのみ使用できます。 2つの `structured_task_group` オブジェクトが宣言されている場合、`cancel` または `is_canceling` を除くメソッドが1つ目のメソッド (外側のオブジェクト) で呼び出される前に、宣言されている2番目のオブジェクト (内部 1) が破棄される必要があります。 この条件は、同じまたは機能的に入れ子になったスコープ内で複数の `structured_task_group` オブジェクトを宣言する場合と、`run` または `run_and_wait` メソッドを介して `structured_task_group` にキューに登録されたタスクの場合の両方に当てはまります。

- 一般的な `task_group` クラスとは異なり、`structured_task_group` クラスのすべての状態は final です。 グループに対してタスクをキューに入れて完了を待機した後、同じグループを再度使用することはできません。

詳細については、「[タスクの並列](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)化」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`structured_task_group`

## <a name="requirements"></a>要件

**ヘッダー:** ppl

**名前空間:** concurrency

## <a name="cancel"></a>キャンセル

では、このタスクグループをルートとする作業のサブツリーをキャンセルすることをお勧めします。 タスクグループにスケジュールされているすべてのタスクは、可能な場合は推移的に取り消されます。

```cpp
void cancel();
```

### <a name="remarks"></a>コメント

詳細については、「[キャンセル](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)」を参照してください。

## <a name="is_canceling"></a>is_canceling

タスクグループが現在キャンセル中であるかどうかを呼び出し元に通知します。 これは必ずしも `structured_task_group` オブジェクトで `cancel` メソッドが呼び出されたことを示しているわけではありません (ただし、このメソッドは確かに**true**を返すことになります)。 `structured_task_group` オブジェクトがインラインで実行されていて、作業ツリー内のタスクグループが取り消された場合もあります。 このような場合、ランタイムは、キャンセルがこの `structured_task_group` オブジェクトを流れる前に事前に判断できます。 **true**も返されます。

```cpp
bool is_canceling();
```

### <a name="return-value"></a>戻り値

`structured_task_group` オブジェクトがキャンセルの途中であるかどうかを示す (または、後で保証されている) かどうかを示します。

### <a name="remarks"></a>コメント

詳細については、「[キャンセル](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation)」を参照してください。

## <a name="run"></a>実行

`structured_task_group` オブジェクトのタスクをスケジュールします。 呼び出し元は、`_Task_handle` パラメーターで渡された `task_handle` オブジェクトの有効期間を管理します。 パラメーター `_Placement` を受け取るバージョンでは、そのパラメーターによって指定された場所で実行されるようにタスクがバイアスされます。

```cpp
template<class _Function>
void run(
    task_handle<_Function>& _Task_handle);

template<class _Function>
void run(
    task_handle<_Function>& _Task_handle,
    location& _Placement);
```

### <a name="parameters"></a>パラメーター

*_Function*<br/>
タスクハンドルの本体を実行するために呼び出される関数オブジェクトの型。

*_Task_handle*<br/>
スケジュールされている作業へのハンドル。 呼び出し元は、このオブジェクトの有効期間を担当していることに注意してください。 ランタイムは、この `structured_task_group` オブジェクトで `wait` または `run_and_wait` のいずれかのメソッドが呼び出されるまで、引き続き有効であると想定します。

*_Placement*<br/>
`_Task_handle` パラメーターによって表されるタスクが実行される場所への参照。

### <a name="remarks"></a>コメント

ランタイムは、このメソッドに渡す作業関数のコピーを作成します。 このメソッドに渡す関数オブジェクトで発生した状態の変更は、その関数オブジェクトのコピーには表示されません。

`structured_task_group` が例外からのスタックアンワインドの結果として destructs 場合、`wait` または `run_and_wait` メソッドのいずれかに対して呼び出しが行われたことを保証する必要はありません。 この場合、デストラクターは適切にキャンセルされ、`_Task_handle` パラメーターによって表されるタスクが完了するまで待機します。

`_Task_handle` パラメーターによって指定されたタスクハンドルが `run` メソッドを使用してタスクグループオブジェクトに既にスケジュールされており、そのタスクグループで `wait` または `run_and_wait` メソッドの呼び出しが介在していない場合は、 [invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)例外をスローします。

## <a name="run_and_wait"></a>run_and_wait

`structured_task_group` オブジェクトを使用して、呼び出し元のコンテキストでインラインで実行されるタスクをスケジュールし、完全なキャンセルをサポートします。 `task_handle` オブジェクトが `run_and_wait`にパラメーターとして渡された場合、呼び出し元は `task_handle` オブジェクトの有効期間を管理します。 次に、関数は、`structured_task_group` オブジェクトのすべての処理が完了するか取り消されるまで待機します。

```cpp
template<class _Function>
task_group_status run_and_wait(task_handle<_Function>& _Task_handle);

template<class _Function>
task_group_status run_and_wait(const _Function& _Func);
```

### <a name="parameters"></a>パラメーター

*_Function*<br/>
タスクを実行するために呼び出される関数オブジェクトの型。

*_Task_handle*<br/>
呼び出し元のコンテキストでインラインで実行されるタスクへのハンドル。 呼び出し元は、このオブジェクトの有効期間を担当していることに注意してください。 ランタイムは、`run_and_wait` メソッドが実行を終了するまで、それが引き続き有効であると想定します。

*_Func*<br/>
作業の本体を呼び出すために呼び出される関数。 これは、`void operator()()`シグネチャを持つ関数呼び出し演算子のバージョンをサポートするラムダまたはその他のオブジェクトである可能性があります。

### <a name="return-value"></a>戻り値

明示的な取り消し操作、またはそのタスクの1つからスローされた例外が原因で、待機が満たされたか、タスクグループが取り消されたかを示す値。 詳細については、「」を参照してください[task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>コメント

この `structured_task_group` オブジェクトに対してスケジュールされた1つ以上のタスクが、呼び出し元のコンテキストでインラインで実行される可能性があることに注意してください。

この `structured_task_group` オブジェクトに対してスケジュールされている1つ以上のタスクが例外をスローした場合、ランタイムはその例外を選択して、`run_and_wait` メソッドの呼び出しの外に伝達します。

この関数が戻ると、`structured_task_group` オブジェクトは最終的な状態と見なされるため、使用しないでください。 `run_and_wait` メソッドから制御が戻った後の使用率によって、未定義の動作が発生することに注意してください。

実行の例外的なパスでは、`structured_task_group` のデストラクターが実行される前に、このメソッドまたは `wait` メソッドのいずれかを呼び出す必要があります。

## <a name="ctor"></a>structured_task_group

新しい `structured_task_group` オブジェクトを構築します。

```cpp
structured_task_group();

structured_task_group(cancellation_token _CancellationToken);
```

### <a name="parameters"></a>パラメーター

*_CancellationToken*<br/>
この構造化タスクグループに関連付けるキャンセルトークン。 トークンが取り消されると、構造化タスクグループは取り消されます。

### <a name="remarks"></a>コメント

キャンセルトークンを受け取るコンストラクターは、トークンに関連付けられているソースが取り消されたときにキャンセルされる `structured_task_group` を作成します。 また、明示的なキャンセルトークンを指定すると、この構造化タスクグループは、別のトークンまたはトークンを持たない親グループからの暗黙的な取り消しに参加しないように分離されます。

## <a name="dtor"></a>~ structured_task_group

`structured_task_group` オブジェクトを破棄します。 例外が原因でスタックアンワインドの結果としてデストラクターが実行されていない限り、デストラクターを実行する前に、オブジェクトの `wait` または `run_and_wait` メソッドを呼び出す必要があります。

```cpp
~structured_task_group();
```

### <a name="remarks"></a>コメント

デストラクターが通常の実行の結果として実行された場合 (たとえば、例外が原因でスタックアンワインドが発生していない場合)、`wait` も `run_and_wait` メソッドも呼び出されていないと、デストラクターは[missing_wait](missing-wait-class.md)例外をスローする可能性があります。

## <a name="wait"></a>待機

`structured_task_group` のすべての作業が完了するか、取り消されるまで待機します。

```cpp
task_group_status wait();
```

### <a name="return-value"></a>戻り値

明示的な取り消し操作、またはそのタスクの1つからスローされた例外が原因で、待機が満たされたか、タスクグループが取り消されたかを示す値。 詳細については、「」を参照してください[task_group_status](concurrency-namespace-enums.md)

### <a name="remarks"></a>コメント

この `structured_task_group` オブジェクトに対してスケジュールされた1つ以上のタスクが、呼び出し元のコンテキストでインラインで実行される可能性があることに注意してください。

この `structured_task_group` オブジェクトに対してスケジュールされている1つ以上のタスクが例外をスローした場合、ランタイムはその例外を選択して、`wait` メソッドの呼び出しの外に伝達します。

この関数が戻ると、`structured_task_group` オブジェクトは最終的な状態と見なされるため、使用しないでください。 `wait` メソッドから制御が戻った後の使用率によって、未定義の動作が発生することに注意してください。

実行の例外的なパスでは、`structured_task_group` のデストラクターが実行される前に、このメソッドまたは `run_and_wait` メソッドのいずれかを呼び出す必要があります。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[task_group クラス](task-group-class.md)<br/>
[task_handle クラス](task-handle-class.md)
