---
title: __rdtscp
ms.date: 09/02/2019
f1_keywords:
- __rdtscp
helpviewer_keywords:
- rdtscp intrinsic
- __rdtscp intrinsic
- rdtscp instruction
ms.assetid: f17d9a9c-88bb-44e0-b69d-d516bc1c93ee
ms.openlocfilehash: 4dcabd6ed0f7fb3f422927815cbdc91f2b4b9d43
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221324"
---
# <a name="__rdtscp"></a>__rdtscp

**Microsoft 固有の仕様**

`rdtscp`命令を生成してメモリに`TSC_AUX[31:0`を書き込み、64 ビットのタイム スタンプ カウンター`TSC)`を返します。

## <a name="syntax"></a>構文

```C
unsigned __int64 __rdtscp(
   unsigned int * AUX
);
```

### <a name="parameters"></a>パラメーター

*助動詞*\
入出力コンピューター固有のレジスタ`TSC_AUX[31:0]`の内容を格納する場所へのポインター。

## <a name="return-value"></a>戻り値

64ビットの符号なし整数のティック数。

## <a name="requirements"></a>要件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__rdtscp`|x86、x64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

組み込み`__rdtscp`によって`rdtscp`命令が生成されます。 この命令のハードウェア サポートを確認するには、組み込み関数`__cpuid`を`InfoType=0x80000001`として呼び出し、`CPUInfo[3] (EDX)`の 27 ビット目を確認してください。 命令がサポートされていればこのビットは 1 となり、サポートされていなければ 0 となります。  `rdtscp`命令をサポートしていないハードウェアに組み込みを使用するコードを実行する場合、結果は予測できません。

この命令は、前のすべての命令が実行され、以前のすべての読み込みがグローバルに表示されるまで待機します。 ただし、シリアル化命令ではありません。 詳細については、Intel および AMD のマニュアルを参照してください。

値`TSC_AUX[31:0]`の意味はオペレーティング システムによって異なります。

## <a name="example"></a>例

```cpp
#include <intrin.h>
#include <stdio.h>
int main()
{
    unsigned __int64 i;
    unsigned int ui;
    i = __rdtscp(&ui);
    printf_s("%I64d ticks\n", i);
    printf_s("TSC_AUX was %x\n", ui);
}
```

```Output
3363423610155519 ticks
TSC_AUX was 0
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__rdtsc](../intrinsics/rdtsc.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
