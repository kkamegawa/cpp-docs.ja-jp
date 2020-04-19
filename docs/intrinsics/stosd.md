---
title: __stosd
ms.date: 09/02/2019
f1_keywords:
- __stosd
helpviewer_keywords:
- stosd instruction
- rep stosd instruction
- __stosd intrinsic
ms.assetid: 03104247-1cea-49f6-b6f8-287917bf5680
ms.openlocfilehash: c46bb124390ff23d79361c66530493c48faf3f0a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219981"
---
# <a name="__stosd"></a>__stosd

**Microsoft 固有の仕様**

ストア文字列命令 (`rep stosd`) を生成します。

## <a name="syntax"></a>構文

```C
void __stosd(
   unsigned long* Destination,
   unsigned long Data,
   size_t Count
);
```

### <a name="parameters"></a>パラメーター

*インストール*\
入出力操作の転送先。

*データ*\
から格納するデータ。

*数*\
から書き込むダブルワードのブロックの長さ。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__stosd`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

その結果、ダブルワード*データ*は、*変換先*が指すメモリ位置にある*Count*ダブルワードのブロックに書き込まれます。

このルーチンは、組み込みとしてのみ使用できます。

## <a name="example"></a>例

```C
// stosd.c
// processor: x86, x64

#include <stdio.h>
#include <memory.h>
#include <intrin.h>

#pragma intrinsic(__stosd)

int main()
{
    unsigned long val = 99999;
    unsigned long a[10];

    memset(a, 0, sizeof(a));
    __stosd(a+1, val, 2);

printf_s( "%u %u %u %u",
              a[0], a[1], a[2], a[3]);
}
```

```Output
0 99999 99999 0
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
