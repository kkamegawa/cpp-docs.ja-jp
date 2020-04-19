---
title: source_block クラス
ms.date: 11/04/2016
f1_keywords:
- source_block
- AGENTS/concurrency::source_block
- AGENTS/concurrency::source_block::source_block
- AGENTS/concurrency::source_block::accept
- AGENTS/concurrency::source_block::acquire_ref
- AGENTS/concurrency::source_block::consume
- AGENTS/concurrency::source_block::link_target
- AGENTS/concurrency::source_block::release
- AGENTS/concurrency::source_block::release_ref
- AGENTS/concurrency::source_block::reserve
- AGENTS/concurrency::source_block::unlink_target
- AGENTS/concurrency::source_block::unlink_targets
- AGENTS/concurrency::source_block::accept_message
- AGENTS/concurrency::source_block::async_send
- AGENTS/concurrency::source_block::consume_message
- AGENTS/concurrency::source_block::enable_batched_processing
- AGENTS/concurrency::source_block::initialize_source
- AGENTS/concurrency::source_block::link_target_notification
- AGENTS/concurrency::source_block::process_input_messages
- AGENTS/concurrency::source_block::propagate_output_messages
- AGENTS/concurrency::source_block::propagate_to_any_targets
- AGENTS/concurrency::source_block::release_message
- AGENTS/concurrency::source_block::remove_targets
- AGENTS/concurrency::source_block::reserve_message
- AGENTS/concurrency::source_block::resume_propagation
- AGENTS/concurrency::source_block::sync_send
- AGENTS/concurrency::source_block::unlink_target_notification
- AGENTS/concurrency::source_block::wait_for_outstanding_async_sends
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
ms.openlocfilehash: 3a0d69bc2e2904b1dcf37a7e9891d95bd869a610
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142715"
---
# <a name="source_block-class"></a>source_block クラス

`source_block` クラスは、ソースのみのブロックの抽象基底クラスです。 このクラスには、基本的なリンク管理機能および一般的なエラー チェック機能が用意されています。

## <a name="syntax"></a>構文

```cpp
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```

### <a name="parameters"></a>パラメーター

*_TargetLinkRegistry*<br/>
ターゲットリンクを保持するために使用されるリンクレジストリ。

