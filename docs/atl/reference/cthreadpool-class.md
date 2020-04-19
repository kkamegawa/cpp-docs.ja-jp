---
title: CThreadPool クラス
ms.date: 11/04/2016
f1_keywords:
- CThreadPool
- ATLUTIL/ATL::CThreadPool
- ATLUTIL/ATL::CThreadPool::CThreadPool
- ATLUTIL/ATL::CThreadPool::AddRef
- ATLUTIL/ATL::CThreadPool::GetNumThreads
- ATLUTIL/ATL::CThreadPool::GetQueueHandle
- ATLUTIL/ATL::CThreadPool::GetSize
- ATLUTIL/ATL::CThreadPool::GetTimeout
- ATLUTIL/ATL::CThreadPool::Initialize
- ATLUTIL/ATL::CThreadPool::QueryInterface
- ATLUTIL/ATL::CThreadPool::QueueRequest
- ATLUTIL/ATL::CThreadPool::Release
- ATLUTIL/ATL::CThreadPool::SetSize
- ATLUTIL/ATL::CThreadPool::SetTimeout
- ATLUTIL/ATL::CThreadPool::Shutdown
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
ms.openlocfilehash: f0b732efdce5cf04349f468363b8d86621d90204
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496307"
---
# <a name="cthreadpool-class"></a>CThreadPool クラス

このクラスは、作業項目のキューを処理するワーカースレッドのプールを提供します。

## <a name="syntax"></a>構文

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>パラメーター

*者*<br/>
スレッドプールでキューに置かれた作業項目を処理するために使用されるコードを提供する、[ワーカーの原型](../../atl/reference/worker-archetype.md)クラスに準拠するクラス。

