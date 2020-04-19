---
title: CComApartment クラス
ms.date: 11/04/2016
f1_keywords:
- CComApartment
- ATLBASE/ATL::CComApartment
- ATLBASE/ATL::CComApartment::CComApartment
- ATLBASE/ATL::CComApartment::Apartment
- ATLBASE/ATL::CComApartment::GetLockCount
- ATLBASE/ATL::CComApartment::Lock
- ATLBASE/ATL::CComApartment::Unlock
- ATLBASE/ATL::CComApartment::m_dwThreadID
- ATLBASE/ATL::CComApartment::m_hThread
- ATLBASE/ATL::CComApartment::m_nLockCnt
helpviewer_keywords:
- apartments in ATL EXE modules
- CComApartment class
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
ms.openlocfilehash: 5f4c7fc356e61210e9b99bf9989b1bb3f0abc98a
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821676"
---
# <a name="ccomapartment-class"></a>CComApartment クラス

このクラスは、スレッドプールされた EXE モジュールでアパートメントを管理するためのサポートを提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CComApartment
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|[名前]|説明|
|----------|-----------------|
|[CComApartment::CComApartment](#ccomapartment)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|[名前]|説明|
|----------|-----------------|
|[CComApartment::Apartment](#apartment)|スレッドの開始アドレスをマークします。|
|[CComApartment::GetLockCount](#getlockcount)|スレッドの現在のロック数を返します。|
|[CComApartment::Lock](#lock)|スレッドのロックカウントをインクリメントします。|
|[CComApartment:: Unlock](#unlock)|スレッドのロックカウントをデクリメントします。|

### <a name="public-data-members"></a>パブリック データ メンバー

|[名前]|説明|
|----------|-----------------|
|[CComApartment:: m_dwThreadID](#m_dwthreadid)|スレッドの識別子を格納します。|
|[CComApartment:: m_hThread](#m_hthread)|スレッドのハンドルを格納します。|
|[CComApartment::m_nLockCnt](#m_nlockcnt)|スレッドの現在のロック数を格納します。|

## <a name="remarks"></a>Remarks

`CComApartment` は、スレッドプールされた EXE モジュールでアパートメントを管理するために[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)によって使用されます。 `CComApartment` には、スレッドのロックカウントをインクリメントおよびデクリメントするためのメソッドが用意されています。

## <a name="requirements"></a>要件

**ヘッダー:** atlbase. h

##  <a name="apartment"></a>  CComApartment::Apartment

スレッドの開始アドレスをマークします。

```
DWORD Apartment();
```

### <a name="return-value"></a>戻り値

常に 0 です。

### <a name="remarks"></a>Remarks

[CComAutoThreadModule:: Init](../../atl/reference/ccomautothreadmodule-class.md#init)時に自動的に設定されます。

##  <a name="ccomapartment"></a>CComApartment::CComApartment

コンストラクターです。

```
CComApartment();
```

### <a name="remarks"></a>Remarks

`CComApartment` のデータメンバー [m_nLockCnt](#m_nlockcnt)と[m_hThread](#m_hthread)を初期化します。

##  <a name="getlockcount"></a>  CComApartment::GetLockCount

スレッドの現在のロック数を返します。

```
LONG GetLockCount();
```

### <a name="return-value"></a>戻り値

スレッドのロック数。

##  <a name="lock"></a>  CComApartment::Lock

スレッドのロックカウントをインクリメントします。

```
LONG Lock();
```

### <a name="return-value"></a>戻り値

診断またはテストに役立つ可能性のある値。

### <a name="remarks"></a>Remarks

[CComAutoThreadModule:: Lock](../../atl/reference/ccomautothreadmodule-class.md#lock)によって呼び出されます。

スレッドのロックカウントは統計的な目的で使用されます。

##  <a name="m_dwthreadid"></a>CComApartment:: m_dwThreadID

スレッドの識別子を格納します。

```
DWORD m_dwThreadID;
```

##  <a name="m_hthread"></a>  CComApartment::m_hThread

スレッドのハンドルを格納します。

```
HANDLE m_hThread;
```

##  <a name="m_nlockcnt"></a>  CComApartment::m_nLockCnt

スレッドの現在のロック数を格納します。

```
LONG m_nLockCnt;
```

##  <a name="unlock"></a>  CComApartment::Unlock

スレッドのロックカウントをデクリメントします。

```
LONG Unlock();
```

### <a name="return-value"></a>戻り値

診断またはテストに役立つ可能性のある値。

### <a name="remarks"></a>Remarks

[CComAutoThreadModule:: Unlock](../../atl/reference/ccomautothreadmodule-class.md#lock)によって呼び出されます。

スレッドのロックカウントは統計的な目的で使用されます。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
