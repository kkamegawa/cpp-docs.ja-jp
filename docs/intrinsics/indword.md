---
title: __indword
ms.date: 09/02/2019
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
ms.openlocfilehash: 790b65c8a565124df92b82b7ea17174788086a96
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222119"
---
# <a name="__indword"></a>__indword

**Microsoft 固有の仕様**

`in`命令を使用して、指定したポートから1つのデータを読み取ります。

## <a name="syntax"></a>構文

```C
unsigned long __indword(
   unsigned short Port
);
```

### <a name="parameters"></a>パラメーター

*ポート*\
から読み取り元のポート。

## <a name="return-value"></a>戻り値

ポートから読み取られた単語。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__indword`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

このルーチンは、組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
