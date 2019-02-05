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
ms.openlocfilehash: 5ecde92cbd9fb9e028e79c9a0ce75859ce85790a
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893458"
---
# <a name="cworkerthread-class"></a>CWorkerThread クラス

このクラスは、ワーカー スレッドを作成します。 または、既存のものを使用して化し、1 つ以上のカーネル オブジェクトのハンドルを待機ハンドルがシグナル通知されたときに、指定したクライアント関数を実行します。

> [!IMPORTANT]
> このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>パラメーター

*ThreadTraits*<br/>
など、スレッド作成関数を提供するクラス[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)または[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)します。

## <a name="members"></a>メンバー

### <a name="protected-structures"></a>保護されている構造体

|名前|説明|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CWorkerThread::CWorkerThread](#cworkerthread)|ワーカー スレッドのコンス トラクターです。|
|[CWorkerThread::~CWorkerThread](#dtor)|ワーカー スレッドのデストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CWorkerThread::AddHandle](#addhandle)|待機可能オブジェクトのハンドルをワーカー スレッドによって管理されるリストに追加するには、このメソッドを呼び出します。|
|[CWorkerThread::AddTimer](#addtimer)|ワーカー スレッドによって保持される一覧に定期的な待機可能なタイマーを追加するには、このメソッドを呼び出します。|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|ワーカー スレッドのスレッドのハンドルを取得するには、このメソッドを呼び出します。|
|[CWorkerThread::GetThreadId](#getthreadid)|ワーカー スレッドのスレッド ID を取得するには、このメソッドを呼び出します。|
|[CWorkerThread::Initialize](#initialize)|ワーカー スレッドを初期化するためには、このメソッドを呼び出します。|
|[CWorkerThread::RemoveHandle](#removehandle)|ハンドルを待機可能オブジェクトの一覧から削除するには、このメソッドを呼び出します。|
|[CWorkerThread::Shutdown](#shutdown)|ワーカー スレッドをシャット ダウンするには、このメソッドを呼び出します。|

## <a name="remarks"></a>Remarks

### <a name="to-use-cworkerthread"></a>CWorkerThread を使用するには

1. このクラスのインスタンスを作成します。

1. 呼び出す[CWorkerThread::Initialize](#initialize)します。

1. 呼び出す[CWorkerThread::AddHandle](#addhandle)カーネル オブジェクトとの実装へのポインターのハンドルを持つ[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)します。

   \- または -

   呼び出す[CWorkerThread::AddTimer](#addtimer)の実装へのポインターを[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)します。

1. 実装[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)ハンドルまたはタイマーがシグナル通知されたときに、何らかのアクションを実行します。

1. 待機可能オブジェクトの一覧からオブジェクトを削除するには、呼び出す[CWorkerThread::RemoveHandle](#removehandle)します。

1. スレッドを終了するには、呼び出す[CWorkerThread::Shutdown](#shutdown)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlutil.h

##  <a name="addhandle"></a>  CWorkerThread::AddHandle

待機可能オブジェクトのハンドルをワーカー スレッドによって管理されるリストに追加するには、このメソッドを呼び出します。

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>パラメーター

*hObject*<br/>
待機可能オブジェクトへのハンドル。

*pClient*<br/>
ポインター、 [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)ハンドルがシグナル通知されたときに呼び出されるオブジェクトのインターフェイス。

*dwParam*<br/>
渡されるパラメーター [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)ハンドルがシグナル通知されたとき。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)を介して呼び出される*pClient*ときに、ハンドル*hObject*、通知されます。

##  <a name="addtimer"></a>  CWorkerThread::AddTimer

ワーカー スレッドによって保持される一覧に定期的な待機可能なタイマーを追加するには、このメソッドを呼び出します。

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>パラメーター

*dwInterval*<br/>
タイマーの間隔をミリ秒単位で指定します。

*pClient*<br/>
ポインター、 [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)ハンドルがシグナル通知されたときに呼び出されるオブジェクトのインターフェイス。

*dwParam*<br/>
渡されるパラメーター [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)ハンドルがシグナル通知されたとき。

*phTimer*<br/>
[out]成功した場合、新しく作成した、タイマーを識別するハンドルを受け取るハンドル変数のアドレス。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)を介して呼び出される*pClient*タイマーが通知されます。

タイマー ハンドルを渡す*phTimer*に[CWorkerThread::RemoveHandle](#removehandle)タイマーを閉じます。

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

呼び出し[CWorkerThread::Shutdown](#shutdown)します。

##  <a name="getthreadhandle"></a>  CWorkerThread::GetThreadHandle

ワーカー スレッドのスレッドのハンドルを取得するには、このメソッドを呼び出します。

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>戻り値

ワーカー スレッドが初期化されていない場合は、スレッド ハンドルまたは NULL を返します。

##  <a name="getthreadid"></a>  CWorkerThread::GetThreadId

ワーカー スレッドのスレッド ID を取得するには、このメソッドを呼び出します。

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>戻り値

ワーカー スレッドが初期化されていない場合は、スレッド ID または NULL を返します。

##  <a name="initialize"></a>  CWorkerThread::Initialize

ワーカー スレッドを初期化するためには、このメソッドを呼び出します。

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>パラメーター

*pThread*<br/>
既存のワーカー スレッド。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

このメソッドは、作成後、または呼び出しの後に、オブジェクトを初期化するために呼び出す必要があります[CWorkerThread::Shutdown](#shutdown)します。

2 つ以上が`CWorkerThread`オブジェクトが同じワーカー スレッドを使用して、任意の引数には、そのオブジェクトへのポインターを渡すし渡さずにそれらのいずれかの初期化、`Initialize`他のメソッド。 ポインターを使用して初期化されるオブジェクトは、オブジェクトの初期化に使用する前にシャット ダウンする必要があります。

参照してください[CWorkerThread::Shutdown](#shutdown)については、既存のオブジェクトへのポインターを使用して初期化されるときに、そのメソッドの動作がどのように変化するか。

##  <a name="removehandle"></a>  CWorkerThread::RemoveHandle

ハンドルを待機可能オブジェクトの一覧から削除するには、このメソッドを呼び出します。

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>パラメーター

*hObject*<br/>
削除するハンドル。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

ハンドルが削除されたとき[IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle)に渡された関連付けられているオブジェクトで呼び出される[AddHandle](#addhandle)します。 この呼び出しが失敗した場合、 `CWorkerThread` 、Windows を呼び出す[CloseHandle](/windows/desktop/api/handleapi/nf-handleapi-closehandle)関数のハンドル。

##  <a name="shutdown"></a>  CWorkerThread::Shutdown

ワーカー スレッドをシャット ダウンするには、このメソッドを呼び出します。

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>パラメーター

*dwWait*<br/>
ワーカー スレッドをシャット ダウンするを待機するミリ秒単位の時間。 ATL_WORKER_THREAD_WAIT の既定値は 10 秒です。 Atlutil.h する前に、必要に応じて、このシンボルは、独自の値を定義できます。

### <a name="return-value"></a>戻り値

成功した場合、または場合など、エラー発生時のエラー HRESULT が S_OK を返します、タイムアウト値を*内部*を超えています。

### <a name="remarks"></a>Remarks

オブジェクトを再利用するには、呼び出す[CWorkerThread::Initialize](#initialize)このメソッドを呼び出した後。

呼び出して`Shutdown`別にポインターを使用して初期化されるオブジェクトで`CWorkerThread`オブジェクトが影響を与えませんし、常に S_OK を返します。

## <a name="see-also"></a>関連項目

[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[クラス](../../atl/reference/atl-classes.md)<br/>
[マルチ スレッド。ワーカー スレッドを作成します。](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient インターフェイス](../../atl/reference/iworkerthreadclient-interface.md)
