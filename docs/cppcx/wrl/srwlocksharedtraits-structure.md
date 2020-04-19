---
title: SRWLockSharedTraits 構造体
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock method
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
ms.openlocfilehash: af567fd333854519df4543ad24084e52cda4d96e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383283"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits 構造体

一般的な特性について説明します、`SRWLock`共有ロック モードでのクラス。

## <a name="syntax"></a>構文

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

名前   | 説明
------ | --------------------------------------------------------------------------
`Type` | ポインターのシノニム、 [SRWLOCK](srwlock-class.md)クラス。

### <a name="public-methods"></a>パブリック メソッド

名前                                                     | 説明
-------------------------------------------------------- | -----------------------------------------------------------------
[SRWLockSharedTraits::GetInvalidValue](#getinvalidvalue) | 取得、`SRWLockSharedTraits`オブジェクトは常に有効です。
[Srwlocksharedtraits::unlock](#unlock)                   | 指定したの排他的制御を解放`SRWLock`オブジェクト。

## <a name="inheritance-hierarchy"></a>継承階層

`SRWLockSharedTraits`

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers.h

**名前空間:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>SRWLockSharedTraits::GetInvalidValue

取得、`SRWLockSharedTraits`オブジェクトは常に有効です。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>戻り値

識別するハンドルを`SRWLockSharedTraits`オブジェクト。

## <a name="unlock"></a>Srwlocksharedtraits::unlock

指定したの排他的制御を解放`SRWLock`オブジェクト。

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>パラメーター

*srwlock*<br/>
識別するハンドルを`SRWLock`オブジェクト。
