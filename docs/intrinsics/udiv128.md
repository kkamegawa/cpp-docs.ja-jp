---
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: 5e8cc9ca3dbf19a04d07edb1d73df84f2e29a5c3
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857984"
---
# <a name="_udiv128"></a>_udiv128

`_udiv128` 組み込みは、128ビット符号なし整数を64ビット符号なし整数で除算します。 戻り値は商を保持し、組み込みはポインターパラメーターを使用して剰余を返します。 `_udiv128` は**Microsoft 固有**です。

## <a name="syntax"></a>構文

```C
unsigned __int64 _udiv128(
   unsigned __int64 highDividend,
   unsigned __int64 lowDividend,
   unsigned __int64 divisor,
   unsigned __int64 *remainder
);
```

### <a name="parameters"></a>パラメーター

*Highdividend* \
から被除数の上位64ビット。

*Lowdividend* \
から被除数の下位64ビット。

*除数* \
から除算する64ビット整数。

*残り*の \
入出力剰余の64ビット整数ビット。

## <a name="return-value"></a>戻り値

商の64ビット。

## <a name="remarks"></a>Remarks

128ビット被除数の上位64ビットを*Highdividend*に、低い64ビットを*lowdividend*に渡します。 組み込みは、この値を*除数*で除算します。 剰余が*剰余*によって示された64ビット符号なし整数に格納し、商の64ビットを返します。

`_udiv128` 組み込みは、Visual Studio 2019 RTM 以降で使用できます。

## <a name="requirements"></a>要件

|組み込み|アーキテクチャ|Header|
|---------------|------------------|------------|
|`_udiv128`|x64|\<immintrin.h>|

## <a name="see-also"></a>参照

[_div128](div128.md) \
[コンパイラの組み込み](compiler-intrinsics.md)
