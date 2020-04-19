---
title: task_group クラス
ms.date: 07/20/2018
f1_keywords:
- task_group
- PPL/concurrency::task_group
- PPL/concurrency::task_group::task_group
helpviewer_keywords:
- task_group class
ms.openlocfilehash: 60c147f38ddc3936f47aea0cfd1ab1548b382441
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142567"
---
# <a name="task_group-class"></a>task_group クラス

`task_group` クラスは、待機または取り消しができる並列処理のコレクションを表します。

## <a name="syntax"></a>構文

```cpp
class task_group;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[task_group](#ctor)|オーバーロードされます。 新しい `task_group` オブジェクトを構築します。|
|[~ task_group デストラクター](#dtor)|`task_group` オブジェクトを破棄します。 例外により、デストラクターがスタックアンワインドの結果として実行されていない限り、デストラクターを実行する前に、オブジェクトの `wait` または `run_and_wait` メソッドを呼び出す必要があります。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[cancel](#cancel)|では、このタスクグループをルートとする作業のサブツリーをキャンセルすることをお勧めします。 タスクグループにスケジュールされているすべてのタスクは、可能な場合は推移的に取り消されます。|
|[is_canceling](#is_canceling)|タスクグループが現在キャンセル中であるかどうかを呼び出し元に通知します。 これは必ずしも `task_group` オブジェクトで `cancel` メソッドが呼び出されたことを示しているわけではありません (ただし、このメソッドは `true`を返すことが確かです)。 `task_group` オブジェクトがインラインで実行されていて、作業ツリー内のタスクグループが取り消された場合もあります。 このような場合、ランタイムは、キャンセルがこの `task_group` オブジェクトを流れる前に事前に判断でき、`true` も返されます。|
|[run](#run)|オーバーロードされます。 `task_group` オブジェクトのタスクをスケジュールします。 `task_handle` オブジェクトが `run`にパラメーターとして渡された場合、呼び出し元は `task_handle` オブジェクトの有効期間を管理します。 パラメーターとして関数オブジェクトへの参照を受け取るメソッドのバージョンは、ランタイム内でのヒープ割り当てに関係します。これは、`task_handle` オブジェクトへの参照を受け取るバージョンを使用する場合に比べて、実行される可能性が低くなります。 パラメーター `_Placement` を受け取るバージョンでは、そのパラメーターによって指定された場所で実行されるようにタスクがバイアスされます。|
|[run_and_wait](#run_and_wait)|オーバーロードされます。 `task_group` オブジェクトを使用して、呼び出し元のコンテキストでインラインで実行されるタスクをスケジュールし、完全なキャンセルをサポートします。 次に、関数は、`task_group` オブジェクトのすべての処理が完了するか取り消されるまで待機します。 `task_handle` オブジェクトが `run_and_wait`にパラメーターとして渡された場合、呼び出し元は `task_handle` オブジェクトの有効期間を管理します。|
|[待機](#wait)|`task_group` オブジェクトのすべての作業が完了するか、取り消されるまで待機します。|

## <a name="remarks"></a>コメント

非常に制限された `structured_task_group` クラスとは異なり、`task_group` クラスは、より一般的な構成要素です。 [Structured_task_group](structured-task-group-class.md)で説明されている制限事項はありません。 `task_group` オブジェクトはスレッド間で安全に使用でき、自由形式の方法で利用できます。 `task_group` コンストラクトの欠点は、少量の作業を実行するタスクの `structured_task_group` コンストラクトと同様に実行できないことです。

詳細については、「[タスクの並列](../task-parallelism-concurrency-runtime.md)化」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`task_group`

## <a name="requirements"></a>要件

**ヘッダー:** ppl

**名前空間:** concurrency

## <a name="cancel"></a>キャンセル

では、このタスクグループをルートとする作業のサブツリーをキャンセルすることをお勧めします。 タスクグループにスケジュールされているすべてのタスクは、可能な場合は推移的に取り消されます。

```cpp
void cancel();
```

### <a name="remarks"></a>コメント

詳細については、「[キャンセル](../cancellation-in-the-ppl.md)」を参照してください。

## <a name="is_canceling"></a>is_canceling

タスクグループが現在キャンセル中であるかどうかを呼び出し元に通知します。 これは必ずしも `task_group` オブジェクトで `cancel` メソッドが呼び出されたことを示しているわけではありません (ただし、このメソッドは `true`を返すことが確かです)。 `task_group` オブジェクトがインラインで実行されていて、作業ツリー内のタスクグループが取り消された場合もあります。 このような場合、ランタイムは、キャンセルがこの `task_group` オブジェクトを流れる前に事前に判断でき、`true` も返されます。

```cpp
bool is_canceling();
```

### <a name="return-value"></a>戻り値

`task_group` オブジェクトがキャンセルの途中であるかどうかを示す (または、後で保証されている) かどうかを示します。

### <a name="remarks"></a>コメント

詳細については、「[キャンセル](../cancellation-in-the-ppl.md)」を参照してください。

## <a name="run"></a>実行

`task_group` オブジェクトのタスクをスケジュールします。 `task_handle` オブジェクトが `run`にパラメーターとして渡された場合、呼び出し元は `task_handle` オブジェクトの有効期間を管理します。 パラメーターとして関数オブジェクトへの参照を受け取るメソッドのバージョンは、ランタイム内でのヒープ割り当てに関係します。これは、`task_handle` オブジェクトへの参照を受け取るバージョンを使用する場合に比べて、実行される可能性が低くなります。 パラメーター `_Placement` を受け取るバージョンでは、そのパラメーターによって指定された場所で実行されるようにタスクがバイアスされます。

```cpp
template<
   typename _Function
