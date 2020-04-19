---
title: completion_future クラス
ms.date: 11/04/2016
f1_keywords:
- completion_future
- AMPRT/completion_future
- AMPRT/Concurrency::completion_future::completion_future
- AMPRT/Concurrency::completion_future::get
- AMPRT/Concurrency::completion_future::then
- AMPRT/Concurrency::completion_future::to_task
- AMPRT/Concurrency::completion_future::valid
- AMPRT/Concurrency::completion_future::wait
- AMPRT/Concurrency::completion_future::wait_for
- AMPRT/Concurrency::completion_future::wait_until
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
ms.openlocfilehash: 69aacad02df5290f161e9d8d311be347668be9f9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127021"
---
# <a name="completion_future-class"></a>completion_future クラス

C ++. AMP の非同期操作に対応するフューチャを表します。

## <a name="syntax"></a>構文

```cpp
class completion_future;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[completion_future コンストラクター](#ctor)|`completion_future` クラスの新しいインスタンスを初期化します。|
|[~ completion_future デストラクター](#dtor)|`completion_future` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[get](#get)|関連する非同期操作が完了するまで待機します。|
|[そうしたら](#then)|関連する非同期操作の実行が終了するときに、実行される `completion_future` オブジェクトにコールバック関数オブジェクトを継承します。|
|[to_task](#to_task)|関連する非同期操作に対応する `task` オブジェクトを返します。|
|[妥当](#valid)|オブジェクトが非同期操作に関連するかどうかを示すブール値を取得します。|
|[待機](#wait)|関連する非同期操作が完了するまでブロックします。|
|[wait_for](#wait_for)|関連する非同期操作が完了するまで、または `_Rel_time` で指定された時間が経過するまで、ブロックします。|
|[wait_until](#wait_until)|関連する非同期操作が完了するまで、または現在の時間が `_Abs_time` によって指定された値を超過するまで、ブロックします。|

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|[演算子 std:: shared_future\<void >](#operator_shared_future)|`completion_future` オブジェクトを `std::shared_future` オブジェクトに暗黙的に変換します。|
|[operator=](#operator_eq)|指定された `completion_future` オブジェクトの内容をこのオブジェクトにコピーします。|

## <a name="inheritance-hierarchy"></a>継承階層

`completion_future`

## <a name="requirements"></a>［要件］

**ヘッダー:** amprt. h

**名前空間:** concurrency

## <a name="ctor"></a>completion_future

`completion_future` クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
completion_future();

completion_future(
    const completion_future& _Other );

completion_future(
    completion_future&& _Other );
```

### <a name="parameters"></a>パラメーター

*_Other*<br/>
コピーまたは移動する `completion_future` オブジェクト。

### <a name="overloads-list"></a>オーバーロードの一覧

|Name|説明|
|----------|-----------------|
|`completion_future();`|`completion_future` クラスの新しいインスタンスを初期化します。|
|`completion_future(const completion_future& _Other);`|コンストラクターをコピーすることによって `completion_future` クラスの新しいインスタンスを初期化します。|
|`completion_future(completion_future&& _Other);`|コンストラクターを移動して、`completion_future` クラスの新しいインスタンスを初期化します。|

## <a name="get"></a>取得

関連する非同期操作が完了するまで待機します。 非同期操作中に検出された例外をスローします。

### <a name="syntax"></a>構文

```cpp
void get() const;
```

## <a name="operator_shared_future"></a>演算子 std:: shared_future\<void >

`completion_future` オブジェクトを `std::shared_future` オブジェクトに暗黙的に変換します。

### <a name="syntax"></a>構文

```cpp
operator std::shared_future<void>() const;
```

### <a name="return-value"></a>戻り値

`std::shared_future` オブジェクト。

## <a name="operator_eq"></a>operator =

指定された `completion_future` オブジェクトの内容をこのオブジェクトにコピーします。

### <a name="syntax"></a>構文

