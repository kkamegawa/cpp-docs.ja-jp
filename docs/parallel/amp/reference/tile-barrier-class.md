---
title: tile_barrier クラス
ms.date: 03/27/2019
f1_keywords:
- tile_barrier
- AMP/tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::wait
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_all_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_global_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_tile_static_memory_fence
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
ms.openlocfilehash: 757309a10da3e6d1c9c053430cce2cf603380b1f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127765"
---
# <a name="tile_barrier-class"></a>tile_barrier クラス

`wait` メソッドを使用してスレッド グループ (タイル) で実行されているスレッドの実行を同期します。 ランタイムのみがこのクラスをインスタンス化できます。

## <a name="syntax"></a>構文

```cpp
class tile_barrier;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[tile_barrier コンストラクター](#ctor)|`tile_barrier` クラスの新しいインスタンスを初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[待機](#wait)|タイルのすべてのスレッドの待機が完了するまで、スレッド グループ (タイル) のすべてのスレッドの実行を停止するように指示します。|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|すべてのメモリ アクセスが完了し、タイルのすべてのスレッドがこの呼び出しに到達するまで、タイルのすべてのスレッドの実行をブロックします。|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|すべてのグローバル メモリ アクセスが完了し、タイルのすべてのスレッドがこの呼び出しに到達するまで、タイルのすべてのスレッドの実行をブロックします。|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|すべての `tile_static` メモリ アクセスが完了し、タイルのすべてのスレッドがこの呼び出しに到達するまで、タイルのすべてのスレッドの実行をブロックします。|

## <a name="inheritance-hierarchy"></a>継承階層

`tile_barrier`

## <a name="requirements"></a>［要件］

**ヘッダー:** amp.h

**名前空間:** Concurrency

## <a name="ctor"></a>tile_barrier コンストラクター

既存のインスタンスをコピーして、クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Other*<br/>
コピーする `tile_barrier` オブジェクト。

## <a name="wait"></a>wait

タイル内のすべてのスレッドが待機を終了するまで、スレッドグループ (タイル) 内のすべてのスレッドが実行を停止するように指示します。

### <a name="syntax"></a>構文

```cpp
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence

タイルのすべてのスレッドがこの呼び出しに到達するまで、タイルのすべてのスレッドの実行をブロックします。 これによって、すべてのメモリ アクセスがスレッド タイルの他のスレッドから参照でき、プログラムの順序で実行されます。

### <a name="syntax"></a>構文

```cpp
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewait_with_global_memory_fence-wait_with_global_memory_fence"></a><a name="wait_with_global_memory_fence"> wait_with_global_memory_fence

タイルのすべてのスレッドがこの呼び出しに到達するまで、タイルのすべてのスレッドの実行をブロックします。 これによって、すべてのグローバル メモリ アクセスがスレッド タイルの他のスレッドから参照でき、プログラムの順序で実行されます。

### <a name="syntax"></a>構文

```cpp
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewait_with_tile_static_memory_fence-wait_with_tile_static_memory_fence"></a><a name="wait_with_tile_static_memory_fence"> wait_with_tile_static_memory_fence

タイルのすべてのスレッドがこの呼び出しに到達するまで、タイルのすべてのスレッドの実行をブロックします。 これにより、`tile_static` のメモリアクセスがスレッドタイルの他のスレッドから参照でき、プログラムの順序で実行されます。

### <a name="syntax"></a>構文

```cpp
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
