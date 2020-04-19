---
title: unbounded_buffer クラス
ms.date: 11/04/2016
f1_keywords:
- unbounded_buffer
- AGENTS/concurrency::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::dequeue
- AGENTS/concurrency::unbounded_buffer::enqueue
- AGENTS/concurrency::unbounded_buffer::accept_message
- AGENTS/concurrency::unbounded_buffer::consume_message
- AGENTS/concurrency::unbounded_buffer::link_target_notification
- AGENTS/concurrency::unbounded_buffer::process_input_messages
- AGENTS/concurrency::unbounded_buffer::propagate_message
- AGENTS/concurrency::unbounded_buffer::propagate_output_messages
- AGENTS/concurrency::unbounded_buffer::release_message
- AGENTS/concurrency::unbounded_buffer::reserve_message
- AGENTS/concurrency::unbounded_buffer::resume_propagation
- AGENTS/concurrency::unbounded_buffer::send_message
- AGENTS/concurrency::unbounded_buffer::supports_anonymous_source
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
ms.openlocfilehash: d0f2f81957ee88d4263c6acd879bd286c95631eb
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142333"
---
# <a name="unbounded_buffer-class"></a>unbounded_buffer クラス

`unbounded_buffer` メッセージング ブロックは、メッセージを無制限に格納することができる、複数のターゲットと複数のソースを持つ順序付けられた `propagator_block` です。

## <a name="syntax"></a>構文

```cpp
template<
   class             _Type
>
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;
```

### <a name="parameters"></a>パラメーター