```cpp
completion_future&  operator= (const completion_future& _Other );
completion_future&  operator= (completion_future&& _Other );
```

### <a name="parameters"></a>パラメーター

*_Other*<br/>
コピー元のオブジェクト。

### <a name="return-value"></a>戻り値

この `completion_future` オブジェクトへの参照。

## <a name="overloads-list"></a>オーバーロードの一覧

|Name|説明|
|----------|-----------------|
|`completion_future& operator=(const completion_future& _Other);`|詳細コピーを使用して、指定された `completion_future` オブジェクトの内容をこのオブジェクトにコピーします。|
|`completion_future& operator=(completion_future&& _Other);`|移動代入を使用して、指定した `completion_future` オブジェクトの内容をこのオブジェクトにコピーします。|

## <a name="then"></a>そうしたら

関連する非同期操作の実行が終了するときに、実行される `completion_future` オブジェクトにコールバック関数オブジェクトを継承します。

### <a name="syntax"></a>構文

```cpp
template <typename _Functor>
void then(const _Functor & _Func ) const;
```

### <a name="parameters"></a>パラメーター

*_Functor*<br/>
コールバックファンクタ。

*_Func*<br/>
コールバック関数オブジェクト。

## <a name="to_task"></a>to_task

関連する非同期操作に対応する `task` オブジェクトを返します。

### <a name="syntax"></a>構文

```cpp
concurrency::task<void> to_task() const;
```

### <a name="return-value"></a>戻り値

関連付けられた非同期操作に対応する `task` オブジェクト。

## <a name="valid"></a>妥当

オブジェクトが非同期操作に関連付けられているかどうかを示すブール値を取得します。

### <a name="syntax"></a>構文

```cpp
bool valid() const;
```

### <a name="return-value"></a>戻り値

オブジェクトが非同期操作に関連付けられている場合は**true** 。それ以外の場合は**false**。

## <a name="wait"></a>待機

関連する非同期操作が完了するまでブロックします。

### <a name="syntax"></a>構文

```cpp
void wait() const;
```

## <a name="wait_for"></a>wait_for

関連する非同期操作が完了するまで、または `_Rel_time` で指定された時間が経過するまで、ブロックします。

### <a name="syntax"></a>構文

```cpp
template <
    class _Rep,
    class _Period
>
std::future_status::future_status wait_for(
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;
```

### <a name="parameters"></a>パラメーター

*_Rep*<br/>
タイマー刻みの数を表す演算型。

*_Period*<br/>
タイマー刻みごとに経過する秒数を表す std::ratio。

*_Rel_time*<br/>
操作が完了するまでの最大待機時間。

### <a name="return-value"></a>戻り値

戻り値:

- 関連する非同期操作が実行されていない場合、`std::future_status::deferred`。

- 関連する非同期操作が終了した場合、`std::future_status::ready`。

- 指定した期間が経過した場合、`std::future_status::timeout`。

## <a name="wait_until"></a>wait_until

関連する非同期操作が完了するまで、または現在の時間が `_Abs_time` によって指定された値を超過するまで、ブロックします。

### <a name="syntax"></a>構文

```cpp
template <
    class _Clock,
    class _Duration
>
std::future_status::future_status wait_until(
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;
```

### <a name="parameters"></a>パラメーター

*_Clock*<br/>
このタイム ポイントが測定されたクロック。

*_Duration*<br/>
`_Clock` のエポックの開始からの期間、その後で関数がタイムアウトします。

*_Abs_time*<br/>
その後で関数がタイムアウトする時点。

### <a name="return-value"></a>戻り値

戻り値:

1. 関連する非同期操作が実行されていない場合、`std::future_status::deferred`。

1. 関連する非同期操作が終了した場合、`std::future_status::ready`。

1. 指定された期間が経過した場合、`std::future_status::timeout`。

## <a name="dtor"></a>~ completion_future

`completion_future` オブジェクトを破棄します。

### <a name="syntax"></a>構文

```cpp
~completion_future();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
