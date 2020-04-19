---
title: Semaphore クラス
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Semaphore
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Semaphore class
- Microsoft::WRL::Wrappers::Semaphore::Lock method
- Microsoft::WRL::Wrappers::Semaphore::operator= operator
- Microsoft::WRL::Wrappers::Semaphore::Semaphore, constructor
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
ms.openlocfilehash: 10357bb1cd46a33a8d4090c1ccc30050584d1816
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403135"
---
# <a name="semaphore-class"></a>Semaphore クラス

ユーザーの数に制限をサポートできる共有リソースを制御する同期オブジェクトを表します。

## <a name="syntax"></a>構文

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

名前       | 説明
---------- | ------------------------------------------------------
`SyncLock` | 同期ロックをサポートするクラスのシノニムです。

### <a name="public-constructors"></a>パブリック コンストラクター

名前                               | 説明
---------------------------------- | ----------------------------------------------------
[Semaphore::semaphore](#semaphore) | `Semaphore` クラスの新しいインスタンスを初期化します。

### <a name="public-methods"></a>パブリック メソッド

名前                     | 説明
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[Semaphore::Lock](#lock) | シグナルの状態にある現在のオブジェクトまたは指定したハンドルに関連付けられたオブジェクトまでの待機、または指定されたタイムアウト期間が経過しました。

### <a name="public-operators"></a>パブリック演算子

名前                                     | 説明
---------------------------------------- | ---------------------------------------------------------------------------------------
[Semaphore::operator=](#operator-assign) | 指定したハンドルの移動、`Semaphore`現在オブジェクト`Semaphore`オブジェクト。

## <a name="inheritance-hierarchy"></a>継承階層

`Semaphore`

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers.h

**名前空間:** Microsoft::WRL::Wrappers

## <a name="lock"></a>Semaphore::Lock

現在のオブジェクトまでの待機、または`Semaphore`オブジェクトに関連付けられている指定したハンドルがシグナル状態で、または指定されたタイムアウト期間が経過しました。

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>パラメーター

*(ミリ秒)*<br/>
タイムアウト間隔 (ミリ秒単位)。 既定値は、INFINITE で、無期限に待機します。

*h*<br/>
識別するハンドルを`Semaphore`オブジェクト。

### <a name="return-value"></a>戻り値

`Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`。

## <a name="operator-assign"></a>Semaphore::operator=

指定したハンドルの移動、`Semaphore`現在オブジェクト`Semaphore`オブジェクト。

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
右辺値参照を`Semaphore`オブジェクト。

### <a name="return-value"></a>戻り値

現在への参照を`Semaphore`オブジェクト。

## <a name="semaphore"></a>Semaphore::semaphore

`Semaphore` クラスの新しいインスタンスを初期化します。

```cpp
explicit Semaphore(
   HANDLE h
);

WRL_NOTHROW Semaphore(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
ハンドルまたはへの右辺値参照を`Semaphore`オブジェクト。
