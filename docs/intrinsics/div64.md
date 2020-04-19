---
title: _div64
ms.date: 09/02/2019
f1_keywords:
- _div64
helpviewer_keywords:
- _div64 intrinsic
ms.openlocfilehash: 59c5eae66f9e93cb88f9512e405376f2ef5f1ceb
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858023"
---
# <a name="_div64"></a>_div64

`_div64` 組み込みは、64ビット整数を32ビット整数で除算します。 戻り値は商を保持し、組み込みはポインターパラメーターを使用して剰余を返します。 `_div64` は**Microsoft 固有**です。

## <a name="syntax"></a>構文

```C
int _div64(
   __int64 dividend,
   int divisor,
   int* remainder
);
```

### <a name="parameters"></a>パラメーター

*被除数* \
から除算する64ビット整数。

*除数* \
から除算する32ビット整数。

*残り*の \
入出力剰余の32ビット整数ビット。

## <a name="return-value"></a>戻り値

商の32ビット。

## <a name="remarks"></a>Remarks

`_div64` 組み込みは、*被除数*を*除数*で除算します。 剰余は*剰余*によって示された32ビット整数に格納され、商の32ビットを返します。

`_div64` 組み込みは、Visual Studio 2019 RTM 以降で使用できます。

## <a name="requirements"></a>要件

|組み込み|アーキテクチャ|Header|
|---------------|------------------|------------|
|`_div64`|x86、x64|\<immintrin.h>|

## <a name="see-also"></a>参照

[_udiv64](udiv64.md) \
[コンパイラの組み込み](compiler-intrinsics.md)
