---
title: __writecr8
ms.date: 09/02/2019
f1_keywords:
- _writecr8
helpviewer_keywords:
- _writecr8 intrinsic
ms.assetid: 6f8bd632-dddb-4335-971e-1acee24aa2b9
ms.openlocfilehash: c8df13c15b5cd8a51b77d65ad930a1852809ee30
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219240"
---
# <a name="__writecr8"></a>__writecr8

**Microsoft 固有の仕様**

値`Data`を CR8 register に書き込みます。

## <a name="syntax"></a>構文

```C
void writecr8(
   unsigned __int64 Data
);
```

### <a name="parameters"></a>パラメーター

*データ*\
からCR8 register に書き込む値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__writecr8`|X64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

`__writecr8`組み込みはカーネルモードでのみ使用でき、ルーチンは組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
