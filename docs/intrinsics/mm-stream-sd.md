---
title: _mm_stream_sd
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_sd
helpviewer_keywords:
- _mm_stream_sd intrinsic
- movntsd instruction
ms.assetid: 2b4bea5e-e64e-45fa-9afc-88a2e4b82cfc
ms.openlocfilehash: 7f0c6457cc0806a0f1764300cffa1c9878b8a600
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217364"
---
# <a name="_mm_stream_sd"></a>_mm_stream_sd

**Microsoft 固有の仕様**

キャッシュを汚染せずに、64ビットのデータをメモリ位置に書き込みます。

## <a name="syntax"></a>構文

```C
void _mm_stream_sd(
   double * Dest,
   __m128d Source
);
```

### <a name="parameters"></a>パラメーター

*先*\
入出力ソースデータが書き込まれる場所へのポインター。

*Source*\
から下位64ビットで記述される`double`値を格納している128ビット値。

## <a name="return-value"></a>戻り値

なし。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_mm_stream_sd`|SSE4a|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

組み込みによって`movntsd`命令が生成されます。 この命令のハードウェアサポートを確認するには`__cpuid` 、で`InfoType=0x80000001`組み込みのを呼び出し、 `CPUInfo[2] (ECX)`のビット6を確認します。 ハードウェアでこの命令がサポートされている場合、このビットは1になり、それ以外の場合は0になります。

命令`movntsd`をサポートし`_mm_stream_sd`ていないハードウェアに組み込みを使用するコードを実行する場合、結果は予測できません。

## <a name="example"></a>例

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128d vals;
    double d[2];

    d[0] = -1.;
    d[1] = -2.;
    vals.m128d_f64[0] = 0.;
    vals.m128d_f64[1] = 1.;
    _mm_stream_sd(&d[1], vals);
    cout << "d[0] = " << d[0] << ", d[1] = " << d[1] << endl;
}
```

```Output
d[0] = -1, d[1] = 1
```

**Microsoft 固有の仕様はここまで**

高度なマイクロデバイス (Inc.) による部分の著作権2007All rights reserved. 上級マイクロデバイス (Inc.) からのアクセス許可を使用して再現されます。

## <a name="see-also"></a>関連項目

[_mm_stream_ss](../intrinsics/mm-stream-ss.md)\
[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