*_Type*<br/>
バッファーによって格納および反映されるメッセージのペイロードの種類。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[unbounded_buffer](#ctor)|オーバーロードされます。 `unbounded_buffer` メッセージングブロックを構築します。|
|[~ unbounded_buffer デストラクター](#dtor)|`unbounded_buffer` メッセージングブロックを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[取り出さ](#dequeue)|`unbounded_buffer` メッセージングブロックから項目を削除します。|
|[入れ](#enqueue)|`unbounded_buffer` メッセージングブロックに項目を追加します。|

### <a name="protected-methods"></a>プロテクト メソッド

|Name|説明|
|----------|-----------------|
|[accept_message](#accept_message)|この `unbounded_buffer` メッセージングブロックによって提供されたメッセージを受け取り、所有権を呼び出し元に転送します。|
|[consume_message](#consume_message)|`unbounded_buffer` メッセージングブロックによって既に提供され、ターゲットによって予約されているメッセージを使用して、所有権を呼び出し元に譲渡します。|
|[link_target_notification](#link_target_notification)|新しいターゲットがこの `unbounded_buffer` メッセージングブロックにリンクされていることを通知するコールバック。|
|[process_input_messages](#process_input_messages)|`message` `_PMessage` をこの `unbounded_buffer` メッセージングブロックに配置し、リンクされたすべてのターゲットに提供しようとします。|
|[propagate_message](#propagate_message)|`ISource` ブロックからこの `unbounded_buffer` メッセージングブロックに非同期的にメッセージを渡します。 これは、ソースブロックによって呼び出されたときに、`propagate` メソッドによって呼び出されます。|
|[propagate_output_messages](#propagate_output_messages)|`message` `_PMessage` をこの `unbounded_buffer` メッセージングブロックに配置し、リンクされたすべてのターゲットに提供しようとします。 ( [Source_block::p ropagate_output_messages](source-block-class.md#propagate_output_messages)をオーバーライドします。)|
|[release_message](#release_message)|以前のメッセージ予約を解放します。 ( [Source_block:: release_message](source-block-class.md#release_message)をオーバーライドします。)|
|[reserve_message](#reserve_message)|この `unbounded_buffer` メッセージングブロックによって以前に提供されたメッセージを予約します。 ( [Source_block:: reserve_message](source-block-class.md#reserve_message)をオーバーライドします。)|
|[resume_propagation](#resume_propagation)|予約が解放された後、伝達を再開します。 ( [Source_block:: resume_propagation](source-block-class.md#resume_propagation)をオーバーライドします。)|
|[send_message](#send_message)|`ISource` ブロックからのメッセージを、この `unbounded_buffer` メッセージングブロックに同期的に渡します。 これは、ソースブロックによって呼び出されたときに、`send` メソッドによって呼び出されます。|
|[supports_anonymous_source](#supports_anonymous_source)|`supports_anonymous_source` メソッドをオーバーライドして、このブロックがリンクされていないソースによって提供されるメッセージを受け入れることができることを示します。 ( [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source)よりも優先されます)。|

詳細については、「[非同期メッセージブロック](../asynchronous-message-blocks.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`unbounded_buffer`

## <a name="requirements"></a>［要件］

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="accept_message"></a>accept_message

この `unbounded_buffer` メッセージングブロックによって提供されたメッセージを受け取り、所有権を呼び出し元に転送します。

```cpp
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
提供された `message` オブジェクトの `runtime_object_identity`。

### <a name="return-value"></a>戻り値

呼び出し元が所有権を持っている `message` オブジェクトへのポインター。

## <a name="consume_message"></a>consume_message

`unbounded_buffer` メッセージングブロックによって既に提供され、ターゲットによって予約されているメッセージを使用して、所有権を呼び出し元に譲渡します。

```cpp
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
使用されている `message` オブジェクトの `runtime_object_identity`。

### <a name="return-value"></a>戻り値

呼び出し元が所有権を持っている `message` オブジェクトへのポインター。

### <a name="remarks"></a>解説

`accept`と似ていますが、常に `reserve`の呼び出しが前に続きます。

## <a name="dequeue"></a>取り出さ

`unbounded_buffer` メッセージングブロックから項目を削除します。

```cpp
_Type dequeue();
```

### <a name="return-value"></a>戻り値

`unbounded_buffer`から削除されたメッセージのペイロード。

## <a name="enqueue"></a>入れ

`unbounded_buffer` メッセージングブロックに項目を追加します。

```cpp
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>パラメーター

*_Item*<br/>
追加する項目。

### <a name="return-value"></a>戻り値

項目が受け入れられた場合は**true** 。それ以外の場合は**false** 。

## <a name="link_target_notification"></a>link_target_notification

新しいターゲットがこの `unbounded_buffer` メッセージングブロックにリンクされていることを通知するコールバック。

```cpp
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
新しくリンクされたターゲットへのポインター。

## <a name="propagate_message"></a>propagate_message

`ISource` ブロックからこの `unbounded_buffer` メッセージングブロックに非同期的にメッセージを渡します。 これは、ソースブロックによって呼び出されたときに、`propagate` メソッドによって呼び出されます。

```cpp
virtual message_status propagate_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
`message` オブジェクトを指すポインター。

*_PSource*<br/>
メッセージを提供するソースブロックへのポインター。

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した[message_status](concurrency-namespace-enums.md#message_status)を示します。

## <a name="propagate_output_messages"></a>propagate_output_messages

`message` `_PMessage` をこの `unbounded_buffer` メッセージングブロックに配置し、リンクされたすべてのターゲットに提供しようとします。

```cpp
virtual void propagate_output_messages();
```

### <a name="remarks"></a>解説

`unbounded_buffer`で既に別のメッセージが受信されている場合は、以前のメッセージが受理または使用されるまで、リンクされたターゲットへの反映は行われません。 メッセージを正常に `accept` または `consume` するために最初にリンクされたターゲットは所有権を取得し、それ以外のターゲットはメッセージを取得できません。

## <a name="process_input_messages"></a>process_input_messages

`message` `_PMessage` をこの `unbounded_buffer` メッセージングブロックに配置し、リンクされたすべてのターゲットに提供しようとします。

```cpp
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
処理するメッセージへのポインター。

## <a name="release_message"></a>release_message

以前のメッセージ予約を解放します。

```cpp
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
解放される `message` オブジェクトの `runtime_object_identity`。

## <a name="reserve_message"></a>reserve_message

この `unbounded_buffer` メッセージングブロックによって以前に提供されたメッセージを予約します。

```cpp
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
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

`ISource` ブロックからのメッセージを、この `unbounded_buffer` メッセージングブロックに同期的に渡します。 これは、ソースブロックによって呼び出されたときに、`send` メソッドによって呼び出されます。

```cpp
virtual message_status send_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
`message` オブジェクトを指すポインター。

*_PSource*<br/>
メッセージを提供するソースブロックへのポインター。

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した[message_status](concurrency-namespace-enums.md#message_status)を示します。

## <a name="supports_anonymous_source"></a>supports_anonymous_source

`supports_anonymous_source` メソッドをオーバーライドして、このブロックがリンクされていないソースによって提供されるメッセージを受け入れることができることを示します。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>戻り値

ブロックは提供されたメッセージを延期しないため、 **true**になります。

## <a name="ctor"></a>unbounded_buffer

`unbounded_buffer` メッセージングブロックを構築します。

```cpp
unbounded_buffer();

unbounded_buffer(
   filter_method const&                 _Filter
);

unbounded_buffer(
   Scheduler&                 _PScheduler
);

unbounded_buffer(
   Scheduler&                 _PScheduler,
   filter_method const&                 _Filter
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup,
   filter_method const&                 _Filter
);
```

### <a name="parameters"></a>パラメーター

*_Filter*<br/>
提供されたメッセージを受け入れるかどうかを決定するフィルター関数。

*_PScheduler*<br/>
その内部で `Scheduler` メッセージング ブロックの反映タスクがスケジュールされる `unbounded_buffer` オブジェクト。

*_PScheduleGroup*<br/>
その内部で `ScheduleGroup` メッセージング ブロックの反映タスクがスケジュールされる `unbounded_buffer` オブジェクト。 使用される `Scheduler` オブジェクトは、スケジュール グループによって暗黙的に指定されます。

### <a name="remarks"></a>解説

`_PScheduler` または `_PScheduleGroup` パラメーターを指定しない場合、ランタイムは既定のスケジューラを使用しています。

`filter_method` 型は、提供されたメッセージを受け入れるかどうかを判断するために、この `unbounded_buffer` メッセージングブロックによって呼び出される、シグネチャ `bool (_Type const &)` のファンクタです。

## <a name="dtor"></a>~ unbounded_buffer

`unbounded_buffer` メッセージングブロックを破棄します。

```cpp
~unbounded_buffer();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[overwrite_buffer クラス](overwrite-buffer-class.md)<br/>
[single_assignment クラス](single-assignment-class.md)