*ThreadTraits*<br/>
プール内のスレッドを作成するために使用される関数を提供するクラス。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|スレッドプールのコンストラクター。|
|[CThreadPool::~CThreadPool](#dtor)|スレッドプールのデストラクター。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CThreadPool::AddRef](#addref)|の`IUnknown::AddRef`実装。|
|[CThreadPool::GetNumThreads](#getnumthreads)|プール内のスレッドの数を取得するには、このメソッドを呼び出します。|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|作業項目をキューに置いて使用する IO 完了ポートのハンドルを取得するには、このメソッドを呼び出します。|
|[CThreadPool::GetSize](#getsize)|プール内のスレッドの数を取得するには、このメソッドを呼び出します。|
|[CThreadPool::GetTimeout](#gettimeout)|スレッドプールがスレッドのシャットダウンを待機する最大時間 (ミリ秒) を取得するには、このメソッドを呼び出します。|
|[CThreadPool::Initialize](#initialize)|スレッドプールを初期化するには、このメソッドを呼び出します。|
|[CThreadPool::QueryInterface](#queryinterface)|の`IUnknown::QueryInterface`実装。|
|[CThreadPool::QueueRequest](#queuerequest)|プール内のスレッドによって処理されるように作業項目をキューに配置するには、このメソッドを呼び出します。|
|[CThreadPool::Release](#release)|の`IUnknown::Release`実装。|
|[CThreadPool:: SetSize](#setsize)|プール内のスレッドの数を設定するには、このメソッドを呼び出します。|
|[CThreadPool::SetTimeout](#settimeout)|スレッドプールがスレッドのシャットダウンを待機する最大時間をミリ秒単位で設定するには、このメソッドを呼び出します。|
|[CThreadPool::Shutdown](#shutdown)|スレッドプールをシャットダウンするには、このメソッドを呼び出します。|

## <a name="remarks"></a>Remarks

プール内のスレッドは、プールが初期化、サイズ変更、またはシャットダウンされるときに作成され、破棄されます。 クラス*ワーカー*のインスタンスは、プール内の各ワーカースレッドのスタック上に作成されます。 各インスタンスは、スレッドの有効期間にわたって存続します。

スレッドが作成されるとすぐに、その`Initialize`スレッドに関連付けられているオブジェクトで Worker:: が呼び出されます。 スレッドを破棄する直前に、 *Worker*::`Terminate`が呼び出されます。 どちらのメソッドも、 **void** <strong>\*</strong>引数を受け取る必要があります。 この引数の値は、 [CThreadPool:: Initialize](#initialize)の*pvworkerparam*パラメーターを通じてスレッドプールに渡されます。

キューに作業項目があり、ワーカースレッドが作業に使用できる場合、ワーカースレッドはキューから項目を取得し、そのスレッド`Execute`の*ワーカー*オブジェクトのメソッドを呼び出します。 次に、3つの項目がメソッドに渡されます。これは、 `pvWorkerParam`キューからの項目、 `Initialize` *worker*:: および`Terminate` *worker*:: に渡される項目、および IO 完了ポートキューに使用される[重複](/windows/win32/api/minwinbase/ns-minwinbase-overlapped)した構造体へのポインターです.

*ワーカー*クラスは、Typedef ( *worker*:: `RequestType`) を指定することによって、スレッドプールでキューに登録される項目の型を宣言します。 この型は、ULONG_PTR との間でキャストできる必要があります。

*ワーカー*クラスの例として、 [Cnonstatelessworker クラス](../../atl/reference/cnonstatelessworker-class.md)があります。

## <a name="inheritance-hierarchy"></a>継承階層

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlutil. h

##  <a name="addref"></a>  CThreadPool::AddRef

の`IUnknown::AddRef`実装。

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>戻り値

常に1を返します。

### <a name="remarks"></a>Remarks

このクラスは、参照カウントを使用した有効期間制御を実装しません。

##  <a name="cthreadpool"></a>  CThreadPool::CThreadPool

スレッドプールのコンストラクター。

```
CThreadPool() throw();
```

### <a name="remarks"></a>Remarks

タイムアウト値を ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT に初期化します。 既定の時間は36秒です。 必要に応じて、このシンボルに対して独自の正の整数値を定義してから atlutil. h を含めることができます。

##  <a name="dtor"></a>CThreadPool:: ~ CThreadPool

スレッドプールのデストラクター。

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Remarks

[CThreadPool:: Shutdown](#shutdown)を呼び出します。

##  <a name="getnumthreads"></a>  CThreadPool::GetNumThreads

プール内のスレッドの数を取得するには、このメソッドを呼び出します。

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>戻り値

プール内のスレッドの数を返します。

##  <a name="getqueuehandle"></a>  CThreadPool::GetQueueHandle

作業項目をキューに置いて使用する IO 完了ポートのハンドルを取得するには、このメソッドを呼び出します。

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>戻り値

キューハンドルを返します。スレッドプールが初期化されていない場合は NULL を返します。

##  <a name="getsize"></a>  CThreadPool::GetSize

プール内のスレッドの数を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>パラメーター

*pnNumThreads*<br/>
入出力成功した場合、プール内のスレッドの数を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="gettimeout"></a>  CThreadPool::GetTimeout

スレッドプールがスレッドのシャットダウンを待機する最大時間 (ミリ秒) を取得するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>パラメーター

*pdwMaxWait*<br/>
入出力成功した場合、スレッドプールがスレッドのシャットダウンを待機する最大時間 (ミリ秒) を受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

このタイムアウト値は、そのメソッドに他の値が指定されていない場合に、 [CThreadPool:: Shutdown](#shutdown)によって使用されます。

##  <a name="initialize"></a>  CThreadPool::Initialize

スレッドプールを初期化するには、このメソッドを呼び出します。

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>パラメーター

*pvWorkerParam*<br/>
ワーカースレッドオブジェクトの、 `Initialize` `Execute`、および`Terminate`の各メソッドに渡されるワーカーパラメーター。

*nNumThreads*<br/>
プール内の要求されたスレッド数。

*Nnumthreads*が負の場合は、スレッドの合計数を取得するために、その絶対値にマシンのプロセッサ数を掛けた値が乗算されます。

*Nnumthreads*が0の場合、ATLS_DEFAULT_THREADSPERPROC には、スレッドの合計数を取得するためにコンピューター内のプロセッサ数が乗算されます。  既定値は、プロセッサあたり2スレッドです。 必要に応じて、このシンボルに対して独自の正の整数値を定義してから atlutil. h を含めることができます。

*dwStackSize*<br/>
プール内の各スレッドのスタックサイズ。

*hCompletion*<br/>
完了ポートに関連付けるオブジェクトのハンドル。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="queryinterface"></a>  CThreadPool::QueryInterface

の`IUnknown::QueryInterface`実装。

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Remarks

このクラスのオブジェクトは、 `IUnknown`および[ithreadpoolconfig](../../atl/reference/ithreadpoolconfig-interface.md)インターフェイスに対してクエリを正常に実行できます。

##  <a name="queuerequest"></a>  CThreadPool::QueueRequest

プール内のスレッドによって処理されるように作業項目をキューに配置するには、このメソッドを呼び出します。

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>パラメーター

*申請*<br/>
キューに登録する要求。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメソッドは、作業項目をキューに追加します。 プール内のスレッドは、受信された順にキューから項目を取得します。

##  <a name="release"></a>  CThreadPool::Release

の`IUnknown::Release`実装。

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>戻り値

常に1を返します。

### <a name="remarks"></a>Remarks

このクラスは、参照カウントを使用した有効期間制御を実装しません。

##  <a name="setsize"></a>  CThreadPool::SetSize

プール内のスレッドの数を設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>パラメーター

*nNumThreads*<br/>
プール内の要求されたスレッド数。

*Nnumthreads*が負の場合は、スレッドの合計数を取得するために、その絶対値にマシンのプロセッサ数を掛けた値が乗算されます。

*Nnumthreads*が0の場合、ATLS_DEFAULT_THREADSPERPROC には、スレッドの合計数を取得するためにコンピューター内のプロセッサ数が乗算されます。 既定値は、プロセッサあたり2スレッドです。 必要に応じて、このシンボルに対して独自の正の整数値を定義してから atlutil. h を含めることができます。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

指定されたスレッド数が、プール内の現在のスレッド数よりも少ない場合、オブジェクトは、待機中のスレッドによって取得されるシャットダウンメッセージをキューに配置します。 待機中のスレッドがメッセージをキューから取り出すと、スレッドプールに通知され、スレッドプロシージャが終了します。 このプロセスは、プール内のスレッドの数が、指定された数に達するか、 [gettimeout](#gettimeout)/ [SetTimeout](#settimeout)によって指定された期間内にスレッドが終了するまで繰り返されます。 このような状況では、メソッドは WAIT_TIMEOUT に対応する HRESULT を返し、保留中のシャットダウンメッセージはキャンセルされます。

##  <a name="settimeout"></a>  CThreadPool::SetTimeout

スレッドプールがスレッドのシャットダウンを待機する最大時間をミリ秒単位で設定するには、このメソッドを呼び出します。

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>パラメーター

*dwMaxWait*<br/>
スレッドプールがスレッドのシャットダウンを待機する最大要求時間 (ミリ秒単位)。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

タイムアウトは ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT に初期化されます。 既定の時間は36秒です。 必要に応じて、このシンボルに対して独自の正の整数値を定義してから atlutil. h を含めることができます。

*Dwmaxwait*は、1つのスレッドがシャットダウンするのをプールが待機する時間であることに注意してください。 プールから複数のスレッドを削除するために実行される最大時間は、 *Dwmaxwait*にスレッド数を乗算した値よりもわずかに少ない場合があります。

##  <a name="shutdown"></a>  CThreadPool::Shutdown

スレッドプールをシャットダウンするには、このメソッドを呼び出します。

```
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>パラメーター

*dwMaxWait*<br/>
スレッドプールがスレッドのシャットダウンを待機する最大要求時間 (ミリ秒単位)。 0または値が指定されていない場合、このメソッドは[CThreadPool:: SetTimeout](#settimeout)によって設定されたタイムアウトを使用します。

### <a name="remarks"></a>Remarks

このメソッドは、プール内のすべてのスレッドにシャットダウン要求をポストします。 タイムアウトが経過すると、このメソッドは終了しなかったすべてのスレッドで[TerminateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-terminatethread)を呼び出します。 このメソッドは、クラスのデストラクターから自動的に呼び出されます。

## <a name="see-also"></a>関連項目

[IThreadPoolConfig インターフェイス](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[クラス](../../atl/reference/atl-classes.md)
