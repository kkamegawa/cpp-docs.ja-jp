---
title: _InterlockedAddLargeStatistic
ms.date: 09/02/2019
f1_keywords:
- _InterlockedAddLargeStatistic
- _InterlockedAddLargeStatistic_cpp
helpviewer_keywords:
- _InterlockedAddLargeStatistic intrinsic
- InterlockedAddLargeStatistic intrinsic
ms.assetid: 2802e74b-bcee-46e4-b562-894908d44409
ms.openlocfilehash: de8c5b7dfd2462dddcb98324ebacc44c8148d85e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222091"
---
# <a name="_interlockedaddlargestatistic"></a>_InterlockedAddLargeStatistic

**Microsoft 固有の仕様**

最初のオペランドが64ビット値である、インタロックされた加算を実行します。

## <a name="syntax"></a>構文

```C
long _InterlockedAddLargeStatistic(
   __int64 volatile * Addend,
   long Value
);
```

### <a name="parameters"></a>パラメーター

*加数*\
[入力、出力]追加操作の最初のオペランドへのポインター。 が指す値は、加算の結果に置き換えられます。

*数値*\
から2番目のオペランド。1番目のオペランドに追加する値。

## <a name="return-value"></a>戻り値

2番目のオペランドの値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_InterlockedAddLargeStatistic`|x86|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

組み込み`_InterlockedAddLargeStatistic`はアトミックではありません。これは、2つの個別のロックされた命令として実装されるためです。 組み込みのの実行中に別のスレッドで発生したアトミックの64ビット読み取りは、一貫性のない値の読み取りにつながる可能性があります。

`_InterlockedAddLargeStatistic`読み取り/書き込みのバリアとして動作します。 詳細については、「 [Readwriteバリア](../intrinsics/readwritebarrier.md)」を参照してください。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[x86 コンパイラとの競合](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
