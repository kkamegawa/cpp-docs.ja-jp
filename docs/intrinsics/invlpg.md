---
title: __invlpg
ms.date: 09/02/2019
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: ba8bd81498f805992336b0dc4163fe18fa157a2c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221900"
---
# <a name="__invlpg"></a>__invlpg

**Microsoft 固有の仕様**

では、 `invlpg` *アドレス*が指すメモリに関連付けられているページの変換ルックアサイドバッファー (TLB) を無効にする x86 命令が生成されます。

## <a name="syntax"></a>構文

```C
void __invlpg(
   void* Address
);
```

### <a name="parameters"></a>パラメーター

*先*\
から64ビットアドレス。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__invlpg`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

組み込み`__invlpg`は特権命令を出力し、特権レベル (CPL) が0のカーネルモードでのみ使用できます。

このルーチンは、組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
