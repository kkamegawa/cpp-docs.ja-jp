---
title: __nop
ms.date: 09/02/2019
f1_keywords:
- __nop
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
ms.openlocfilehash: 4561bcb84063f3707825c8ca164867d41500e2db
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221672"
---
# <a name="__nop"></a>__nop

**Microsoft 固有の仕様**

操作を実行しないプラットフォーム固有のマシンコードを生成します。

## <a name="syntax"></a>構文

```C
void __nop();
```

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__nop`|x86、ARM、x64、ARM64|

**ヘッダーファイル**\<>

**Microsoft 固有の仕様はここまで**

## <a name="remarks"></a>Remarks

`__nop` 関数は `NOP` マシン語命令と同じです。 X86 と x64 の詳細については、「Intel Architecture Software Developer's Manual, Volume 2:」を検索してください。命令セットリファレンス、「 [」を参照してください](https://software.intel.com/articles/intel-sdm)。

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__noop](../intrinsics/noop.md)
