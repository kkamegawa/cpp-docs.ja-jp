---
title: ITarget クラス
ms.date: 11/04/2016
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
ms.openlocfilehash: dc9eacad744536e640417a4ebf51b975bd05bcc7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142028"
---
# <a name="itarget-class"></a>ITarget クラス

`ITarget` クラスは、すべてのターゲット ブロックのインターフェイスです。 ターゲット ブロックは、`ISource` ブロックから提供されたメッセージを処理します。

## <a name="syntax"></a>構文

```cpp
template<class T>
class ITarget;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
ターゲットブロックによって受け入れられるメッセージ内のペイロードのデータ型。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|Name|説明|
|----------|-----------------|
|`filter_method`|提供されたメッセージを受け入れる必要があるかどうかを判断するために `bool` 値を返す、ブロックによって使用されるメソッドのシグネチャ。|
|`type`|`T`の型のエイリアス。|

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[~ ITarget デストラクター](#dtor)|`ITarget` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[伝](#propagate)|派生クラスでオーバーライドされると、ソースブロックからこのターゲットブロックにメッセージを非同期的に渡します。|
|[send](#send)|派生クラスでオーバーライドされると、ターゲットブロックにメッセージを同期的に渡します。|
|[supports_anonymous_source](#supports_anonymous_source)|派生クラスでオーバーライドされると、リンクされていないソースによって提供されるメッセージをメッセージブロックが受け入れるかどうかに応じて、true または false を返します。 オーバーライドされたメソッドが**true**を返す場合、指定されたメッセージをターゲットが延期することはできません。延期されたメッセージを後で使用する場合は、ソースリンクレジストリでソースを識別する必要があります。|

### <a name="protected-methods"></a>プロテクト メソッド

|Name|説明|
|----------|-----------------|
|[link_source](#link_source)|派生クラスでオーバーライドされると、指定したソースブロックをこの `ITarget` ブロックにリンクします。|
|[unlink_source](#unlink_source)|派生クラスでオーバーライドされると、指定したソースブロックをこの `ITarget` ブロックからリンク解除します。|
|[unlink_sources](#unlink_sources)|派生クラスでオーバーライドされた場合、この `ITarget` ブロックのすべてのソースブロックのリンクを解除します。|

## <a name="remarks"></a>解説

詳細については、「[非同期メッセージブロック](../../../parallel/concrt/asynchronous-message-blocks.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`ITarget`

## <a name="requirements"></a>［要件］

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="dtor"></a>~ ITarget

`ITarget` オブジェクトを破棄します。

```cpp
virtual ~ITarget();
```

## <a name="link_source"></a>link_source

派生クラスでオーバーライドされると、指定したソースブロックをこの `ITarget` ブロックにリンクします。

```cpp
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>パラメーター

*_PSource*<br/>
この `ITarget` ブロックにリンクされている `ISource` ブロック。

### <a name="remarks"></a>解説

この関数は、`ITarget` ブロックで直接呼び出すことはできません。 ブロックは、`ISource` ブロックの `link_target` メソッドを使用して接続する必要があります。これにより、対応するターゲットの `link_source` メソッドが呼び出されます。

## <a name="propagate"></a>伝

派生クラスでオーバーライドされると、ソースブロックからこのターゲットブロックにメッセージを非同期的に渡します。

```cpp
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
`message` オブジェクトを指すポインター。

*_PSource*<br/>
メッセージを提供するソースブロックへのポインター。

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した[message_status](concurrency-namespace-enums.md)を示します。

### <a name="remarks"></a>解説

`_PMessage` または `_PSource` パラメーターが `NULL`の場合、メソッドは[invalid_argument](../../../standard-library/invalid-argument-class.md)例外をスローします。

## <a name="send"></a>送信

派生クラスでオーバーライドされると、ターゲットブロックにメッセージを同期的に渡します。

```cpp
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>パラメーター

*_PMessage*<br/>
`message` オブジェクトを指すポインター。

*_PSource*<br/>
メッセージを提供するソースブロックへのポインター。

### <a name="return-value"></a>戻り値

対象がメッセージに対して実行することを決定した[message_status](concurrency-namespace-enums.md)を示します。

### <a name="remarks"></a>解説

`_PMessage` または `_PSource` パラメーターが `NULL`の場合、メソッドは[invalid_argument](../../../standard-library/invalid-argument-class.md)例外をスローします。

メッセージの開始時以外に `send` メソッドを使用し、ネットワーク内でメッセージを伝達することは危険であり、デッドロックにつながる可能性があります。

`send` が返された場合、メッセージは既に受け入れられていて、ターゲットブロックに転送されているか、ターゲットによって拒否されています。

## <a name="supports_anonymous_source"></a>supports_anonymous_source

派生クラスでオーバーライドされると、リンクされていないソースによって提供されるメッセージをメッセージブロックが受け入れるかどうかに応じて、true または false を返します。 オーバーライドされたメソッドが**true**を返す場合、提供されたメッセージをターゲットが延期することはできません。延期されたメッセージを後で使用する場合は、ソースが sourse リンクレジストリで識別される必要があります。

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>戻り値

ブロックがリンクされていないソースからのメッセージを受け入れることができる場合は**true** 、それ以外の場合は**false** 。

## <a name="unlink_source"></a>unlink_source

派生クラスでオーバーライドされると、指定したソースブロックをこの `ITarget` ブロックからリンク解除します。

```cpp
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>パラメーター

*_PSource*<br/>
この `ITarget` ブロックからリンク解除されている `ISource` ブロック。

### <a name="remarks"></a>解説

この関数は、`ITarget` ブロックで直接呼び出すことはできません。 ブロックは、`unlink_target` または `ISource` ブロックの `unlink_targets` メソッドを使用して切断する必要があります。これにより、対応するターゲットで `unlink_source` メソッドが呼び出されます。

## <a name="unlink_sources"></a>unlink_sources

派生クラスでオーバーライドされた場合、この `ITarget` ブロックのすべてのソースブロックのリンクを解除します。

```cpp
virtual void unlink_sources() = 0;
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[ISource クラス](isource-class.md)
