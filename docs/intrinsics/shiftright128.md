---
title: __shiftright128
ms.date: 09/02/2019
f1_keywords:
- __shiftright128
helpviewer_keywords:
- __shiftright128 intrinsic
ms.assetid: 5419a6c4-0de1-43fb-b314-4faa5b2d051f
ms.openlocfilehash: a18a9958a51f291e4997c23e87ee48f739562416
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220019"
---
# <a name="__shiftright128"></a>__shiftright128

**Microsoft 固有の仕様**

64 ビットの 2 つの数 `LowPart` および `HighPart` で表される 128 ビットの数を、`Shift` で指定されたビット数だけ右にシフトし、結果の下位 64 ビットを返します。

## <a name="syntax"></a>構文

```C
unsigned __int64 __shiftright128(
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

結果の下位 64 ビット。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__shiftright128`|X64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

`Shift` の値は常にモジュロ 64 です。このため、たとえば `__shiftright128(0, 1, 64)` をコールすると、上位部分が `0` ビット右にシフトされ、下位部分である `0` が返されます。`1` ではありません。

## <a name="example"></a>例

例については、「 [__shiftleft128](../intrinsics/shiftleft128.md)」を参照してください。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__shiftleft128](../intrinsics/shiftleft128.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
