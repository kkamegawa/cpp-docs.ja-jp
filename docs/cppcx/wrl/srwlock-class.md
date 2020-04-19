---
title: SRWLock クラス
ms.date: 09/25/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock_
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::~SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
helpviewer_keywords:
- Microsoft::WRL::Wrappers::SRWLock class
- Microsoft::WRL::Wrappers::SRWLock::LockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::LockShared method
- Microsoft::WRL::Wrappers::SRWLock::SRWLock, constructor
- Microsoft::WRL::Wrappers::SRWLock::SRWLock_ data member
- Microsoft::WRL::Wrappers::SRWLock::~SRWLock, destructor
- Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::TryLockShared method
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
ms.openlocfilehash: 079f1abe652d8c1610a084f5e1158cc5798d61c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498288"
---
# <a name="srwlock-class"></a>SRWLock クラス

スリムリーダー/ライターロックを表します。

## <a name="syntax"></a>構文

```cpp
class SRWLock;
```

## <a name="remarks"></a>Remarks

スリムリーダー/ライターロックは、スレッド間のアクセスをオブジェクトまたはリソースに同期するために使用されます。 詳細については、「[同期関数](/windows/win32/Sync/synchronization-functions)」を参照してください。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

名前                | 説明
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | 排他モードで`SRWLock`取得されるオブジェクトのシノニム。
`SyncLockShared`    | 共有モードで`SRWLock`取得されるオブジェクトのシノニム。

### <a name="public-constructors"></a>パブリック コンストラクター

名前                                     | 説明
---------------------------------------- | --------------------------------------------------
[SRWLock:: SRWLock](#srwlock-constructor) | `SRWLock` クラスの新しいインスタンスを初期化します。
[SRWLock:: ~ SRWLock](#tilde-srwlock)      | `SRWLock`クラスのインスタンスを初期化解除します。

### <a name="public-methods"></a>パブリック メソッド

名前                                           | 説明
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock:: LockExclusive](#lockexclusive)       | 排他モード`SRWLock`でオブジェクトを取得します。
[SRWLock:: LockShared](#lockshared)             | 共有モード`SRWLock`でオブジェクトを取得します。
[SRWLock:: TryLockExclusive](#trylockexclusive) | 現在のオブジェクトまた`SRWLock`は指定された`SRWLock`オブジェクトに対して、排他モードでのオブジェクトの取得を試みます。
[SRWLock:: TryLockShared](#trylockshared)       | 現在のオブジェクトまた`SRWLock`は指定された`SRWLock`オブジェクトについて、共有モードのオブジェクトの取得を試みます。

### <a name="protected-data-member"></a>保護されるデータメンバー

名前                                      | 説明
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock:: SRWLock_](#srwlock-data-member) | 現在`SRWLock`のオブジェクトの基になるロック変数を格納します。

## <a name="inheritance-hierarchy"></a>継承階層

`SRWLock`

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers .h

**名前空間:** Microsoft:: WRL:: Wrapper

## <a name="tilde-srwlock"></a>SRWLock:: ~ SRWLock

`SRWLock`クラスのインスタンスを初期化解除します。

```cpp
~SRWLock();
```

## <a name="lockexclusive"></a>SRWLock:: LockExclusive

排他モード`SRWLock`でオブジェクトを取得します。

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>パラメーター

*lock*<br/>
`SRWLock`オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

排他モードのオブジェクト。 `SRWLock`

## <a name="lockshared"></a>SRWLock:: LockShared

共有モード`SRWLock`でオブジェクトを取得します。

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>パラメーター

*lock*<br/>
`SRWLock`オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

共有モードのオブジェクトです。 `SRWLock`

## <a name="srwlock-constructor"></a>SRWLock:: SRWLock

`SRWLock` クラスの新しいインスタンスを初期化します。

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>SRWLock:: SRWLock_

現在`SRWLock`のオブジェクトの基になるロック変数を格納します。

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>SRWLock:: TryLockExclusive

現在のオブジェクトまた`SRWLock`は指定された`SRWLock`オブジェクトに対して、排他モードでのオブジェクトの取得を試みます。 呼び出しが成功すると、呼び出し元のスレッドはロックの所有権を取得します。

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>パラメーター

*lock*<br/>
`SRWLock`オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

成功した場合`SRWLock` 、排他モードのオブジェクトと呼び出し元のスレッドは、ロックの所有権を取得します。 それ以外の`SRWLock`場合は、状態が無効であるオブジェクト。

## <a name="trylockshared"></a>SRWLock:: TryLockShared

現在のオブジェクトまた`SRWLock`は指定された`SRWLock`オブジェクトについて、共有モードのオブジェクトの取得を試みます。

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>パラメーター

*lock*<br/>
`SRWLock`オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

成功する`SRWLock`と、共有モードのオブジェクトと呼び出し元のスレッドが、ロックの所有権を取得します。 それ以外の`SRWLock`場合は、状態が無効であるオブジェクト。
