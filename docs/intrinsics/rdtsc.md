---
title: __rdtsc
ms.date: 09/02/2019
f1_keywords:
- __rdtsc
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
ms.openlocfilehash: 837b68ca6ac63587cd43a7e8828777221c677e3c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217148"
---
# <a name="__rdtsc"></a>__rdtsc

**Microsoft 固有の仕様**

プロセッサのタイムスタンプを返す命令を生成します。`rdtsc` プロセッサのタイムスタンプには、前回のリセットからのクロックサイクル数が記録されます。

## <a name="syntax"></a>構文

```C
unsigned __int64 __rdtsc();
```

## <a name="return-value"></a>戻り値

ティック数を表す64ビット符号なし整数。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__rdtsc`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

このルーチンは、組み込みとしてのみ使用できます。

新しい世代のハードウェアでの TSC 値の解釈は、以前のバージョンの x64 の場合と異なります。 詳細については、ハードウェアのマニュアルを参照してください。

## <a name="example"></a>例

```cpp
// rdtsc.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__rdtsc)

int main()
{
    unsigned __int64 i;
    i = __rdtsc();
    printf_s("%I64d ticks\n", i);
}
```

```Output
3363423610155519 ticks
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
