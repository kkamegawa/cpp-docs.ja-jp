---
title: __readmsr
ms.date: 09/02/2019
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 4398b9d42369e3a914dbec1ed2d14cafecf58483
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222341"
---
# <a name="__readmsr"></a>__readmsr

**Microsoft 固有の仕様**

によって`register`指定されたモデル固有のレジスタを読み取り、その値を返す命令を生成します。`rdmsr`

## <a name="syntax"></a>構文

```C
__int64 __readmsr(
   int register
);
```

### <a name="parameters"></a>パラメーター

*取引*\
から読み取るモデル固有のレジスタ。

## <a name="return-value"></a>戻り値

指定したレジスタの値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__readmsr`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

この関数はカーネルモードでのみ使用でき、ルーチンは組み込みとしてのみ使用できます。

詳細については、AMD のドキュメントを参照してください。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
