---
title: _InterlockedCompareExchange128
ms.date: 11/04/2016
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
ms.openlocfilehash: 3cfe9d650b66dc08a96599652b52f0b153198afa
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627399"
---
# <a name="interlockedcompareexchange128"></a>_InterlockedCompareExchange128

**Microsoft 固有の仕様**

128 ビットのインタロックされた比較および交換を実行します。

## <a name="syntax"></a>構文

```
unsigned char _InterlockedCompareExchange128(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
```

#### <a name="parameters"></a>パラメーター

*変換先*<br/>
[入力、出力]2 つの 64 ビット整数の配列は、変換先へのポインターは、128 ビット フィールドとしてと見なされます。 変換先のデータが一般保護違反を回避するために、配置、16 バイトである必要があります。

*ExchangeHigh*<br/>
[in]64 ビットの整数で、変換先の高い部分と交換される可能性があります。

*ExchangeLow*<br/>
[in]64 ビットの整数で、変換先の低い部分と交換される可能性があります。

*ComparandResult*<br/>
[入力、出力]\(128 ビット フィールドとしてと見なされます) 2 つの 64 ビット整数の配列へのポインターのコピー先と比較します。  出力では、これは、変換先の元の値で上書きされます。

## <a name="return-value"></a>戻り値

128 ビットの比較対照値が変換先の元の値に等しい場合は 1。 `ExchangeHigh` `ExchangeLow` 128 ビットの変換先を上書きします。

比較対照値が変換先の元の値と等しくない場合は 0 を返します。 変換先の値は変更されず、比較対照値の値は、変換先の値で上書きされます。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_InterlockedCompareExchange128`|X64|

**ヘッダー ファイル** \<intrin.h >

## <a name="remarks"></a>Remarks

この組み込みを生成、`cmpxchg16b`命令 (で、`lock`プレフィックス) は、128 ビットのロックされている比較と exchange を実行します。 AMD 64 ビット ハードウェアの初期のバージョンは、この命令をサポートしていません。 ハードウェアのサポートを確認する、`cmpxchg16b`命令を呼び出し、`__cpuid`で組み込み`InfoType=0x00000001 (standard function 1)`。 ビット 13 `CPUInfo[2]` (ECX)、命令がサポートされている場合は 1 です。

> [!NOTE]
>  値`ComparandResult`は常に上書きされます。 後に、`lock`命令では、この組み込みの初期値をすぐにコピーする`Destination`に`ComparandResult`します。 このため、`ComparandResult`と`Destination`予期しない動作を回避するために別個のメモリ位置を指す必要があります。

使用できますが、 `_InterlockedCompareExchange128` 、低レベルのスレッドの同期には小さな同期関数を使用する場合は、128 ビットを超えるを同期する必要はありません (など、他の`_InterlockedCompareExchange`組み込み) 代わりにします。 使用`_InterlockedCompareExchange128`メモリ内の 128 ビット値をアトミックにアクセスする場合。

`cmpxchg16b`命令が搭載されていないハードウェア上でこの組み込み関数を呼び出した場合、その結果は保証されません。

このルーチンは組み込みとしてのみ使用できます。

## <a name="example"></a>例

この例では`_InterlockedCompareExchange128`の高値と安値の単語の合計で 2 つの 64 ビット整数の配列の上位ワードを置換して、下位ワードをインクリメントします。 BigInt.Int 配列へのアクセスは、アトミックですが、この例は、1 つのスレッドを使用し、わかりやすくするためのロックは無視されます。

```
// cmpxchg16b.c
// processor: x64
// compile with: /EHsc /O2
#include <stdio.h>
#include <intrin.h>

typedef struct _LARGE_INTEGER_128 {
    __int64 Int[2];
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;

volatile LARGE_INTEGER_128 BigInt;

// This AtomicOp() function atomically performs:
//   BigInt.Int[1] += BigInt.Int[0]
//   BigInt.Int[0] += 1
void AtomicOp ()
{
    LARGE_INTEGER_128 Comparand;
    Comparand.Int[0] = BigInt.Int[0];
    Comparand.Int[1] = BigInt.Int[1];
    do {
        ; // nothing
    } while (_InterlockedCompareExchange128(BigInt.Int,
                                            Comparand.Int[0] + Comparand.Int[1],
                                            Comparand.Int[0] + 1,
                                            Comparand.Int) == 0);
}

// In a real application, several threads contend for the value
// of BigInt.
// Here we focus on the compare and exchange for simplicity.
int main(void)
{
   BigInt.Int[1] = 23;
   BigInt.Int[0] = 11;
   AtomicOp();
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",
      BigInt.Int[1],BigInt.Int[0]);
}
```

```Output
BigInt.Int[1] = 34, BigInt.Int[0] = 12
```

**Microsoft 固有の仕様はここまで**

高度なマイクロ デバイス, inc. copyright 2007All rights reserved. 高度なマイクロ デバイス, Inc. からのアクセス許可を持つ再現

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)<br/>
[_InterlockedCompareExchange の組み込み関数](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)<br/>
[x86 コンパイラとの競合](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)