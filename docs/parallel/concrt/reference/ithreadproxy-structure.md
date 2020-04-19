---
title: IThreadProxy 構造体
ms.date: 11/04/2016
f1_keywords:
- IThreadProxy
- CONCRTRM/concurrency::IThreadProxy
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::GetId
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchOut
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::SwitchTo
- CONCRTRM/concurrency::IThreadProxy::IThreadProxy::YieldToSystem
helpviewer_keywords:
- IThreadProxy structure
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
ms.openlocfilehash: b87694393af4634ec97d05070aa5513cd132098a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140081"
---
# <a name="ithreadproxy-structure"></a>IThreadProxy 構造体

実行スレッドの抽象化です。 作成するスケジューラの `SchedulerType` ポリシー キーに応じて、リソース マネージャーは、通常の Win32 スレッドまたはユーザー モード スケジュール可能 (UMS: User-Mode Schedulable) スレッドによってサポートされるスレッド プロキシを許可します。 UMS スレッドは、Windows 7 以上のバージョンの 64 ビット オペレーティング システムでサポートされます。

## <a name="syntax"></a>構文

```cpp
struct IThreadProxy;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[IThreadProxy:: GetId](#getid)|スレッドプロキシの一意の識別子を返します。|
|[IThreadProxy:: SwitchOut](#switchout)|基になる仮想プロセッサ ルートからコンテキストの関連付けを解除します。|
|[IThreadProxy:: SwitchTo](#switchto)|現在実行中のコンテキストから別のコンテキストへの協調的なコンテキスト切り替えを実行します。|
|[IThreadProxy:: YieldToSystem](#yieldtosystem)|呼び出し元のスレッドから、現在のプロセッサ上で実行する準備が整っている別のスレッドに実行を切り替えます。 オペレーティングシステムは、次に実行されるスレッドを選択します。|

## <a name="remarks"></a>コメント

スレッドプロキシは、処理をディスパッチする手段として、インターフェイス `IExecutionContext` によって表される実行コンテキストと結合されます。

## <a name="inheritance-hierarchy"></a>継承階層

`IThreadProxy`

## <a name="requirements"></a>要件

**ヘッダー:** concrtrm. h

**名前空間:** concurrency

## <a name="getid"></a>IThreadProxy:: GetId メソッド

スレッドプロキシの一意の識別子を返します。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>戻り値

一意の整数識別子。

## <a name="switchout"></a>IThreadProxy:: SwitchOut メソッド

基になる仮想プロセッサ ルートからコンテキストの関連付けを解除します。

```cpp
virtual void SwitchOut(SwitchingProxyState switchState = Blocking) = 0;
```

### <a name="parameters"></a>パラメーター

*switchState*<br/>
切り替えを実行しているスレッド プロキシの状態を示します。 `SwitchingProxyState` 型のパラメーター。

### <a name="remarks"></a>コメント

なんらかの理由で、実行している仮想プロセッサ ルートからコンテキストの関連付けを解除する必要がある場合には、`SwitchOut` を使用します。 パラメーター `switchState` に渡す値によって、または仮想プロセッサ ルート上で実行されるかどうかによって、呼び出しはすぐに制御を返すか、またはコンテキストに関連付けられたスレッド プロキシをブロックします。 パラメーターを `SwitchOut` に設定して `Idle` を呼び出すと、エラーになります。 これにより、 [invalid_argument](../../../standard-library/invalid-argument-class.md)例外が発生します。

`SwitchOut` は、リソース マネージャーから指示があった場合か、オーバーサブスクリプション状態の一時仮想プロセッサ ルートを要求した後、その処理が終了した場合に、スケジューラの仮想プロセッサ ルートの数を減らす必要があるときに便利です。 この場合、パラメーター `switchState` を `Blocking`に設定して `SwitchOut` を呼び出す前に、仮想プロセッサルートのメソッド[Ivirtualprocessorroot:: Remove](iexecutionresource-structure.md#remove)を呼び出す必要があります。 これによってスレッド プロキシはブロックされ、スケジューラの別の仮想プロセッサ ルートが処理を実行できるようになると、実行を再開します。 ブロック状態のスレッド プロキシを再開するには、`SwitchTo` 関数を呼び出してこのスレッド プロキシの実行コンテキストに切り替えます。 関連付けられているコンテキストを使用して仮想プロセッサ ルートをアクティブ化することにより、スレッド プロキシを再開することもできます。 これを行う方法の詳細については、「 [Ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)」を参照してください。

また、`SwitchOut` を使用して、仮想プロセッサを再初期化することもできます。これによって、スレッド プロキシをブロックするか、または一時的に実行している仮想プロセッサ ルートと処理をディスパッチしているスケジューラからデタッチしながら、後でアクティブ化可能なようにできます。 スレッド プロキシをブロックする場合には、パラメーター `SwitchOut` を `switchState` に設定して `Blocking` を使用します。 既に説明したように、`SwitchTo` か `IVirtualProcessorRoot::Activate` を使用して後で再開できます。 このスレッド プロキシが実行されている仮想プロセッサ ルートから、そのスレッド プロキシと、仮想プロセッサが関連付けられているスケジューラとを一時的にデタッチする必要がある場合は、パラメーターを `SwitchOut` に設定して `Nesting` を使用します。 仮想プロセッサ ルートで実行中に `SwitchOut` パラメーターを `switchState` に設定して `Nesting` を呼び出した場合、ルートは再初期化され、現在のスレッド プロキシはそれを必要とせずに実行を継続します。 スレッドプロキシは、後で `Blocking` を指定して[Ithreadproxy:: SwitchOut](#switchout)メソッドを呼び出すまで、スケジューラの外部にあると見なされます。 パラメーターを `SwitchOut` に設定して `Blocking` を再び呼び出すと、コンテキストをブロックされた状態に戻し、`SwitchTo` またはデタッチされたスケジューラの `IVirtualProcessorRoot::Activate` によって再開できるようにします。 これは仮想プロセッサ ルートで実行されていないため、再初期化は行われません。

再初期化された仮想プロセッサ ルートは、スケジューラがリソース マネージャーから許可された新しい仮想プロセッサ ルートと同様です。 `IVirtualProcessorRoot::Activate` を使った実行コンテキストによりアクティブ化することによって、それを実行に使用できます。

`SwitchOut` は、現在実行中のスレッドを表す `IThreadProxy` インターフェイスで呼び出す必要があります。それ以外の場合、結果は保証されません。

Visual Studio 2010 に付属のライブラリとヘッダーでは、このメソッドはパラメーターを受け取らず、仮想プロセッサ ルートを再初期化しませんでした。 従来の動作を保持するために、既定のパラメーター値 `Blocking` が用意されています。

## <a name="switchto"></a>IThreadProxy:: SwitchTo メソッド

現在実行中のコンテキストから別のコンテキストへの協調的なコンテキスト切り替えを実行します。

```cpp
virtual void SwitchTo(
    _Inout_ IExecutionContext* pContext,
    SwitchingProxyState switchState) = 0;
