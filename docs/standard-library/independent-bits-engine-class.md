---
title: independent_bits_engine クラス
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: 28c9301d270ef516a1acc59f6ab06f0e61a1c9c5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687938"
---
# <a name="independent_bits_engine-class"></a>independent_bits_engine クラス

ベースのエンジンから返された値のビットを再パックすることで、指定したビット数で数値のランダム シーケンスを生成します。

## <a name="syntax"></a>構文

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>パラメーター

*エンジン*の \
ベースのエンジンの型。

*W* \
**ワード サイズ**。 生成される各数値のサイズ (ビット数)。 **前提条件**: `0 < W ≤ numeric_limits<UIntType>::digits`

*Uinttype* \
結果を表す符号なし整数型。 使用可能な型については、「[\<random>](../standard-library/random.md)」を参照してください。

## <a name="members"></a>メンバー

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

エンジンのメンバーの詳細については、[\<random>](../standard-library/random.md) をご覧ください。

## <a name="remarks"></a>Remarks

このクラステンプレートは、ベースエンジンによって返される値からビットを再パックして値を生成する*エンジンアダプター*を記述し、その結果、 *W*ビット値になります。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<random>

**名前空間:** std

## <a name="see-also"></a>関連項目

[\<random>](../standard-library/random.md)
