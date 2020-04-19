---
title: discard_block_engine クラス
ms.date: 11/04/2016
f1_keywords:
- random/std::discard_block_engine
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
ms.openlocfilehash: eb00945084affb2be9299953e5ca9352c56d3b32
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688106"
---
# <a name="discard_block_engine-class"></a>discard_block_engine クラス

ベースとなるエンジンから返された値を破棄することによってランダム シーケンスを生成します。

## <a name="syntax"></a>構文

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>パラメーター

*エンジン*の \
ベースのエンジンの型。

*P* \
**ブロック サイズ**。 各ブロックの値の数。

*R*\
**使用されるブロック**。 使用される各ブロックの値の数。 残りの部分は破棄されます (`P`  -  `R`)。 **前提条件**: `0 < R ≤ P`

## <a name="members"></a>メンバー

||||
|-|-|-|
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|

エンジンのメンバーの詳細については、[\<random>](../standard-library/random.md) をご覧ください。

## <a name="remarks"></a>Remarks

このクラステンプレートは、ベースエンジンによって返された値の一部を破棄することによって値を生成するエンジンアダプターを表します。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<random>

**名前空間:** std

## <a name="see-also"></a>関連項目

[\<random>](../standard-library/random.md)