```

### <a name="parameters"></a>パラメーター

*pContext*<br/>
協調的に切り替える実行コンテキスト。

*switchState*<br/>
切り替えを実行しているスレッド プロキシの状態を示します。 `SwitchingProxyState` 型のパラメーター。

### <a name="remarks"></a>コメント

最初の実行コンテキストの[Iexecutioncontext::D ispatch](iexecutioncontext-structure.md#dispatch)メソッドから別の実行コンテキストに切り替えるには、このメソッドを使用します。 メソッドは、実行コンテキストがまだ関連付けられていない場合は、その `pContext` をスレッドプロキシに関連付けます。 現在のスレッドプロキシの所有権は、`switchState` 引数に指定した値によって決まります。

現在実行中のスレッドプロキシをリソースマネージャーに返す場合は、`Idle` 値を使用します。 パラメーター `switchState` を `Idle` に設定して `SwitchTo` を呼び出すと、基になる実行リソースに対して実行コンテキスト `pContext` の実行が開始されます。 このスレッドプロキシの所有権はリソースマネージャーに転送され、転送を完了するために `SwitchTo` が返された直後に実行コンテキストの `Dispatch` メソッドから戻ることが想定されています。 スレッドプロキシによってディスパッチされた実行コンテキストはスレッドプロキシとの関連付けが解除され、スケジューラは自由に再利用するか、またはそれに応じて破棄することができます。

このスレッドプロキシがブロックされた状態になるようにする場合は、`Blocking` 値を使用します。 パラメーター `switchState` を `Blocking` に設定して `SwitchTo` を呼び出すと、実行コンテキスト `pContext` の実行が開始され、現在のスレッドプロキシが再開されるまでブロックされます。 スレッドプロキシが `Blocking` 状態のとき、スケジューラはスレッドプロキシの所有権を保持します。 ブロック状態のスレッド プロキシを再開するには、`SwitchTo` 関数を呼び出してこのスレッド プロキシの実行コンテキストに切り替えます。 関連付けられているコンテキストを使用して仮想プロセッサ ルートをアクティブ化することにより、スレッド プロキシを再開することもできます。 これを行う方法の詳細については、「 [Ivirtualprocessorroot:: Activate](ivirtualprocessorroot-structure.md#activate)」を参照してください。

このスレッドプロキシが実行されている仮想プロセッサルートからこのスレッドプロキシを一時的に切断する場合は、値 `Nesting` を使用します。また、そのスレッドが処理の対象となるスケジューラを一時的に切断する場合は、を使用します。 パラメーター `switchState` を `Nesting` に設定して `SwitchTo` を呼び出すと、実行コンテキスト `pContext` の実行が開始され、現在のスレッドプロキシも仮想プロセッサルートを必要とせずに実行を継続します。 スレッドプロキシは、後で[Ithreadproxy:: SwitchOut](#switchout)メソッドを呼び出すまで、スケジューラの外部にあると見なされます。 `IThreadProxy::SwitchOut` メソッドは、仮想プロセッサルートを再スケジュールできるようになるまで、スレッドプロキシをブロックする可能性があります。

`SwitchTo` は、現在実行中のスレッドを表す `IThreadProxy` インターフェイスで呼び出す必要があります。それ以外の場合、結果は保証されません。 パラメーター `pContext` が `NULL`に設定されている場合、関数は `invalid_argument` をスローします。

## <a name="yieldtosystem"></a>IThreadProxy:: YieldToSystem メソッド

呼び出し元のスレッドから、現在のプロセッサ上で実行する準備が整っている別のスレッドに実行を切り替えます。 オペレーティングシステムは、次に実行されるスレッドを選択します。

```cpp
virtual void YieldToSystem() = 0;
```

### <a name="remarks"></a>コメント

通常の Windows スレッドによってサポートされるスレッドプロキシによって呼び出された場合、`YieldToSystem` は Windows の関数 `SwitchToThread`とまったく同じように動作します。 ただし、ユーザーモードスケジュール可能 (UMS) スレッドから呼び出された場合、`SwitchToThread` 関数は、次のスレッドを選択して、オペレーティングシステムではなくユーザーモードスケジューラに実行するタスクを委任します。 システムで別の準備ができているスレッドに切り替えるために必要な効果を実現するには、`YieldToSystem`を使用します。

`YieldToSystem` は、現在実行中のスレッドを表す `IThreadProxy` インターフェイスで呼び出す必要があります。それ以外の場合、結果は保証されません。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[IExecutionContext 構造体](iexecutioncontext-structure.md)<br/>
[IScheduler 構造体](ischeduler-structure.md)<br/>
[IVirtualProcessorRoot 構造体](ivirtualprocessorroot-structure.md)
