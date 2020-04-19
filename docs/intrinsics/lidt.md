---
title: __lidt
ms.date: 09/02/2019
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 24778b761ada56830b155a2fc65e90f54ba729ed
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217509"
---
# <a name="__lidt"></a>__lidt

**Microsoft 固有の仕様**

指定されたメモリ位置の値を使用して、割り込み記述子テーブルレジスタ (IDTR) を読み込みます。

## <a name="syntax"></a>構文

```C
void __lidt(void * Source);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*ソース*|からIDTR にコピーされる値へのポインター。|

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__lidt`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

関数は`LIDT`コンピューター命令と同じであり、カーネルモードでのみ使用できます。 `__lidt` 詳細については、「Intel Architecture Software Developer's Manual, Volume 2:命令セットリファレンス、「 [」を参照してください](https://software.intel.com/articles/intel-sdm)。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__sidt](../intrinsics/sidt.md)