>
void run(
   const _Function& _Func
);

template<
   typename _Function
>
void run(
   const _Function& _Func,
   location& _Placement
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle
);

template<
   typename _Function
>
void run(
   task_handle<_Function>& _Task_handle,
   location& _Placement
);
```

### <a name="parameters"></a>パラメーター

*_Function*<br/>
タスクハンドルの本体を実行するために呼び出される関数オブジェクトの型。

*_Func*<br/>
タスクの本体を呼び出すために呼び出される関数。 これは、ラムダ式またはその他のオブジェクトである可能性があります。このオブジェクトは、`void operator()()`シグネチャを持つ関数呼び出し演算子のバージョンをサポートしています。

*_Placement*<br/>
`_Func` パラメーターによって表されるタスクが実行される場所への参照。

*_Task_handle*<br/>
スケジュールされている作業へのハンドル。 呼び出し元は、このオブジェクトの有効期間を担当していることに注意してください。 ランタイムは、この `task_group` オブジェクトで `wait` または `run_and_wait` のいずれかのメソッドが呼び出されるまで、引き続き有効であると想定します。

### <a name="remarks"></a>コメント

ランタイムは、指定された作業関数を後で実行するようにスケジュールを設定します。これは、呼び出し元の関数から制御が戻った後でも実行できます。 このメソッドは、 [task_handle](task-handle-class.md)オブジェクトを使用して、指定された作業関数のコピーを保持します。 このため、このメソッドに渡す関数オブジェクトで発生した状態の変更は、その関数オブジェクトのコピーには表示されません。 また、ポインターによって渡されるオブジェクトまたは work 関数への参照によって渡されるオブジェクトの有効期間は、処理関数が返されるまで有効なままにしておいてください。

`task_group` が例外からのスタックアンワインドの結果として destructs 場合、`wait` または `run_and_wait` メソッドのいずれかに対して呼び出しが行われたことを保証する必要はありません。 この場合、デストラクターは適切にキャンセルされ、`_Task_handle` パラメーターによって表されるタスクが完了するまで待機します。

`_Task_handle` パラメーターによって指定されたタスクハンドルが `run` メソッドを使用してタスクグループオブジェクトに既にスケジュールされており、そのタスクグループで `wait` または `run_and_wait` メソッドの呼び出しが介在していない場合、メソッドは[invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)例外をスローします。

## <a name="run_and_wait"></a>run_and_wait

`task_group` オブジェクトを使用して、呼び出し元のコンテキストでインラインで実行されるタスクをスケジュールし、完全なキャンセルをサポートします。 次に、関数は、`task_group` オブジェクトのすべての処理が完了するか取り消されるまで待機します。 `task_handle` オブジェクトが `run_and_wait`にパラメーターとして渡された場合、呼び出し元は `task_handle` オブジェクトの有効期間を管理します。

```cpp
template<
   class _Function
>
task_group_status run_and_wait(
   task_handle<_Function>& _Task_handle
);

template<
   class _Function
