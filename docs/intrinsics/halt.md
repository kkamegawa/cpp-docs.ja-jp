---
title: __halt
ms.date: 09/02/2019
f1_keywords:
- __halt
- __halt_cpp
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
ms.openlocfilehash: 66f5e05e7673523966ef35ac743fc585930b511c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222151"
---
# <a name="__halt"></a>__halt

**Microsoft 固有の仕様**

有効な割り込み、nonmaskable interrupt (NMI)、またはリセットが発生するまで、マイクロプロセッサを停止します。

## <a name="syntax"></a>構文

```C
void __halt( void );
```

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__halt`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

関数は`HLT`コンピューター命令と同じであり、カーネルモードでのみ使用できます。 `__halt` 詳細については、「Intel Architecture Software Developer's Manual, Volume 2:命令セットリファレンス、「 [」を参照してください](https://software.intel.com/articles/intel-sdm)。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
