---
title: IScheduler 構造体
ms.date: 11/04/2016
f1_keywords:
- IScheduler
- CONCRTRM/concurrency::IScheduler
- CONCRTRM/concurrency::IScheduler::IScheduler::AddVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::GetId
- CONCRTRM/concurrency::IScheduler::IScheduler::GetPolicy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyBusy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyIdle
- CONCRTRM/concurrency::IScheduler::IScheduler::RemoveVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::Statistics
helpviewer_keywords:
- IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
ms.openlocfilehash: cd7b04b0dc5ca1bc496ce87a6459d00ed5813bf7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854177"
---
# <a name="ischeduler-structure"></a>IScheduler 構造体

作業スケジューラの抽象化のインターフェイスです。 同時実行ランタイムのリソース マネージャーは、このインターフェイスを使用して作業スケジューラと通信します。

## <a name="syntax"></a>構文

```cpp
struct IScheduler;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|Description|
|----------|-----------------|
|[IScheduler:: AddVirtualProcessors](#addvirtualprocessors)|スケジューラに、使用するための一連の仮想プロセッサルートを提供します。 各 `IVirtualProcessorRoot` インターフェイスは、スケジューラに代わって処理を実行できる1つのスレッドを実行する権限を表します。|
|[IScheduler:: GetId](#getid)|スケジューラの一意の識別子を返します。|
|[IScheduler:: GetPolicy](#getpolicy)|スケジューラのポリシーのコピーを返します。 Scheduler ポリシーの詳細については、「スケジューラ[ポリシー](schedulerpolicy-class.md)」を参照してください。|
|[IScheduler:: NotifyResourcesExternallyBusy](#notifyresourcesexternallybusy)|配列 `ppVirtualProcessorRoots` の仮想プロセッサルートのセットによって表されるハードウェアスレッドが、現在、他のスケジューラによって使用されていることを、このスケジューラに通知します。|
|[IScheduler:: NotifyResourcesExternallyIdle](#notifyresourcesexternallyidle)|配列 `ppVirtualProcessorRoots` の仮想プロセッサルートのセットによって表されるハードウェアスレッドが、他のスケジューラによって使用されていないことを、このスケジューラに通知します。|
|[IScheduler:: RemoveVirtualProcessors](#removevirtualprocessors)|以前にこのスケジューラに割り当てられた仮想プロセッサルートの削除を開始します。|
|[IScheduler:: Statistics](#statistics)|タスクの到着と完了率に関する情報を提供し、スケジューラのキューの長さを変更します。|

## <a name="remarks"></a>解説

リソースマネージャーと通信するカスタムスケジューラを実装する場合は、`IScheduler` インターフェイスの実装を提供する必要があります。 このインターフェイスは、スケジューラとリソースマネージャーの間の通信の双方向チャネルの1つの端です。 もう一方の端は、リソースマネージャーによって実装される `IResourceManager` および `ISchedulerProxy` インターフェイスによって表されます。

## <a name="inheritance-hierarchy"></a>継承階層

`IScheduler`

## <a name="requirements"></a>必要条件

**ヘッダー:** concrtrm. h

**名前空間:** concurrency

## <a name="addvirtualprocessors"></a>IScheduler:: AddVirtualProcessors メソッド

スケジューラに、使用するための一連の仮想プロセッサルートを提供します。 各 `IVirtualProcessorRoot` インターフェイスは、スケジューラに代わって処理を実行できる1つのスレッドを実行する権限を表します。

```cpp
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>パラメーター

*ppVirtualProcessorRoots*<br/>
スケジューラに追加されている仮想プロセッサルートを表す `IVirtualProcessorRoot` インターフェイスの配列。

*count*<br/>
配列内の `IVirtualProcessorRoot` インターフェイスの数。

### <a name="remarks"></a>解説

リソースマネージャーは、`AddVirtualProcessor` メソッドを呼び出して、最初の仮想プロセッサルートのセットをスケジューラに付与します。 また、スケジューラ間でリソースをバランスするときに、メソッドを呼び出して、仮想プロセッサルートをスケジューラに追加することもできます。

## <a name="getid"></a>IScheduler:: GetId メソッド

スケジューラの一意の識別子を返します。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>戻り値

一意の整数識別子。

### <a name="remarks"></a>解説

