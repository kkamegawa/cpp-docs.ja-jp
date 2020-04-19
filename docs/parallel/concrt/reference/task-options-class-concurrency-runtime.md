---
title: task_options クラス (コンカレンシー ランタイム)
ms.date: 11/04/2016
f1_keywords:
- ppltasks/concurrency::task_options
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
ms.openlocfilehash: 5f60a07d709a79f3ce4845c8fbd1c40cb2ee7328
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142545"
---
# <a name="task_options-class-concurrency-runtime"></a>task_options クラス (コンカレンシー ランタイム)

タスクの作成に使用できるオプションを表します。

## <a name="syntax"></a>構文

```cpp
class task_options;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[task_options:: task_options コンストラクター (同時実行ランタイム)](#ctor)|オーバーロードされます。 タスクの作成オプションに関する既定の一覧|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[task_options:: get_cancellation_token メソッド (同時実行ランタイム)](#get_cancellation_token)|キャンセル トークンを返します|
|[task_options:: get_continuation_context メソッド (同時実行ランタイム)](#get_continuation_context)|継続コンテキストを返します|
|[task_options:: get_scheduler メソッド (同時実行ランタイム)](#get_scheduler)|スケジューラを返します|
|[task_options:: has_cancellation_token メソッド (同時実行ランタイム)](#has_cancellation_token)|キャンセル トークンがユーザーによって指定されているかどうかを示します|
|[task_options:: has_scheduler メソッド (同時実行ランタイム)](#has_scheduler)|スケジューラがユーザーによって指定されているかどうかを示します|
|[task_options:: set_cancellation_token メソッド (同時実行ランタイム)](#set_cancellation_token)|指定されたトークンをオプションに設定します|
|[task_options:: set_continuation_context メソッド (同時実行ランタイム)](#set_continuation_context)|指定された継続コンテキストをオプションに設定します|

## <a name="inheritance-hierarchy"></a>継承階層

`task_options`

## <a name="requirements"></a>［要件］

**ヘッダー:** ppltasks.h

**名前空間:** concurrency

## <a name="get_cancellation_token"></a>task_options:: get_cancellation_token メソッド (同時実行ランタイム)

キャンセル トークンを返します

```cpp
cancellation_token get_cancellation_token() const;
```

### <a name="return-value"></a>戻り値

## <a name="get_continuation_context"></a>task_options:: get_continuation_context メソッド (同時実行ランタイム)

継続コンテキストを返します

```cpp
task_continuation_context get_continuation_context() const;
```

### <a name="return-value"></a>戻り値

## <a name="get_scheduler"></a>task_options:: get_scheduler メソッド (同時実行ランタイム)

スケジューラを返します

```cpp
scheduler_ptr get_scheduler() const;
```

### <a name="return-value"></a>戻り値

## <a name="has_cancellation_token"></a>task_options:: has_cancellation_token メソッド (同時実行ランタイム)

キャンセル トークンがユーザーによって指定されているかどうかを示します

```cpp
bool has_cancellation_token() const;
```

### <a name="return-value"></a>戻り値

## <a name="has_scheduler"></a>task_options:: has_scheduler メソッド (同時実行ランタイム)

スケジューラがユーザーによって指定されているかどうかを示します

```cpp
bool has_scheduler() const;
```

### <a name="return-value"></a>戻り値

## <a name="set_cancellation_token"></a>task_options:: set_cancellation_token メソッド (同時実行ランタイム)

指定されたトークンをオプションに設定します

```cpp
void set_cancellation_token(cancellation_token _Token);
```

### <a name="parameters"></a>パラメーター

`_Token`

## <a name="set_continuation_context"></a>task_options:: set_continuation_context メソッド (同時実行ランタイム)

指定された継続コンテキストをオプションに設定します

```cpp
void set_continuation_context(task_continuation_context _ContinuationContext);
```

### <a name="parameters"></a>パラメーター

`_ContinuationContext`

## <a name="ctor"></a>task_options:: task_options コンストラクター (同時実行ランタイム)

タスクの作成オプションに関する既定の一覧

```cpp
task_options();

task_options(
    cancellation_token _Token);

task_options(
    task_continuation_context _ContinuationContext);

task_options(
    cancellation_token _Token,
    task_continuation_context _ContinuationContext);

template<typename _SchedType>
task_options(
    std::shared_ptr<_SchedType> _Scheduler);

task_options(
    scheduler_interface& _Scheduler);

task_options(
    scheduler_ptr _Scheduler);

task_options(
    const task_options& _TaskOptions);
```

### <a name="parameters"></a>パラメーター

`_SchedType`

`_Token`

`_ContinuationContext`

`_Scheduler`

`_TaskOptions`

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
