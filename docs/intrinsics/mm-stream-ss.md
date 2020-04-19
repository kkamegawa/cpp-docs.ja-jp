---
title: _mm_stream_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: 005f4f697d64f6ea68b35dc32daf1217be463a2a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217351"
---
# <a name="_mm_stream_ss"></a>_mm_stream_ss

**Microsoft 固有の仕様**

キャッシュを汚染せずに、32ビットのデータをメモリ位置に書き込みます。

## <a name="syntax"></a>構文

```C
void _mm_stream_ss(
   float * Destination,
   __m128 Source
);
```

### <a name="parameters"></a>パラメーター

*インストール*\
入出力ソースデータが書き込まれる場所へのポインター。

*Source*\
から下位32ビットに書き込まれる`float`値を含む128ビットの数値。

## <a name="return-value"></a>戻り値

なし。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

組み込みによって`movntss`命令が生成されます。 この命令のハードウェアサポートを確認するには`__cpuid` 、で`InfoType=0x80000001`組み込みのを呼び出し、 `CPUInfo[2] (ECX)`のビット6を確認します。 命令がサポートされている場合はこのビットが1になり、それ以外の場合は0になります。

命令`movntss`をサポートし`_mm_stream_ss`ていないハードウェアに組み込みを使用するコードを実行する場合、結果は予測できません。

## <a name="example"></a>例

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128 vals;
    float f[4];

    f[0] = -1.;
    f[1] = -2.;
    f[2] = -3.;
    f[3] = -4.;
    vals.m128_f32[0] = 0.;
    vals.m128_f32[1] = 1.;
    vals.m128_f32[2] = 2.;
    vals.m128_f32[3] = 3.;
    _mm_stream_ss(&f[3], vals);
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;
}
```

```Output
f[0] = -1, f[1] = -2
f[2] = -3, f[3] = 3
```

**Microsoft 固有の仕様はここまで**

高度なマイクロデバイス (Inc.) による部分の著作権2007All rights reserved. 上級マイクロデバイス (Inc.) からのアクセス許可を使用して再現されます。

## <a name="see-also"></a>関連項目

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)\
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)\
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
