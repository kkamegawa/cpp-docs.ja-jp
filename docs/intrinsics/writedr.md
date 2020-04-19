---
title: __writedr
ms.date: 09/02/2019
f1_keywords:
- __writedr
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
ms.openlocfilehash: 473e7223e9974d0125e772c152ea85ae90b97342
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858062"
---
# <a name="__writedr"></a>__writedr

**Microsoft 固有の仕様**

指定された値を指定されたデバッグレジスタに書き込みます。

## <a name="syntax"></a>構文

```C
void __writedr(unsigned DebugRegister, unsigned DebugValue); /* x86 */
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue); /* x64 */
```

### <a name="parameters"></a>パラメーター

*Debugregister*\
からデバッグレジスタを識別する 0 ~ 7 の数値。

*Debugvalue*\
からデバッグレジスタに書き込む値。

## <a name="remarks"></a>Remarks

これらの組み込みはカーネルモードでのみ使用でき、ルーチンは組み込みとしてのみ使用できます。

## <a name="requirements"></a>要件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__writedr`|x86、x64|

**ヘッダーファイル**\<に存在します。 h >

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[__readdr](../intrinsics/readdr.md)
