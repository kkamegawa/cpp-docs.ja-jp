---
title: join クラス
ms.date: 11/04/2016
f1_keywords:
- join
- AGENTS/concurrency::join
- AGENTS/concurrency::join::join
- AGENTS/concurrency::join::accept_message
- AGENTS/concurrency::join::consume_message
- AGENTS/concurrency::join::link_target_notification
- AGENTS/concurrency::join::propagate_message
- AGENTS/concurrency::join::propagate_to_any_targets
- AGENTS/concurrency::join::release_message
- AGENTS/concurrency::join::reserve_message
- AGENTS/concurrency::join::resume_propagation
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
ms.openlocfilehash: f75cf8483e7d6d65d118cc8f0ea756302d1b1d7c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139845"
---
# <a name="join-class"></a>join クラス

`join` メッセージング ブロックは、単一のターゲットと複数のソースを持つ順序付けられた `propagator_block` であり、各ソースから、種類が `T` であるメッセージを結合します。

## <a name="syntax"></a>構文

```cpp
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
ブロックによって結合および伝達されたメッセージのペイロードの種類。

*_Jtype*<br/>
`join` ブロックの種類は、`greedy` またはのいずれかになり `non_greedy`

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[join](#ctor)|オーバーロードされます。 `join` メッセージング ブロックを構築します。|
|[~ 結合デストラクター](#dtor)|`join` ブロックを破棄します。|

### <a name="protected-methods"></a>プロテクト メソッド

|Name|説明|
|----------|-----------------|
|[accept_message](#accept_message)|この `join` メッセージングブロックによって提供されたメッセージを受け取り、所有権を呼び出し元に転送します。|
|[consume_message](#consume_message)|`join` メッセージングブロックによって既に提供され、ターゲットによって予約されているメッセージを使用して、所有権を呼び出し元に譲渡します。|
|[link_target_notification](#link_target_notification)|新しいターゲットがこの `join` メッセージングブロックにリンクされていることを通知するコールバック。|
|[propagate_message](#propagate_message)|`ISource` ブロックからこの `join` メッセージングブロックに非同期的にメッセージを渡します。 これは、ソースブロックによって呼び出されたときに、`propagate` メソッドによって呼び出されます。|
|[propagate_to_any_targets](#propagate_to_any_targets)|すべての送信元からの入力メッセージを含む出力メッセージを構築します。 この出力メッセージを各ターゲットに送信します。|
|[release_message](#release_message)|以前のメッセージ予約を解放します。 ( [Source_block:: release_message](source-block-class.md#release_message)をオーバーライドします。)|
|[reserve_message](#reserve_message)|この `join` メッセージングブロックによって以前に提供されたメッセージを予約します。 ( [Source_block:: reserve_message](source-block-class.md#reserve_message)をオーバーライドします。)|
|[resume_propagation](#resume_propagation)|予約が解放された後、伝達を再開します。 ( [Source_block:: resume_propagation](source-block-class.md#resume_propagation)をオーバーライドします。)|

## <a name="remarks"></a>コメント

詳細については、「[非同期メッセージブロック](../../../parallel/concrt/asynchronous-message-blocks.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`join`

## <a name="requirements"></a>要件

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="accept_message"></a>accept_message

この `join` メッセージングブロックによって提供されたメッセージを受け取り、所有権を呼び出し元に転送します。

```cpp
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
提供された `message` オブジェクトの `runtime_object_identity`。

### <a name="return-value"></a>戻り値

呼び出し元が所有権を持っている `message` オブジェクトへのポインター。

## <a name="consume_message"></a>consume_message

`join` メッセージングブロックによって既に提供され、ターゲットによって予約されているメッセージを使用して、所有権を呼び出し元に譲渡します。

```cpp
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
使用されている `message` オブジェクトの `runtime_object_identity`。

### <a name="return-value"></a>戻り値

呼び出し元が所有権を持っている `message` オブジェクトへのポインター。

### <a name="remarks"></a>コメント

`accept`と似ていますが、常に `reserve`の呼び出しが前に続きます。

## <a name="ctor"></a>結合

`join` メッセージング ブロックを構築します。

```cpp
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```

### <a name="parameters"></a>パラメーター

*_NumInputs*<br/>
この `join` ブロックが許可される入力の数。

*_Filter*<br/>
提供されたメッセージを受け入れるかどうかを決定するフィルター関数。

*_PScheduler*<br/>
その内部で `Scheduler` メッセージング ブロックの反映タスクがスケジュールされる `join` オブジェクト。

*_PScheduleGroup*<br/>
その内部で `ScheduleGroup` メッセージング ブロックの反映タスクがスケジュールされる `join` オブジェクト。 使用される `Scheduler` オブジェクトは、スケジュール グループによって暗黙的に指定されます。

### <a name="remarks"></a>コメント

`_PScheduler` または `_PScheduleGroup` パラメーターを指定しない場合、ランタイムは既定のスケジューラを使用しています。

`filter_method` 型は、提供されたメッセージを受け入れるかどうかを判断するために、この `join` メッセージングブロックによって呼び出される、シグネチャ `bool (T const &)` のファンクタです。

## <a name="dtor"></a>~ join

`join` ブロックを破棄します。

```cpp
~join();
```

## <a name="link_target_notification"></a>link_target_notification

新しいターゲットがこの `join` メッセージングブロックにリンクされていることを通知するコールバック。

```cpp
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```

## <a name="propagate_message"></a>propagate_message

`ISource` ブロックからこの `join` メッセージングブロックに非同期的にメッセージを渡します。 これは、ソースブロックによって呼び出されたときに、`propagate` メソッドによって呼び出されます。

```cpp
message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
`message` オブジェクトを指すポインター。

*_PSource*<br/>
メッセージを提供するソースブロックへのポインター。

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した[message_status](concurrency-namespace-enums.md)を示します。

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

すべての送信元からの入力メッセージを含む出力メッセージを構築します。 この出力メッセージを各ターゲットに送信します。

```cpp
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
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

この `join` メッセージングブロックによって以前に提供されたメッセージを予約します。

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
提供された `message` オブジェクトの `runtime_object_identity`。

### <a name="return-value"></a>戻り値

メッセージが正常に予約されている場合は**true** 、それ以外の場合は**false** 。

### <a name="remarks"></a>コメント

`reserve` が呼び出された後、 **true**が返された場合は、メッセージの所有権を取得または解放するために、`consume` または `release` のいずれかを呼び出す必要があります。

## <a name="resume_propagation"></a>resume_propagation

予約が解放された後、伝達を再開します。

```cpp
virtual void resume_propagation();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[choice クラス](choice-class.md)<br/>
[multitype_join クラス](multitype-join-class.md)
