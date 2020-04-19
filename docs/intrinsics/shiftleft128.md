---
title: __shiftleft128
ms.date: 09/02/2019
f1_keywords:
- __shiftleft128
helpviewer_keywords:
- __shiftleft128 intrinsic
ms.assetid: 557b846a-8fb0-469d-91ac-1b1fad80dc2a
ms.openlocfilehash: 5da9ac81cedbdd24e10eb438892f88510c32ca24
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218003"
---
# <a name="__shiftleft128"></a>__shiftleft128

**Microsoft 固有の仕様**

64 ビットの 2 つの数 `LowPart` および `HighPart` で表される 128 ビットの数を、`Shift` で指定されたビット数だけ左にシフトし、結果の上位 64 ビットを返します。

## <a name="syntax"></a>構文

```C
unsigned __int64 __shiftleft128(
   unsigned __int64 LowPart,
   unsigned __int64 HighPart,
   unsigned char Shift
);
```

### <a name="parameters"></a>パラメーター

*LowPart*\
からシフトする128ビット数量の下位64ビット。

*Largeint.highpart*\
からシフトする128ビット数量の上位64ビット。

*転換*\
からシフトするビット数。

## <a name="return-value"></a>戻り値

結果の上位 64 ビット。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__shiftleft128`|X64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

*シフト*値は常にモジュロ64であるため、たとえば、を呼び出す`__shiftleft128(1, 0, 64)`と、関数は低位部分`0`のビットを左にシフトし、の大`0`部分を`1`返しますが、それ以外の場合はを返します。

## <a name="example"></a>例

```C
// shiftleft128.c
// processor: IPF, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic (__shiftleft128, __shiftright128)

int main()
{
    unsigned __int64 i = 0x1I64;
    unsigned __int64 j = 0x10I64;
    unsigned __int64 ResultLowPart;
    unsigned __int64 ResultHighPart;

    ResultLowPart = i << 1;
    ResultHighPart = __shiftleft128(i, j, 1);

    // concatenate the low and high parts padded with 0's
    // to display correct hexadecimal 128 bit values
    printf_s("0x%02I64x%016I64x << 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);

    ResultHighPart = j >> 1;
    ResultLowPart = __shiftright128(i, j, 1);

    printf_s("0x%02I64x%016I64x >> 1 = 0x%02I64x%016I64x\n",
             j, i, ResultHighPart, ResultLowPart);
}
```

```Output
0x100000000000000001 << 1 = 0x200000000000000002
0x100000000000000001 >> 1 = 0x080000000000000000
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__shiftright128](../intrinsics/shiftright128.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
