---
title: ordered_message_processor クラス
ms.date: 11/04/2016
f1_keywords:
- ordered_message_processor
- AGENTS/concurrency::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::async_send
- AGENTS/concurrency::ordered_message_processor::initialize
- AGENTS/concurrency::ordered_message_processor::initialize_batched_processing
- AGENTS/concurrency::ordered_message_processor::sync_send
- AGENTS/concurrency::ordered_message_processor::wait
- AGENTS/concurrency::ordered_message_processor::process_incoming_message
helpviewer_keywords:
- ordered_message_processor class
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
ms.openlocfilehash: ea9ca799f36cac0d843a578eb7cef9c1e9c5cda6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138782"
---
# <a name="ordered_message_processor-class"></a>ordered_message_processor クラス

`ordered_message_processor` は、メッセージ ブロックがメッセージを受け取った順序で処理できるようにする `message_processor` です。

## <a name="syntax"></a>構文

```cpp
template<class T>
class ordered_message_processor : public message_processor<T>;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
プロセッサによって処理されるメッセージのペイロードの種類。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック Typedef

|Name|説明|
|----------|-----------------|
|`type`|`T`の型のエイリアス。|

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[ordered_message_processor](#ctor)|`ordered_message_processor` オブジェクトを構築します。|
|[~ ordered_message_processor デストラクター](#dtor)|`ordered_message_processor` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[async_send](#async_send)|メッセージを非同期にキューに登録し、処理タスクを開始します (まだ完了していない場合)。 ( [Message_processor:: async_send](message-processor-class.md#async_send)をオーバーライドします。)|
|[化](#initialize)|適切なコールバック関数、スケジューラ、およびスケジュールグループを使用して、`ordered_message_processor` オブジェクトを初期化します。|
|[initialize_batched_processing](#initialize_batched_processing)|バッチ処理されたメッセージの処理の初期化|
|[sync_send](#sync_send)|メッセージを同期的にキューに登録し、処理タスクを開始します (まだ完了していない場合)。 ( [Message_processor:: sync_send](message-processor-class.md#sync_send)をオーバーライドします。)|
|[待機](#wait)|ブロックを破棄する前に、すべての非同期処理タスクが完了するまでの時間を確保するために、メッセージブロックのデストラクターで使用されるプロセッサ固有のスピン待機。 ( [Message_processor:: wait](message-processor-class.md#wait)をオーバーライドします)。|

### <a name="protected-methods"></a>プロテクト メソッド

|Name|説明|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|非同期的に呼び出される処理関数。 メッセージをデキューし、処理を開始します。 ( [Message_processor::p rocess_incoming_message](message-processor-class.md#process_incoming_message)をオーバーライドします。)|

## <a name="inheritance-hierarchy"></a>継承階層

[message_processor](message-processor-class.md)

`ordered_message_processor`

## <a name="requirements"></a>要件

**ヘッダー:** agents.h

**名前空間:** concurrency

## <a name="async_send"></a>async_send

メッセージを非同期にキューに登録し、処理タスクを開始します (まだ完了していない場合)。

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>パラメーター

*_Msg*<br/>
メッセージへのポインター。

## <a name="initialize"></a>化

適切なコールバック関数、スケジューラ、およびスケジュールグループを使用して、`ordered_message_processor` オブジェクトを初期化します。

```cpp
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```

### <a name="parameters"></a>パラメーター

*_PScheduler*<br/>
軽量タスクをスケジュールするために使用するスケジューラへのポインター。

*_PScheduleGroup*<br/>
ライトウェイトタスクをスケジュールするために使用されるスケジュールグループへのポインター。

*_Handler*<br/>
コールバック中に呼び出されたハンドラーファンクタ。

## <a name="initialize_batched_processing"></a>initialize_batched_processing

バッチ処理されたメッセージの処理の初期化

```cpp
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```

### <a name="parameters"></a>パラメーター

*_Processor*<br/>
コールバック中に呼び出されたプロセッサファンクタ。

*_Propagator*<br/>
コールバック中に呼び出された伝達子のファンクタ。

## <a name="ctor"></a>ordered_message_processor

`ordered_message_processor` オブジェクトを構築します。

```cpp
ordered_message_processor();
```

### <a name="remarks"></a>コメント

この `ordered_message_processor` は、`initialize` 関数が呼び出されるまで、非同期ハンドラーまたは同期ハンドラーのスケジュールを設定しません。

## <a name="dtor"></a>~ ordered_message_processor

`ordered_message_processor` オブジェクトを破棄します。

```cpp
virtual ~ordered_message_processor();
```

### <a name="remarks"></a>コメント

すべての未処理の非同期操作を待機してから、プロセッサを破棄します。

## <a name="process_incoming_message"></a>process_incoming_message

非同期的に呼び出される処理関数。 メッセージをデキューし、処理を開始します。

```cpp
virtual void process_incoming_message();
```

## <a name="sync_send"></a>sync_send

メッセージを同期的にキューに登録し、処理タスクを開始します (まだ完了していない場合)。

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>パラメーター

*_Msg*<br/>
メッセージへのポインター。

## <a name="wait"></a>待機

ブロックを破棄する前に、すべての非同期処理タスクが完了するまでの時間を確保するために、メッセージブロックのデストラクターで使用されるプロセッサ固有のスピン待機。

```cpp
virtual void wait();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
