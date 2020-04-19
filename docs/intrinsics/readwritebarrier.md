---
title: _ReadWriteBarrier
ms.date: 09/02/2019
f1_keywords:
- _ReadWriteBarrier
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
ms.openlocfilehash: d755d045970da01d2eee33377c1452191eac4fe2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217974"
---
# <a name="_readwritebarrier"></a>_ReadWriteBarrier

**Microsoft 固有の仕様**

呼び出し場所全体にわたってメモリ アクセスの順序を変更できるコンパイラの最適化を制限します。

> [!CAUTION]
> コンパイラ組み込み関数 `_ReadBarrier`、`_WriteBarrier`、`_ReadWriteBarrier` と、`MemoryBarrier` マクロは、すべて非推奨とらてているため、使用しないでください。 スレッド間通信には、 [ C++標準ライブラリ](../standard-library/cpp-standard-library-reference.md)で定義されている[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)や[std::\<atomic T >](../standard-library/atomic.md)などの機構を使用します。 ハードウェアアクセスの場合は、 [volatile](../cpp/volatile-cpp.md)キーワードと共に[/volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md)コンパイラオプションを使用します。

## <a name="syntax"></a>構文

```C
void _ReadWriteBarrier(void);
```

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_ReadWriteBarrier`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

`_ReadWriteBarrier` 組み込み関数は、呼び出し場所全体にわたってメモリ アクセスを削除または順序変更できるコンパイラの最適化を制限します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_ReadBarrier](../intrinsics/readbarrier.md)\
[_WriteBarrier](../intrinsics/writebarrier.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[キーワード](../cpp/keywords-cpp.md)