*_MessageProcessorType*<br/>
メッセージ処理のプロセッサの種類。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|Name|説明|
|----------|-----------------|
|`target_iterator`|接続されたターゲットをウォークする反復子。|

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[source_block](#ctor)|`source_block` オブジェクトを構築します。|
|[~ source_block デストラクター](#dtor)|`source_block` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[受入](#accept)|この `source_block` オブジェクトによって提供されたメッセージを受け取り、所有権を呼び出し元に転送します。|
|[acquire_ref](#acquire_ref)|この `source_block` オブジェクトの参照カウントを取得して、削除されないようにします。|
|[使用](#consume)|この `source_block` オブジェクトによって既に提供され、ターゲットによって正常に予約されているメッセージを使用して、所有権を呼び出し元に譲渡します。|
|[link_target](#link_target)|ターゲットブロックをこの `source_block` オブジェクトにリンクします。|
|[release](#release)|前回成功したメッセージの予約を解放します。|
|[release_ref](#release_ref)|この `source_block` オブジェクトの参照カウントを解放します。|
|[reserve](#reserve)|この `source_block` オブジェクトによって以前に提供されたメッセージを予約します。|
|[unlink_target](#unlink_target)|ターゲットブロックをこの `source_block` オブジェクトからリンク解除します。|
|[unlink_targets](#unlink_targets)|この `source_block` オブジェクトからすべてのターゲットブロックのリンクを解除します。 ( [ISource:: unlink_targets](isource-class.md#unlink_targets)よりも優先されます)。|

### <a name="protected-methods"></a>プロテクト メソッド

|Name|説明|
|----------|-----------------|
|[accept_message](#accept_message)|派生クラスでオーバーライドされると、ソースによって提供されるメッセージを受け入れます。 メッセージブロックは、`_MsgId` を検証してメッセージを返すように、このメソッドをオーバーライドする必要があります。|
|[async_send](#async_send)|メッセージを非同期にキューに入れ、伝達タスクを開始します (まだ完了していない場合)。|
|[consume_message](#consume_message)|派生クラスでオーバーライドされると、以前に予約されていたメッセージを使用します。|
|[enable_batched_processing](#enable_batched_processing)|このブロックのバッチ処理を有効にします。|
|[initialize_source](#initialize_source)|この `source_block`内の `message_propagator` を初期化します。|
|[link_target_notification](#link_target_notification)|新しいターゲットがこの `source_block` オブジェクトにリンクされていることを通知するコールバック。|
|[process_input_messages](#process_input_messages)|入力メッセージを処理します。 これは、から派生した伝達子ブロックにのみ有効です source_block|
|[propagate_output_messages](#propagate_output_messages)|メッセージをターゲットに伝達します。|
|[propagate_to_any_targets](#propagate_to_any_targets)|派生クラスでオーバーライドされると、指定したメッセージをリンクされたターゲットのいずれかまたはすべてに伝達します。 これは、メッセージブロックの主要な反映ルーチンです。|
|[release_message](#release_message)|派生クラスでオーバーライドされると、以前のメッセージ予約を解放します。|
|[remove_targets](#remove_targets)|このソースブロックのターゲットリンクをすべて削除します。 これは、デストラクターから呼び出す必要があります。|
|[reserve_message](#reserve_message)|派生クラスでオーバーライドされると、この `source_block` オブジェクトによって以前に提供されたメッセージを予約します。|
|[resume_propagation](#resume_propagation)|派生クラスでオーバーライドされると、予約が解放された後に伝達を再開します。|
|[sync_send](#sync_send)|既に実行されていない場合は、メッセージを同期的にキューに入れ、伝達タスクを開始します。|
|[unlink_target_notification](#unlink_target_notification)|ターゲットがこの `source_block` オブジェクトからリンク解除されたことを通知するコールバック。|
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|すべての非同期伝達が完了するまで待機します。 この伝達子に固有のスピン待機は、すべての非同期伝達がブロックを破棄する前に完了するまでの時間を確保するために、メッセージブロックのデストラクターで使用されます。|

## <a name="remarks"></a>解説

このクラスによって提供されるリンク管理と同期を利用するには、メッセージブロックをこのブロックから派生させる必要があります。

## <a name="inheritance-hierarchy"></a>継承階層

[ISource](isource-class.md)

`source_block`

## <a name="requirements"></a>［要件］

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="accept"></a>受入

この `source_block` オブジェクトによって提供されたメッセージを受け取り、所有権を呼び出し元に転送します。

```cpp
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
提供された `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`accept` メソッドを呼び出しているターゲットブロックへのポインター。

### <a name="return-value"></a>戻り値

呼び出し元が所有権を持っている `message` オブジェクトへのポインター。

### <a name="remarks"></a>解説

パラメーター `_PTarget` が `NULL`場合、メソッドは[invalid_argument](../../../standard-library/invalid-argument-class.md)例外をスローします。

`accept` メソッドは、この `ISource` ブロックによってメッセージが提供されている間、ターゲットによって呼び出されます。 返されるメッセージポインターは、このソースがメッセージのコピーを作成することにした場合、`ITarget` ブロックの `propagate` メソッドに渡されたものと異なる場合があります。

## <a name="accept_message"></a>accept_message

派生クラスでオーバーライドされると、ソースによって提供されるメッセージを受け入れます。 メッセージブロックは、`_MsgId` を検証してメッセージを返すように、このメソッドをオーバーライドする必要があります。

```cpp
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
`message` オブジェクトのランタイムオブジェクト id。

### <a name="return-value"></a>戻り値

現在呼び出し元に所有権があることを示すメッセージへのポインター。

### <a name="remarks"></a>解説

所有権を譲渡するには、元のメッセージポインターが返される必要があります。 所有権を維持するには、メッセージペイロードのコピーを作成して返す必要があります。

## <a name="acquire_ref"></a>acquire_ref

この `source_block` オブジェクトの参照カウントを取得して、削除されないようにします。

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```

### <a name="remarks"></a>解説

このメソッドは、`link_target` メソッド中にこのソースにリンクされている `ITarget` オブジェクトによって呼び出されます。

## <a name="async_send"></a>async_send

メッセージを非同期にキューに入れ、伝達タスクを開始します (まだ完了していない場合)。

```cpp
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>パラメーター

*_Msg*<br/>
非同期に送信する `message` オブジェクトへのポインター。

## <a name="consume"></a>可能性

この `source_block` オブジェクトによって既に提供され、ターゲットによって正常に予約されているメッセージを使用して、所有権を呼び出し元に譲渡します。

```cpp
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
予約された `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`consume` メソッドを呼び出しているターゲットブロックへのポインター。

### <a name="return-value"></a>戻り値

呼び出し元が所有権を持っている `message` オブジェクトへのポインター。

### <a name="remarks"></a>解説

パラメーター `_PTarget` が `NULL`場合、メソッドは[invalid_argument](../../../standard-library/invalid-argument-class.md)例外をスローします。

パラメーター `_PTarget` が `reserve`を呼び出したターゲットを表していない場合、メソッドは[bad_target](bad-target-class.md)例外をスローします。

`consume` メソッドは `accept`に似ていますが、常に**true**を返す `reserve` を呼び出す必要があります。

## <a name="consume_message"></a>consume_message

派生クラスでオーバーライドされると、以前に予約されていたメッセージを使用します。

```cpp
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
使用されている `message` オブジェクトの `runtime_object_identity`。

### <a name="return-value"></a>戻り値

現在呼び出し元に所有権があることを示すメッセージへのポインター。

### <a name="remarks"></a>解説

`accept`と似ていますが、常に `reserve`の呼び出しが前に続きます。

## <a name="enable_batched_processing"></a>enable_batched_processing

このブロックのバッチ処理を有効にします。

```cpp
void enable_batched_processing();
```

## <a name="initialize_source"></a>initialize_source

この `source_block`内の `message_propagator` を初期化します。

```cpp
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>パラメーター

*_PScheduler*<br/>
タスクをスケジュールするために使用するスケジューラ。

*_PScheduleGroup*<br/>
タスクをスケジュールするために使用されるスケジュールグループ。

## <a name="link_target"></a>link_target

ターゲットブロックをこの `source_block` オブジェクトにリンクします。

```cpp
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
この `source_block` オブジェクトにリンクする `ITarget` ブロックへのポインター。

### <a name="remarks"></a>解説

パラメーター `_PTarget` が `NULL`場合、メソッドは[invalid_argument](../../../standard-library/invalid-argument-class.md)例外をスローします。

## <a name="link_target_notification"></a>link_target_notification

新しいターゲットがこの `source_block` オブジェクトにリンクされていることを通知するコールバック。

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```

## <a name="process_input_messages"></a>process_input_messages

入力メッセージを処理します。 これは、から派生した伝達子ブロックにのみ有効です source_block

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
処理するメッセージへのポインター。

## <a name="propagate_output_messages"></a>propagate_output_messages

メッセージをターゲットに伝達します。

```cpp
virtual void propagate_output_messages();
```

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

派生クラスでオーバーライドされると、指定したメッセージをリンクされたターゲットのいずれかまたはすべてに伝達します。 これは、メッセージブロックの主要な反映ルーチンです。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
伝達されるメッセージへのポインター。

## <a name="release"></a>解除

前回成功したメッセージの予約を解放します。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
予約された `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`release` メソッドを呼び出しているターゲットブロックへのポインター。

### <a name="remarks"></a>解説

パラメーター `_PTarget` が `NULL`場合、メソッドは[invalid_argument](../../../standard-library/invalid-argument-class.md)例外をスローします。

パラメーター `_PTarget` が `reserve`を呼び出したターゲットを表していない場合、メソッドは[bad_target](bad-target-class.md)例外をスローします。

## <a name="release_message"></a>release_message

派生クラスでオーバーライドされると、以前のメッセージ予約を解放します。

```cpp
virtual void release_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
解放される `message` オブジェクトの `runtime_object_identity`。

## <a name="release_ref"></a>release_ref

この `source_block` オブジェクトの参照カウントを解放します。

```cpp
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
このメソッドを呼び出しているターゲットブロックへのポインター。

### <a name="remarks"></a>解説

このメソッドは、このソースからリンク解除されている `ITarget` オブジェクトによって呼び出されます。 ソースブロックは、ターゲットブロック用に予約されているすべてのリソースを解放できます。

## <a name="remove_targets"></a>remove_targets

このソースブロックのターゲットリンクをすべて削除します。 これは、デストラクターから呼び出す必要があります。

```cpp
void remove_targets();
```

## <a name="reserve"></a>省

この `source_block` オブジェクトによって以前に提供されたメッセージを予約します。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
提供された `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`reserve` メソッドを呼び出しているターゲットブロックへのポインター。

### <a name="return-value"></a>戻り値

メッセージが正常に予約されている場合は**true** 、それ以外の場合は**false** 。 予約は、さまざまな理由で失敗する可能性があります。これには、メッセージが既に別のターゲットによって既に予約または受け入れられている場合、ソースが予約を拒否する場合などがあります。

### <a name="remarks"></a>解説

パラメーター `_PTarget` が `NULL`場合、メソッドは[invalid_argument](../../../standard-library/invalid-argument-class.md)例外をスローします。

`reserve`を呼び出した後に成功した場合は、メッセージの所有を取得または取得するために、`consume` または `release` をそれぞれ呼び出す必要があります。

## <a name="reserve_message"></a>reserve_message

派生クラスでオーバーライドされると、この `source_block` オブジェクトによって以前に提供されたメッセージを予約します。

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
予約されている `message` オブジェクトの `runtime_object_identity`。

### <a name="return-value"></a>戻り値

メッセージが正常に予約されている場合は**true** 、それ以外の場合は**false** 。

### <a name="remarks"></a>解説

`reserve` が呼び出された後、 **true**が返された場合は、メッセージの所有権を取得または解放するために、`consume` または `release` のいずれかを呼び出す必要があります。

## <a name="resume_propagation"></a>resume_propagation

派生クラスでオーバーライドされると、予約が解放された後に伝達を再開します。

```cpp
virtual void resume_propagation() = 0;
```

## <a name="ctor"></a>source_block

`source_block` オブジェクトを構築します。

```cpp
source_block();
```

## <a name="dtor"></a>~ source_block

`source_block` オブジェクトを破棄します。

```cpp
virtual ~source_block();
```

## <a name="sync_send"></a>sync_send

既に実行されていない場合は、メッセージを同期的にキューに入れ、伝達タスクを開始します。

```cpp
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>パラメーター

*_Msg*<br/>
同期的に送信する `message` オブジェクトへのポインター。

## <a name="unlink_target"></a>unlink_target

ターゲットブロックをこの `source_block` オブジェクトからリンク解除します。

```cpp
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
この `source_block` オブジェクトからリンクを解除する `ITarget` ブロックへのポインター。

### <a name="remarks"></a>解説

パラメーター `_PTarget` が `NULL`場合、メソッドは[invalid_argument](../../../standard-library/invalid-argument-class.md)例外をスローします。

## <a name="unlink_target_notification"></a>unlink_target_notification

ターゲットがこの `source_block` オブジェクトからリンク解除されたことを通知するコールバック。

```cpp
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
リンク解除された `ITarget` ブロック。

## <a name="unlink_targets"></a>unlink_targets

この `source_block` オブジェクトからすべてのターゲットブロックのリンクを解除します。

```cpp
virtual void unlink_targets();
```

## <a name="wait_for_outstanding_async_sends"></a>wait_for_outstanding_async_sends

すべての非同期伝達が完了するまで待機します。 この伝達子に固有のスピン待機は、すべての非同期伝達がブロックを破棄する前に完了するまでの時間を確保するために、メッセージブロックのデストラクターで使用されます。

```cpp
void wait_for_outstanding_async_sends();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[ISource クラス](isource-class.md)
