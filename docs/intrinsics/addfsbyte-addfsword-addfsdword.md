---
title: __addfsbyte、__addfsword、__addfsdword
ms.date: 09/02/2019
f1_keywords:
- __addfsbyte_cpp
- __addfsdword
- __addfsword_cpp
- __addfsbyte
- __addfsword
- __addfsdword_cpp
helpviewer_keywords:
- __addfsdword intrinsic
- __addfsword intrinsic
- __addfsbyte intrinsic
ms.assetid: 706c70df-6b52-4401-9268-2977ed8ad715
ms.openlocfilehash: 302e58ed13c144913e7806a0a8b7adc202a67ef6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218526"
---
# <a name="__addfsbyte-__addfsword-__addfsdword"></a>__addfsbyte、__addfsword、__addfsdword

**Microsoft 固有の仕様**

`FS`セグメントの先頭を基準としたオフセットによって指定されたメモリ位置に値を追加します。

## <a name="syntax"></a>構文

```C
void __addfsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __addfsword(
   unsigned long Offset,
   unsigned short Data
);
void __addfsdword(
   unsigned long Offset,
   unsigned long Data
);
```

### <a name="parameters"></a>パラメーター

*影*\
からの`FS`先頭からのオフセット。

*データ*\
からメモリ位置に追加する値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__addfsbyte`|x86|
|`__addfsword`|x86|
|`__addfsdword`|x86|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

これらのルーチンは、組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__ インシデント fsbyte、 \_visual word、 \_visual word](../intrinsics/incfsbyte-incfsword-incfsdword.md)\
[__ readfsbyte、 \_"readfsdword \_"、"readfsqword \_"、"readfsword"](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[__ writefsbyte、 \_ \_writefsdword、writefsqword、 \_writefソード](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
