---
title: single_assignment クラス
ms.date: 11/04/2016
f1_keywords:
- single_assignment
- AGENTS/concurrency::single_assignment
- AGENTS/concurrency::single_assignment::single_assignment
- AGENTS/concurrency::single_assignment::has_value
- AGENTS/concurrency::single_assignment::value
- AGENTS/concurrency::single_assignment::accept_message
- AGENTS/concurrency::single_assignment::consume_message
- AGENTS/concurrency::single_assignment::link_target_notification
- AGENTS/concurrency::single_assignment::propagate_message
- AGENTS/concurrency::single_assignment::propagate_to_any_targets
- AGENTS/concurrency::single_assignment::release_message
- AGENTS/concurrency::single_assignment::reserve_message
- AGENTS/concurrency::single_assignment::resume_propagation
- AGENTS/concurrency::single_assignment::send_message
helpviewer_keywords:
- single_assignment class
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
ms.openlocfilehash: 0d302f4f7f85737d9c3b2368e3ae04d88bc1a370
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142734"
---
# <a name="single_assignment-class"></a>single_assignment クラス

`single_assignment` メッセージング ブロックは、一度だけ書き込むことができる `propagator_block` を 1 つ格納できる、複数のターゲットと複数のソースを持つ順序付けられた `message` です。

## <a name="syntax"></a>構文

