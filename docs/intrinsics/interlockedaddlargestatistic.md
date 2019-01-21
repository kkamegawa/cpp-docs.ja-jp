---
title: _InterlockedAddLargeStatistic
ms.date: 11/04/2016
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: 88ada0a906b777ab8ac676ddfe0a5166e906999d
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627473"
---
# <a name="interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Microsoft 固有の仕様**

最初のオペランドが 64 ビット値はインタロックされた加算を実行します。

## <a name="syntax"></a>構文

```
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

#### <a name="parameters"></a>パラメーター

*加数*<br/>
[入力、出力]追加操作の最初のオペランドへのポインター。 指す値は、加算の結果によって置き換えられます。

*[値]*<br/>
[in]2 番目のオペランド。最初のオペランドを加算する値。

## <a name="return-value"></a>戻り値

2 番目のオペランドの値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**ヘッダー ファイル** \<intrin.h >

## <a name="remarks"></a>Remarks

この組み込みはアトミックため 2 つの個別のロックされている指示として実装されます。 組み込みこれの実行中に別のスレッドで発生するアトミックの 64 ビット読み取りは、読み取られる一貫性のない値になる可能性があります。

この関数は、読み取り/書き込みバリアとして動作します。 詳細については、次を参照してください。 [_ReadWriteBarrier](../intrinsics/readwritebarrier.md)します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)<br/>
[x86 コンパイラとの競合](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)