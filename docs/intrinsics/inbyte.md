---
title: __inbyte
ms.date: 09/02/2019
f1_keywords:
- __inbyte
- __inbyte_cpp
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
ms.openlocfilehash: f0036763ed7315a54fbfe6dcc873b46b52f0730c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222144"
---
# <a name="__inbyte"></a>__inbyte

**Microsoft 固有の仕様**

命令を生成し、によって`Port`指定されたポートから読み取った1バイトを返します。 `in`

## <a name="syntax"></a>構文

```C
unsigned char __inbyte(
   unsigned short Port
);
```

### <a name="parameters"></a>パラメーター

*ポート*\
から読み取り元のポート。

## <a name="return-value"></a>戻り値

指定したポートから読み取ったバイト。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__inbyte`|x86、x64|

**ヘッダーファイル**\<>

**Microsoft 固有の仕様はここまで**

## <a name="remarks"></a>Remarks

このルーチンは、組み込みとしてのみ使用できます。

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
