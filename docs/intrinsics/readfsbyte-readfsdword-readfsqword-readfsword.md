---
title: __readfsbyte、__readfsdword、__readfsqword、__readfsword
ms.date: 09/02/2019
f1_keywords:
- __readfsword
- __readfsdword
- __readfsbyte
- __readfsqword
helpviewer_keywords:
- __readfsword intrinsic
- readfsword intrinsic
- __readfsdword intrinsic
- readfsbyte intrinsic
- __readfsbyte intrinsic
- readfsdword intrinsic
- readfsqword intrinsic
- __readfsqword intrinsic
ms.assetid: f6ee7203-4179-402c-a464-0746c84ce6ac
ms.openlocfilehash: 30040b33fe8c686bc0cda585c525ae2926cdf314
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222363"
---
# <a name="__readfsbyte-__readfsdword-__readfsqword-__readfsword"></a>__readfsbyte、__readfsdword、__readfsqword、__readfsword

**Microsoft 固有の仕様**

オフセットによって指定された場所から、FS セグメントの先頭を基準とするメモリを読み取ります。

## <a name="syntax"></a>構文

```C
unsigned char __readfsbyte(
   unsigned long Offset
);
unsigned short __readfsword(
   unsigned long Offset
);
unsigned long __readfsdword(
   unsigned long Offset
);
unsigned __int64 __readfsqword(
   unsigned long Offset
);
```

### <a name="parameters"></a>パラメーター

*影*\
からの`FS`先頭から読み取るオフセット。

## <a name="return-value"></a>戻り値

バイト、ワード、ダブルワード、または quadword のメモリの内容 (呼び出された関数の名前によって示され`FS:[Offset]`ます)。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__readfsbyte`|x86|
|`__readfsdword`|x86|
|`__readfsqword`|x86|
|`__readfsword`|x86|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

これらのルーチンは、組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__ writefsbyte、 \_ \_writefsdword、writefsqword、 \_writefソード](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
