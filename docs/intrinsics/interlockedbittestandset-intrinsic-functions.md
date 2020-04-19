---
title: _interlockedbittestandset 組み込み関数
ms.date: 09/02/2019
f1_keywords:
- _interlockedbittestandset_cpp
- _interlockedbittestandset_HLEAcquire
- _interlockedbittestandset64
- _interlockedbittestandset64_acq
- _interlockedbittestandset64_nf
- _interlockedbittestandset64_rel
- _interlockedbittestandset
- _interlockedbittestandset_rel
- _interlockedbittestandset64_HLEAcquire
- _interlockedbittestandset_HLERelease
- _interlockedbittestandset_acq
- _interlockedbittestandset_nf
- _interlockedbittestandset64_cpp
- _interlockedbittestandset64_HLERelease
helpviewer_keywords:
- _interlockedbittestandset intrinsic
- _interlockedbittestandset64 intrinsic
- lock_bts instruction
ms.assetid: b1b7e334-53ea-48cf-ba60-5fa3ef51a1fc
ms.openlocfilehash: 9679abf674b5ef366818e73504c3c8c80c5d8ed7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217762"
---
# <a name="_interlockedbittestandset-intrinsic-functions"></a>_interlockedbittestandset 組み込み関数

**Microsoft 固有の仕様**

1に設定する前に`b` 、アドレス`a`のビットを調べて現在の値を返す命令を生成します。

## <a name="syntax"></a>構文

```C
unsigned char _interlockedbittestandset(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_acq(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_HLEAcquire(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_HLERelease(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_nf(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_rel(
   long *a,
   long b
);
unsigned char _interlockedbittestandset64(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_acq(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_nf(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_rel(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_HLEAcquire(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_HLERelease(
   __int64 *a,
   __int64 b
);
```

### <a name="parameters"></a>パラメーター

*ある*\
から検査するメモリへのポインター。

*b*\
からテストするビット位置。

## <a name="return-value"></a>戻り値

が設定される前の位置`b`のビットの値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|Header|
|---------------|------------------|------------|
|`_interlockedbittestandset`|x86、ARM、x64、ARM64|\<intrin.h>|
|`_interlockedbittestandset_acq`、 `_interlockedbittestandset_nf`、 `_interlockedbittestandset_rel`|ARM、ARM64|\<intrin.h>|
|`_interlockedbittestandset64_acq`、 `_interlockedbittestandset64_nf`、 `_interlockedbittestandset64_rel`|ARM64|\<intrin.h>|
|`_interlockedbittestandset_HLEAcquire`, `_interlockedbittestandset_HLERelease`|x86、x64|\<immintrin.h>|
|`_interlockedbittestandset64`|x64、ARM64|\<intrin.h>|
|`_interlockedbittestandset64_HLEAcquire`, `_interlockedbittestandset64_HLERelease`|x64|\<immintrin.h>|

## <a name="remarks"></a>Remarks

X86 および x64 プロセッサでは、これらの組み込み`lock bts`は、命令を使用して、指定されたビットを読み取り、指定したビットを1に設定します。 この操作はアトミックです。

ARM および ARM64 プロセッサでは、クリティカルセクションの`_acq`開始`_rel`時や終了時などの取得と解放のセマンティクスに、およびサフィックスの付いた組み込みを使用します。 `_nf` ("フェンスなし") サフィックスを持つ ARM 組み込みは、メモリバリアとしては機能しません。

Hardware Lock Elision (HLE) 命令をサポートする Intel プロセッサでは、`_HLEAcquire` および `_HLERelease` サフィックスの付いた組み込みにプロセッサへのヒントが含まれています。このヒントによりハードウェアでのロック書き込み手順を省くことで、パフォーマンスを向上させることができます。 これらの組み込みが HLE をサポートしていないプロセッサで呼び出された場合、ヒントは無視されます。

これらのルーチンは、組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[x86 コンパイラとの競合](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
