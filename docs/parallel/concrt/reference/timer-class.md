---
title: timer クラス
ms.date: 11/04/2016
f1_keywords:
- timer
- AGENTS/concurrency::timer
- AGENTS/concurrency::timer::timer
- AGENTS/concurrency::timer::pause
- AGENTS/concurrency::timer::start
- AGENTS/concurrency::timer::stop
- AGENTS/concurrency::timer::accept_message
- AGENTS/concurrency::timer::consume_message
- AGENTS/concurrency::timer::link_target_notification
- AGENTS/concurrency::timer::propagate_to_any_targets
- AGENTS/concurrency::timer::release_message
- AGENTS/concurrency::timer::reserve_message
- AGENTS/concurrency::timer::resume_propagation
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
ms.openlocfilehash: c39afc565a7ec775600b9c9fb6f15a89acdef57b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142530"
---
# <a name="timer-class"></a>timer クラス

`timer` メッセージング ブロックは単一のターゲットを持つ `source_block` であり、指定された時間の経過後か、特定の間隔で、メッセージをターゲットに送信することができます。

## <a name="syntax"></a>構文

```cpp
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
このブロックの出力メッセージのペイロードの種類。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[期限](#ctor)|オーバーロードされます。 指定された期間の後に特定のメッセージを起動する `timer` メッセージングブロックを構築します。|
|[~ timer デストラクター](#dtor)|`timer` メッセージングブロックを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[停止](#pause)|`timer` メッセージングブロックを停止します。 繰り返し `timer` メッセージングブロックの場合は、後続の `start()` 呼び出しを使用して再起動できます。 非繰り返しタイマーの場合、これは `stop` の呼び出しと同じ効果があります。|
|[start](#start)|`timer` メッセージングブロックを開始します。 このが呼び出されてから指定されたミリ秒数が経過すると、指定された値は `message`として下流に伝達されます。|
|[stop](#stop)|`timer` メッセージングブロックを停止します。|

### <a name="protected-methods"></a>プロテクト メソッド

|Name|説明|
|----------|-----------------|
|[accept_message](#accept_message)|この `timer` メッセージングブロックによって提供されたメッセージを受け取り、所有権を呼び出し元に転送します。|
|[consume_message](#consume_message)|`timer` が以前に提供し、ターゲットによって予約されているメッセージを使用して、所有権を呼び出し元に譲渡します。|
|[link_target_notification](#link_target_notification)|新しいターゲットがこの `timer` メッセージングブロックにリンクされていることを通知するコールバック。|
|[propagate_to_any_targets](#propagate_to_any_targets)|`timer` ブロックによって生成されたメッセージを、リンクされたすべてのターゲットに提供しようとします。|
|[release_message](#release_message)|以前のメッセージ予約を解放します。 ( [Source_block:: release_message](source-block-class.md#release_message)をオーバーライドします。)|
|[reserve_message](#reserve_message)|この `timer` メッセージングブロックによって以前に提供されたメッセージを予約します。 ( [Source_block:: reserve_message](source-block-class.md#reserve_message)をオーバーライドします。)|
|[resume_propagation](#resume_propagation)|予約が解放された後、伝達を再開します。 ( [Source_block:: resume_propagation](source-block-class.md#resume_propagation)をオーバーライドします。)|

## <a name="remarks"></a>コメント

詳細については、「[非同期メッセージブロック](../../../parallel/concrt/asynchronous-message-blocks.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[ISource](isource-class.md)

[source_block](source-block-class.md)

`timer`

## <a name="requirements"></a>要件

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="accept_message"></a>accept_message

この `timer` メッセージングブロックによって提供されたメッセージを受け取り、所有権を呼び出し元に転送します。

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
提供された `message` オブジェクトの `runtime_object_identity`。

### <a name="return-value"></a>戻り値

呼び出し元が所有権を持っている `message` オブジェクトへのポインター。

## <a name="consume_message"></a>consume_message

`timer` が以前に提供し、ターゲットによって予約されているメッセージを使用して、所有権を呼び出し元に譲渡します。

```cpp
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
使用されている `message` オブジェクトの `runtime_object_identity`。

### <a name="return-value"></a>戻り値

呼び出し元が所有権を持っている `message` オブジェクトへのポインター。

### <a name="remarks"></a>コメント

`accept`と似ていますが、常に `reserve`の呼び出しが前に続きます。

## <a name="link_target_notification"></a>link_target_notification

新しいターゲットがこの `timer` メッセージングブロックにリンクされていることを通知するコールバック。

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
新しくリンクされたターゲットへのポインター。

## <a name="pause"></a>停止

`timer` メッセージングブロックを停止します。 繰り返し `timer` メッセージングブロックの場合は、後続の `start()` 呼び出しを使用して再起動できます。 非繰り返しタイマーの場合、これは `stop` の呼び出しと同じ効果があります。

```cpp
void pause();
```

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

`timer` ブロックによって生成されたメッセージを、リンクされたすべてのターゲットに提供しようとします。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
```

## <a name="release_message"></a>release_message

以前のメッセージ予約を解放します。

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
解放される `message` オブジェクトの `runtime_object_identity`。

## <a name="reserve_message"></a>reserve_message

この `timer` メッセージングブロックによって以前に提供されたメッセージを予約します。

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
予約されている `message` オブジェクトの `runtime_object_identity`。

### <a name="return-value"></a>戻り値

メッセージが正常に予約されている場合は**true** 、それ以外の場合は**false** 。

### <a name="remarks"></a>コメント

`reserve` が呼び出された後、 **true**が返された場合は、メッセージの所有権を取得または解放するために、`consume` または `release` のいずれかを呼び出す必要があります。

## <a name="resume_propagation"></a>resume_propagation

予約が解放された後、伝達を再開します。

```cpp
virtual void resume_propagation();
```

## <a name="start"></a>着手

`timer` メッセージングブロックを開始します。 このが呼び出されてから指定されたミリ秒数が経過すると、指定された値は `message`として下流に伝達されます。

```cpp
void start();
```

## <a name="stop"></a>停止

`timer` メッセージングブロックを停止します。

```cpp
void stop();
```

## <a name="ctor"></a>期限

指定された期間の後に特定のメッセージを起動する `timer` メッセージングブロックを構築します。

```cpp
timer(
    unsigned int _Ms,
    T const& value,
    ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    Scheduler& _Scheduler,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    ScheduleGroup& _ScheduleGroup,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);
```

### <a name="parameters"></a>パラメーター

*_Ms*<br/>
指定したメッセージが下流に伝達されるまでの呼び出しが開始されてからの経過時間 (ミリ秒単位)。

*value*<br/>
タイマーが経過したときにダウンストリームに反映される値。

*_PTarget*<br/>
タイマーがメッセージを伝達するターゲット。

*_Repeating*<br/>
True の場合は、タイマーが `_Ms` ミリ秒ごとに定期的に起動されることを示します。

*_Scheduler*<br/>
`timer` メッセージングブロックの反映タスクがスケジュールされている `Scheduler` オブジェクトがスケジュールされています。

*_ScheduleGroup*<br/>
その内部で `ScheduleGroup` メッセージング ブロックの反映タスクがスケジュールされる `timer` オブジェクト。 使用される `Scheduler` オブジェクトは、スケジュール グループによって暗黙的に指定されます。

### <a name="remarks"></a>コメント

`_Scheduler` または `_ScheduleGroup` パラメーターを指定しない場合、ランタイムは既定のスケジューラを使用しています。

## <a name="dtor"></a>~ timer

`timer` メッセージングブロックを破棄します。

```cpp
~timer();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
