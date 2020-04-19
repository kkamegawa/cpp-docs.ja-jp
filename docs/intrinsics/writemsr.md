---
title: __writemsr
ms.date: 09/02/2019
f1_keywords:
- __writemsr
helpviewer_keywords:
- Write Model Specific Register instruction
- wrmsr instruction
- __writemsr intrinsic
ms.assetid: 938b1553-51a8-4822-a818-6bed79b0fde5
ms.openlocfilehash: 7819477edb8d4e6b18a1213a73ba67065ea7ff57
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219135"
---
# <a name="__writemsr"></a>__writemsr

**Microsoft 固有の仕様**

モデル固有のレジスタ (`wrmsr`) 命令への書き込みを生成します。

## <a name="syntax"></a>構文

```C
void __writemsr(
   unsigned long Register,
   unsigned __int64 Value
);
```

### <a name="parameters"></a>パラメーター

*取引*\
からモデル固有のレジスタ。

*数値*\
から書き込む値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__writemsr`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

この関数はカーネルモードでのみ使用でき、このルーチンは組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
