---
title: CComCritSecLock クラス
ms.date: 11/04/2016
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
ms.openlocfilehash: 045e64504707fa8978c8236b376037d9f57bf12c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259808"
---
# <a name="ccomcritseclock-class"></a>CComCritSecLock クラス

このクラスは、ロックとクリティカル セクション オブジェクトをロック解除のためのメソッドを提供します。

## <a name="syntax"></a>構文

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>パラメーター

*TLock*<br/>
ロックおよびロック解除するオブジェクト。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComCritSecLock::CComCritSecLock](#ctor)|コンストラクターです。|
|[CComCritSecLock:: ~ CComCritSecLock](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComCritSecLock::Lock](#lock)|クリティカル セクション オブジェクトをロックするには、このメソッドを呼び出します。|
|[CComCritSecLock::Unlock](#unlock)|クリティカル セクション オブジェクトのロックを解除するには、このメソッドを呼び出します。|

## <a name="remarks"></a>Remarks

ロックおよびより安全な方法でオブジェクトをロック解除をこのクラスを使用して、 [CComCriticalSection クラス](../../atl/reference/ccomcriticalsection-class.md)または[CComAutoCriticalSection クラス](../../atl/reference/ccomautocriticalsection-class.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="ctor"></a>  CComCritSecLock::CComCritSecLock

コンストラクターです。

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>パラメーター

*cs*<br/>
クリティカル セクション オブジェクト。

*bInitialLock*<br/>
最初のロックの状態: **true**ロックされていることを意味します。

### <a name="remarks"></a>Remarks

クリティカル セクション オブジェクトを初期化します。

##  <a name="dtor"></a>  CComCritSecLock:: ~ CComCritSecLock

デストラクターです。

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>Remarks

クリティカル セクション オブジェクトのロックを解除します。

##  <a name="lock"></a>  CComCritSecLock::Lock

クリティカル セクション オブジェクトをロックするには、このメソッドを呼び出します。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>戻り値

オブジェクトが正常にロックされた場合、S_OK またはエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

オブジェクトが既にロックされているデバッグ ビルドでアサート エラーが発生します。

##  <a name="unlock"></a>  CComCritSecLock::Unlock

クリティカル セクション オブジェクトのロックを解除するには、このメソッドを呼び出します。

```
void Unlock() throw();
```

### <a name="remarks"></a>Remarks

オブジェクトは、既にロックされているが、デバッグ ビルドでアサート エラーが発生します。

## <a name="see-also"></a>関連項目

[CComCriticalSection クラス](../../atl/reference/ccomcriticalsection-class.md)<br/>
[CComAutoCriticalSection クラス](../../atl/reference/ccomautocriticalsection-class.md)
