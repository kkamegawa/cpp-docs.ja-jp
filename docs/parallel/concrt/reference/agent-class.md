---
title: agent クラス
ms.date: 11/04/2016
f1_keywords:
- agent
- AGENTS/concurrency::agent
- AGENTS/concurrency::agent::agent
- AGENTS/concurrency::agent::cancel
- AGENTS/concurrency::agent::start
- AGENTS/concurrency::agent::status
- AGENTS/concurrency::agent::status_port
- AGENTS/concurrency::agent::wait
- AGENTS/concurrency::agent::wait_for_all
- AGENTS/concurrency::agent::wait_for_one
- AGENTS/concurrency::agent::done
- AGENTS/concurrency::agent::run
helpviewer_keywords:
- agent class
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
ms.openlocfilehash: f0092f5f90bbdf253c09dbdc80849c3db472212f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142888"
---
# <a name="agent-class"></a>agent クラス

すべての独立エージェントの基底クラスとして使用されるクラスです。 他のエージェントに状態が表示されないようにしたり、メッセージ渡しでやり取りしたりする目的で使用されます。

## <a name="syntax"></a>構文

```cpp
class agent;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[・](#ctor)|オーバーロードされます。 エージェントを構築します。|
|[~ エージェントデストラクター](#dtor)|エージェントを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[cancel](#cancel)|エージェントを `agent_created` または `agent_runnable` の状態から `agent_canceled` 状態に移動します。|
|[start](#start)|エージェントを `agent_created` 状態から `agent_runnable` 状態に移動し、実行のスケジュールをスケジュールします。|
|[status](#status)|エージェントからの状態情報の同期ソース。|
|[status_port](#status_port)|エージェントからの状態情報の非同期ソース。|
|[待機](#wait)|エージェントのタスクが完了するまで待機します。|
|[wait_for_all](#wait_for_all)|指定されたすべてのエージェントのタスクが完了するまで待機します。|
|[wait_for_one](#wait_for_one)|指定されたいずれかのエージェントがタスクを完了するまで待機します。|

### <a name="protected-methods"></a>プロテクト メソッド

|Name|説明|
|----------|-----------------|
|[完成です](#done)|エージェントを `agent_done` 状態に移動し、エージェントが完了したことを示します。|
|[run](#run)|エージェントのメインタスクを表します。 `run` は、派生クラスでオーバーライドする必要があり、エージェントが開始された後に実行する必要があるものを指定します。|

## <a name="remarks"></a>解説

詳細については、「[非同期エージェント](../../../parallel/concrt/asynchronous-agents.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`agent`

## <a name="requirements"></a>［要件］

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="ctor"></a>・

エージェントを構築します。

```cpp
agent();

agent(Scheduler& _PScheduler);

