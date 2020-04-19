---
title: CComCriticalSection クラス
ms.date: 11/04/2016
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
ms.openlocfilehash: ee4ce32ed4ae04bc3b390af5cf104b8a0af599f8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497281"
---
# <a name="ccomcriticalsection-class"></a>CComCriticalSection クラス

このクラスには、クリティカルセクションオブジェクトの所有権を取得および解放するためのメソッドが用意されています。

## <a name="syntax"></a>構文

```
class CComCriticalSection
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComCriticalSection:: Init](#init)|クリティカルセクションオブジェクトを作成し、初期化します。|
|[CComCriticalSection::Lock](#lock)|クリティカルセクションオブジェクトの所有権を取得します。|
|[CComCriticalSection:: Term](#term)|クリティカルセクションオブジェクトによって使用されているシステムリソースを解放します。|
|[CComCriticalSection:: Unlock](#unlock)|クリティカルセクションオブジェクトの所有権を解放します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CComCriticalSection::m_sec](#m_sec)|CRITICAL_SECTION オブジェクトです。|

## <a name="remarks"></a>Remarks

`CComCriticalSection`はクラス[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)に似ていますが、クリティカルセクションを明示的に初期化して解放する必要がある点が異なります。

通常、 **typedef**名`CComCriticalSection` [CriticalSection](ccommultithreadmodel-class.md#criticalsection)を使用します。 この名前は`CComCriticalSection` 、 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)が使用されている場合に参照されます。

とを`Lock` 直接呼び出すよりも、このクラスを安全に使用する方法については、「[CComCritSecLock クラス](../../atl/reference/ccomcritseclock-class.md)」を参照してください。`Unlock`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcore .h

##  <a name="ccomcriticalsection"></a>CComCriticalSection::CComCriticalSection

コンストラクターです。

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>Remarks

[M_sec](#m_sec)データメンバーを NULL に設定します。

##  <a name="init"></a>  CComCriticalSection::Init

Win32 関数[InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection)を呼び出します。この関数は、 [m_sec](#m_sec)データメンバーに格納されている重要なセクションオブジェクトを初期化します。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合は E_OUTOFMEMORY または E_FAIL を返します。

##  <a name="lock"></a>  CComCriticalSection::Lock

Win32 関数[EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection)を呼び出します。この関数は、スレッドが[m_sec](#m_sec)データメンバーに格納されているクリティカルセクションオブジェクトの所有権を取得するまで待機します。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合は E_OUTOFMEMORY または E_FAIL を返します。

### <a name="remarks"></a>Remarks

クリティカルセクションオブジェクトは、 [Init](#init)メソッドを呼び出すことによって最初に初期化する必要があります。 保護されたコードの実行が完了したら、スレッドは[ロック解除](#unlock)を呼び出して、クリティカルセクションの所有権を解放する必要があります。

##  <a name="m_sec"></a>  CComCriticalSection::m_sec

すべて`CComCriticalSection`のメソッドで使用されるクリティカルセクションオブジェクトを格納します。

```
CRITICAL_SECTION m_sec;
```

##  <a name="term"></a>CComCriticalSection:: Term

Win32 関数[DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection)を呼び出します。この関数は、 [m_sec](#m_sec)データメンバーに格納されているクリティカルセクションオブジェクトによって使用されているすべてのリソースを解放します。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>戻り値

S_OK を返します。

### <a name="remarks"></a>Remarks

`Term`が呼び出されると、クリティカルセクションを同期に使用できなくなります。

##  <a name="unlock"></a>CComCriticalSection:: Unlock

Win32 関数[LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection)を呼び出します。この関数は、 [m_sec](#m_sec)データメンバーに格納されている重要なセクションオブジェクトの所有権を解放します。

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>戻り値

S_OK を返します。

### <a name="remarks"></a>Remarks

最初に所有権を取得するには、スレッドが[ロック](#lock)メソッドを呼び出す必要があります。 へ`Lock`の各呼び出しでは、クリティカル`Unlock`セクションの所有権を解放するために、対応する呼び出しが必要です。

## <a name="see-also"></a>関連項目

[CComFakeCriticalSection クラス](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[CComCritSecLock クラス](../../atl/reference/ccomcritseclock-class.md)
