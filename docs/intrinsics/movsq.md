---
title: __movsq
ms.date: 09/02/2019
f1_keywords:
- __movsq
helpviewer_keywords:
- __movsq intrinsic
- rep movsq instruction
- movsq instruction
ms.assetid: be116a6e-2176-4ca4-93b1-9ccf3e7e7835
ms.openlocfilehash: 66de1971c48f6697fd06579fac635cce31545e92
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217264"
---
# <a name="__movsq"></a>__movsq

**Microsoft 固有の仕様**

繰り返しの移動文字列 (`rep movsq`) 命令を生成します。

## <a name="syntax"></a>構文

```C
void __movsq(
   unsigned char* Destination,
   unsigned char* Source,
   size_t Count
);
```

### <a name="parameters"></a>パラメーター

*インストール*\
入出力操作の転送先。

*Source*\
から操作のソース。

*数*\
からコピーする quadwords の数。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__movsq`|X64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

結果として、*ソース*によってポイントされている最初の*カウント*Quadwords が、コピー*先*の文字列にコピーされます。

このルーチンは、組み込みとしてのみ使用できます。

## <a name="example"></a>例

```cpp
// movsq.cpp
// processor: x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsq)

int main()
{
    unsigned __int64 a1[10];
    unsigned __int64 a2[10] = {950, 850, 750, 650, 550, 450, 350, 250,
                               150, 50};
    __movsq(a1, a2, 10);

    for (int i = 0; i < 10; i++)
       printf_s("%d ", a1[i]);
    printf_s("\n");
}
```

```Output
950 850 750 650 550 450 350 250 150 50
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