インターフェイスをリソースマネージャーによって提供されるメソッドのパラメーターとして使用する前に、 [GetSchedulerId](concurrency-namespace-functions.md)関数を使用して、`IScheduler` インターフェイスを実装するオブジェクトの一意の識別子を取得する必要があります。 `GetId` 関数が呼び出されたときに、同じ識別子を返すことが想定されています。

別のソースから取得した識別子は、未定義の動作を引き起こす可能性があります。

## <a name="getpolicy"></a>IScheduler:: GetPolicy メソッド

スケジューラのポリシーのコピーを返します。 Scheduler ポリシーの詳細については、「スケジューラ[ポリシー](schedulerpolicy-class.md)」を参照してください。

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>戻り値

スケジューラのポリシーのコピー。

## <a name="notifyresourcesexternallybusy"></a>IScheduler:: NotifyResourcesExternallyBusy メソッド

配列 `ppVirtualProcessorRoots` の仮想プロセッサルートのセットによって表されるハードウェアスレッドが、現在、他のスケジューラによって使用されていることを、このスケジューラに通知します。

```cpp
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>パラメーター

*ppVirtualProcessorRoots*<br/>
他のスケジューラがビジー状態になったハードウェアスレッドに関連付けられている `IVirtualProcessorRoot` インターフェイスの配列。

*count*<br/>
配列内の `IVirtualProcessorRoot` インターフェイスの数。

### <a name="remarks"></a>解説

特定のハードウェアスレッドを同時に複数のスケジューラに割り当てることができます。 その理由の1つは、リソースを共有せずに、すべてのスケジューラの最小同時実行数を満たすために、システム上に十分なハードウェアスレッドがないことです。 もう1つの可能性として、所有しているスケジューラが非アクティブ化されているハードウェアスレッド上のすべての仮想プロセッサルートから、リソースが一時的に他のスケジューラに割り当てられていない可能性もあります。

ハードウェアスレッドのサブスクリプションレベルは、そのハードウェアスレッドに関連付けられている、サブスクライブしているスレッドとアクティブ化された仮想プロセッサのルートの数によって示されます。 特定のスケジューラの観点から見ると、ハードウェアスレッドの外部サブスクリプションレベルは、他のスケジューラが貢献するサブスクリプションの部分です。 リソースが外部でビジー状態であることを示す通知は、ハードウェアスレッドの外部サブスクリプションレベルがゼロから正の区域に移動したときにスケジューラに送信されます。

このメソッドによる通知は、`MinConcurrency` ポリシーキーの値が `MaxConcurrency` ポリシーキーの値と同じポリシーを持つスケジューラにのみ送信されます。 Scheduler ポリシーの詳細については、「スケジューラ[ポリシー](schedulerpolicy-class.md)」を参照してください。

通知を受け取るスケジューラは、作成時に初期通知のセットを取得し、それが割り当てられたリソースが外部でビジー状態かアイドル状態かを通知します。

## <a name="notifyresourcesexternallyidle"></a>IScheduler:: NotifyResourcesExternallyIdle メソッド

配列 `ppVirtualProcessorRoots` の仮想プロセッサルートのセットによって表されるハードウェアスレッドが、他のスケジューラによって使用されていないことを、このスケジューラに通知します。

```cpp
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>パラメーター

*ppVirtualProcessorRoots*<br/>
他のスケジューラがアイドル状態になったハードウェアスレッドに関連付けられている `IVirtualProcessorRoot` インターフェイスの配列。

*count*<br/>
配列内の `IVirtualProcessorRoot` インターフェイスの数。

### <a name="remarks"></a>解説

特定のハードウェアスレッドを同時に複数のスケジューラに割り当てることができます。 その理由の1つは、リソースを共有せずに、すべてのスケジューラの最小同時実行数を満たすために、システム上に十分なハードウェアスレッドがないことです。 もう1つの可能性として、所有しているスケジューラが非アクティブ化されているハードウェアスレッド上のすべての仮想プロセッサルートから、リソースが一時的に他のスケジューラに割り当てられていない可能性もあります。

ハードウェアスレッドのサブスクリプションレベルは、そのハードウェアスレッドに関連付けられている、サブスクライブしているスレッドとアクティブ化された仮想プロセッサのルートの数によって示されます。 特定のスケジューラの観点から見ると、ハードウェアスレッドの外部サブスクリプションレベルは、他のスケジューラが貢献するサブスクリプションの部分です。 リソースが外部でビジー状態になっていることを示す通知は、ハードウェアスレッドの外部サブスクリプションレベルが前の正の値からゼロになるとスケジューラに送信されます。

