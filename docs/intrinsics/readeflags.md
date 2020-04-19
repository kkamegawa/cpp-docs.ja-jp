---
title: __readeflags
ms.date: 09/02/2019
f1_keywords:
- __readeflags
helpviewer_keywords:
- __readeflags intrinsic
ms.assetid: f9d2f4d8-c428-491f-b8de-04d0566b2b6b
ms.openlocfilehash: 6afdc0f20a3ae72865a80ba2eb7f896f79f63171
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857906"
---
# <a name="__readeflags"></a>__readeflags

**Microsoft 固有の仕様**

プログラムの状態と制御 (EFLAGS) レジスタを読み取ります。

## <a name="syntax"></a>構文

```C
unsigned     int __readeflags(void); /* x86 */
unsigned __int64 __readeflags(void); /* x64 */
```

## <a name="return-value"></a>戻り値

EFLAGS レジスタの値。 戻り値は、32ビットプラットフォームでは32ビット長、64ビットプラットフォームでは64ビット長です。

## <a name="remarks"></a>Remarks

これらのルーチンは、組み込みとしてのみ使用できます。

## <a name="requirements"></a>要件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__readeflags`|x86、x64|

**ヘッダーファイル**\<に存在します。 h >

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__writeeflags](../intrinsics/writeeflags.md)
