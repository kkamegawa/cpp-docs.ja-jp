---
title: __writecr0
ms.date: 09/02/2019
f1_keywords:
- _writecr0
helpviewer_keywords:
- _writecr0 intrinsic
ms.assetid: a143d08d-0333-4e1b-91b4-4acb2ae91b5a
ms.openlocfilehash: 1f00796242ae352d32935c2551d50f2d93d734ec
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219307"
---
# <a name="__writecr0"></a>__writecr0

**Microsoft 固有の仕様**

値`Data`を cr0 レジスタ register に書き込みます。

## <a name="syntax"></a>構文

```C
void writecr0(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>パラメーター

*データ*\
からCR0 レジスタ register に書き込む値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__writecr0`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

この組み込みはカーネル モードのみで使用でき、そのルーチンは組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
