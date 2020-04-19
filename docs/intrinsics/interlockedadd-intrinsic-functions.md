---
title: _InterlockedAdd 組み込み関数
ms.date: 09/02/2019
f1_keywords:
- _InterlockedAdd64_acq_cpp
- _InterlockedAdd64_acq
- _InterlockedAdd_acq
- _InterlockedAdd_nf
- _InterlockedAdd64_rel
- _InterlockedAdd64
- _InterlockedAdd_cpp
- _InterlockedAdd_rel_cpp
- _InterlockedAdd_rel
- _InterlockedAdd64_rel_cpp
- _InterlockedAdd64_cpp
- _InterlockedAdd_acq_cpp
- _InterlockedAdd64_nf
- _InterlockedAdd
helpviewer_keywords:
- _InterlockedAdd_nf intrinsic
- _InterlockedAdd_rel intrinsic
- _InterlockedAdd intrinsic
- _InterlockedAdd64 intrinsic
- _InterlockedAdd64_acq intrinsic
- _InterlockedAdd64_nf intrinsic
- _InterlockedAdd_acq intrinsic
- _InterlockedAdd64_rel intrinsic
ms.assetid: 3d319603-ea9c-4fdd-ae61-e52430ccc3b1
ms.openlocfilehash: c540cfe6abd8ae6dc2933e7fb21e2a331c21ea71
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217728"
---
# <a name="_interlockedadd-intrinsic-functions"></a>_InterlockedAdd 組み込み関数

**Microsoft 固有の仕様**

これらの関数はアトミックな加算を実行します。これにより、複数のスレッドが共有変数にアクセスしたときに、操作が正常に完了するようになります。

## <a name="syntax"></a>構文

```C
long _InterlockedAdd(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_acq(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_nf(
   long volatile * Addend,
   long Value
);
long _InterlockedAdd_rel(
   long volatile * Addend,
   long Value
);
__int64 _InterlockedAdd64(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_acq(
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_nf (
   __int64 volatile * Addend,
   __int64 Value
);
__int64 _InterlockedAdd64_rel(
   __int64 volatile * Addend,
   __int64 Value
);
```

### <a name="parameters"></a>パラメーター

*加数*\
[入力、出力]に追加する整数へのポインター。加算の結果に置き換えられます。

*数値*\
から追加する値。

## <a name="return-value"></a>戻り値

どちらの関数も加算の結果を返します。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_InterlockedAdd`|ARM、ARM64|
|`_InterlockedAdd_acq`|ARM、ARM64|
|`_InterlockedAdd_nf`|ARM、ARM64|
|`_InterlockedAdd_rel`|ARM、ARM64|
|`_InterlockedAdd64`|ARM、ARM64|
|`_InterlockedAdd64_acq`|ARM、ARM64|
|`_InterlockedAdd64_nf`|ARM、ARM64|
|`_InterlockedAdd64_rel`|ARM、ARM64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

これらの関数の `_acq` または `_rel` サフィックスの付いたバージョンは、取得または解放のセマンティクスに従うインタロックされた加算を実行します。 *取得セマンティクス*とは、その後のメモリの読み取りと書き込みの前に、操作の結果がすべてのスレッドおよびプロセッサに対して表示されることを意味します。 クリティカル セクションを開始するときには、取得が役立ちます。 *リリースセマンティクス*とは、操作の結果が表示される前に、すべてのメモリ読み取りと書き込みが強制的にすべてのスレッドとプロセッサに対して可視になることを意味します。 クリティカル セクションを終了するときには、解放が役立ちます。 `_nf` ("フェンスなし") サフィックスの付いた組み込みは、メモリバリアとしては機能しません。

これらのルーチンは、組み込みとしてのみ使用できます。

## <a name="example"></a>例

```cpp
// interlockedadd.cpp
// Compile with: /Oi /EHsc
// processor: ARM
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_InterlockedAdd)

int main()
{
        long data1 = 0xFF00FF00;
        long data2 = 0x00FF0000;
        long retval;
        retval = _InterlockedAdd(&data1, data2);
        printf("0x%x 0x%x 0x%x", data1, data2, retval);
}
```

## <a name="output"></a>Output

```Output
0xffffff00 0xff0000 0xffffff00
```

## <a name="example"></a>例

```cpp
// interlockedadd64.cpp
// compile with: /Oi /EHsc
// processor: ARM
#include <iostream>
#include <intrin.h>
using namespace std;

#pragma intrinsic(_InterlockedAdd64)

int main()
{
        __int64 data1 = 0x0000FF0000000000;
        __int64 data2 = 0x00FF0000FFFFFFFF;
        __int64 retval;
        cout << hex << data1 << " + " << data2 << " = " ;
        retval = _InterlockedAdd64(&data1, data2);
        cout << data1 << endl;
        cout << "Return value: " << retval << endl;
}
```

## <a name="output"></a>出力

```Output
ff0000000000 + ff0000ffffffff = ffff00ffffffff
Return value: ffff00ffffffff
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[x86 コンパイラとの競合](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
