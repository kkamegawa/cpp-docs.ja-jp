---
title: ワーカーの原型クラス
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: 7f28b9e64c88a5be440417dd9d22f129ee7d6edf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495270"
---
# <a name="worker-archetype"></a>ワーカーの原型クラス

*ワーカー*の原型物に準拠するクラスは、スレッドプールでキューに置かれた作業項目を処理するコードを提供します。

**実装**

この原型に準拠するクラスを実装するには、クラスに次の機能を提供する必要があります。

|メソッド|説明|
|------------|-----------------|
|[Initialize](#initialize)|要求が[Execute](#execute)に渡される前にワーカーオブジェクトを初期化するために呼び出されます。|
|[Execute](#execute)|作業項目を処理するために呼び出されます。|
|[Terminate](#terminate)|すべての要求が[実行](#execute)されると、ワーカーオブジェクトを初期化解除するために呼び出されます。|

|Typedef|説明|
|-------------|-----------------|
|[RequestType](#requesttype)|ワーカークラスで処理できる作業項目の種類の typedef。|

一般的な*ワーカー*クラスは次のようになります。

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**既存の実装**

これらのクラスは、この原型に準拠しています。

|クラス|説明|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|スレッドプールから要求を受信し、要求ごとに作成および破棄されたワーカーオブジェクトに渡します。|

**使用**

これらのテンプレートパラメーターは、クラスがこの原型に準拠していることを想定しています。

|パラメーター名|使用元|
|--------------------|-------------|
|*者*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*者*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>必要条件

**ヘッダー:** atlutil. h

## <a name="execute"></a>WorkerArchetype:: Execute

作業項目を処理するために呼び出されます。

```
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>パラメーター

*申請*<br/>
処理される作業項目。 作業項目の種類はと`RequestType`同じです。

*pvWorkerParam*<br/>
ワーカークラスによって認識されるカスタムパラメーター。 また、と`WorkerArchetype::Initialize` `Terminate`にも渡されます。

*pOverlapped*<br/>
作業項目がキューに格納されたキューを作成するために使用される、[オーバーラップ](/windows/win32/api/minwinbase/ns-minwinbase-overlapped)された構造体へのポインター。

## <a name="initialize"></a>WorkerArchetype:: Initialize

要求がに`WorkerArchetype::Execute`渡される前にワーカーオブジェクトを初期化するために呼び出されます。
```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>パラメーター

*pvParam*<br/>
ワーカークラスによって認識されるカスタムパラメーター。 また、と`WorkerArchetype::Terminate` `WorkerArchetype::Execute`にも渡されます。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

## <a name="requesttype"></a> WorkerArchetype::RequestType

ワーカークラスで処理できる作業項目の種類の typedef。

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>Remarks

この型は、の最初の`WorkerArchetype::Execute`パラメーターとして使用する必要があり、ULONG_PTR との間でキャストできる必要があります。

## <a name="terminate"></a>WorkerArchetype:: Terminate

すべての要求がに`WorkerArchetype::Execute`渡された後にワーカーオブジェクトを初期化解除するために呼び出されます。

```
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>パラメーター

*pvParam*<br/>
ワーカークラスによって認識されるカスタムパラメーター。 また、と`WorkerArchetype::Initialize` `WorkerArchetype::Execute`にも渡されます。

## <a name="see-also"></a>関連項目

[概念](../../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM デスクトップ コンポーネント](../../atl/atl-com-desktop-components.md)
