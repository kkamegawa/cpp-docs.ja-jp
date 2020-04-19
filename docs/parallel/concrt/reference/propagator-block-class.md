---
title: propagator_block クラス
ms.date: 11/04/2016
f1_keywords:
- propagator_block
- AGENTS/concurrency::propagator_block
- AGENTS/concurrency::propagator_block::propagator_block
- AGENTS/concurrency::propagator_block::propagate
- AGENTS/concurrency::propagator_block::send
- AGENTS/concurrency::propagator_block::decline_incoming_messages
- AGENTS/concurrency::propagator_block::initialize_source_and_target
- AGENTS/concurrency::propagator_block::link_source
- AGENTS/concurrency::propagator_block::process_input_messages
- AGENTS/concurrency::propagator_block::propagate_message
- AGENTS/concurrency::propagator_block::register_filter
- AGENTS/concurrency::propagator_block::remove_network_links
- AGENTS/concurrency::propagator_block::send_message
- AGENTS/concurrency::propagator_block::unlink_source
- AGENTS/concurrency::propagator_block::unlink_sources
helpviewer_keywords:
- propagator_block class
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
ms.openlocfilehash: 340af181669cbbf4c5ba910aa3ee862bd40ba27f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138739"
---
# <a name="propagator_block-class"></a>propagator_block クラス

`propagator_block` クラスは、ソースでもありターゲットでもあるメッセージ ブロックの抽象基底クラスです。 `source_block` クラスと `target_block` クラスの両方の機能が組み合わされています。

## <a name="syntax"></a>構文

```cpp
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

### <a name="parameters"></a>パラメーター

*_TargetLinkRegistry*<br/>
ターゲットリンクを保持するために使用されるリンクレジストリ。

*_SourceLinkRegistry*<br/>
ソースリンクを保持するために使用されるリンクレジストリ。

*_MessageProcessorType*<br/>
メッセージ処理のプロセッサの種類。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック Typedef

|Name|説明|
|----------|-----------------|
|`source_iterator`|この `propagator_block`の `source_link_manager` の反復子の型。|

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[propagator_block](#ctor)|`propagator_block` オブジェクトを構築します。|
|[~ propagator_block デストラクター](#dtor)|`propagator_block` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[伝](#propagate)|ソースブロックからこのターゲットブロックにメッセージを非同期的に渡します。|
|[send](#send)|このブロックへのメッセージを同期的に開始します。 `ISource` ブロックによって呼び出されます。 この関数が完了すると、メッセージは既にブロックに反映されています。|

### <a name="protected-methods"></a>プロテクト メソッド

|Name|説明|
|----------|-----------------|
|[decline_incoming_messages](#decline_incoming_messages)|新しいメッセージを拒否するブロックを示します。|
|[initialize_source_and_target](#initialize_source_and_target)|基本オブジェクトを初期化します。 具体的には、`message_processor` オブジェクトを初期化する必要があります。|
|[link_source](#link_source)|指定されたソースブロックをこの `propagator_block` オブジェクトにリンクします。|
|[process_input_messages](#process_input_messages)|入力メッセージを処理します。 これは、source_block から派生した伝達子ブロックにのみ有効です ( [source_block::p rocess_input_messages](source-block-class.md#process_input_messages)をオーバーライドします)。|
|[propagate_message](#propagate_message)|派生クラスでオーバーライドされた場合、このメソッドは、`ISource` ブロックからこの `propagator_block` オブジェクトにメッセージを非同期的に渡します。 これは、ソースブロックによって呼び出されたときに、`propagate` メソッドによって呼び出されます。|
|[register_filter](#register_filter)|受信したすべてのメッセージに対して呼び出されるフィルターメソッドを登録します。|
|[remove_network_links](#remove_network_links)|この `propagator_block` オブジェクトから、ソースとターゲットのネットワークリンクをすべて削除します。|
|[send_message](#send_message)|派生クラスでオーバーライドされた場合、このメソッドは、`ISource` ブロックからこの `propagator_block` オブジェクトにメッセージを同期的に渡します。 これは、ソースブロックによって呼び出されたときに、`send` メソッドによって呼び出されます。|
|[unlink_source](#unlink_source)|指定したソースブロックをこの `propagator_block` オブジェクトからリンク解除します。|
|[unlink_sources](#unlink_sources)|この `propagator_block` オブジェクトからすべてのソースブロックのリンクを解除します。 ( [ITarget:: unlink_sources](itarget-class.md#unlink_sources)よりも優先されます)。|

## <a name="remarks"></a>コメント

複数の継承を回避するために、`propagator_block` クラスは `source_block` クラスと `ITarget` 抽象クラスから継承されます。 `target_block` クラスの機能のほとんどは、ここでレプリケートされます。

## <a name="inheritance-hierarchy"></a>継承階層

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

`propagator_block`

## <a name="requirements"></a>要件

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="decline_incoming_messages"></a>decline_incoming_messages

新しいメッセージを拒否するブロックを示します。

```cpp
void decline_incoming_messages();
```

### <a name="remarks"></a>コメント

このメソッドは、破棄の実行中に新しいメッセージが拒否されるようにするために、デストラクターによって呼び出されます。

## <a name="initialize_source_and_target"></a>initialize_source_and_target

基本オブジェクトを初期化します。 具体的には、`message_processor` オブジェクトを初期化する必要があります。

```cpp
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>パラメーター

