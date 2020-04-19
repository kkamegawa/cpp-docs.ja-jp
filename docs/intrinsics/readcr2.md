---
title: __readcr2
ms.date: 09/02/2019
f1_keywords:
- __readcr2
helpviewer_keywords:
- __readcr2 intrinsic
ms.assetid: d02c97d8-1953-46e7-a79e-a781e2c5bf27
ms.openlocfilehash: 482f4548a692d6aa3b65fbc42caabda29bb393c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217111"
---
# <a name="__readcr2"></a>__readcr2

**Microsoft 固有の仕様**

CR2 register を読み取り、その値を返します。

## <a name="syntax"></a>構文

```C
unsigned __int64 __readcr2(void);
```

## <a name="return-value"></a>戻り値

CR2 レジスタの値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__readcr2`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

組み込みはカーネルモードでのみ使用でき、ルーチンは組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
