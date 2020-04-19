---
title: __writefsbyte、__writefsdword、__writefsqword、__writefsword
ms.date: 09/02/2019
f1_keywords:
- __writefsword
- __writefsbyte
- __writefsqword
- __writefsdword
helpviewer_keywords:
- writefsbyte intrinsic
- __writefsword intrinsic
- writefsqword intrinsic
- writefsdword intrinsic
- __writefsdword intrinsic
- __writefsqword intrinsic
- __writefsbyte intrinsic
- writefsword intrinsic
ms.assetid: 23ac6e8e-bc91-4e90-a4c6-da02993637ad
ms.openlocfilehash: c0cb70986fc75d14f23fb70efe89f48e10fb047e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219119"
---
# <a name="__writefsbyte-__writefsdword-__writefsqword-__writefsword"></a>__writefsbyte、__writefsdword、__writefsqword、__writefsword

**Microsoft 固有の仕様**

メモリを、FS セグメントの先頭を基準としたオフセットで指定された位置に書き込みます。

## <a name="syntax"></a>構文

```C
void __writefsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __writefsword(
   unsigned long Offset,
   unsigned short Data
);
void __writefsdword(
   unsigned long Offset,
   unsigned long Data
);
void __writefsqword(
   unsigned long Offset,
   unsigned __int64 Data
);
```

### <a name="parameters"></a>パラメーター

*影*\
から書き込み先の FS の先頭からのオフセット。

*データ*\
から書き込む値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__writefsbyte`|x86|
|`__writefsword`|x86|
|`__writefsdword`|x86|
|`__writefsqword`|x86|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

これらのルーチンは、組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__ readfsbyte、 \_"readfsdword \_"、"readfsqword \_"、"readfsword"](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
