---
title: __ll_lshift
ms.date: 09/02/2019
f1_keywords:
- __ll_lshift_cpp
- __ll_lshift
helpviewer_keywords:
- ll_lshift intrinsic
- __ll_lshift intrinsic
ms.assetid: fe98f733-426d-44b3-8f24-5d0d6d44bd94
ms.openlocfilehash: 158ecbf39320d70b51f1f498a0b689ba58fec363
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221811"
---
# <a name="__ll_lshift"></a>__ll_lshift

**Microsoft 固有の仕様**

指定した64ビット値を、指定したビット数だけ左にシフトします。

## <a name="syntax"></a>構文

```C
unsigned __int64 __ll_lshift(
   unsigned __int64 Mask,
   int nBit
);
```

### <a name="parameters"></a>パラメーター

*隠す*\
から左にシフトする64ビット整数値。

*nBit*\
からシフトするビット数。

## <a name="return-value"></a>戻り値

ビットによって左`nBit`にシフトされたマスク。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__ll_lshift`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

64ビットアーキテクチャ`nBit`のプログラムをコンパイルし、が63よりも大きい場合、シフトするビット数は`nBit`モジュロ64になります。 32ビットアーキテクチャ`nBit`のプログラムをコンパイルし、が31より大きい場合、シフトするビット数は`nBit`モジュロ32になります。

名前`ll`のは、(`__int64`) に対する`long long`操作であることを示します。

## <a name="example"></a>例

```cpp
// ll_lshift.cpp
// compile with: /EHsc
// processor: x86, x64
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(__ll_lshift)

int main()
{
   unsigned __int64 Mask = 0x100;
   int nBit = 8;
   Mask = __ll_lshift(Mask, nBit);
   cout << hex << Mask << endl;
}
```

## <a name="output"></a>Output

```Output
10000
```

> [!NOTE]
> 左シフト演算に署名されていないバージョンはありません。 これは、 `__ll_lshift`既に符号なしの入力パラメーターが使用されているためです。 右シフトとは異なり、左シフトには符号に依存しません。これは、シフトされた値の符号に関係なく、結果の最下位ビットが常に0に設定されるためです。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__ll_rshift](../intrinsics/ll-rshift.md)\
[__ull_rshift](../intrinsics/ull-rshift.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
