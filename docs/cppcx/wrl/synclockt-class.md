---
title: SyncLockT クラス
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::sync_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockT class
- Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockT::sync_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT, constructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT, destructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock method
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
ms.openlocfilehash: d27e6ba8601d0e822113bf3a4a65269c89437271
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398161"
---
# <a name="synclockt-class"></a>SyncLockT クラス

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>パラメーター

*SyncTraits*<br/>
この型は、リソースの所有権を取得できます。

## <a name="remarks"></a>Remarks

排他的に使用できる型を表すか、リソースの所有権を共有します。

`SyncLockT`クラスの使用などの実装に役立つ、 [SRWLock](srwlock-class.md)クラス。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

名前                                      | 説明
----------------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt)        | `SyncLockT` クラスの新しいインスタンスを初期化します。
[SyncLockT::~SyncLockT](#tilde-synclockt) | インスタンスを初期化解除、`SyncLockT`クラス。

### <a name="protected-constructors"></a>プロテクト コンストラクター

名前                               | 説明
---------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt) | `SyncLockT` クラスの新しいインスタンスを初期化します。

### <a name="public-methods"></a>パブリック メソッド

名前                             | 説明
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLockT::IsLocked](#islocked) | 示すかどうか、現在`SyncLockT`リソースを所有するオブジェクトです。 つまり、`SyncLockT`オブジェクトが*ロック*します。
[Synclockt::unlock](#unlock)     | 現在保持されているリソースの制御を解放`SyncLockT`オブジェクトが存在する場合。

### <a name="protected-data-members"></a>プロテクト データ メンバー

名前                      | 説明
------------------------- | -------------------------------------------------------------------
[SyncLockT::sync_](#sync) | によって表される、基になるリソースを保持、`SyncLockT`クラス。

## <a name="inheritance-hierarchy"></a>継承階層

`SyncLockT`

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers.h

**名前空間:** Microsoft::WRL::Wrappers::Details

## <a name="tilde-synclockt"></a>SyncLockT::~SyncLockT

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
~SyncLockT();
```

### <a name="remarks"></a>Remarks

インスタンスを初期化解除、`SyncLockT`クラス。

このデストラクターの現在のロックを解除も`SyncLockT`インスタンス。

## <a name="islocked"></a>SyncLockT::IsLocked

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>戻り値

**true**場合、`SyncLockT`オブジェクトがロックされている場合はそれ以外の場合、 **false**します。

### <a name="remarks"></a>Remarks

示すかどうか、現在`SyncLockT`リソースを所有するオブジェクトです。 つまり、`SyncLockT`オブジェクトが*ロック*します。

## <a name="sync"></a>SyncLockT::sync_

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>Remarks

によって表される、基になるリソースを保持、`SyncLockT`クラス。

## <a name="synclockt"></a>SyncLockT::SyncLockT

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>パラメーター

*other*<br/>
別の右辺値参照`SyncLockT`オブジェクト。

*sync*<br/>
別の参照`SyncLockWithStatusT`オブジェクト。

### <a name="remarks"></a>Remarks

`SyncLockT` クラスの新しいインスタンスを初期化します。

最初のコンス トラクターは、現在`SyncLockT`から別のオブジェクト`SyncLockT`パラメーターで指定されたオブジェクト*他*、し、もう一方を無効に`SyncLockT`オブジェクト。 2 番目のコンス トラクターは`protected`、し、現在初期化`SyncLockT`オブジェクトを無効な状態にします。

## <a name="unlock"></a>Synclockt::unlock

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
void Unlock();
```

### <a name="remarks"></a>Remarks

現在保持されているリソースの制御を解放`SyncLockT`オブジェクトが存在する場合。
