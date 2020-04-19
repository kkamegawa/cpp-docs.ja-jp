---
title: choice クラス
ms.date: 11/04/2016
f1_keywords:
- choice
- AGENTS/concurrency::choice
- AGENTS/concurrency::choice::choice
- AGENTS/concurrency::choice::accept
- AGENTS/concurrency::choice::acquire_ref
- AGENTS/concurrency::choice::consume
- AGENTS/concurrency::choice::has_value
- AGENTS/concurrency::choice::index
- AGENTS/concurrency::choice::link_target
- AGENTS/concurrency::choice::release
- AGENTS/concurrency::choice::release_ref
- AGENTS/concurrency::choice::reserve
- AGENTS/concurrency::choice::unlink_target
- AGENTS/concurrency::choice::unlink_targets
- AGENTS/concurrency::choice::value
helpviewer_keywords:
- choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
ms.openlocfilehash: 3e718d0d34580d3bf2f13937159e431134631218
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142215"
---
# <a name="choice-class"></a>choice クラス

`choice` メッセージング ブロックは、複数のソースと単一のターゲットを持つブロックであり、一連のソースとの制御フローの相互作用を表します。 choice ブロックは、複数のソースのいずれかがメッセージを生成するのを待ち、そのメッセージを生成したソースのインデックスを伝達します。

## <a name="syntax"></a>構文

```cpp
template<
    class T
>
class choice: public ISource<size_t>;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
入力ソースのペイロードを表す `tuple`ベースの型。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック Typedef

|Name|説明|
|----------|-----------------|
|`type`|`T`の型のエイリアス。|

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[どれ](#ctor)|オーバーロードされます。 `choice` メッセージング ブロックを構築します。|
|[~ choice デストラクター](#dtor)|`choice` メッセージングブロックを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[受入](#accept)|この `choice` ブロックによって提供されたメッセージを受け入れ、所有権を呼び出し元に転送します。|
|[acquire_ref](#acquire_ref)|この `choice` メッセージングブロックの参照カウントを取得して、削除されないようにします。|
|[使用](#consume)|は、この `choice` メッセージングブロックによって以前に提供され、ターゲットによって正常に予約されているメッセージを使用して、所有権を呼び出し元に譲渡します。|
|[has_value](#has_value)|この `choice` メッセージングブロックが値を使用して初期化されているかどうかを確認します。|
|[インデックス](#index)|`choice` メッセージングブロックによって選択された要素を表す `tuple` 内のインデックスを返します。|
|[link_target](#link_target)|ターゲットブロックをこの `choice` メッセージングブロックにリンクします。|
|[release](#release)|前回成功したメッセージの予約を解放します。|
|[release_ref](#release_ref)|この `choice` メッセージングブロックの参照カウントを解放します。|
|[reserve](#reserve)|この `choice` メッセージングブロックによって以前に提供されたメッセージを予約します。|
|[unlink_target](#unlink_target)|この `choice` メッセージングブロックからターゲットブロックをリンク解除します。|
|[unlink_targets](#unlink_targets)|この `choice` メッセージングブロックからすべてのターゲットのリンクを解除します。 ( [ISource:: unlink_targets](isource-class.md#unlink_targets)よりも優先されます)。|
|[value](#value)|`choice` メッセージングブロックによってインデックスが選択されたメッセージを取得します。|

## <a name="remarks"></a>コメント

Choice ブロックは、受信メッセージの1つのみが使用されることを保証します。

詳細については、「[非同期メッセージブロック](../../../parallel/concrt/asynchronous-message-blocks.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[ISource](isource-class.md)

`choice`

## <a name="requirements"></a>要件

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="accept"></a>受入

この `choice` ブロックによって提供されたメッセージを受け入れ、所有権を呼び出し元に転送します。

```cpp
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
提供された `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`accept` メソッドを呼び出しているターゲットブロックへのポインター。

### <a name="return-value"></a>戻り値

現在呼び出し元に所有権があることを示すメッセージへのポインター。

## <a name="acquire_ref"></a>acquire_ref

この `choice` メッセージングブロックの参照カウントを取得して、削除されないようにします。

```cpp
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
このメソッドを呼び出しているターゲットブロックへのポインター。

### <a name="remarks"></a>コメント

このメソッドは、`link_target` メソッド中にこのソースにリンクされている `ITarget` オブジェクトによって呼び出されます。

## <a name="ctor"></a>どれ

`choice` メッセージング ブロックを構築します。

```cpp
explicit choice(
    T _Tuple);

choice(
    Scheduler& _PScheduler,
    T _Tuple);

choice(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

choice(
    choice&& _Choice);
```

### <a name="parameters"></a>パラメーター

*_Tuple*<br/>
選択肢のソースの `tuple` です。

*_PScheduler*<br/>
その内部で `Scheduler` メッセージング ブロックの反映タスクがスケジュールされる `choice` オブジェクト。

