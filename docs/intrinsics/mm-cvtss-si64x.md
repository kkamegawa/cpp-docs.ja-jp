---
title: _mm_cvtss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvtss_si64x
helpviewer_keywords:
- cvtss2si intrinsic
- _mm_cvtss_si64x intrinsic
ms.assetid: c279aff2-ee29-4271-8829-3ec691bf7718
ms.openlocfilehash: 6079ed7846a35ff16355f0341d63430f9846057f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217436"
---
# <a name="_mm_cvtss_si64x"></a>_mm_cvtss_si64x

**Microsoft 固有の仕様**

スカラー単精度浮動小数点数を64ビット整数 (`cvtss2si`) 命令に変換した x64 拡張バージョンを生成します。

## <a name="syntax"></a>構文

```C
__int64 _mm_cvtss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>パラメーター

*value*\
から浮動小数点値を格納している構造体。`__m128`

## <a name="return-value"></a>戻り値

1番目の浮動小数点値を整数に変換した結果の64ビット整数。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_mm_cvtss_si64x`|X64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

構造体の値の最初の要素が整数に変換され、が返されます。 MXCSR の丸め制御ビットは、丸め動作を決定するために使用されます。 既定の丸めモードは、10進部分が0.5 の場合に、近似値に丸められます。 構造体`__m128`は XMM register を表すので、組み込みは XMM レジスタからの値を受け取り、それをシステムメモリに書き込みます。

このルーチンは、組み込みとしてのみ使用できます。

## <a name="example"></a>例

```cpp
// _mm_cvtss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvtss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] =
                           { 101.25, 200.75, 300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvtss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__m128d](../cpp/m128d.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
