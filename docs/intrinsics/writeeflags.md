---
title: __writeeflags
ms.date: 09/02/2019
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: 6b9b6976369ed810789e5749a2e30029cad4c2d7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858049"
---
# <a name="__writeeflags"></a>__writeeflags

**Microsoft 固有の仕様**

指定した値をプログラムの状態と制御 (EFLAGS) レジスタに書き込みます。

## <a name="syntax"></a>構文

```C
void __writeeflags(unsigned Value); /* x86 */
void __writeeflags(unsigned __int64 Value); /* x64 */
```

### <a name="parameters"></a>パラメーター

*値*\
からEFLAGS レジスタに書き込む値。 `Value` パラメーターは32ビットプラットフォームの場合は32ビット長、64ビットプラットフォームの場合は64ビット長です。

## <a name="remarks"></a>Remarks

これらのルーチンは、組み込みとしてのみ使用できます。

## <a name="requirements"></a>要件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__writeeflags`|x86、x64|

**ヘッダーファイル**\<に存在します。 h >

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
