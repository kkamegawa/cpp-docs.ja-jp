---
title: IExecutionContext 構造体
ms.date: 11/04/2016
f1_keywords:
- IExecutionContext
- CONCRTRM/concurrency::IExecutionContext
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::Dispatch
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetId
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetProxy
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::GetScheduler
- CONCRTRM/concurrency::IExecutionContext::IExecutionContext::SetProxy
helpviewer_keywords:
- IExecutionContext structure
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
ms.openlocfilehash: 45d65a5e16121d39233c3ceb801933aa1f5a5f8e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138909"
---
# <a name="iexecutioncontext-structure"></a>IExecutionContext 構造体

特定の仮想プロセッサで実行でき、協調的にコンテキストを切り替えることができる実行コンテキストへのインターフェイスです。

## <a name="syntax"></a>構文

```cpp
struct IExecutionContext;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[IExecutionContext::D ispatch](#dispatch)|スレッドプロキシが特定の実行コンテキストの実行を開始するときに呼び出されるメソッド。 これは、スケジューラのメインワーカールーチンです。|
|[IExecutionContext:: GetId](#getid)|実行コンテキストの一意の識別子を返します。|
|[IExecutionContext:: GetProxy](#getproxy)|このコンテキストを実行しているスレッドプロキシへのインターフェイスを返します。|
|[IExecutionContext:: GetScheduler](#getscheduler)|この実行コンテキストが属するスケジューラへのインターフェイスを返します。|
|[IExecutionContext:: SetProxy](#setproxy)|スレッドプロキシをこの実行コンテキストに関連付けます。 関連付けられたスレッドプロキシは、コンテキストの `Dispatch` メソッドの実行を開始する直前に、このメソッドを呼び出します。|

## <a name="remarks"></a>解説

同時実行ランタイムの Resource Manager とのインターフェイスを持つカスタムスケジューラを実装する場合は、`IExecutionContext` インターフェイスを実装する必要があります。 リソースマネージャーによって作成されたスレッドは、`IExecutionContext::Dispatch` メソッドを実行することによって、スケジューラに代わって作業を実行します。

## <a name="inheritance-hierarchy"></a>継承階層

`IExecutionContext`

## <a name="requirements"></a>［要件］

**ヘッダー:** concrtrm. h

**名前空間:** concurrency

## <a name="dispatch"></a>IExecutionContext::D ispatch メソッド

スレッドプロキシが特定の実行コンテキストの実行を開始するときに呼び出されるメソッド。 これは、スケジューラのメインワーカールーチンです。

```cpp
virtual void Dispatch(_Inout_ DispatchState* pDispatchState) = 0;
```

### <a name="parameters"></a>パラメーター

*pDispatchState*<br/>
この実行コンテキストがディスパッチされている状態へのポインター。 ディスパッチ状態の詳細については、「 [DispatchState](dispatchstate-structure.md)」を参照してください。

## <a name="getid"></a>IExecutionContext:: GetId メソッド

実行コンテキストの一意の識別子を返します。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>戻り値

一意の整数識別子。

### <a name="remarks"></a>解説

インターフェイスをリソースマネージャーによって提供されるメソッドのパラメーターとして使用する前に、`GetExecutionContextId` メソッドを使用して、`IExecutionContext` インターフェイスを実装するオブジェクトの一意の識別子を取得する必要があります。 `GetId` 関数が呼び出されたときに、同じ識別子を返すことが想定されています。

別のソースから取得した識別子は、未定義の動作を引き起こす可能性があります。

## <a name="getproxy"></a>IExecutionContext:: GetProxy メソッド

このコンテキストを実行しているスレッドプロキシへのインターフェイスを返します。

```cpp
virtual IThreadProxy* GetProxy() = 0;
```

### <a name="return-value"></a>戻り値

`IThreadProxy` インターフェイス。 実行コンテキストのスレッドプロキシが `SetProxy`の呼び出しで初期化されていない場合、関数は `NULL`を返す必要があります。

### <a name="remarks"></a>解説

リソースマネージャーは、コンテキストのに `Dispatch` メソッドを入力する前に、パラメーターとして `IThreadProxy` インターフェイスを使用して、実行コンテキストで `SetProxy` メソッドを呼び出します。 この引数を格納し、`GetProxy()`の呼び出しに返すことが想定されています。

## <a name="getscheduler"></a>IExecutionContext:: GetScheduler メソッド

この実行コンテキストが属するスケジューラへのインターフェイスを返します。

```cpp
virtual IScheduler* GetScheduler() = 0;
```

### <a name="return-value"></a>戻り値

`IScheduler` インターフェイス。

### <a name="remarks"></a>解説

リソースマネージャーによって提供されるメソッドのパラメーターとして使用する前に、有効な `IScheduler` インターフェイスを使用して実行コンテキストを初期化する必要があります。

## <a name="setproxy"></a>IExecutionContext:: SetProxy メソッド

スレッドプロキシをこの実行コンテキストに関連付けます。 関連付けられたスレッドプロキシは、コンテキストの `Dispatch` メソッドの実行を開始する直前に、このメソッドを呼び出します。

```cpp
virtual void SetProxy(_Inout_ IThreadProxy* pThreadProxy) = 0;
```

### <a name="parameters"></a>パラメーター

*pThreadProxy*<br/>
この実行コンテキストで `Dispatch` メソッドを入力しようとしているスレッドプロキシへのインターフェイス。

### <a name="remarks"></a>解説

パラメーター `pThreadProxy` を保存し、`GetProxy` メソッドの呼び出しで返すことが想定されています。 リソースマネージャーは、スレッドプロキシが `Dispatch` メソッドを実行している間に、実行コンテキストに関連付けられているスレッドプロキシが変更されないことを保証します。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[IScheduler 構造体](ischeduler-structure.md)<br/>
[IThreadProxy 構造体](ithreadproxy-structure.md)
