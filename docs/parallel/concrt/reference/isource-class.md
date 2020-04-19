---
title: ISource クラス
ms.date: 11/04/2016
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
ms.openlocfilehash: a9ef9990db6376536f2f2a15c053b3b1d4ed12cf
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139314"
---
# <a name="isource-class"></a>ISource クラス

`ISource` クラスは、すべてのソース ブロック用のインターフェイスです。 ソース ブロックは、メッセージを `ITarget` ブロックに伝達します。

## <a name="syntax"></a>構文

```cpp
template<class T>
class ISource;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
ソースブロックによって生成されるメッセージ内のペイロードのデータ型。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック Typedef

|Name|説明|
|----------|-----------------|
|`source_type`|`T`の型のエイリアス。|

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[~ ISource デストラクター](#dtor)|`ISource` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[受入](#accept)|派生クラスでオーバーライドされると、この `ISource` ブロックによって提供されたメッセージを受け取り、所有権を呼び出し元に転送します。|
|[acquire_ref](#acquire_ref)|派生クラスでオーバーライドされると、この `ISource` ブロックの参照カウントを取得して、削除されないようにします。|
|[使用](#consume)|派生クラスでオーバーライドされると、この `ISource` ブロックによって以前に提供され、ターゲットによって正常に予約されたメッセージを使用して、所有権を呼び出し元に譲渡します。|
|[link_target](#link_target)|派生クラスでオーバーライドされると、ターゲットブロックをこの `ISource` ブロックにリンクします。|
|[release](#release)|派生クラスでオーバーライドされると、前回成功したメッセージの予約を解放します。|
|[release_ref](#release_ref)|派生クラスでオーバーライドされると、この `ISource` ブロックの参照カウントを解放します。|
|[reserve](#reserve)|派生クラスでオーバーライドされると、この `ISource` ブロックによって以前に提供されたメッセージを予約します。|
|[unlink_target](#unlink_target)|派生クラスでオーバーライドされた場合、この `ISource` ブロックからターゲットブロックをリンク解除します。|
|[unlink_targets](#unlink_targets)|派生クラスでオーバーライドされると、この `ISource` ブロックからすべてのターゲットブロックのリンクを解除します。|

## <a name="remarks"></a>コメント

詳細については、「[非同期メッセージブロック](../../../parallel/concrt/asynchronous-message-blocks.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`ISource`

## <a name="requirements"></a>要件

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="accept"></a>受入

派生クラスでオーバーライドされると、この `ISource` ブロックによって提供されたメッセージを受け取り、所有権を呼び出し元に転送します。

```cpp
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
提供された `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`accept` メソッドを呼び出しているターゲットブロックへのポインター。

### <a name="return-value"></a>戻り値

現在呼び出し元に所有権があることを示すメッセージへのポインター。

### <a name="remarks"></a>コメント

`accept` メソッドは、この `ISource` ブロックによってメッセージが提供されている間、ターゲットによって呼び出されます。 返されるメッセージポインターは、このソースがメッセージのコピーを作成することにした場合、`ITarget` ブロックの `propagate` メソッドに渡されたものと異なる場合があります。

## <a name="acquire_ref"></a>acquire_ref

派生クラスでオーバーライドされると、この `ISource` ブロックの参照カウントを取得して、削除されないようにします。

```cpp
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
このメソッドを呼び出しているターゲットブロックへのポインター。

### <a name="remarks"></a>コメント

このメソッドは、`link_target` メソッド中にこのソースにリンクされている `ITarget` オブジェクトによって呼び出されます。

## <a name="consume"></a>可能性

派生クラスでオーバーライドされると、この `ISource` ブロックによって以前に提供され、ターゲットによって正常に予約されたメッセージを使用して、所有権を呼び出し元に譲渡します。

```cpp
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
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

## <a name="dtor"></a>~ ISource

`ISource` オブジェクトを破棄します。

```cpp
virtual ~ISource();
```

## <a name="link_target"></a>link_target

派生クラスでオーバーライドされると、ターゲットブロックをこの `ISource` ブロックにリンクします。

```cpp
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
この `ISource` ブロックにリンクされているターゲットブロックへのポインター。

## <a name="release"></a>解除

派生クラスでオーバーライドされると、前回成功したメッセージの予約を解放します。

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
予約された `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`release` メソッドを呼び出しているターゲットブロックへのポインター。

## <a name="release_ref"></a>release_ref

派生クラスでオーバーライドされると、この `ISource` ブロックの参照カウントを解放します。

```cpp
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
このメソッドを呼び出しているターゲットブロックへのポインター。

### <a name="remarks"></a>コメント

このメソッドは、このソースからリンク解除されている `ITarget` オブジェクトによって呼び出されます。 ソースブロックは、ターゲットブロック用に予約されているすべてのリソースを解放できます。

## <a name="reserve"></a>省

派生クラスでオーバーライドされると、この `ISource` ブロックによって以前に提供されたメッセージを予約します。

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>パラメーター

*_MsgId*<br/>
提供された `message` オブジェクトの `runtime_object_identity`。

*_PTarget*<br/>
`reserve` メソッドを呼び出しているターゲットブロックへのポインター。

### <a name="return-value"></a>戻り値

メッセージが正常に予約されている場合は**true** 、それ以外の場合は**false** 。 予約は、さまざまな理由で失敗する可能性があります。これには、メッセージが既に別のターゲットによって既に予約または受け入れられている場合、ソースが予約を拒否する場合などがあります。

### <a name="remarks"></a>コメント

`reserve`を呼び出した後に成功した場合は、メッセージの所有を取得または取得するために、`consume` または `release` をそれぞれ呼び出す必要があります。

## <a name="unlink_target"></a>unlink_target

派生クラスでオーバーライドされた場合、この `ISource` ブロックからターゲットブロックをリンク解除します。

```cpp
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>パラメーター

*_PTarget*<br/>
この `ISource` ブロックからリンク解除されているターゲットブロックへのポインター。

## <a name="unlink_targets"></a>unlink_targets

派生クラスでオーバーライドされると、この `ISource` ブロックからすべてのターゲットブロックのリンクを解除します。

```cpp
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[ITarget クラス](itarget-class.md)
