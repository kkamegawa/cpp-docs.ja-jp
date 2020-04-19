---
title: __lzcnt16、__lzcnt、__lzcnt64
ms.date: 09/02/2019
f1_keywords:
- __lzcnt64
- __lzcnt16
- __lzcnt
helpviewer_keywords:
- __lzcnt intrinsic
- lzcnt instruction
- lzcnt16 intrinsic
- lzcnt intrinsic
- __lzcnt16 intrinsic
- lzcnt64 intrinsic
- __lzcnt64 intrinsic
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
ms.openlocfilehash: fcd801717974a230fbd19cc7802d8f6a011774f7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221805"
---
# <a name="__lzcnt16-__lzcnt-__lzcnt64"></a>__lzcnt16、__lzcnt、__lzcnt64

**Microsoft 固有の仕様**

16、32、または64ビットの整数の先行ゼロの数をカウントします。

## <a name="syntax"></a>構文

```C
unsigned short __lzcnt16(
   unsigned short value
);
unsigned int __lzcnt(
   unsigned int value
);
unsigned __int64 __lzcnt64(
   unsigned __int64 value
);
```

### <a name="parameters"></a>パラメーター

*value*\
から先頭のゼロをスキャンする 16-、32-、または64ビットの符号なし整数。

## <a name="return-value"></a>戻り値

`value`パラメーターの先頭のゼロビットの数。 が`value` 0 の場合、戻り値は入力オペランドのサイズ (16、32、または 64) です。 の`value`最上位ビットが1の場合、戻り値は0です。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__lzcnt16`|AMD高度なビット操作 (ABM)<br /><br /> IntelHaswell|
|`__lzcnt`|AMD高度なビット操作 (ABM)<br /><br /> IntelHaswell|
|`__lzcnt64`|AMD64ビットモードでの高度なビット操作 (ABM)。<br /><br /> IntelHaswell|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

各組み込みは、命令を`lzcnt`生成します。  `lzcnt`命令が返す値のサイズは、引数のサイズと同じです。  32ビットモードでは、64ビットの汎用レジスタがないため、64ビット`lzcnt`はサポートされていません。

`lzcnt`命令のハードウェアサポートを確認するには、 `__cpuid`で`InfoType=0x80000001`組み込みを呼び出し、の`CPUInfo[2] (ECX)`ビット5を確認します。 命令がサポートされている場合、このビットは1になり、それ以外の場合は0になります。 `lzcnt`命令をサポートしていないハードウェアに組み込みを使用するコードを実行する場合、結果は予測できません。

`lzcnt`命令をサポートしていない Intel プロセッサでは、命令バイトエンコーディング`bsr`が (ビットスキャン反転) として実行されます。 コードの移植性に問題がある場合は、 `_BitScanReverse`代わりに組み込みのを使用することを検討してください。 詳細については、「 [_BitScanReverse64」を](../intrinsics/bitscanreverse-bitscanreverse64.md)参照してください。

## <a name="example"></a>例

```cpp
// Compile this test with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
  unsigned short us[3] = {0, 0xFF, 0xFFFF};
  unsigned short usr;
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};
  unsigned int   uir;

  for (int i=0; i<3; i++) {
    usr = __lzcnt16(us[i]);
    cout << "__lzcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __lzcnt(ui[i]);
    cout << "__lzcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__lzcnt16(0x0) = 16
__lzcnt16(0xff) = 8
__lzcnt16(0xffff) = 0
__lzcnt(0x0) = 32
__lzcnt(0xff) = 24
__lzcnt(0xffff) = 16
__lzcnt(0xffffffff) = 0
```

**Microsoft 固有の仕様はここまで**

このコンテンツの一部は、高度なマイクロデバイス (Inc.) の著作権2007です。All rights reserved. 上級マイクロデバイス (Inc.) からのアクセス許可を使用して再現されます。

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
