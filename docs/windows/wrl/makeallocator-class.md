---
title: MakeAllocator クラス
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
- implements/Microsoft::WRL::Details::MakeAllocator::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
helpviewer_keywords:
- Microsoft::WRL::Details::MakeAllocator class
- Microsoft::WRL::Details::MakeAllocator::Allocate method
- Microsoft::WRL::Details::MakeAllocator::Detach method
- Microsoft::WRL::Details::MakeAllocator::MakeAllocator, constructor
- Microsoft::WRL::Details::MakeAllocator::~MakeAllocator, destructor
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
ms.openlocfilehash: 805f0c09b0490d8cec1a0be96dcb1fc99a051371
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336450"
---
# <a name="makeallocator-class"></a>MakeAllocator クラス

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template<
    typename T,
    bool hasWeakReferenceSupport =
          !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,
                        T)
>
class MakeAllocator;

template<typename T>
class MakeAllocator<T, false>;

template<typename T>
class MakeAllocator<T, true>;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
型の名前。

*hasWeakReferenceSupport*<br/>
**true**弱い参照は; をサポートするオブジェクトのメモリを割り当てられません。**false**弱い参照をサポートしていないオブジェクトのメモリを割り当てられません。

## <a name="remarks"></a>Remarks

弱い参照のサポートの有無のアクティブ化可能なクラスのメモリを割り当てます。

上書き、`MakeAllocator`ユーザー定義のメモリ割り当てモデルを実装するクラス。

`MakeAllocator` 通常の構築時にオブジェクトをスローした場合は、メモリ リークを防ぐために使用されます。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

名前                                                  | 説明
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator::MakeAllocator](#makeallocator)        | `MakeAllocator` クラスの新しいインスタンスを初期化します。
[MakeAllocator::~MakeAllocator](#tilde-makeallocator) | 現在のインスタンスの初期化を解除、`MakeAllocator`クラス。

### <a name="public-methods"></a>パブリック メソッド

名前                                 | 説明
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator::Allocate](#allocate) | メモリを割り当て、現在のそれに`MakeAllocator`オブジェクト。
[MakeAllocator::Detach](#detach)     | によって割り当てられたメモリの関連付けを解除、 [Allocate](#allocate)メソッドは、現在から`MakeAllocator`オブジェクト。

## <a name="inheritance-hierarchy"></a>継承階層

`MakeAllocator`

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::WRL::Details

## <a name="allocate"></a>MakeAllocator::Allocate

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>戻り値

成功した場合、割り当てられたメモリ; へのポインターそれ以外の場合、`nullptr`します。

### <a name="remarks"></a>Remarks

メモリを割り当て、現在のそれに`MakeAllocator`オブジェクト。

割り当てられたメモリのサイズは、現在指定された型のサイズ`MakeAllocator`テンプレート パラメーター。

だけをオーバーライドする必要がある開発者、`Allocate()`さまざまなメモリの割り当てモデルを実装するメソッド。

## <a name="detach"></a>MakeAllocator::Detach

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>Remarks

によって割り当てられたメモリの関連付けを解除、 [Allocate](#allocate)メソッドは、現在から`MakeAllocator`オブジェクト。

呼び出す場合`Detach()`、によって提供されるメモリの削除を担当、`Allocate`メソッド。

## <a name="makeallocator"></a>MakeAllocator::MakeAllocator

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
MakeAllocator();
```

### <a name="remarks"></a>Remarks

`MakeAllocator` クラスの新しいインスタンスを初期化します。

## <a name="tilde-makeallocator"></a>MakeAllocator:: ~ MakeAllocator

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>Remarks

現在のインスタンスの初期化を解除、`MakeAllocator`クラス。

このデストラクターは必要な場合も、基になる割り当てられたメモリを削除します。
