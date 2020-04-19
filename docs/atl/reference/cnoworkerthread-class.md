---
title: CNoWorkerThread クラス
ms.date: 11/04/2016
f1_keywords:
- CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread::AddHandle
- ATLUTIL/ATL::CNoWorkerThread::AddTimer
- ATLUTIL/ATL::CNoWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CNoWorkerThread::GetThreadId
- ATLUTIL/ATL::CNoWorkerThread::Initialize
- ATLUTIL/ATL::CNoWorkerThread::RemoveHandle
- ATLUTIL/ATL::CNoWorkerThread::Shutdown
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
ms.openlocfilehash: fcd103283738ce7d573faa2fb1025ee2af642021
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258495"
---
# <a name="cnoworkerthread-class"></a>CNoWorkerThread クラス

引数としてこのクラスを使用して、`MonitorClass`動的キャッシュのメンテナンスを無効にしたい場合はキャッシュ クラスをテンプレート パラメーター。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CNoWorkerThread
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CNoWorkerThread::AddHandle](#addhandle)|非機能的に同等[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)します。|
|[CNoWorkerThread::AddTimer](#addtimer)|非機能的に同等[CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer)します。|
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|非機能的に同等[CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle)します。|
|[CNoWorkerThread::GetThreadId](#getthreadid)|非機能的に同等[CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)します。|
|[CNoWorkerThread::Initialize](#initialize)|非機能的に同等[CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize)します。|
|[CNoWorkerThread::RemoveHandle](#removehandle)|非機能的に同等[CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle)します。|
|[CNoWorkerThread::Shutdown](#shutdown)|非機能的に同等[CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown)します。|

## <a name="remarks"></a>Remarks

このクラスは、同じパブリック インターフェイスとして[CWorkerThread](../../atl/reference/cworkerthread-class.md)します。 提供するこのインターフェイスが必要です、`MonitorClass`キャッシュ クラスをテンプレート パラメーター。

このクラスのメソッドは、何もしない実装されます。 常に HRESULT を返すメソッドは、S_OK を返しを常に、ハンドルまたはスレッドの ID を返すメソッドは 0 を返します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlutil.h

##  <a name="addhandle"></a>  CNoWorkerThread::AddHandle

非機能的に同等[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)します。

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>戻り値

常に S_OK を返します。

### <a name="remarks"></a>Remarks

このクラスによって提供された実装では、何も行われません。

##  <a name="addtimer"></a>  CNoWorkerThread::AddTimer

非機能的に同等[CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer)します。

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>戻り値

常に S_OK を返します。

### <a name="remarks"></a>Remarks

このクラスによって提供された実装では、何も行われません。

##  <a name="getthreadhandle"></a>  CNoWorkerThread::GetThreadHandle

非機能的に同等[CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle)します。

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>戻り値

常に NULL が返されます。

### <a name="remarks"></a>Remarks

このクラスによって提供された実装では、何も行われません。

##  <a name="getthreadid"></a>  CNoWorkerThread::GetThreadId

非機能的に同等[CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)します。

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>戻り値

常に 0 を返します。

### <a name="remarks"></a>Remarks

このクラスによって提供された実装では、何も行われません。

##  <a name="initialize"></a>  CNoWorkerThread::Initialize

非機能的に同等[CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize)します。

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>戻り値

常に S_OK を返します。

### <a name="remarks"></a>Remarks

このクラスによって提供された実装では、何も行われません。

##  <a name="removehandle"></a>  CNoWorkerThread::RemoveHandle

非機能的に同等[CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle)します。

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>戻り値

常に S_OK を返します。

### <a name="remarks"></a>Remarks

このクラスによって提供された実装では、何も行われません。

##  <a name="shutdown"></a>  CNoWorkerThread::Shutdown

非機能的に同等[CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown)します。

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>戻り値

常に S_OK を返します。

### <a name="remarks"></a>Remarks

このクラスによって提供された実装では、何も行われません。
