---
title: simple_partitioner クラス
ms.date: 11/04/2016
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
ms.openlocfilehash: 503f36b90c5eb3319f9aa2d56528172ffa95bb11
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142504"
---
# <a name="simple_partitioner-class"></a>simple_partitioner クラス

`simple_partitioner` クラスは、`parallel_for` によって反復処理される範囲の静的パーティション分割を表します。 パーティショナーは範囲をチャンクに分割します。各チャンクには、少なくともチャンク サイズによって指定された数のイテレーションが含まれます。

## <a name="syntax"></a>構文

```cpp
class simple_partitioner;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[simple_partitioner](#ctor)|`simple_partitioner` オブジェクトを構築します。|
|[~ simple_partitioner デストラクター](#dtor)|`simple_partitioner` オブジェクトを破棄します。|

## <a name="inheritance-hierarchy"></a>継承階層

`simple_partitioner`

## <a name="requirements"></a>［要件］

**ヘッダー:** ppl

**名前空間:** concurrency

## <a name="dtor"></a>~ simple_partitioner

`simple_partitioner` オブジェクトを破棄します。

```cpp
~simple_partitioner();
```

## <a name="ctor"></a>simple_partitioner

`simple_partitioner` オブジェクトを構築します。

```cpp
explicit simple_partitioner(_Size_type _Chunk_size);
```

### <a name="parameters"></a>パラメーター

*_Chunk_size*<br/>
最小パーティションサイズ。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
