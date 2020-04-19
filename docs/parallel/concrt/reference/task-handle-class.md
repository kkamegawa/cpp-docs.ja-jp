---
title: task_handle クラス
ms.date: 03/27/2019
f1_keywords:
- task_handle
- PPL/concurrency::task_handle
- PPL/concurrency::task_handle::task_handle
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
ms.openlocfilehash: a61e72f14448d5033d5be9069ffeec7d3bb08061
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142554"
---
# <a name="task_handle-class"></a>task_handle クラス

`task_handle` クラスは個々の並列作業項目を表します。 このクラスは、1 つの処理を実行するために必要な命令およびデータをカプセル化します。

## <a name="syntax"></a>構文

```cpp
template<
    typename _Function
>
class task_handle : public ::Concurrency::details::_UnrealizedChore;
```

### <a name="parameters"></a>パラメーター

*_Function*<br/>
`task_handle` オブジェクトによって表される作業を実行するために呼び出される関数オブジェクトの型。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[task_handle](#task_handle)|新しい `task_handle` オブジェクトを構築します。 タスクの作業は、コンストラクターへのパラメーターとして指定された関数を呼び出すことによって実行されます。|
|[~ task_handle デストラクター](#dtor)|`task_handle` オブジェクトを破棄します。|

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|[演算子 ()](#task_handle__operator_call)|タスクハンドルの処理を実行するためにランタイムが呼び出す関数呼び出し演算子。|

## <a name="remarks"></a>コメント

`task_handle` オブジェクトを `structured_task_group` またはより一般的な `task_group` オブジェクトと組み合わせて使用して、作業を並列タスクに分解することができます。 詳細については、「[タスクの並列](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)化」を参照してください。

`task_handle` オブジェクトの作成者は、同時実行ランタイムで不要になるまで、作成された `task_handle` オブジェクトの有効期間を維持する必要があることに注意してください。 通常、これは、`task_handle` オブジェクトが、キューに置かれている `task_group` または `structured_task_group` の `wait` または `run_and_wait` メソッドが呼び出されるまで破棄されないことを意味します。

通常、`task_handle` オブジェクトは、ラムダとC++組み合わせて使用されます。 ラムダの実際の型がわからないため、 [make_task](concurrency-namespace-functions.md#make_task)関数は通常、`task_handle` オブジェクトを作成するために使用されます。

ランタイムは、`task_handle` オブジェクトに渡す作業関数のコピーを作成します。 したがって、`task_handle` オブジェクトに渡す関数オブジェクトで発生した状態の変更は、その関数オブジェクトのコピーには表示されません。

## <a name="inheritance-hierarchy"></a>継承階層

`task_handle`

## <a name="requirements"></a>要件

**ヘッダー:** ppl

**名前空間:** concurrency

## <a name="task_handle__operator_call"></a>operator ()

タスクハンドルの処理を実行するためにランタイムが呼び出す関数呼び出し演算子。

```cpp
void operator()() const;
```

## <a name="task_handle"></a>task_handle

新しい `task_handle` オブジェクトを構築します。 タスクの作業は、コンストラクターへのパラメーターとして指定された関数を呼び出すことによって実行されます。

```cpp
task_handle(const _Function& _Func);
```

### <a name="parameters"></a>パラメーター

*_Func*<br/>
`task_handle` オブジェクトによって表される作業を実行するために呼び出される関数。 これには、ラムダファンクタ、関数へのポインター、または `void operator()()`シグネチャを持つ関数呼び出し演算子のバージョンをサポートする任意のオブジェクトを指定できます。

### <a name="remarks"></a>コメント

ランタイムは、コンストラクターに渡す作業関数のコピーを作成します。 したがって、`task_handle` オブジェクトに渡す関数オブジェクトで発生した状態の変更は、その関数オブジェクトのコピーには表示されません。

## <a name="dtor"></a>~ task_handle

`task_handle` オブジェクトを破棄します。

```cpp
~task_handle();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[task_group クラス](task-group-class.md)<br/>
[structured_task_group クラス](structured-task-group-class.md)
