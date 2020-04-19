---
title: _mm_cvtsi64x_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtsi64x_ss
helpviewer_keywords:
- cvtsi2ss instruction
- _mm_cvtsi64x_ss intrinsic
ms.assetid: 01e5d321-c18a-46fd-a6f6-324364514e1f
ms.openlocfilehash: 0e9bacc56f212e804467d1c6e0159a1749235976
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217461"
---
# <a name="_mm_cvtsi64x_ss"></a>_mm_cvtsi64x_ss

**Microsoft 固有の仕様**

スカラー単精度浮動小数点値 (`cvtsi2ss`) 命令に変換64ビット整数の x64 拡張バージョンを生成します。

## <a name="syntax"></a>構文

```C
__m128 _mm_cvtsi64x_ss(
   __m128 a,
   __int64 b
);
```

### <a name="parameters"></a>パラメーター

*ある*\
から4つの単精度浮動小数点値を含む構造体。`__m128`

*b*\
から浮動小数点値に変換する64ビット整数。

## <a name="return-value"></a>戻り値

最初の浮動小数点値が変換の結果である構造体。`__m128` その他の3つの値は *、* から変更されずにコピーされます。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_mm_cvtsi64x_ss`|X64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

構造`__m128`体は XMM register を表します。したがって、組み込みでは、システムメモリの値*b*を XMM レジスタに移動できます。

このルーチンは、組み込みとしてのみ使用できます。

## <a name="example"></a>例

```cpp
// _mm_cvtsi64x_ss.cpp
// processor: x64

#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtsi64x_ss)

int main()
{
    __m128 a;
    __int64 b = 54;

    a.m128_f32[0] = 0;
    a.m128_f32[1] = 0;
    a.m128_f32[2] = 0;
    a.m128_f32[3] = 0;
    a = _mm_cvtsi64x_ss(a, b);

    printf_s( "%lf %lf %lf %lf\n",
              a.m128_f32[0], a.m128_f32[1],
              a.m128_f32[2], a.m128_f32[3] );
}
```

```Output
54.000000 0.000000 0.000000 0.000000
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__m128](../cpp/m128.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
