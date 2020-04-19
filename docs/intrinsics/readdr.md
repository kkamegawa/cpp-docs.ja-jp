---
title: __readdr
ms.date: 09/02/2019
f1_keywords:
- __readdr
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
ms.openlocfilehash: fbaf9e761f9f1450ccd12dc378ab6e498aa0df08
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857880"
---
# <a name="__readdr"></a>__readdr

**Microsoft 固有の仕様**

指定されたデバッグレジスタの値を読み取ります。

## <a name="syntax"></a>構文

```C
unsigned         __readdr(unsigned int DebugRegister); /* x86 */
unsigned __int64 __readdr(unsigned int DebugRegister); /* x64 */
```

### <a name="parameters"></a>パラメーター

*Debugregister*\
からデバッグレジスタを識別する 0 ~ 7 の定数。

## <a name="return-value"></a>戻り値

指定されたデバッグレジスタの値。

## <a name="remarks"></a>Remarks

これらの組み込みはカーネルモードでのみ使用でき、ルーチンは組み込みとしてのみ使用できます。

## <a name="requirements"></a>要件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__readdr`|x86、x64|

**ヘッダーファイル**\<に存在します。 h >

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
