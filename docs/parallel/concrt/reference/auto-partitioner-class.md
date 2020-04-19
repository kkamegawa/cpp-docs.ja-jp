---
title: auto_partitioner クラス
ms.date: 11/04/2016
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
ms.openlocfilehash: 4d1d8f19069412240de8e9d69cdcfb34618f2796
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142867"
---
# <a name="auto_partitioner-class"></a>auto_partitioner クラス

`auto_partitioner` クラスは、反復処理する範囲を分割するために、既定のメソッド `parallel_for`、`parallel_for_each`、および `parallel_transform` の使用を表します。 このパーティション分割方法では、負荷分散と反復処理ごとのキャンセルに対して範囲の盗用が使用されます。

## <a name="syntax"></a>構文

```cpp
class auto_partitioner;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[auto_partitioner](#ctor)|`auto_partitioner` オブジェクトを構築します。|
|[~ auto_partitioner デストラクター](#dtor)|`auto_partitioner` オブジェクトを破棄します。|

## <a name="inheritance-hierarchy"></a>継承階層

`auto_partitioner`

## <a name="requirements"></a>要件

**ヘッダー:** ppl

**名前空間:** concurrency

## <a name="dtor"></a>~ auto_partitioner

`auto_partitioner` オブジェクトを破棄します。

```cpp
~auto_partitioner();
```

## <a name="ctor"></a>auto_partitioner

`auto_partitioner` オブジェクトを構築します。

```cpp
auto_partitioner();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
