---
title: multitype_join クラス
ms.date: 11/04/2016
f1_keywords:
- multitype_join
- AGENTS/concurrency::multitype_join
- AGENTS/concurrency::multitype_join::multitype_join
- AGENTS/concurrency::multitype_join::accept
- AGENTS/concurrency::multitype_join::acquire_ref
- AGENTS/concurrency::multitype_join::consume
- AGENTS/concurrency::multitype_join::link_target
- AGENTS/concurrency::multitype_join::release
- AGENTS/concurrency::multitype_join::release_ref
- AGENTS/concurrency::multitype_join::reserve
- AGENTS/concurrency::multitype_join::unlink_target
- AGENTS/concurrency::multitype_join::unlink_targets
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
ms.openlocfilehash: 4214c43fa0d0ab8fdd29ed54738c19f72a07267a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138951"
---
# <a name="multitype_join-class"></a>multitype_join クラス

`multitype_join` メッセージング ブロックは、複数のソースと単一のターゲットを持つメッセージング ブロックで、それぞれのソースから受け取った異なる種類のメッセージを 1 つに結合して、結合されたメッセージのタプルをターゲットに渡します。

## <a name="syntax"></a>構文

```cpp
template<
    typename T,
    join_type _Jtype = non_greedy
>
class multitype_join: public ISource<typename _Unwrap<T>::type>;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
ブロックによって結合および伝達されるメッセージの `tuple` ペイロードの種類。

*_Jtype*<br/>
`join` ブロックの種類は、`greedy` またはのいずれかになり `non_greedy`

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|Name|説明|
|----------|-----------------|
|`type`|`T`の型のエイリアス。|

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[multitype_join](#ctor)|オーバーロードされます。 `multitype_join` メッセージング ブロックを構築します。|
|[~ multitype_join デストラクター](#dtor)|`multitype_join` メッセージングブロックを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[受入](#accept)|この `multitype_join` ブロックによって提供されたメッセージを受け入れ、所有権を呼び出し元に転送します。|
|[acquire_ref](#acquire_ref)|この `multitype_join` メッセージングブロックの参照カウントを取得して、削除されないようにします。|
|[使用](#consume)|`multitype_join` メッセージングブロックによって既に提供され、ターゲットによって正常に予約されているメッセージを使用して、所有権を呼び出し元に譲渡します。|
|[link_target](#link_target)|ターゲットブロックをこの `multitype_join` メッセージングブロックにリンクします。|
|[release](#release)|前回成功したメッセージの予約を解放します。|
|[release_ref](#release_ref)|この `multiple_join` メッセージングブロックの参照カウントを解放します。|
|[reserve](#reserve)|この `multitype_join` メッセージングブロックによって以前に提供されたメッセージを予約します。|
|[unlink_target](#unlink_target)|この `multitype_join` メッセージングブロックからターゲットブロックをリンク解除します。|
|[unlink_targets](#unlink_targets)|この `multitype_join` メッセージングブロックからすべてのターゲットのリンクを解除します。 ( [ISource:: unlink_targets](isource-class.md#unlink_targets)よりも優先されます)。|

## <a name="remarks"></a>解説

詳細については、「[非同期メッセージブロック](../../../parallel/concrt/asynchronous-message-blocks.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[ISource](isource-class.md)

`multitype_join`

## <a name="requirements"></a>［要件］

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="accept"></a>受入

この `multitype_join` ブロックによって提供されたメッセージを受け入れ、所有権を呼び出し元に転送します。

```cpp
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
提供された `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`accept` メソッドを呼び出しているターゲットブロックへのポインター。

### <a name="return-value"></a>戻り値

現在呼び出し元に所有権があることを示すメッセージへのポインター。

## <a name="acquire_ref"></a>acquire_ref

この `multitype_join` メッセージングブロックの参照カウントを取得して、削除されないようにします。

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
このメソッドを呼び出しているターゲットブロックへのポインター。

### <a name="remarks"></a>解説

このメソッドは、`link_target` メソッド中にこのソースにリンクされている `ITarget` オブジェクトによって呼び出されます。

## <a name="consume"></a>可能性

`multitype_join` メッセージングブロックによって既に提供され、ターゲットによって正常に予約されているメッセージを使用して、所有権を呼び出し元に譲渡します。

```cpp
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
予約された `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`consume` メソッドを呼び出しているターゲットブロックへのポインター。

### <a name="return-value"></a>戻り値

呼び出し元が所有権を持っている `message` オブジェクトへのポインター。

### <a name="remarks"></a>解説

`consume` メソッドは `accept`に似ていますが、常に**true**を返す `reserve` を呼び出す必要があります。

## <a name="link_target"></a>link_target

ターゲットブロックをこの `multitype_join` メッセージングブロックにリンクします。

```cpp
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
この `multitype_join` メッセージングブロックにリンクする `ITarget` ブロックへのポインター。

