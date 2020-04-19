---
title: _interlockedbittestandreset 組み込み関数
ms.date: 09/02/2019
f1_keywords:
- _interlockedbittestandreset_rel
- _interlockedbittestandreset64
- _interlockedbittestandreset64_acq
- _interlockedbittestandreset64_nf
- _interlockedbittestandreset64_rel
- _interlockedbittestandreset64_HLERelease
- _interlockedbittestandreset_HLERelease
- _interlockedbittestandreset_HLEAcquire
- _interlockedbittestandreset_acq
- _interlockedbittestandreset_cpp
- _interlockedbittestandreset_nf
- _interlockedbittestandreset64_cpp
- _interlockedbittestandreset64_HLEAcquire
- _interlockedbittestandreset
helpviewer_keywords:
- lock_btr instruction
- _interlockedbittestandreset64 intrinsic
- _interlockedbittestandreset intrinsic
ms.assetid: 9bbb1442-f2e9-4dc2-b0da-97f3de3493b9
ms.openlocfilehash: 419d7f800d603a8beca5c8ccb0f9c8f8b3bfcfdb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222060"
---
# <a name="_interlockedbittestandreset-intrinsic-functions"></a>_interlockedbittestandreset 組み込み関数

**Microsoft 固有の仕様**

`b` アドレス`a`のビットをゼロに設定し、元の値を返す命令を生成します。

## <a name="syntax"></a>構文

```C
unsigned char _interlockedbittestandreset(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_acq(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_HLEAcquire(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_HLERelease(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_nf(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset_rel(
   long *a,
   long b
);
unsigned char _interlockedbittestandreset64(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_acq(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_nf(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_rel(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_HLEAcquire(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandreset64_HLERelease(
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

`b` で指定された位置にあるビットの元の値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|Header|
|---------------|------------------|------------|
|`_interlockedbittestandreset`|x86、ARM、x64、ARM64|\<intrin.h>|
|`_interlockedbittestandreset_acq`、 `_interlockedbittestandreset_nf`、 `_interlockedbittestandreset_rel`|ARM、ARM64|\<intrin.h>|
|`_interlockedbittestandreset64_acq`、 `_interlockedbittestandreset64_nf`、 `_interlockedbittestandreset64_rel`|ARM64|\<intrin.h>|
|`_interlockedbittestandreset_HLEAcquire`, `_interlockedbittestandreset_HLERelease`|x86、x64|\<immintrin.h>|
|`_interlockedbittestandreset64`|x64、ARM64|\<intrin.h>|
|`_interlockedbittestandreset64_HLEAcquire`, `_interlockedbittestandreset64_HLERelease`|x64|\<immintrin.h>|

## <a name="remarks"></a>Remarks

X86 および x64 プロセッサでは、これらの組み込み`lock btr`は、分割不可能な操作で指定されたビットを読み取り、設定する命令を使用します。

ARM プロセッサでは、クリティカル セクションの最初と最後などでの取得と解放のセマンティクスのために、`_acq` および `_rel` サフィックスの付いた組み込みを使用します。 `_nf` ("フェンスなし") サフィックスを持つ ARM 組み込みは、メモリバリアとしては機能しません。

Hardware Lock Elision (HLE) 命令をサポートする Intel プロセッサでは、`_HLEAcquire` および `_HLERelease` サフィックスの付いた組み込みにプロセッサへのヒントが含まれています。このヒントによりハードウェアでのロック書き込み手順を省くことで、パフォーマンスを向上させることができます。 これらの組み込みが HLE をサポートしていないプロセッサで呼び出された場合、ヒントは無視されます。

これらのルーチンは、組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[x86 コンパイラとの競合](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