agent(ScheduleGroup& _PGroup);
```

### <a name="parameters"></a>パラメーター

*_PScheduler*<br/>
エージェントの実行タスクがスケジュールされている `Scheduler` オブジェクトです。

*_PGroup*<br/>
エージェントの実行タスクがスケジュールされている `ScheduleGroup` オブジェクトです。 使用される `Scheduler` オブジェクトは、スケジュール グループによって暗黙的に指定されます。

### <a name="remarks"></a>解説

`_PScheduler` または `_PGroup` パラメーターを指定しない場合、ランタイムは既定のスケジューラを使用しています。

## <a name="dtor"></a>~ エージェント

エージェントを破棄します。

```cpp
virtual ~agent();
```

### <a name="remarks"></a>解説

ターミナル状態 (`agent_done` または `agent_canceled`) に含まれていないエージェントを破棄すると、エラーになります。 これは、`agent` クラスを継承するクラスのデストラクターでエージェントがターミナル状態になるのを待機することによって回避できます。

## <a name="cancel"></a>キャンセル

エージェントを `agent_created` または `agent_runnable` の状態から `agent_canceled` 状態に移動します。

```cpp
bool cancel();
```

### <a name="return-value"></a>戻り値

エージェントが取り消された場合は**true** 、それ以外の場合は**false** 。 エージェントが既に実行を開始しているか、既に完了している場合、エージェントを取り消すことはできません。

## <a name="done"></a>完成です

エージェントを `agent_done` 状態に移動し、エージェントが完了したことを示します。

```cpp
bool done();
```

### <a name="return-value"></a>戻り値

エージェントが `agent_done` 状態に移動した場合は**true** 、それ以外の場合は**false** 。 取り消されたエージェントを `agent_done` 状態に移行することはできません。

### <a name="remarks"></a>解説

エージェントの実行が完了したことがわかっている場合は、`run` メソッドの最後にこのメソッドを呼び出す必要があります。

## <a name="run"></a>実行

エージェントのメインタスクを表します。 `run` は、派生クラスでオーバーライドする必要があり、エージェントが開始された後に実行する必要があるものを指定します。

```cpp
virtual void run() = 0;
```

### <a name="remarks"></a>解説

このメソッドが呼び出される直前に、エージェントの状態が `agent_started` に変更されます。 メソッドは、を返す前に、適切な状態でエージェントの `done` を呼び出す必要があり、例外をスローしないことがあります。

## <a name="start"></a>着手

エージェントを `agent_created` 状態から `agent_runnable` 状態に移動し、実行のスケジュールをスケジュールします。

```cpp
bool start();
```

### <a name="return-value"></a>戻り値

エージェントが正常に開始された場合は**true** 、それ以外の場合は**false** 。 取り消されたエージェントを開始できません。

## <a name="status"></a>オンライン

エージェントからの状態情報の同期ソース。

```cpp
agent_status status();
```

### <a name="return-value"></a>戻り値

エージェントの現在の状態を返します。 返された状態は、返された直後に変更される可能性があることに注意してください。

## <a name="status_port"></a>status_port

エージェントからの状態情報の非同期ソース。

```cpp
ISource<agent_status>* status_port();
```

### <a name="return-value"></a>戻り値

エージェントの現在の状態に関するメッセージを送信できるメッセージソースを返します。

## <a name="wait"></a>待機

エージェントのタスクが完了するまで待機します。

```cpp
static agent_status __cdecl wait(
    _Inout_ agent* _PAgent,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>パラメーター

*_PAgent*<br/>
待機するエージェントへのポインター。

*_Timeout*<br/>
待機する最大時間 (ミリ秒単位)。

### <a name="return-value"></a>戻り値

待機が完了したときのエージェントの `agent_status`。 これは、`agent_canceled` または `agent_done`のいずれかになります。

### <a name="remarks"></a>解説

エージェントタスクは、エージェントが `agent_canceled` または `agent_done` の状態を入力すると完了します。

パラメーター `_Timeout` に定数 `COOPERATIVE_TIMEOUT_INFINITE`以外の値が指定されている場合、エージェントがそのタスクを完了する前に指定した時間が経過すると、例外[operation_timed_out](operation-timed-out-class.md)がスローされます。

## <a name="wait_for_all"></a>wait_for_all

指定されたすべてのエージェントのタスクが完了するまで待機します。

```cpp
static void __cdecl wait_for_all(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    _Out_writes_opt_(count) agent_status* _PStatus = NULL,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>パラメーター

*count*<br/>
配列 `_PAgents`に存在するエージェントポインターの数。

*_PAgents*<br/>
待機するエージェントへのポインターの配列。

*_PStatus*<br/>
エージェントの状態の配列へのポインター。 各状態値は、メソッドから制御が戻ったときに、対応するエージェントの状態を表します。

*_Timeout*<br/>
待機する最大時間 (ミリ秒単位)。

### <a name="remarks"></a>解説

エージェントタスクは、エージェントが `agent_canceled` または `agent_done` の状態を入力すると完了します。

パラメーター `_Timeout` に定数 `COOPERATIVE_TIMEOUT_INFINITE`以外の値が指定されている場合、エージェントがそのタスクを完了する前に指定した時間が経過すると、例外[operation_timed_out](operation-timed-out-class.md)がスローされます。

## <a name="wait_for_one"></a>wait_for_one

指定されたいずれかのエージェントがタスクを完了するまで待機します。

```cpp
static void __cdecl wait_for_one(
    size_t count,
    _In_reads_(count) agent** _PAgents,
    agent_status& _Status,
    size_t& _Index,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>パラメーター

*count*<br/>
配列 `_PAgents`に存在するエージェントポインターの数。

*_PAgents*<br/>
待機するエージェントへのポインターの配列。

*_Status*<br/>
エージェントの状態を配置する変数への参照。

*_Index*<br/>
エージェントインデックスが配置される変数への参照。

*_Timeout*<br/>
待機する最大時間 (ミリ秒単位)。

### <a name="remarks"></a>解説

エージェントタスクは、エージェントが `agent_canceled` または `agent_done` の状態を入力すると完了します。

パラメーター `_Timeout` に定数 `COOPERATIVE_TIMEOUT_INFINITE`以外の値が指定されている場合、エージェントがそのタスクを完了する前に指定した時間が経過すると、例外[operation_timed_out](operation-timed-out-class.md)がスローされます。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