>
task_group_status run_and_wait(
   const _Function& _Func
);
```

### <a name="parameters"></a>パラメーター

*_Function*<br/>
タスクの本体を実行するために呼び出される関数オブジェクトの型。

*_Task_handle*<br/>
呼び出し元のコンテキストでインラインで実行されるタスクへのハンドル。 呼び出し元は、このオブジェクトの有効期間を担当していることに注意してください。 ランタイムは、`run_and_wait` メソッドが実行を終了するまで、それが引き続き有効であると想定します。

*_Func*<br/>
作業の本体を呼び出すために呼び出される関数。 これは、ラムダ式またはその他のオブジェクトである可能性があります。このオブジェクトは、`void operator()()`シグネチャを持つ関数呼び出し演算子のバージョンをサポートしています。

### <a name="return-value"></a>戻り値

明示的な取り消し操作、またはそのタスクの1つからスローされた例外が原因で、待機が満たされたか、タスクグループが取り消されたかを示す値。 詳細については、「 [task_group_status](concurrency-namespace-enums.md#task_group_status)」を参照してください。

### <a name="remarks"></a>コメント

この `task_group` オブジェクトに対してスケジュールされた1つ以上のタスクが、呼び出し元のコンテキストでインラインで実行される可能性があることに注意してください。

この `task_group` オブジェクトに対してスケジュールされている1つ以上のタスクが例外をスローした場合、ランタイムはその例外を選択して、`run_and_wait` メソッドの呼び出しの外に伝達します。

`task_group` オブジェクトの `run_and_wait` メソッドから戻ると、ランタイムはオブジェクトを再利用できるクリーンな状態にリセットします。 これには、`task_group` オブジェクトが取り消されたケースも含まれます。

実行の例外的なパスでは、`task_group` のデストラクターが実行される前に、このメソッドまたは `wait` メソッドのいずれかを呼び出す必要があります。

## <a name="ctor"></a>task_group

新しい `task_group` オブジェクトを構築します。

```cpp
task_group();

task_group(
   cancellation_token _CancellationToken
);
```

### <a name="parameters"></a>パラメーター

*_CancellationToken*<br/>
このタスクグループに関連付けるキャンセルトークン。 トークンが取り消されると、タスクグループは取り消されます。

### <a name="remarks"></a>コメント

キャンセルトークンを受け取るコンストラクターは、トークンに関連付けられているソースが取り消されたときにキャンセルされる `task_group` を作成します。 また、明示的なキャンセルトークンを指定すると、このタスクグループは、別のトークンまたはトークンを持たない親グループからの暗黙的な取り消しに参加しないように分離されます。

## <a name="dtor"></a>~ task_group

`task_group` オブジェクトを破棄します。 例外により、デストラクターがスタックアンワインドの結果として実行されていない限り、デストラクターを実行する前に、オブジェクトの `wait` または `run_and_wait` メソッドを呼び出す必要があります。

```cpp
~task_group();
```

### <a name="remarks"></a>コメント

デストラクターが通常の実行の結果として実行された場合 (たとえば、例外が原因でスタックアンワインドが発生していない場合)、`wait` も `run_and_wait` メソッドも呼び出されていないと、デストラクターは[missing_wait](missing-wait-class.md)例外をスローする可能性があります。

## <a name="wait"></a>待機

`task_group` オブジェクトのすべての作業が完了するか、取り消されるまで待機します。

```cpp
task_group_status wait();
```

### <a name="return-value"></a>戻り値

明示的な取り消し操作、またはそのタスクの1つからスローされた例外が原因で、待機が満たされたか、タスクグループが取り消されたかを示す値。 詳細については、「 [task_group_status](concurrency-namespace-enums.md#task_group_status)」を参照してください。

### <a name="remarks"></a>コメント

この `task_group` オブジェクトに対してスケジュールされた1つ以上のタスクが、呼び出し元のコンテキストでインラインで実行される可能性があることに注意してください。

この `task_group` オブジェクトに対してスケジュールされている1つ以上のタスクが例外をスローした場合、ランタイムはその例外を選択して、`wait` メソッドの呼び出しの外に伝達します。

`task_group` オブジェクトで `wait` を呼び出すと、再利用できるクリーンな状態にリセットされます。 これには、`task_group` オブジェクトが取り消されたケースも含まれます。

実行の例外的なパスでは、`task_group` のデストラクターが実行される前に、このメソッドまたは `run_and_wait` メソッドのいずれかを呼び出す必要があります。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[structured_task_group クラス](structured-task-group-class.md)<br/>
[task_handle クラス](task-handle-class.md)
