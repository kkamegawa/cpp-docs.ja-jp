---
title: _InterlockedCompareExchangePointer 組み込み関数
ms.date: 09/02/2019
f1_keywords:
- _InterlockedCompareExchangePointer_HLERelease
- _InterlockedCompareExchangePointer_rel
- _InterlockedCompareExchangePointer_acq_cpp
- _InterlockedCompareExchangePointer
- _InterlockedCompareExchangePointer_cpp
- _InterlockedCompareExchangePointer_np
- _InterlockedCompareExchangePointer_rel_cpp
- _InterlockedCompareExchangePointer_HLEAcquire
- _InterlockedCompareExchangePointer_acq
- _InterlockedCompareExchangePointer_nf
helpviewer_keywords:
- InterlockedCompareExchangePointer_acq intrinsic
- _InterlockedCompareExchangePointer_rel intrinsic
- _InterlockedCompareExchangePointer_acq intrinsic
- InterlockedCompareExchangePointer_rel intrinsic
- InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_HLERelease intrinsic
- _InterlockedCompareExchangePointer_HLEAcquire intrinsic
- _InterlockedCompareExchangePointer intrinsic
- _InterlockedCompareExchangePointer_nf intrinsic
- _InterlockedCompareExchangePointer_np intrinsic
ms.assetid: 97fde59d-2bf9-42aa-a0fe-a5b6befdd44b
ms.openlocfilehash: c0a0083c19df51d2d2eccb7a7bbf6521303c1f85
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222037"
---
# <a name="_interlockedcompareexchangepointer-intrinsic-functions"></a>_InterlockedCompareExchangePointer 組み込み関数

**Microsoft 固有の仕様**

`Exchange` と `Destination` アドレスが等しい場合、`Comparand` アドレスに `Destination` アドレスを格納するアトミックな演算を実行します。

## <a name="syntax"></a>構文

```C
void * _InterlockedCompareExchangePointer (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_acq (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_HLEAcquire (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_HLERelease (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_nf (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
void * _InterlockedCompareExchangePointer_np (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
long _InterlockedCompareExchangePointer_rel (
   void * volatile * Destination,
   void * Exchange,
   void * Comparand
);
```

### <a name="parameters"></a>パラメーター

*インストール*\
[入力、出力]対象の値へのポインターへのポインター。 符号は無視されます。

*エクスチェンジ*\
から交換ポインター。 符号は無視されます。

*比較対照値*\
からDestination と比較するポインター。 符号は無視されます。

## <a name="return-value"></a>戻り値

戻り値は、対象の初期値です。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|Header|
|---------------|------------------|------------|
|`_InterlockedCompareExchangePointer`|x86、ARM、x64、ARM64|\<intrin.h>|
|`_InterlockedCompareExchangePointer_acq`、 `_InterlockedCompareExchangePointer_nf`、 `_InterlockedCompareExchangePointer_rel`|ARM、ARM64|\<iiintrin.h>|
|`_InterlockedCompareExchangePointer_HLEAcquire`, `_InterlockedCompareExchangePointer_HLERelease`|x86、x64|\<immintrin.h>|

## <a name="remarks"></a>Remarks

`_InterlockedCompareExchangePointer` は `Destination` アドレスと `Comparand` アドレスのアトミックな比較を実行します。 `Destination` のアドレスが `Comparand` のアドレスと等しい場合、`Exchange` のアドレスは `Destination` で指定したアドレスに格納されます。 それ以外の場合は演算が実行されません。

`_InterlockedCompareExchangePointer`Win32 Windows SDK [InterlockedCompareExchangePointer](/windows-hardware/drivers/ddi/content/wdm/nf-wdm-interlockedcompareexchangepointer)関数のコンパイラ組み込みサポートを提供します。

の使用`_InterlockedCompareExchangePointer`例については、「 [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)」を参照してください。

ARM プラットフォームでは、クリティカル セクションの最初と最後などで取得と解放のセマンティクスを必要とする場合は、`_acq` および `_rel` サフィックスの付いた組み込みを使用します。 ("フェンスなし`_nf` ") サフィックスを持つ ARM 組み込みは、メモリバリアとしては機能しません。

組み込みに `_np` ("プリフェッチなし") サフィックスが付いていると、コンパイラによってプリフェッチ操作が挿入される可能性がなくなります。

Hardware Lock Elision (HLE) 命令をサポートする Intel プラットフォームでは、`_HLEAcquire` および `_HLERelease` サフィックスの付いた組み込みにプロセッサへのヒントが含まれています。このヒントによりハードウェアでのロック書き込み手順を省くことで、パフォーマンスを向上させることができます。 これらの組み込みが HLE をサポートしていないプラットフォームで呼び出された場合、ヒントは無視されます。

これらのルーチンは、組み込みとしてのみ使用できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[キーワード](../cpp/keywords-cpp.md)
