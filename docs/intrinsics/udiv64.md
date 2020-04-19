---
title: _udiv64
ms.date: 09/02/2019
f1_keywords:
- _udiv64
helpviewer_keywords:
- _udiv64 intrinsic
ms.openlocfilehash: ddb46f33b0fccc1cedc2a704265b096ba715b506
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857997"
---
# <a name="_udiv64"></a>_udiv64

`_udiv64` 組み込みは、64ビット符号なし整数を32ビット符号なし整数で除算します。 戻り値は商を保持し、組み込みはポインターパラメーターを使用して剰余を返します。 `_udiv64` は**Microsoft 固有**です。

## <a name="syntax"></a>構文

```C
unsigned int _udiv64(
   unsigned __int64 dividend,
   unsigned int divisor,
   unsigned int* remainder
);
```

### <a name="parameters"></a>パラメーター

*被除数*\
から除算する64ビット符号なし整数。

*除数*\
からによって除算される32ビット符号なし整数。

*残り*の\
入出力32ビット符号なし整数の剰余。

## <a name="return-value"></a>戻り値

商の32ビット。

## <a name="remarks"></a>Remarks

`_udiv64` 組み込みは、*被除数*を*除数*で除算します。 剰余が*剰余*によって示された32ビット符号なし整数に格納し、商の32ビットを返します。

`_udiv64` 組み込みは、Visual Studio 2019 RTM 以降で使用できます。

## <a name="requirements"></a>要件

|組み込み|アーキテクチャ|Header|
|---------------|------------------|------------|
|`_udiv64`|x86、x64|\<immintrin.h>|

## <a name="see-also"></a>参照

[_div64](div64.md) \
[コンパイラの組み込み](compiler-intrinsics.md)