```cpp
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
バッファーによって格納および反映されたメッセージのペイロードの種類。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[single_assignment](#ctor)|オーバーロードされます。 `single_assignment` メッセージング ブロックを構築します。|
|[~ single_assignment デストラクター](#dtor)|`single_assignment` メッセージングブロックを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[has_value](#has_value)|この `single_assignment` メッセージングブロックが値を使用して初期化されているかどうかを確認します。|
|[value](#value)|`single_assignment` messaging ブロックに格納されているメッセージの現在のペイロードへの参照を取得します。|

### <a name="protected-methods"></a>プロテクト メソッド

|Name|説明|
|----------|-----------------|
|[accept_message](#accept_message)|この `single_assignment` メッセージングブロックによって提供されたメッセージを受け取り、メッセージのコピーを呼び出し元に返します。|
|[consume_message](#consume_message)|`single_assignment` によって既に提供され、ターゲットによって予約されているメッセージを使用して、メッセージのコピーを呼び出し元に返します。|
|[link_target_notification](#link_target_notification)|新しいターゲットがこの `single_assignment` メッセージングブロックにリンクされていることを通知するコールバック。|
|[propagate_message](#propagate_message)|`ISource` ブロックからこの `single_assignment` メッセージングブロックに非同期的にメッセージを渡します。 これは、ソースブロックによって呼び出されたときに、`propagate` メソッドによって呼び出されます。|
|[propagate_to_any_targets](#propagate_to_any_targets)|`message _PMessage` をこの `single_assignment` メッセージングブロックに配置し、リンクされたすべてのターゲットに提供します。|
|[release_message](#release_message)|以前のメッセージ予約を解放します。 ( [Source_block:: release_message](source-block-class.md#release_message)をオーバーライドします。)|
|[reserve_message](#reserve_message)|この `single_assignment` メッセージングブロックによって以前に提供されたメッセージを予約します。 ( [Source_block:: reserve_message](source-block-class.md#reserve_message)をオーバーライドします。)|
|[resume_propagation](#resume_propagation)|予約が解放された後、伝達を再開します。 ( [Source_block:: resume_propagation](source-block-class.md#resume_propagation)をオーバーライドします。)|
|[send_message](#send_message)|`ISource` ブロックからのメッセージを、この `single_assignment` メッセージングブロックに同期的に渡します。 これは、ソースブロックによって呼び出されたときに、`send` メソッドによって呼び出されます。|

## <a name="remarks"></a>コメント

`single_assignment` メッセージングブロックは、メッセージのコピーを各ターゲットに伝達します。

詳細については、「[非同期メッセージブロック](../../../parallel/concrt/asynchronous-message-blocks.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`single_assignment`

## <a name="requirements"></a>要件

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="accept_message"></a>accept_message

この `single_assignment` メッセージングブロックによって提供されたメッセージを受け取り、メッセージのコピーを呼び出し元に返します。

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
提供された `message` オブジェクトの `runtime_object_identity`。

### <a name="return-value"></a>戻り値

呼び出し元が所有権を持っている `message` オブジェクトへのポインター。

### <a name="remarks"></a>コメント

`single_assignment` メッセージングブロックは、現在保持されているメッセージの所有権を譲渡するのではなく、メッセージのコピーをターゲットに返します。

## <a name="consume_message"></a>consume_message

`single_assignment` によって既に提供され、ターゲットによって予約されているメッセージを使用して、メッセージのコピーを呼び出し元に返します。

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

## <a name="has_value"></a>has_value

この `single_assignment` メッセージングブロックが値を使用して初期化されているかどうかを確認します。

```cpp
bool has_value() const;
```

### <a name="return-value"></a>戻り値

ブロックが値を受け取った場合は**true** 、それ以外の場合は**false** 。

## <a name="link_target_notification"></a>link_target_notification

新しいターゲットがこの `single_assignment` メッセージングブロックにリンクされていることを通知するコールバック。

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
新しくリンクされたターゲットへのポインター。

## <a name="propagate_message"></a>propagate_message

`ISource` ブロックからこの `single_assignment` メッセージングブロックに非同期的にメッセージを渡します。 これは、ソースブロックによって呼び出されたときに、`propagate` メソッドによって呼び出されます。

```cpp
virtual message_status propagate_message(
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

`message` `_PMessage` をこの `single_assignment` メッセージングブロックに配置し、リンクされたすべてのターゲットに提供します。

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
この `single_assignment` メッセージングブロックが所有権を取得した `message` へのポインター。

## <a name="release_message"></a>release_message

以前のメッセージ予約を解放します。

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
解放される `message` オブジェクトの `runtime_object_identity`。

## <a name="reserve_message"></a>reserve_message

この `single_assignment` メッセージングブロックによって以前に提供されたメッセージを予約します。

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

## <a name="send_message"></a>send_message

`ISource` ブロックからのメッセージを、この `single_assignment` メッセージングブロックに同期的に渡します。 これは、ソースブロックによって呼び出されたときに、`send` メソッドによって呼び出されます。

```cpp
virtual message_status send_message(
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

## <a name="ctor"></a>single_assignment

`single_assignment` メッセージング ブロックを構築します。

```cpp
single_assignment();

single_assignment(
    filter_method const& _Filter);

single_assignment(
    Scheduler& _PScheduler);

single_assignment(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

single_assignment(
    ScheduleGroup& _PScheduleGroup);

single_assignment(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```

### <a name="parameters"></a>パラメーター

*_Filter*<br/>
提供されたメッセージを受け入れるかどうかを決定するフィルター関数。

*_PScheduler*<br/>
その内部で `Scheduler` メッセージング ブロックの反映タスクがスケジュールされる `single_assignment` オブジェクト。

*_PScheduleGroup*<br/>
その内部で `ScheduleGroup` メッセージング ブロックの反映タスクがスケジュールされる `single_assignment` オブジェクト。 使用される `Scheduler` オブジェクトは、スケジュール グループによって暗黙的に指定されます。

### <a name="remarks"></a>コメント

`_PScheduler` または `_PScheduleGroup` パラメーターを指定しない場合、ランタイムは既定のスケジューラを使用しています。

`filter_method` 型は、提供されたメッセージを受け入れるかどうかを判断するために、この `single_assignment` メッセージングブロックによって呼び出される、シグネチャ `bool (T const &)` のファンクタです。

## <a name="dtor"></a>~ single_assignment

`single_assignment` メッセージングブロックを破棄します。

```cpp
~single_assignment();
```

## <a name="value"></a>数値

`single_assignment` messaging ブロックに格納されているメッセージの現在のペイロードへの参照を取得します。

```cpp
T const& value();
```

### <a name="return-value"></a>戻り値

格納されているメッセージのペイロード。

### <a name="remarks"></a>コメント

このメソッドは、`single_assignment` メッセージングブロックに現在メッセージが格納されていない場合、メッセージが到着するまで待機します。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[overwrite_buffer クラス](overwrite-buffer-class.md)<br/>
[unbounded_buffer クラス](unbounded-buffer-class.md)