*_PScheduleGroup*<br/>
その内部で `ScheduleGroup` メッセージング ブロックの反映タスクがスケジュールされる `choice` オブジェクト。 使用される `Scheduler` オブジェクトは、スケジュール グループによって暗黙的に指定されます。

*_Choice*<br/>
コピー元の `choice` メッセージング ブロックです。 元のオブジェクトが孤立しており、これが移動コンストラクターになることに注意してください。

### <a name="remarks"></a>コメント

`_PScheduler` または `_PScheduleGroup` パラメーターを指定しない場合、ランタイムは既定のスケジューラを使用しています。

移動の構築はロックの状況では行われません。ということは、移動時に処理中の軽量タスクがないことを確認するのはユーザーの責任です。 そうしないと、例外または不整合な状態で、多数の競合が発生します。

## <a name="dtor"></a>~ choice

`choice` メッセージングブロックを破棄します。

```cpp
~choice();
```

## <a name="consume"></a>可能性

は、この `choice` メッセージングブロックによって以前に提供され、ターゲットによって正常に予約されているメッセージを使用して、所有権を呼び出し元に譲渡します。

```cpp
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
予約された `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`consume` メソッドを呼び出しているターゲットブロックへのポインター。

### <a name="return-value"></a>戻り値

呼び出し元が所有権を持っている `message` オブジェクトへのポインター。

### <a name="remarks"></a>コメント

`consume` メソッドは `accept`に似ていますが、常に**true**を返す `reserve` を呼び出す必要があります。

## <a name="has_value"></a>has_value

この `choice` メッセージングブロックが値を使用して初期化されているかどうかを確認します。

```cpp
bool has_value() const;
```

### <a name="return-value"></a>戻り値

ブロックが値を受け取った場合は**true** 、それ以外の場合は**false** 。

## <a name="index"></a>化

`choice` メッセージングブロックによって選択された要素を表す `tuple` 内のインデックスを返します。

```cpp
size_t index();
```

### <a name="return-value"></a>戻り値

メッセージインデックス。

### <a name="remarks"></a>コメント

メッセージペイロードは、`get` メソッドを使用して抽出できます。

## <a name="link_target"></a>link_target

ターゲットブロックをこの `choice` メッセージングブロックにリンクします。

```cpp
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
この `choice` メッセージングブロックにリンクする `ITarget` ブロックへのポインター。

## <a name="release"></a>解除

前回成功したメッセージの予約を解放します。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
解放される `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`release` メソッドを呼び出しているターゲットブロックへのポインター。

## <a name="release_ref"></a>release_ref

この `choice` メッセージングブロックの参照カウントを解放します。

```cpp
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
このメソッドを呼び出しているターゲットブロックへのポインター。

### <a name="remarks"></a>コメント

このメソッドは、このソースからリンク解除されている `ITarget` オブジェクトによって呼び出されます。 ソースブロックは、ターゲットブロック用に予約されているすべてのリソースを解放できます。

## <a name="reserve"></a>省

この `choice` メッセージングブロックによって以前に提供されたメッセージを予約します。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
予約されている `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`reserve` メソッドを呼び出しているターゲットブロックへのポインター。

### <a name="return-value"></a>戻り値

メッセージが正常に予約されている場合は**true** 、それ以外の場合は**false** 。 予約は、さまざまな理由で失敗する可能性があります。これには、メッセージが既に別のターゲットによって既に予約または受け入れられている場合、ソースが予約を拒否する場合などがあります。

### <a name="remarks"></a>コメント

`reserve`を呼び出した後に成功した場合は、メッセージの所有を取得または取得するために、`consume` または `release` をそれぞれ呼び出す必要があります。

## <a name="unlink_target"></a>unlink_target

この `choice` メッセージングブロックからターゲットブロックをリンク解除します。

```cpp
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
この `choice` メッセージングブロックからリンクを解除する `ITarget` ブロックへのポインター。

## <a name="unlink_targets"></a>unlink_targets

この `choice` メッセージングブロックからすべてのターゲットのリンクを解除します。

```cpp
virtual void unlink_targets();
```

### <a name="remarks"></a>コメント

内部 `single_assignment` ブロックのデストラクターが適切にリンク解除されるため、このメソッドをデストラクターから呼び出す必要はありません。

## <a name="value"></a>数値

`choice` メッセージングブロックによってインデックスが選択されたメッセージを取得します。

```cpp
template <
    typename _Payload_type
>
_Payload_type const& value();
```

### <a name="parameters"></a>パラメーター

*_Payload_type*<br/>
メッセージペイロードの種類。

### <a name="return-value"></a>戻り値

メッセージのペイロード。

### <a name="remarks"></a>コメント

`choice` メッセージングブロックは、さまざまなペイロードの種類を持つ入力を受け取ることができるので、取得する時点でペイロードの種類を指定する必要があります。 `index` メソッドの結果に基づいて型を特定できます。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[join クラス](join-class.md)<br/>
[single_assignment クラス](single-assignment-class.md)
