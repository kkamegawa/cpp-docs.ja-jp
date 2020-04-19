---
title: CWorkerThread クラス
ms.date: 11/04/2016
f1_keywords:
- CWorkerThread
- ATLUTIL/ATL::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::AddHandle
- ATLUTIL/ATL::CWorkerThread::AddTimer
- ATLUTIL/ATL::CWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CWorkerThread::GetThreadId
- ATLUTIL/ATL::CWorkerThread::Initialize
- ATLUTIL/ATL::CWorkerThread::RemoveHandle
- ATLUTIL/ATL::CWorkerThread::Shutdown
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
ms.openlocfilehash: f1aa76514b98bbf12f8e516d3d54f68e8ef4dd7d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496114"
---
# <a name="cworkerthread-class"></a>CWorkerThread クラス

このクラスは、ワーカースレッドを作成するか、既存のスレッドを使用して1つ以上のカーネルオブジェクトハンドルで待機し、いずれかのハンドルがシグナル状態になったときに、指定されたクライアント関数を実行します。

> [!IMPORTANT]
> このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>パラメーター

*ThreadTraits*<br/>
スレッド作成関数を提供するクラス ( [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)や[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)など)。

## <a name="members"></a>メンバー

### <a name="protected-structures"></a>保護された構造体

|名前|説明|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CWorkerThread::CWorkerThread](#cworkerthread)|ワーカースレッドのコンストラクター。|
|[CWorkerThread::~CWorkerThread](#dtor)|ワーカースレッドのデストラクター。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CWorkerThread::AddHandle](#addhandle)|このメソッドを呼び出して、ワーカースレッドによって管理されるリストに、待機可能なオブジェクトのハンドルを追加します。|
|[CWorkerThread::AddTimer](#addtimer)|ワーカースレッドによって管理されるリストに定期的な待機時間タイマーを追加するには、このメソッドを呼び出します。|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|ワーカースレッドのスレッドハンドルを取得するには、このメソッドを呼び出します。|
|[CWorkerThread::GetThreadId](#getthreadid)|ワーカースレッドのスレッド ID を取得するには、このメソッドを呼び出します。|
|[CWorkerThread::Initialize](#initialize)|ワーカースレッドを初期化するには、このメソッドを呼び出します。|
|[CWorkerThread::RemoveHandle](#removehandle)|待機可能なオブジェクトのリストからハンドルを削除するには、このメソッドを呼び出します。|
|[CWorkerThread::Shutdown](#shutdown)|ワーカースレッドをシャットダウンするには、このメソッドを呼び出します。|

## <a name="remarks"></a>Remarks

### <a name="to-use-cworkerthread"></a>CWorkerThread を使用するには

1. このクラスのインスタンスを作成します。

1. [CWorkerThread:: Initialize](#initialize)を呼び出します。

1. カーネルオブジェクトのハンドルと[Iworkerthreadclient](../../atl/reference/iworkerthreadclient-interface.md)の実装へのポインターを使用して、 [CWorkerThread:: addhandle](#addhandle)を呼び出します。

   \- または -

   [Iworkerthreadclient](../../atl/reference/iworkerthreadclient-interface.md)の実装へのポインターを使用して、 [CWorkerThread:: addtimer](#addtimer)を呼び出します。

1. ハンドルまたはタイマーがシグナル状態になったときに何らかのアクションを実行するには、 [Iworkerthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)を実装します。

1. 待機可能なオブジェクトの一覧からオブジェクトを削除するには、 [CWorkerThread:: RemoveHandle](#removehandle)を呼び出します。

1. スレッドを終了するには、 [CWorkerThread:: Shutdown](#shutdown)を呼び出します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlutil. h

##  <a name="addhandle"></a>  CWorkerThread::AddHandle

このメソッドを呼び出して、ワーカースレッドによって管理されるリストに、待機可能なオブジェクトのハンドルを追加します。

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>パラメーター

*hObject*<br/>
待機可能なオブジェクトへのハンドル。

*pClient*<br/>
ハンドルがシグナル状態になったときに呼び出されるオブジェクト上の[Iworkerthreadclient](../../atl/reference/iworkerthreadclient-interface.md)インターフェイスへのポインター。

*dwParam*<br/>
ハンドルがシグナル状態になったときに[Iworkerthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)に渡されるパラメーター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

[Iworkerthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)は、ハンドル ( *hobject*) がシグナル状態になったときに*pclient*を通じて呼び出されます。

##  <a name="addtimer"></a>  CWorkerThread::AddTimer

ワーカースレッドによって管理されるリストに定期的な待機時間タイマーを追加するには、このメソッドを呼び出します。

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>パラメーター

*dwInterval*<br/>
タイマーの期間をミリ秒単位で指定します。

*pClient*<br/>
ハンドルがシグナル状態になったときに呼び出されるオブジェクト上の[Iworkerthreadclient](../../atl/reference/iworkerthreadclient-interface.md)インターフェイスへのポインター。

*dwParam*<br/>
ハンドルがシグナル状態になったときに[Iworkerthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)に渡されるパラメーター。

*phTimer*<br/>
入出力成功した場合は、新しく作成されたタイマーへのハンドルを受け取るハンドル変数のアドレス。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

[Iworkerthreadclient:: Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)は、タイマーがシグナル状態になったときに*pclient*を通じて呼び出されます。

タイマーハンドルを*phtimer*から[CWorkerThread:: removehandle](#removehandle)に渡して、タイマーを閉じます。

##  <a name="cworkerthread"></a>  CWorkerThread::CWorkerThread

コンストラクターです。

```
CWorkerThread() throw();
```

##  <a name="dtor"></a>  CWorkerThread::~CWorkerThread

デストラクターです。

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>Remarks

[CWorkerThread:: Shutdown](#shutdown)を呼び出します。

##  <a name="getthreadhandle"></a>  CWorkerThread::GetThreadHandle

ワーカースレッドのスレッドハンドルを取得するには、このメソッドを呼び出します。

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>戻り値

スレッドハンドルを返します。ワーカースレッドが初期化されていない場合は NULL を返します。

##  <a name="getthreadid"></a>  CWorkerThread::GetThreadId

ワーカースレッドのスレッド ID を取得するには、このメソッドを呼び出します。

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>戻り値

スレッド ID を返します。ワーカースレッドが初期化されていない場合は NULL を返します。

##  <a name="initialize"></a>  CWorkerThread::Initialize

ワーカースレッドを初期化するには、このメソッドを呼び出します。

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>パラメーター

*pThread*<br/>
既存のワーカースレッド。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

このメソッドは、作成後、または[CWorkerThread:: Shutdown](#shutdown)の呼び出し後にオブジェクトを初期化するために呼び出す必要があります。

複数`CWorkerThread`のオブジェクトが同じワーカースレッドを使用するようにするには、引数を渡さずに1つのオブジェクトを初期化し、 `Initialize`そのオブジェクトへのポインターを他のオブジェクトのメソッドに渡します。 ポインターを使用して初期化されたオブジェクトは、オブジェクトの初期化に使用される前にシャットダウンする必要があります。

既存のオブジェクトへのポインターを使用して初期化されたときのメソッドの動作の変更方法については、「 [CWorkerThread:: Shutdown](#shutdown) 」を参照してください。

##  <a name="removehandle"></a>  CWorkerThread::RemoveHandle

待機可能なオブジェクトのリストからハンドルを削除するには、このメソッドを呼び出します。

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>パラメーター

*hObject*<br/>
削除するハンドル。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

ハンドルが削除されると、 [Addhandle](#addhandle)に渡された関連オブジェクトに対して[Iworkerthreadclient:: CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle)が呼び出されます。 この呼び出しが失敗し`CWorkerThread`た場合、はハンドルに対して Windows [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle)関数を呼び出します。

##  <a name="shutdown"></a>  CWorkerThread::Shutdown

ワーカースレッドをシャットダウンするには、このメソッドを呼び出します。

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>パラメーター

*dwWait*<br/>
ワーカースレッドがシャットダウンするのを待機する時間 (ミリ秒単位)。 ATL_WORKER_THREAD_WAIT の既定値は10秒です。 必要に応じて、このシンボルに対して独自の値を定義してから atlutil. h を含めることができます。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、タイムアウト値*Dwwait*を超えた場合はエラー HRESULT が返されます。

### <a name="remarks"></a>Remarks

オブジェクトを再利用するには、このメソッドを呼び出した後で[CWorkerThread:: Initialize](#initialize)を呼び出します。

`Shutdown` 別`CWorkerThread`のオブジェクトへのポインターで初期化されたオブジェクトに対してを呼び出しても効果はなく、常に S_OK を返します。

## <a name="see-also"></a>関連項目

[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[クラス](../../atl/reference/atl-classes.md)<br/>
[マルチスレッド: マルチスレッド : ワーカー スレッドの作成](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient インターフェイス](../../atl/reference/iworkerthreadclient-interface.md)
