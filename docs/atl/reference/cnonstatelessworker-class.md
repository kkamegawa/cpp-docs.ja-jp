---
title: CNonStatelessWorker Class
ms.date: 11/04/2016
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
helpviewer_keywords:
- CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
ms.openlocfilehash: abfd3e585c843fcc4ed4ad273c8ed217eaaccb7d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245531"
---
# <a name="cnonstatelessworker-class"></a>CNonStatelessWorker Class

スレッド プールからの要求を受信し、要求ごとに作成および破棄される worker オブジェクトに渡されます。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class Worker>
class CNonStatelessWorker
```

#### <a name="parameters"></a>パラメーター

*ワーカー*<br/>
準拠しているワーカー スレッドのクラス、[ワーカーのアーキタイプ](../../atl/reference/worker-archetype.md)のキューに要求を処理するのに適した[CThreadPool](../../atl/reference/cthreadpool-class.md)します。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|[CNonStatelessWorker::RequestType](#requesttype)|実装[WorkerArchetype::RequestType](worker-archetype.md#requesttype)します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CNonStatelessWorker::Execute](#execute)|実装[WorkerArchetype::Execute](worker-archetype.md#execute)します。|
|[CNonStatelessWorker::Initialize](#initialize)|実装[WorkerArchetype::Initialize](worker-archetype.md#initialize)します。|
|[CNonStatelessWorker::Terminate](#terminate)|実装[WorkerArchetype::Terminate](worker-archetype.md#terminate)します。|

## <a name="remarks"></a>Remarks

このクラスで使用するための単純なワーカー スレッドは、 [CThreadPool](../../atl/reference/cthreadpool-class.md)します。 このクラスは、独自の任意の要求処理機能を提供しません。 代わりに、1 つのインスタンスをインスタンス化*ワーカー* 1 回の要求し、そのインスタンスにそのメソッドの実装にデリゲートします。

このクラスの利点は、既存のワーカー スレッド クラスの状態モデルを変更する便利な手段を提供します。 `CThreadPool` スレッドの有効期間にわたって 1 つのワーカーが作成されますので、worker クラスには、状態が保持している場合は、複数の要求間で保持、これは。 単にそのクラスをラップすることによって、`CNonStatelessWorker`テンプレートで使用する前に`CThreadPool`、作業者と 1 つの要求に制限されていますが、保持している状態の有効期間。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlutil.h

##  <a name="execute"></a>  CNonStatelessWorker::Execute

実装[WorkerArchetype::Execute](worker-archetype.md#execute)します。

```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>Remarks

このメソッドのインスタンスを作成、*ワーカー*で呼び出し、stack クラス[初期化](worker-archetype.md#initialize)そのオブジェクト。 初期化が成功した場合、このメソッドも呼び出します[Execute](worker-archetype.md#execute)と[Terminate](worker-archetype.md#terminate)同一のオブジェクト。

##  <a name="initialize"></a>  CNonStatelessWorker::Initialize

実装[WorkerArchetype::Initialize](worker-archetype.md#initialize)します。

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>戻り値

常に TRUE を返します。

### <a name="remarks"></a>Remarks

このクラスすべての初期化を実行しません`Initialize`します。

##  <a name="requesttype"></a>  CNonStatelessWorker::RequestType

実装[WorkerArchetype::RequestType](worker-archetype.md#requesttype)します。

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>Remarks

このクラスは処理に使用されるクラスと同じ種類の作業項目の*ワーカー*テンプレート パラメーター。 参照してください[CNonStatelessWorker 概要](../../atl/reference/cnonstatelessworker-class.md)詳細についてはします。

##  <a name="terminate"></a>  CNonStatelessWorker::Terminate

実装[WorkerArchetype::Terminate](worker-archetype.md#terminate)します。

```
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>Remarks

このクラス、クリーンアップを実行しません`Terminate`します。

## <a name="see-also"></a>関連項目

[CThreadPool クラス](../../atl/reference/cthreadpool-class.md)<br/>
[ワーカーのアーキタイプ](../../atl/reference/worker-archetype.md)<br/>
[クラス](../../atl/reference/atl-classes.md)
