---
title: __ll_rshift
ms.date: 09/02/2019
f1_keywords:
- __ll_rshift_cpp
- __ll_rshift
helpviewer_keywords:
- __ll_rshift intrinsic
- ll_rshift intrinsic
ms.assetid: ef13b732-d122-44a0-add9-f5544a2c4ab2
ms.openlocfilehash: ad17991d84acb7e531baf9435610ebd566197a22
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217503"
---
# <a name="__ll_rshift"></a>__ll_rshift

**Microsoft 固有の仕様**

最初のパラメーターで指定された64ビット値を、2番目のパラメーターで指定されたビット数だけ右にシフトします。

## <a name="syntax"></a>構文

```C
__int64 __ll_rshift(
   __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>パラメーター

*隠す*\
から右にシフトする64ビット整数値。

*nBit*\
からシフトするビット数、x64 の場合は64、x86 の場合はモジュロ32。

## <a name="return-value"></a>戻り値

ビットで`nBit`シフトされたマスク。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__ll_rshift`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

2番目のパラメーターが x64 の 64 (x86 の場合は 32) を超える場合は、シフトするビット数を決定するために、その数値が 64 (x86 の場合は 32) によって取得されます。 プレフィックス`ll`は、が`long long`操作であることを示します。これ`__int64`は、64ビットの符号付き整数型である別の名前です。

## <a name="example"></a>例

```cpp
// ll_rshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_rshift)

int main()
{
   __int64 Mask = - 0x100;
   int nBit = 4;
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
   Mask = __ll_rshift(Mask, nBit);
   cout << hex << Mask << endl;
   cout << " - " << (- Mask) << endl;
}
```

## <a name="output"></a>Output

```Output
ffffffffffffff00
- 100
fffffffffffffff0
- 10
```

> [!NOTE]
> が`_ull_rshift`使用されている場合は、右シフトされた値の MSB が0になったため、目的の結果が負の値の場合に取得されていません。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__ll_lshift](../intrinsics/ll-lshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)
