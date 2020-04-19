---
title: __wbinvd
ms.date: 09/02/2019
f1_keywords:
- __wbinvd
helpviewer_keywords:
- __wbinvd intrinsic
- wbinvd instruction
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
ms.openlocfilehash: fe888ef578f0c2e077911537d401890b63372a0b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219388"
---
# <a name="__wbinvd"></a>__wbinvd

**Microsoft 固有の仕様**

書き戻しを生成し、Cache (`wbinvd`) 命令を無効にします。

## <a name="syntax"></a>構文

```C
void __wbinvd(void);
```

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__wbinvd`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

この関数は、特権レベル (CPL) が0のカーネルモードでのみ使用でき、ルーチンは組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
