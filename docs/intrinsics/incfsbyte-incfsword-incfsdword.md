---
title: __incfsbyte、__incfsword、__incfsdword
ms.date: 09/02/2019
f1_keywords:
- __incfsword
- __incfsbyte_cpp
- __incfsbyte
- __incfsdword
- __incfsword_cpp
- __incfsdword_cpp
helpviewer_keywords:
- __incfsword intrinsic
- __incfsdword intrinsic
- __incfsbyte intrinsic
ms.assetid: 820457fb-e35e-42d3-bcb6-725da3281c64
ms.openlocfilehash: 43824829043304f5762d049b5c75a72b57e2102c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222129"
---
# <a name="__incfsbyte-__incfsword-__incfsdword"></a>__incfsbyte、__incfsword、__incfsdword

**Microsoft 固有の仕様**

`FS`セグメントの先頭を基準としたオフセットによって指定されたメモリ位置の値に1つを追加します。

## <a name="syntax"></a>構文

```C
void __incfsbyte(
   unsigned long Offset
);
void __incfsword(
   unsigned long Offset
);
void __incfsdword(
   unsigned long Offset
);
```

### <a name="parameters"></a>パラメーター

*影*\
からの`FS`先頭からのオフセット。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__incfsbyte`|x86|
|`__incfsword`|x86|
|`__incfsdword`|x86|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

これらの組み込みはカーネルモードでのみ使用でき、ルーチンは組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[\_addfsbyte、 \_addfsword、 \_addfsdword (_s)](../intrinsics/addfsbyte-addfsword-addfsdword.md)\
[\_readfsbyte、 \_readfsdword、 \_readfsqword \_、readfsword (_d)](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[\_writefsbyte、 \_ \_writefsdword、writefsqword \_、writefソード (_c)](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
