---
title: IVirtualProcessorRoot 構造体
ms.date: 11/04/2016
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
ms.openlocfilehash: 60757b0edea6b60d080c2175d4df4830ffec0cc3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139894"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot 構造体

スレッド プロキシが実行できるハードウェア スレッドの抽象化です。

## <a name="syntax"></a>構文

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[IVirtualProcessorRoot:: Activate](#activate)|実行コンテキストインターフェイス `pContext` に関連付けられているスレッドプロキシが、この仮想プロセッサルートで実行を開始します。|
|[IVirtualProcessorRoot::D eactivate](#deactivate)|この仮想プロセッサルートで現在実行されているスレッドプロキシが、実行コンテキストのディスパッチを停止します。 スレッドプロキシは、`Activate` メソッドの呼び出しで実行を再開します。|
|[IVirtualProcessorRoot:: EnsureAllTasksVisible](#ensurealltasksvisible)|個々のプロセッサのメモリ階層に格納されているデータが、システム上のすべてのプロセッサに対して可視になります。 これにより、メソッドが返される前に、すべてのプロセッサで完全なメモリフェンスが実行されます。|
|[IVirtualProcessorRoot:: GetId](#getid)|仮想プロセッサルートの一意の識別子を返します。|

## <a name="remarks"></a>コメント

すべての仮想プロセッサルートには、実行リソースが関連付けられています。 `IVirtualProcessorRoot` インターフェイスは、 [Iexecutionresource](iexecutionresource-structure.md)インターフェイスから継承されます。 複数の仮想プロセッサルートが、同じ基になるハードウェアスレッドに対応している可能性があります。

リソースマネージャーは、リソースへの要求に応答して、仮想プロセッサルートをスケジューラに付与します。 スケジューラは、仮想プロセッサルートを使用して、実行コンテキストでアクティブ化することで、作業を実行できます。

## <a name="inheritance-hierarchy"></a>継承階層

[IExecutionResource](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>要件

**ヘッダー:** concrtrm. h

**名前空間:** concurrency

## <a name="activate"></a>IVirtualProcessorRoot:: Activate メソッド

実行コンテキストインターフェイス `pContext` に関連付けられているスレッドプロキシが、この仮想プロセッサルートで実行を開始します。

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>パラメーター

*pContext*<br/>
この仮想プロセッサルートでディスパッチされる実行コンテキストへのインターフェイス。

### <a name="remarks"></a>コメント

リソースマネージャーは、実行コンテキストインターフェイスに関連付けられていない場合、スレッドプロキシを指定し `pContext`

`Activate` メソッドを使用して、リソースマネージャーによって返された新しい仮想プロセッサルートでの作業の実行を開始したり、非アクティブ化されたまたは非アクティブ化しようとしている仮想プロセッサルートでスレッドプロキシを再開したりすることができます。 非アクティブ化の詳細については、「 [Ivirtualprocessorroot::D eactivate](#deactivate) 」を参照してください。 非アクティブ化された仮想プロセッサルートを再開する場合、パラメーター `pContext` は、仮想プロセッサルートを非アクティブ化するために使用するパラメーターと同じである必要があります。

仮想プロセッサルートが初めてアクティブ化されると、それ以降の `Deactivate` と `Activate` の呼び出しのペアが競合する可能性があります。 つまり、リソースマネージャーは、目的の `Deactivate` 呼び出しを受け取る前に、`Activate` の呼び出しを受け取ることができます。

仮想プロセッサルートをアクティブ化すると、この仮想プロセッサルートが現在ビジー状態であることがリソースマネージャーに通知されます。 スケジューラがこのルートで実行する作業を見つけられない場合は、仮想プロセッサのルートがアイドル状態であることをリソースマネージャーに通知する `Deactivate` メソッドを呼び出す必要があります。 リソースマネージャーは、このデータを使用してシステムの負荷を分散します。

引数 `pContext` に `NULL`値がある場合、`invalid_argument` がスローされます。

`invalid_operation` は、引数 `pContext` が、この仮想プロセッサルートによって最後にディスパッチされた実行コンテキストを表していない場合にスローされます。

仮想プロセッサルートをアクティブ化すると、基になるハードウェアスレッドのサブスクリプションレベルが1ずつ増加します。 サブスクリプションレベルの詳細については、「 [Iexecutionresource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)」を参照してください。

## <a name="deactivate"></a>IVirtualProcessorRoot::D eactivate メソッド

この仮想プロセッサルートで現在実行されているスレッドプロキシが、実行コンテキストのディスパッチを停止します。 スレッドプロキシは、`Activate` メソッドの呼び出しで実行を再開します。

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>パラメーター

*pContext*<br/>
このルートによって現在ディスパッチされているコンテキスト。

### <a name="return-value"></a>戻り値

ブール値。 値が**true の場合**は、`Activate` メソッドへの呼び出しに応答して、`Deactivate` メソッドからスレッドプロキシが返されたことを示します。 値 `false` は、リソースマネージャーの通知イベントに応答してスレッドプロキシがメソッドから返されたことを示します。 ユーザーモードスケジュール可能 (UMS) スレッドスケジューラでは、これは項目がスケジューラの入力候補一覧に表示され、スケジューラがそれらを処理する必要があることを示します。

### <a name="remarks"></a>コメント

スケジューラに作業が見つからない場合に、このメソッドを使用して、仮想プロセッサルートの実行を一時的に停止します。 `Deactivate` メソッドの呼び出しは、仮想プロセッサのルートが最後にアクティブ化された実行コンテキストの `Dispatch` メソッド内から行う必要があります。 言い換えると、`Deactivate` メソッドを呼び出すスレッドプロキシは、仮想プロセッサルートで現在実行されているものである必要があります。 実行されていない仮想プロセッサルートでメソッドを呼び出すと、未定義の動作が発生する可能性があります。

非アクティブ化された仮想プロセッサルートは、`Deactivate` メソッドに渡されたものと同じ引数を使用して、`Activate` メソッドを呼び出すことによってウェイクアップできます。 スケジューラは、`Activate` および `Deactivate` メソッドの呼び出しがペアになっていることを確認する役割を担いますが、特定の順序で受信する必要はありません。 リソースマネージャーは、目的の `Deactivate` メソッドへの呼び出しを受け取る前に、`Activate` メソッドへの呼び出しの受信を処理できます。

仮想プロセッサのルート awakens と `Deactivate` メソッドからの戻り値が**false**の場合、スケジューラは、`IUMSCompletionList::GetUnblockNotifications` メソッドを使用して UMS 入力候補の一覧に対してクエリを実行し、その情報を操作した後、`Deactivate` メソッドを再度呼び出します。 これは、`Deactivate` メソッドが `true`値を返すまで繰り返されます。

引数 `pContext` の値が NULL の場合、`invalid_argument` がスローされます。

`invalid_operation` は、仮想プロセッサルートがアクティブになったことがない場合、または引数 `pContext` が、この仮想プロセッサルートによって最後にディスパッチされた実行コンテキストを表していない場合にスローされます。

仮想プロセッサルートを非アクティブ化することにより、基になるハードウェアスレッドのサブスクリプションレベルが1ずつ減少します。 サブスクリプションレベルの詳細については、「 [Iexecutionresource:: CurrentSubscriptionLevel](iexecutionresource-structure.md#currentsubscriptionlevel)」を参照してください。

## <a name="ensurealltasksvisible"></a>IVirtualProcessorRoot:: EnsureAllTasksVisible メソッド

個々のプロセッサのメモリ階層に格納されているデータが、システム上のすべてのプロセッサに対して可視になります。 これにより、メソッドが返される前に、すべてのプロセッサで完全なメモリフェンスが実行されます。

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>パラメーター

*pContext*<br/>
この仮想プロセッサルートによって現在ディスパッチされているコンテキスト。

### <a name="remarks"></a>コメント

この方法は、新しい作業をスケジューラに追加することで、仮想プロセッサルートの非アクティブ化を同期する場合に便利です。 パフォーマンス上の理由から、メモリバリアを実行せずに作業項目をスケジューラに追加することを決定できます。つまり、あるプロセッサで実行されているスレッドによって追加された作業項目は、他のすべてのプロセッサですぐには表示されません。 このメソッドを `Deactivate` メソッドと組み合わせて使用することで、スケジューラのコレクションに作業項目が存在している間、スケジューラがすべての仮想プロセッサルートを非アクティブ化しないようにすることができます。

`EnsureAllTasksVisibleThe` メソッドの呼び出しは、仮想プロセッサのルートが最後にアクティブ化された実行コンテキストの `Dispatch` メソッド内から行う必要があります。 言い換えると、`EnsureAllTasksVisible` メソッドを呼び出すスレッドプロキシは、仮想プロセッサルートで現在実行されているものである必要があります。 実行されていない仮想プロセッサルートでメソッドを呼び出すと、未定義の動作が発生する可能性があります。

引数 `pContext` に `NULL`値がある場合、`invalid_argument` がスローされます。

`invalid_operation` は、仮想プロセッサルートがアクティブになったことがない場合、または引数 `pContext` が、この仮想プロセッサルートによって最後にディスパッチされた実行コンテキストを表していない場合にスローされます。

## <a name="getid"></a>IVirtualProcessorRoot:: GetId メソッド

仮想プロセッサルートの一意の識別子を返します。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>戻り値

整数識別子。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
