---
title: affinity_partitioner クラス
ms.date: 11/04/2016
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
ms.openlocfilehash: 0ae6bbee49d1b8873190a7054e55f65b40b31b13
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142874"
---
# <a name="affinity_partitioner-class"></a>affinity_partitioner クラス

`affinity_partitioner` クラスは `static_partitioner` クラスに似ていますが、ワーカー スレッドへのマッピングのサブ範囲の選択によってキャッシュの関係が向上します。 同じデータ セットに対してループ処理が再実行されるときにパフォーマンスを大幅に向上させることができ、データはキャッシュに収まります。 データの局所性のメリットを利用するには、特定のデータ セットに対して実行される並列ループの以降のイテレーションで、同じ `affinity_partitioner` オブジェクトを使用する必要があります。

## <a name="syntax"></a>構文

```cpp
class affinity_partitioner;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[affinity_partitioner](#ctor)|`affinity_partitioner` オブジェクトを構築します。|
|[~ affinity_partitioner デストラクター](#dtor)|`affinity_partitioner` オブジェクトを破棄します。|

## <a name="inheritance-hierarchy"></a>継承階層

`affinity_partitioner`

## <a name="requirements"></a>［要件］

**ヘッダー:** ppl

**名前空間:** concurrency

## <a name="dtor"></a>~ affinity_partitioner

`affinity_partitioner` オブジェクトを破棄します。

```cpp
~affinity_partitioner();
```

## <a name="ctor"></a>affinity_partitioner

`affinity_partitioner` オブジェクトを構築します。

```cpp
affinity_partitioner();
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
