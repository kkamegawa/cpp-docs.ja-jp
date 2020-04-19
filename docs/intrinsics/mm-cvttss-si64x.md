---
title: _mm_cvttss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: 69016a4e23b020b2c4c79c6b97a5a76f2b2dc028
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217420"
---
# <a name="_mm_cvttss_si64x"></a>_mm_cvttss_si64x

**Microsoft 固有の仕様**

切り捨ての単精度浮動小数点数を64ビット整数 (`cvttss2si`) 命令に変換した x64 拡張バージョンを出力します。

## <a name="syntax"></a>構文

```C
__int64 _mm_cvttss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>パラメーター

*value*\
から単精度浮動小数点値を含む構造体。`__m128`

## <a name="return-value"></a>戻り値

最初の浮動小数点値を64ビット整数に変換した結果。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_mm_cvttss_si64x`|X64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

組み込みは、不`_mm_cvtss_si64x`正確な変換が0方向に切り捨てられた場合にのみ異なります。 構造体`__m128`は XMM register を表しているため、生成された命令は XMM レジスタからシステムメモリにデータを移動します。

このルーチンは、組み込みとしてのみ使用できます。

## <a name="example"></a>例

```cpp
// _mm_cvttss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvttss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] = { 101.5, 200.75,
                                          300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvttss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__m128](../cpp/m128.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
