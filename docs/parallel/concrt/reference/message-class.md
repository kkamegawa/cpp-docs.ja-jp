---
title: message クラス
ms.date: 11/04/2016
f1_keywords:
- message
- AGENTS/concurrency::message
- AGENTS/concurrency::message::message
- AGENTS/concurrency::message::add_ref
- AGENTS/concurrency::message::msg_id
- AGENTS/concurrency::message::remove_ref
- AGENTS/concurrency::message::payload
helpviewer_keywords:
- message class
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
ms.openlocfilehash: 700d052b6f22c970387a3ab45d299538a5b74e1b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139541"
---
# <a name="message-class"></a>message クラス

メッセージング ブロック間で渡されるデータ ペイロードが格納される、基本的なメッセージ エンベロープ。

## <a name="syntax"></a>構文

```cpp
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
メッセージ内のペイロードのデータ型。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|Name|説明|
|----------|-----------------|
|`type`|`T`の型のエイリアス。|

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[message](#ctor)|オーバーロードされます。 `message` オブジェクトを構築します。|
|[~ メッセージデストラクター](#dtor)|`message` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[add_ref](#add_ref)|`message` オブジェクトの参照カウントにを追加します。 メッセージの有効期間を決定するために参照カウントを必要とするメッセージブロックに使用されます。|
|[msg_id](#msg_id)|`message` オブジェクトの ID を返します。|
|[remove_ref](#remove_ref)|`message` オブジェクトの参照カウントから減算します。 メッセージの有効期間を決定するために参照カウントを必要とするメッセージブロックに使用されます。|

### <a name="public-data-members"></a>パブリック データ メンバー

|Name|説明|
|----------|-----------------|
|[payload](#payload)|`message` オブジェクトのペイロード。|

## <a name="remarks"></a>解説

詳細については、「[非同期メッセージブロック](../../../parallel/concrt/asynchronous-message-blocks.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`message`

## <a name="requirements"></a>［要件］

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="add_ref"></a>add_ref

`message` オブジェクトの参照カウントにを追加します。 メッセージの有効期間を決定するために参照カウントを必要とするメッセージブロックに使用されます。

```cpp
long add_ref();
```

### <a name="return-value"></a>戻り値

参照カウントの新しい値。

## <a name="ctor"></a>メッセージ

`message` オブジェクトを構築します。

```cpp
message(
    T const& _P);

message(
    T const& _P,
    runtime_object_identity _Id);

message(
    message const& _Msg);

message(
    _In_ message const* _Msg);
```

### <a name="parameters"></a>パラメーター

*_P*<br/>
このメッセージのペイロード。

*_Id*<br/>
このメッセージの一意の ID。

*_Msg*<br/>
`message` オブジェクトへの参照またはポインター。

### <a name="remarks"></a>解説

引数として `message` オブジェクトへのポインターを受け取るコンストラクターは、パラメーター `_Msg` が `NULL`場合に[invalid_argument](../../../standard-library/invalid-argument-class.md)例外をスローします。

## <a name="dtor"></a>~ メッセージ

`message` オブジェクトを破棄します。

```cpp
virtual ~message();
```

## <a name="msg_id"></a>msg_id

`message` オブジェクトの ID を返します。

```cpp
runtime_object_identity msg_id() const;
```

### <a name="return-value"></a>戻り値

`runtime_object_identity` オブジェクトの `message` です。

## <a name="payload"></a>ペイ

`message` オブジェクトのペイロード。

```cpp
T const payload;
```

## <a name="remove_ref"></a>remove_ref

`message` オブジェクトの参照カウントから減算します。 メッセージの有効期間を決定するために参照カウントを必要とするメッセージブロックに使用されます。

```cpp
long remove_ref();
```

### <a name="return-value"></a>戻り値

参照カウントの新しい値。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
