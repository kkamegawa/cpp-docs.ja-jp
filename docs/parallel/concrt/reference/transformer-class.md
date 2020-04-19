---
title: transformer クラス
ms.date: 11/04/2016
f1_keywords:
- transformer
- AGENTS/concurrency::transformer
- AGENTS/concurrency::transformer::transformer
- AGENTS/concurrency::transformer::accept_message
- AGENTS/concurrency::transformer::consume_message
- AGENTS/concurrency::transformer::link_target_notification
- AGENTS/concurrency::transformer::propagate_message
- AGENTS/concurrency::transformer::propagate_to_any_targets
- AGENTS/concurrency::transformer::release_message
- AGENTS/concurrency::transformer::reserve_message
- AGENTS/concurrency::transformer::resume_propagation
- AGENTS/concurrency::transformer::send_message
- AGENTS/concurrency::transformer::supports_anonymous_source
helpviewer_keywords:
- transformer class
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
ms.openlocfilehash: 75c7697087b8b3ad8ff15ae4d08f2b4701aaa36a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142353"
---
# <a name="transformer-class"></a>transformer クラス

`transformer` メッセージング ブロックは、単一のターゲットと複数のソースを持つ順序付けられた `propagator_block` であり、1 つの種類のメッセージを複数受け入れ、別の種類のメッセージを無制限に格納することができます。

## <a name="syntax"></a>構文

```cpp
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```

### <a name="parameters"></a>パラメーター

*_Input*<br/>
バッファーによって受け入れられるメッセージのペイロードの種類。

