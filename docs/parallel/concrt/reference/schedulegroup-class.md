---
title: ScheduleGroup クラス
ms.date: 11/04/2016
f1_keywords:
- ScheduleGroup
- CONCRT/concurrency::ScheduleGroup
- CONCRT/concurrency::ScheduleGroup::Id
- CONCRT/concurrency::ScheduleGroup::Reference
- CONCRT/concurrency::ScheduleGroup::Release
- CONCRT/concurrency::ScheduleGroup::ScheduleTask
helpviewer_keywords:
- ScheduleGroup class
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
ms.openlocfilehash: 8686b5ef0906e3188a1e683d1190bbe6124cd19e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143267"
---
# <a name="schedulegroup-class"></a>ScheduleGroup クラス

スケジュール グループの抽象化を表します。 スケジュール グループは、(別のグループに移動する前に同じグループ内の別のタスクを実行することで) 一時的に、または (同じ NUMA ノードまたは物理ソケットの同じグループ内の複数の項目を実行することにより) 空間的に、短い間隔でスケジュールするとメリットがある関連作業のセットを編成します。

## <a name="syntax"></a>構文

```cpp
class ScheduleGroup;
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|Name|説明|
|----------|-----------------|
|[~ ScheduleGroup デストラクター](#dtor)||

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[Id](#id)|スケジュール グループが属するスケジューラ内で一意のスケジュール グループの識別子を返します。|
|[リファレンス](#reference)|スケジュール グループの参照カウントをインクリメントします。|
|[リリース](#release)|スケジュール グループの参照カウントをデクリメントします。|
|[ScheduleTask](#scheduletask)|スケジュール グループ内の軽量タスクをスケジュールします。|

## <a name="inheritance-hierarchy"></a>継承階層

`ScheduleGroup`

## <a name="requirements"></a>要件

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="id"></a>番号

スケジュール グループが属するスケジューラ内で一意のスケジュール グループの識別子を返します。

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>戻り値

グループが属するスケジューラ内で一意であるスケジュールグループの識別子。

## <a name="operator_delete"></a>delete 演算子

`ScheduleGroup` オブジェクトは、すべての外部参照が解放されると、ランタイムによって内部的に破棄されます。 明示的に削除することはできません。

```cpp
void operator delete(
    void* _PObject);

void operator delete(
    void* _PObject,
    int,
const char *,
    int);
```

### <a name="parameters"></a>パラメーター

*_PObject*<br/>
削除するオブジェクトへのポインター。

## <a name="reference"></a>「

スケジュール グループの参照カウントをインクリメントします。

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>戻り値

新しくインクリメントされた参照カウント。

### <a name="remarks"></a>コメント

これは通常、構成のスケジュールグループの有効期間を管理するために使用されます。 スケジュールグループの参照カウントがゼロになると、スケジュールグループはランタイムによって削除されます。 [Currentscheduler:: CreateScheduleGroup](currentscheduler-class.md#createschedulegroup)メソッドまたは[Scheduler:: CreateScheduleGroup](scheduler-class.md#createschedulegroup)メソッドを使用して作成されたスケジュールグループは、参照カウントを1つとして開始します。

## <a name="release"></a>解除

スケジュール グループの参照カウントをデクリメントします。

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>戻り値

新しくデクリメントされた参照カウント。

### <a name="remarks"></a>コメント

これは通常、構成のスケジュールグループの有効期間を管理するために使用されます。 スケジュールグループの参照カウントがゼロになると、スケジュールグループはランタイムによって削除されます。 `Release` メソッドを特定の回数だけ呼び出して、作成参照カウントと、`Reference` メソッドを使用して追加されたその他の参照を削除した後は、スケジュールグループをさらに利用することはできません。 これを行うと、未定義の動作が発生します。

スケジュールグループは、特定のスケジューラインスタンスに関連付けられています。 スケジューラへのすべての参照がリリースされる前に、スケジュールグループへのすべての参照が解放されていることを確認する必要があります。これは、スケジューラが破棄される可能性があるためです。 それ以外の場合は、未定義の動作が発生します。

## <a name="dtor"></a>~ ScheduleGroup

```cpp
virtual ~ScheduleGroup();
```

## <a name="scheduletask"></a>ScheduleTask

スケジュール グループ内の軽量タスクをスケジュールします。

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;
```

### <a name="parameters"></a>パラメーター

*_Proc*<br/>
ライトウェイトタスクの本体を実行するために実行する関数へのポインター。

*_Data*<br/>
タスクの本体にパラメーターとして渡されるデータへの void ポインター。

### <a name="remarks"></a>コメント

`ScheduleTask` メソッドを呼び出すと、スケジュールグループに参照カウントが暗黙的に配置されます。これは、タスクの実行後にランタイムによって適切なタイミングで削除されます。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[CurrentScheduler クラス](currentscheduler-class.md)<br/>
[Scheduler クラス](scheduler-class.md)<br/>
[タスク スケジューラ](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
