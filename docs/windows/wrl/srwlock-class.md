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
ms.openlocfilehash: 6d4a504d9465c858af59a88cf0ef611bf88c3fde
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336525"
---
# <a name="srwlock-class"></a>SRWLock クラス

スリム リーダー/ライター ロックを表します。

## <a name="syntax"></a>構文

```cpp
class SRWLock;
```

## <a name="remarks"></a>Remarks

スリム リーダー/ライター ロックは、オブジェクトやリソースをスレッド間でのアクセスを同期に使用されます。 詳細については、次を参照してください。[同期関数](/windows/desktop/Sync/synchronization-functions)します。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

名前                | 説明
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | シノニム、`SRWLock`排他モードで取得したオブジェクト。
`SyncLockShared`    | シノニム、`SRWLock`共有モードで取得したオブジェクト。

### <a name="public-constructors"></a>パブリック コンストラクター

名前                                     | 説明
---------------------------------------- | --------------------------------------------------
[Srwlock::srwlock](#srwlock-constructor) | `SRWLock` クラスの新しいインスタンスを初期化します。
[SRWLock:: ~ SRWLock](#tilde-srwlock)      | インスタンスを初期化解除、`SRWLock`クラス。

### <a name="public-methods"></a>パブリック メソッド

名前                                           | 説明
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | 取得、`SRWLock`排他モードでのオブジェクト。
[SRWLock::LockShared](#lockshared)             | 取得、`SRWLock`共有モードでのオブジェクト。
[SRWLock::TryLockExclusive](#trylockexclusive) | 取得を試みる、`SRWLock`オブジェクトの現在または指定された排他モードで`SRWLock`オブジェクト。
[SRWLock::TryLockShared](#trylockshared)       | 取得を試みる、`SRWLock`オブジェクトの現在または指定した共有モードで`SRWLock`オブジェクト。

### <a name="protected-data-member"></a>保護されたデータ メンバー

名前                                      | 説明
----------------------------------------- | -----------------------------------------------------------------------
[Srwlock::srwlock _](#srwlock-data-member) | 現在の基になるロック変数が含まれる`SRWLock`オブジェクト。

## <a name="inheritance-hierarchy"></a>継承階層

`SRWLock`

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers.h

**名前空間:** Microsoft::WRL::Wrappers

## <a name="tilde-srwlock"></a>SRWLock:: ~ SRWLock

インスタンスを初期化解除、`SRWLock`クラス。

```cpp
~SRWLock();
```

## <a name="lockexclusive"></a>SRWLock::LockExclusive

取得、`SRWLock`排他モードでのオブジェクト。

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>パラメーター

*lock*<br/>
ポインター、`SRWLock`オブジェクト。

### <a name="return-value"></a>戻り値

`SRWLock`排他モードでのオブジェクト。

## <a name="lockshared"></a>SRWLock::LockShared

取得、`SRWLock`共有モードでのオブジェクト。

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>パラメーター

*lock*<br/>
ポインター、`SRWLock`オブジェクト。

### <a name="return-value"></a>戻り値

`SRWLock`共有モードでのオブジェクト。

## <a name="srwlock-constructor"></a>Srwlock::srwlock

`SRWLock` クラスの新しいインスタンスを初期化します。

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>Srwlock::srwlock _

現在の基になるロック変数が含まれる`SRWLock`オブジェクト。

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>Srwlock::trylockexclusive

取得を試みる、`SRWLock`オブジェクトの現在または指定された排他モードで`SRWLock`オブジェクト。 呼び出しが成功した場合、呼び出し元のスレッドはロックの所有権を取得します。

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>パラメーター

*lock*<br/>
ポインター、`SRWLock`オブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、`SRWLock`排他モードと呼び出し元のスレッド内のオブジェクトは、ロックの所有権を取得します。 それ以外の場合、`SRWLock`オブジェクトの状態が無効です。

## <a name="trylockshared"></a>SRWLock::TryLockShared

取得を試みる、`SRWLock`オブジェクトの現在または指定した共有モードで`SRWLock`オブジェクト。

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>パラメーター

*lock*<br/>
ポインター、`SRWLock`オブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、`SRWLock`共有モードと呼び出し元のスレッド内のオブジェクトは、ロックの所有権を取得します。 それ以外の場合、`SRWLock`オブジェクトの状態が無効です。