*_PScheduler*<br/>
タスクをスケジュールするために使用するスケジューラ。

*_PScheduleGroup*<br/>
タスクをスケジュールするために使用されるスケジュールグループ。

## <a name="link_source"></a>link_source

指定されたソースブロックをこの `propagator_block` オブジェクトにリンクします。

```cpp
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>パラメーター

*_PSource*<br/>
リンクされる `ISource` ブロックへのポインター。

## <a name="process_input_messages"></a>process_input_messages

入力メッセージを処理します。 これは、から派生した伝達子ブロックにのみ有効です source_block

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
処理するメッセージへのポインター。

## <a name="propagate"></a>伝

ソースブロックからこのターゲットブロックにメッセージを非同期的に渡します。

```cpp
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
`message` オブジェクトを指すポインター。

*_PSource*<br/>
メッセージを提供するソースブロックへのポインター。

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した[message_status](concurrency-namespace-enums.md)を示します。

### <a name="remarks"></a>コメント

`propagate` メソッドは、リンクされたソースブロックによってターゲットブロックで呼び出されます。 メッセージがまだキューに登録されていない場合、または実行中でない場合は、非同期タスクをキューに配置してメッセージを処理します。

`_PMessage` または `_PSource` パラメーターが `NULL`の場合、メソッドは[invalid_argument](../../../standard-library/invalid-argument-class.md)例外をスローします。

## <a name="propagate_message"></a>propagate_message

派生クラスでオーバーライドされた場合、このメソッドは、`ISource` ブロックからこの `propagator_block` オブジェクトにメッセージを非同期的に渡します。 これは、ソースブロックによって呼び出されたときに、`propagate` メソッドによって呼び出されます。

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
`message` オブジェクトを指すポインター。

*_PSource*<br/>
メッセージを提供するソースブロックへのポインター。

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した[message_status](concurrency-namespace-enums.md)を示します。

## <a name="ctor"></a>propagator_block

`propagator_block` オブジェクトを構築します。

```cpp
propagator_block();
```

## <a name="dtor"></a>~ propagator_block

`propagator_block` オブジェクトを破棄します。

```cpp
virtual ~propagator_block();
```

## <a name="register_filter"></a>register_filter

受信したすべてのメッセージに対して呼び出されるフィルターメソッドを登録します。

```cpp
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>パラメーター

*_Filter*<br/>
フィルターメソッド。

## <a name="remove_network_links"></a>remove_network_links

この `propagator_block` オブジェクトから、ソースとターゲットのネットワークリンクをすべて削除します。

```cpp
void remove_network_links();
```

## <a name="send"></a>送信

このブロックへのメッセージを同期的に開始します。 `ISource` ブロックによって呼び出されます。 この関数が完了すると、メッセージは既にブロックに反映されています。

```cpp
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
`message` オブジェクトを指すポインター。

*_PSource*<br/>
メッセージを提供するソースブロックへのポインター。

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した[message_status](concurrency-namespace-enums.md)を示します。

### <a name="remarks"></a>コメント

このメソッドは、`_PMessage` または `_PSource` パラメーターが `NULL`場合に、 [invalid_argument](../../../standard-library/invalid-argument-class.md)例外をスローします。

## <a name="send_message"></a>send_message

派生クラスでオーバーライドされた場合、このメソッドは、`ISource` ブロックからこの `propagator_block` オブジェクトにメッセージを同期的に渡します。 これは、ソースブロックによって呼び出されたときに、`send` メソッドによって呼び出されます。

```cpp
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した[message_status](concurrency-namespace-enums.md)を示します。

### <a name="remarks"></a>コメント

既定では、派生クラスによってオーバーライドされない限り、このブロックは `declined` を返します。

## <a name="unlink_source"></a>unlink_source

指定したソースブロックをこの `propagator_block` オブジェクトからリンク解除します。

```cpp
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>パラメーター

*_PSource*<br/>
リンク解除する `ISource` ブロックへのポインター。

## <a name="unlink_sources"></a>unlink_sources

この `propagator_block` オブジェクトからすべてのソースブロックのリンクを解除します。

```cpp
virtual void unlink_sources();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[source_block クラス](source-block-class.md)<br/>
[ITarget クラス](itarget-class.md)