*_Output*<br/>
バッファーに格納され、バッファーによって伝達されるメッセージのペイロードの種類。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[変換](#ctor)|オーバーロードされます。 `transformer` メッセージング ブロックを構築します。|
|[~ トランスフォーマーデストラクター](#dtor)|`transformer` メッセージングブロックを破棄します。|

### <a name="protected-methods"></a>プロテクト メソッド

|Name|説明|
|----------|-----------------|
|[accept_message](#accept_message)|この `transformer` メッセージングブロックによって提供されたメッセージを受け取り、所有権を呼び出し元に転送します。|
|[consume_message](#consume_message)|`transformer` が以前に提供し、ターゲットによって予約されているメッセージを使用して、所有権を呼び出し元に譲渡します。|
|[link_target_notification](#link_target_notification)|新しいターゲットがこの `transformer` メッセージングブロックにリンクされていることを通知するコールバック。|
|[propagate_message](#propagate_message)|`ISource` ブロックからこの `transformer` メッセージングブロックに非同期的にメッセージを渡します。 これは、ソースブロックによって呼び出されたときに、`propagate` メソッドによって呼び出されます。|
|[propagate_to_any_targets](#propagate_to_any_targets)|入力メッセージに対してトランスフォーマー関数を実行します。|
|[release_message](#release_message)|以前のメッセージ予約を解放します。 ( [Source_block:: release_message](source-block-class.md#release_message)をオーバーライドします。)|
|[reserve_message](#reserve_message)|この `transformer` メッセージングブロックによって以前に提供されたメッセージを予約します。 ( [Source_block:: reserve_message](source-block-class.md#reserve_message)をオーバーライドします。)|
|[resume_propagation](#resume_propagation)|予約が解放された後、伝達を再開します。 ( [Source_block:: resume_propagation](source-block-class.md#resume_propagation)をオーバーライドします。)|
|[send_message](#send_message)|`ISource` ブロックからのメッセージを、この `transformer` メッセージングブロックに同期的に渡します。 これは、ソースブロックによって呼び出されたときに、`send` メソッドによって呼び出されます。|
|[supports_anonymous_source](#supports_anonymous_source)|`supports_anonymous_source` メソッドをオーバーライドして、このブロックがリンクされていないソースによって提供されるメッセージを受け入れることができることを示します。 ( [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source)よりも優先されます)。|

## <a name="remarks"></a>解説

詳細については、「[非同期メッセージブロック](../../../parallel/concrt/asynchronous-message-blocks.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`transformer`

## <a name="requirements"></a>［要件］

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="accept_message"></a>accept_message

この `transformer` メッセージングブロックによって提供されたメッセージを受け取り、所有権を呼び出し元に転送します。

```cpp
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
提供された `message` オブジェクトの `runtime_object_identity`。

### <a name="return-value"></a>戻り値

呼び出し元が所有権を持っている `message` オブジェクトへのポインター。

## <a name="consume_message"></a>consume_message

`transformer` が以前に提供し、ターゲットによって予約されているメッセージを使用して、所有権を呼び出し元に譲渡します。

```cpp
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
使用されている `message` オブジェクトの `runtime_object_identity`。

### <a name="return-value"></a>戻り値

呼び出し元が所有権を持っている `message` オブジェクトへのポインター。

### <a name="remarks"></a>解説

`accept`と似ていますが、常に `reserve`の呼び出しが前に続きます。

## <a name="link_target_notification"></a>link_target_notification

新しいターゲットがこの `transformer` メッセージングブロックにリンクされていることを通知するコールバック。

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

## <a name="propagate_message"></a>propagate_message

`ISource` ブロックからこの `transformer` メッセージングブロックに非同期的にメッセージを渡します。 これは、ソースブロックによって呼び出されたときに、`propagate` メソッドによって呼び出されます。

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
`message` オブジェクトを指すポインター。

*_PSource*<br/>
メッセージを提供するソースブロックへのポインター。

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した[message_status](concurrency-namespace-enums.md)を示します。

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

入力メッセージに対してトランスフォーマー関数を実行します。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
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

この `transformer` メッセージングブロックによって以前に提供されたメッセージを予約します。

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
予約されている `message` オブジェクトの `runtime_object_identity`。

### <a name="return-value"></a>戻り値

メッセージが正常に予約されている場合は**true** 、それ以外の場合は**false** 。

### <a name="remarks"></a>解説

`reserve` が呼び出された後、 **true**が返された場合は、メッセージの所有権を取得または解放するために、`consume` または `release` のいずれかを呼び出す必要があります。

## <a name="resume_propagation"></a>resume_propagation

予約が解放された後、伝達を再開します。

```cpp
virtual void resume_propagation();
```

## <a name="send_message"></a>send_message

`ISource` ブロックからのメッセージを、この `transformer` メッセージングブロックに同期的に渡します。 これは、ソースブロックによって呼び出されたときに、`send` メソッドによって呼び出されます。

```cpp
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
`message` オブジェクトを指すポインター。

*_PSource*<br/>
メッセージを提供するソースブロックへのポインター。

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した[message_status](concurrency-namespace-enums.md)を示します。

## <a name="supports_anonymous_source"></a>supports_anonymous_source

`supports_anonymous_source` メソッドをオーバーライドして、このブロックがリンクされていないソースによって提供されるメッセージを受け入れることができることを示します。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>戻り値

ブロックは提供されたメッセージを延期しないため、 **true**になります。

## <a name="ctor"></a>変換

`transformer` メッセージング ブロックを構築します。

```cpp
transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);
```

### <a name="parameters"></a>パラメーター

*_Func*<br/>
受け入れられた各メッセージに対して呼び出される関数。

*_PTarget*<br/>
トランスフォーマーとリンクするターゲットブロックへのポインター。

*_Filter*<br/>
提供されたメッセージを受け入れるかどうかを決定するフィルター関数。

*_PScheduler*<br/>
その内部で `Scheduler` メッセージング ブロックの反映タスクがスケジュールされる `transformer` オブジェクト。

*_PScheduleGroup*<br/>
その内部で `ScheduleGroup` メッセージング ブロックの反映タスクがスケジュールされる `transformer` オブジェクト。 使用される `Scheduler` オブジェクトは、スケジュール グループによって暗黙的に指定されます。

### <a name="remarks"></a>解説

`_PScheduler` または `_PScheduleGroup` パラメーターを指定しない場合、ランタイムは既定のスケジューラを使用しています。

`_Transform_method` 型は、メッセージを処理するためにこの `transformer` メッセージングブロックによって呼び出されるシグネチャ `_Output (_Input const &)` を持つファンクタです。

`filter_method` 型は、提供されたメッセージを受け入れるかどうかを判断するために、この `transformer` メッセージングブロックによって呼び出される、シグネチャ `bool (_Input const &)` のファンクタです。

## <a name="dtor"></a>~ トランスフォーマー

`transformer` メッセージングブロックを破棄します。

```cpp
~transformer();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[call クラス](call-class.md)
