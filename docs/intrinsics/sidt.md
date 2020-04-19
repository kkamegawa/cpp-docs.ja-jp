---
title: __sidt
ms.date: 09/02/2019
f1_keywords:
- __sidt
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
ms.openlocfilehash: d6b685da0e02373307a3149c5b7b28213f37ad40
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222326"
---
# <a name="__sidt"></a>__sidt

**Microsoft 固有の仕様**

指定されたメモリ位置に割り込み記述子テーブルレジスタ (IDTR) の値を格納します。

## <a name="syntax"></a>構文

```C
void __sidt(void * Destination);
```

### <a name="parameters"></a>パラメーター

*インストール*\
からIDTR が格納されているメモリ位置へのポインター。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__sidt`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

`__sidt` 関数は `SIDT` マシン語命令と同じです。 詳細については、「Intel Architecture Software Developer's Manual, Volume 2:命令セットリファレンス、「 [」を参照してください](https://software.intel.com/articles/intel-sdm)。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__lidt](../intrinsics/lidt.md)
