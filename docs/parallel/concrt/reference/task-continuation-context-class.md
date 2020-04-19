---
title: task_continuation_context クラス
ms.date: 11/04/2016
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
ms.openlocfilehash: ae8ac425f035839cdddc0b19f4f40d3b6369202a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142583"
---
# <a name="task_continuation_context-class"></a>task_continuation_context クラス

`task_continuation_context` クラスを使用すると、継続する場所を指定できます。 Windows ランタイムアプリからこのクラスを使用する場合にのみ役立ちます。 非 Windows ランタイムアプリの場合、タスクの継続の実行コンテキストはランタイムによって決定され、構成することはできません。

## <a name="syntax"></a>構文

```cpp
class task_continuation_context : public details::_ContextCallback;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[get_current_winrt_context](#get_current_winrt_context)|現在の winrt スレッドコンテキストを表すタスクの継続コンテキストオブジェクトを返します。|
|[use_arbitrary](#use_arbitrary)|タスクの継続コンテキストを作成します。このコンテキストを使用すると、ランタイムで継続用の実行コンテキストを選択できます。|
|[use_current](#use_current)|現在の実行コンテキストを表すタスクの継続コンテキスト オブジェクトを返します。|
|[use_default](#use_default)|タスクの既定の継続コンテキストを作成します。|
|[use_synchronous_execution](#use_synchronous_execution)|同期実行コンテキストを表すタスクの継続コンテキストオブジェクトを返します。|

## <a name="inheritance-hierarchy"></a>継承階層

`_ContextCallback`

`task_continuation_context`

## <a name="requirements"></a>［要件］

**ヘッダー:** ppltasks.h

**名前空間:** concurrency

## <a name="get_current_winrt_context"></a>get_current_winrt_context

現在の WinRT スレッドコンテキストを表すタスクの継続コンテキストオブジェクトを返します。

### <a name="syntax"></a>構文

```cpp
static task_continuation_context get_current_winrt_context();
```

### <a name="return-value"></a>戻り値

現在の Windows ランタイムスレッドコンテキスト。 Windows ランタイム以外のコンテキストから呼び出された場合は、空の task_continuation_context を返します。

### <a name="remarks"></a>解説

`get_current_winrt_context` メソッドは、呼び出し元の Windows ランタイムスレッドコンテキストをキャプチャします。 このメソッドは、Windows ランタイム以外の呼び出し元に空のコンテキストを返します。

`get_current_winrt_context` によって返される値を使用して、継続元タスクがアパートメントに対応しているかどうかに関係なく、キャプチャされたコンテキスト (STA vs MTA) のアパートメントモデルで継続を実行する必要があることをランタイムに示すことができます。 アパートメントに対応するタスクとは、Windows Runtime `IAsyncInfo` インターフェイスのラップを解除するタスク、またはそのようなタスクの子となるタスクです。

このメソッドは `use_current` メソッドに似ていますが、/Cx 拡張機能をC++サポートせC++ずにネイティブコードで使用することもできます。 これは、ネイティブと Windows ランタイムの両方のC++呼び出し元に対して、独立したライブラリコードを記述する高度なユーザーによる使用を目的としています。 この機能が必要な場合を除き、`use_current` 方法をお勧めします。 C++この方法は、/cx クライアントでのみ使用できます。

## <a name="use_arbitrary"></a>use_arbitrary

タスクの継続コンテキストを作成します。このコンテキストを使用すると、ランタイムで継続用の実行コンテキストを選択できます。

### <a name="syntax"></a>構文

```cpp
static task_continuation_context use_arbitrary();
```

### <a name="return-value"></a>戻り値

任意の位置を表すタスクの継続コンテキスト。

### <a name="remarks"></a>解説

この継続コンテキストを使用すると、タスクの継続は、ランタイムが選択したコンテキストで実行されます。これは、継続元タスクがアパートメントに対応している場合でも同様です。

`use_arbitrary` を使用すると、STA で作成されたアパートメント対応のタスクの継続に関する既定の動作を無効にすることができます。

このメソッドは、Windows ランタイムアプリでのみ使用できます。

## <a name="use_current"></a>use_current

現在の実行コンテキストを表すタスクの継続コンテキスト オブジェクトを返します。

```cpp
static task_continuation_context use_current();
```

### <a name="return-value"></a>戻り値

現在の実行コンテキスト。

### <a name="remarks"></a>解説

このメソッドは、正しいアパートメントで継続が実行できるように、呼び出し元の Windows ランタイムのコンテキストをキャプチャします。

`use_current` によって返される値を使用することで、ランタイムに対して、継続はキャプチャされたコンテキスト (STA と MTA) で実行されることを示すことができます。このような実行は、継続元タスクがアパートメントに対応しているかどうかに関係なく行われます。 アパートメントに対応するタスクとは、Windows Runtime `IAsyncInfo` インターフェイスのラップを解除するタスク、またはそのようなタスクの子となるタスクです。

このメソッドは、Windows ランタイムアプリでのみ使用できます。

## <a name="use_default"></a>use_default

タスクの既定の継続コンテキストを作成します。

```cpp
static task_continuation_context use_default();
```

### <a name="return-value"></a>戻り値

既定の継続コンテキスト。

### <a name="remarks"></a>解説

`then` メソッドを呼び出すときに継続コンテキストを指定しない場合は、既定のコンテキストが使用されます。 Windows 7 以前に対応した Windows アプリケーション、および Windows 8 以降に対応したデスクトップ アプリケーションでは、ランタイムによって、タスクの継続を実行する状況が判別されます。 ただし、Windows ランタイムアプリでは、アパートメント対応タスクの継続の既定の継続コンテキストは、`then` が呼び出されるアパートメントです。

アパートメントに対応するタスクとは、Windows Runtime `IAsyncInfo` インターフェイスのラップを解除するタスク、またはそのようなタスクの子となるタスクです。 したがって、Windows ランタイム STA でアパートメント対応のタスクについて継続をスケジュールする場合、継続はその STA で実行されます。

アパートメント以外に対応するタスクの継続は、ランタイムが選択したコンテキストで実行されます。

## <a name="use_synchronous_execution"></a>task_continuation_context:: use_synchronous_execution

同期実行コンテキストを表すタスクの継続コンテキストオブジェクトを返します。

### <a name="syntax"></a>構文

```cpp
static task_continuation_context use_synchronous_execution();
```

### <a name="return-value"></a>戻り値

同期実行コンテキスト。

### <a name="remarks"></a>解説

`use_synchronous_execution` メソッドは、継続タスクをコンテキスト上で同期的に実行するように強制します。これにより、継続元タスクの完了が発生します。

継続がアタッチされたときに継続元タスクが既に完了している場合、継続は、継続をアタッチするコンテキストで同期的に実行されます。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
