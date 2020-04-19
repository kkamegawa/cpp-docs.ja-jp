---
title: event クラス
ms.date: 11/04/2016
f1_keywords:
- event
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
ms.openlocfilehash: 2c72b4b086e932f4fe404259c25f8d2c8be2be31
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138845"
---
# <a name="event-class"></a>event クラス

コンカレンシー ランタイムを明示的に認識する手動リセット イベントです。

## <a name="syntax"></a>構文

```cpp
class event;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[~ イベントデストラクター](#dtor)|イベントを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[reset](#reset)|イベントを非シグナル状態にリセットします。|
|[set](#set)|イベントを通知します。|
|[待機](#wait)|イベントがシグナル状態になるのを待機します。|
|[wait_for_multiple](#wait_for_multiple)|複数のイベントがシグナル状態になるのを待機します。|

### <a name="public-constants"></a>パブリック定数

|Name|説明|
|----------|-----------------|
|[timeout_infinite](#timeout_infinite)|待機がタイムアウトしないことを示す値。|

## <a name="remarks"></a>コメント

詳細については、「[同期データ構造](../../../parallel/concrt/synchronization-data-structures.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`event`

## <a name="requirements"></a>要件

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="ctor"></a>場合

新しいイベントを構築します。

```cpp
_CRTIMP event();
```

### <a name="remarks"></a>コメント

## <a name="dtor"></a>~ イベント

イベントを破棄します。

```cpp
~event();
```

### <a name="remarks"></a>コメント

デストラクターが実行されるとイベントで待機するスレッドがなくなると想定されます。 まだ待機しているスレッドと共にイベントが破棄されるようにすると、未定義の動作が発生します。

## <a name="reset"></a>解除

イベントを非シグナル状態にリセットします。

```cpp
void reset();
```

## <a name="set"></a>一連

イベントを通知します。

```cpp
void set();
```

### <a name="remarks"></a>コメント

イベントを通知すると、イベントを待機している任意の数のコンテキストが実行できるようになります。

## <a name="timeout_infinite"></a>timeout_infinite

待機がタイムアウトしないことを示す値。

```cpp
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```

## <a name="wait"></a>待機

イベントがシグナル状態になるのを待機します。

```cpp
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>パラメーター

*_Timeout*<br/>
待機がタイムアウトするまでのミリ秒数を示します。`COOPERATIVE_TIMEOUT_INFINITE` 値は、タイムアウトがないことを示します。

### <a name="return-value"></a>戻り値

待機条件が満たされた場合は、値 `0` を返します。それ以外の場合は、イベントがシグナル状態になることなく待機がタイムアウトしたことを示す `COOPERATIVE_WAIT_TIMEOUT` 値を返します。

> [!IMPORTANT]
> ユニバーサル Windows プラットフォーム (UWP) アプリでは、ASTA スレッドで `wait` を呼び出さないでください。この呼び出しは現在のスレッドをブロックし、アプリが応答しなくなる可能性があるためです。

## <a name="wait_for_multiple"></a>wait_for_multiple

複数のイベントがシグナル状態になるのを待機します。

```cpp
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>パラメーター

*_PPEvents*<br/>
待機するイベントの配列。 配列内のイベントの数は、`count` パラメーターによって指定されます。

*count*<br/>
配列内のイベントの数は、`_PPEvents` パラメーターで指定されます。

*_FWaitAll*<br/>
値が**true**に設定されている場合、パラメーターでは、`_PPEvents` パラメーターに指定された配列内のすべてのイベントが、待機を満たすためにシグナル状態になる必要があることを指定します。 値が**false**に設定されている場合は、`_PPEvents` パラメーターに指定された配列内のすべてのイベントがシグナル状態になることを指定します。

*_Timeout*<br/>
待機がタイムアウトするまでのミリ秒数を示します。`COOPERATIVE_TIMEOUT_INFINITE` 値は、タイムアウトがないことを示します。

### <a name="return-value"></a>戻り値

待機条件が満たされた場合は、`_PPEvents` パラメーターに指定された配列内の、待機条件を満たしたインデックス。それ以外の場合は、条件が満たされることなく待機がタイムアウトしたことを示す `COOPERATIVE_WAIT_TIMEOUT` 値。

### <a name="remarks"></a>コメント

`_FWaitAll` パラメーターの値を `true` に設定した場合は、すべてのイベントがシグナル状態になって初めて待機条件を満たしたことになります。その場合、この関数によって返されるインデックスには、`COOPERATIVE_WAIT_TIMEOUT` 値ではないという事実を除いて、特別な意味はありません。

> [!IMPORTANT]
> ユニバーサル Windows プラットフォーム (UWP) アプリでは、ASTA スレッドで `wait_for_multiple` を呼び出さないでください。この呼び出しは現在のスレッドをブロックし、アプリが応答しなくなる可能性があるためです。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