このメソッドによる通知は、`MinConcurrency` ポリシーキーの値が `MaxConcurrency` ポリシーキーの値と同じポリシーを持つスケジューラにのみ送信されます。 Scheduler ポリシーの詳細については、「スケジューラ[ポリシー](schedulerpolicy-class.md)」を参照してください。

通知を受け取るスケジューラは、作成時に初期通知のセットを取得し、それが割り当てられたリソースが外部でビジー状態かアイドル状態かを通知します。

## <a name="removevirtualprocessors"></a>IScheduler:: RemoveVirtualProcessors メソッド

以前にこのスケジューラに割り当てられた仮想プロセッサルートの削除を開始します。

```cpp
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```

### <a name="parameters"></a>パラメーター

*ppVirtualProcessorRoots*<br/>
削除する仮想プロセッサルートを表す `IVirtualProcessorRoot` インターフェイスの配列。

*count*<br/>
配列内の `IVirtualProcessorRoot` インターフェイスの数。

### <a name="remarks"></a>解説

リソースマネージャーは、`RemoveVirtualProcessors` メソッドを呼び出して、スケジューラから一連の仮想プロセッサルートを取得します。 スケジューラは、仮想プロセッサルートで実行されたときに、各インターフェイスで[Remove](iexecutionresource-structure.md#remove)メソッドを呼び出すことが想定されています。 `Remove` メソッドを呼び出した後は、`IVirtualProcessorRoot` インターフェイスを使用しないでください。

パラメーター `ppVirtualProcessorRoots` は、インターフェイスの配列を指します。 削除する一連の仮想プロセッサルートの中で、`Remove` メソッドを使用して、ルートがアクティブになったことがない状態ですぐに返すことができます。 アクティブ化され、作業を実行している、または非アクティブ化され、作業が到着するのを待機しているルートは、非同期的に返される必要があります。 スケジューラは、仮想プロセッサルートをできるだけ早く削除しようとする必要があります。 仮想プロセッサルートの削除を遅らせていると、スケジューラ内で、意図しないオーバーサブスクリプションが発生する可能性があります。

## <a name="statistics"></a>IScheduler:: Statistics メソッド

タスクの到着と完了率に関する情報を提供し、スケジューラのキューの長さを変更します。

```cpp
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```

### <a name="parameters"></a>パラメーター

*Ptask"レート"*<br/>
このメソッドの最後の呼び出し以降にスケジューラによって完了されたタスクの数。

*pTaskArrivalRate*<br/>
このメソッドの最後の呼び出し以降にスケジューラに到着したタスクの数。

*キューに登録された pnumberoftasksen*<br/>
すべてのスケジューラキュー内のタスクの合計数。

### <a name="remarks"></a>解説

このメソッドは、スケジューラの統計情報を収集するためにリソースマネージャーによって呼び出されます。 ここで収集された統計情報は、動的なフィードバックアルゴリズムを使用して、スケジューラにより多くのリソースを割り当て、リソースをどこに配置するかを判断するために使用されます。 スケジューラによって提供される値はオプティミスティックにすることができ、現在のカウントを正確に反映する必要があるとは限りません。

リソースマネージャーが、スケジューラとリソースマネージャーに登録されている他のスケジューラとの間でリソースのバランスを取る方法を決定するために、タスクの到着といったフィードバックを使用する場合は、このメソッドを実装する必要があります。 統計情報を収集しない場合は、ポリシーキー `DynamicProgressFeedback` を scheduler のポリシーの `DynamicProgressFeedbackDisabled` 値に設定できます。このメソッドは、リソースマネージャーによってスケジューラで呼び出されません。

統計情報がない場合、Resource Manager はハードウェアスレッドサブスクリプションレベルを使用して、リソースの割り当てと移行に関する決定を行います。 サブスクリプションレベルの詳細については、「 [Iexecutionresource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)」を参照してください。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[SchedulerPolicy クラス](schedulerpolicy-class.md)<br/>
[IExecutionContext 構造体](iexecutioncontext-structure.md)<br/>
[IThreadProxy 構造体](ithreadproxy-structure.md)<br/>
[IVirtualProcessorRoot 構造体](ivirtualprocessorroot-structure.md)<br/>
[IResourceManager 構造体](iresourcemanager-structure.md)
