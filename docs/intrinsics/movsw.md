---
title: __movsw
ms.date: 09/02/2019
f1_keywords:
- __movsw
helpviewer_keywords:
- movsw instruction
- rep movsw instruction
- __movsw intrinsic
ms.assetid: db402ad5-7f0e-449a-b0b0-eea9928d6435
ms.openlocfilehash: 67eef7fe0a5b9803650f345740a8c40262cd2014
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221727"
---
# <a name="__movsw"></a>__movsw

**Microsoft 固有の仕様**

Move String (`rep movsw`) 命令を生成します。

## <a name="syntax"></a>構文

```C
void __movsw(
   unsigned short* Destination,
   unsigned short* Source,
   size_t Count
);
```

### <a name="parameters"></a>パラメーター

*インストール*\
入出力操作の転送先。

*Source*\
から操作のソース。

*数*\
からコピーする単語数。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__movsw`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

結果として、*ソース*によって参照されている最初の*カウント*単語が、コピー*先*の文字列にコピーされます。

このルーチンは、組み込みとしてのみ使用できます。

## <a name="example"></a>例

```cpp
// movsw.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__movsw)

int main()
{
    unsigned short s1[10];
    unsigned short s2[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
    __movsw(s1, s2, 10);

    for (int i = 0; i < 10; i++)
        printf_s("%d ", s1[i]);
    printf_s("\n");
}
```

```Output
0 1 2 3 4 5 6 7 8 9
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