## <a name="ctor"></a>multitype_join

`multitype_join` メッセージング ブロックを構築します。

```cpp
explicit multitype_join(
    T _Tuple);

multitype_join(
    Scheduler& _PScheduler,
    T _Tuple);

multitype_join(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

multitype_join(
    multitype_join&& _Join);
```

### <a name="parameters"></a>パラメーター

*_Tuple*<br/>
この `tuple` メッセージング ブロックのソースの `multitype_join` です。

*_PScheduler*<br/>
その内部で `Scheduler` メッセージング ブロックの反映タスクがスケジュールされる `multitype_join` オブジェクト。

*_PScheduleGroup*<br/>
その内部で `ScheduleGroup` メッセージング ブロックの反映タスクがスケジュールされる `multitype_join` オブジェクト。 使用される `Scheduler` オブジェクトは、スケジュール グループによって暗黙的に指定されます。

*_Join*<br/>
コピー元の `multitype_join` メッセージング ブロックです。 元のオブジェクトが孤立しており、これが移動コンストラクターになることに注意してください。

### <a name="remarks"></a>解説

`_PScheduler` または `_PScheduleGroup` パラメーターを指定しない場合、ランタイムは既定のスケジューラを使用しています。

移動の構築はロックの状況では行われません。ということは、移動時に処理中の軽量タスクがないことを確認するのはユーザーの責任です。 そうしないと、例外または不整合な状態で、多数の競合が発生します。

## <a name="dtor"></a>~ multitype_join

`multitype_join` メッセージングブロックを破棄します。

```cpp
~multitype_join();
```

## <a name="release"></a>解除

前回成功したメッセージの予約を解放します。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
解放される `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`release` メソッドを呼び出しているターゲットブロックへのポインター。

## <a name="release_ref"></a>release_ref

この `multiple_join` メッセージングブロックの参照カウントを解放します。

```cpp
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
このメソッドを呼び出しているターゲットブロックへのポインター。

### <a name="remarks"></a>解説

このメソッドは、このソースからリンク解除されている `ITarget` オブジェクトによって呼び出されます。 ソースブロックは、ターゲットブロック用に予約されているすべてのリソースを解放できます。

## <a name="reserve"></a>省

この `multitype_join` メッセージングブロックによって以前に提供されたメッセージを予約します。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
予約されている `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`reserve` メソッドを呼び出しているターゲットブロックへのポインター。

### <a name="return-value"></a>戻り値

メッセージが正常に予約された場合は `true`。それ以外の場合は `false`。 予約は、さまざまな理由で失敗する可能性があります。これには、メッセージが既に別のターゲットによって既に予約または受け入れられている場合、ソースが予約を拒否する場合などがあります。

### <a name="remarks"></a>解説

`reserve`を呼び出した後に成功した場合は、メッセージの所有を取得または取得するために、`consume` または `release` をそれぞれ呼び出す必要があります。

## <a name="unlink_target"></a>unlink_target

この `multitype_join` メッセージングブロックからターゲットブロックをリンク解除します。

```cpp
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
この `multitype_join` メッセージングブロックからリンクを解除する `ITarget` ブロックへのポインター。

## <a name="unlink_targets"></a>unlink_targets

この `multitype_join` メッセージングブロックからすべてのターゲットのリンクを解除します。

```cpp
virtual void unlink_targets();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[choice クラス](choice-class.md)<br/>
[join クラス](join-class.md)
