---
title: _AddressOfReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
ms.openlocfilehash: d705029c30fdbc117c4c6e96923691e43e072e23
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221078"
---
# <a name="_addressofreturnaddress"></a>_AddressOfReturnAddress

**Microsoft 固有の仕様**

現在の関数の戻りアドレスを保持するメモリ位置のアドレスを提供します。 このアドレスは、他のメモリ位置 (関数の引数など) へのアクセスには使用できません。

## <a name="syntax"></a>構文

```C
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86、x64、ARM、ARM64|

**ヘッダーファイル**\<>

## <a name="remarks"></a>Remarks

[/clr](../build/reference/clr-common-language-runtime-compilation.md) でコンパイルされたプログラムで `_AddressOfReturnAddress` を使用する場合、 `_AddressOfReturnAddress`呼び出しを含む関数はネイティブ関数としてコンパイルされます。 を含む`_AddressOfReturnAddress`関数へのマネージ呼び出しとしてコンパイルさ`_AddressOfReturnAddress`れた関数が、予期したとおりに動作しないことがあります。

このルーチンは、組み込みとしてのみ使用できます。

## <a name="example"></a>例

```cpp
// compiler_intrinsics_AddressOfReturnAddress.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

// This function will print three values:
//   (1) The address retrieved from _AddressOfReturnAdress
//   (2) The return address stored at the location returned in (1)
//   (3) The return address retrieved the _ReturnAddress* intrinsic
// Note that (2) and (3) should be the same address.
__declspec(noinline)
void func() {
   void* pvAddressOfReturnAddress = _AddressOfReturnAddress();
   printf_s("%p\n", pvAddressOfReturnAddress);
   printf_s("%p\n", *((void**) pvAddressOfReturnAddress));
   printf_s("%p\n", _ReturnAddress());
}

int main() {
   func();
}
```

```Output
0012FF78
00401058
00401058
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[キーワード](../cpp/keywords-cpp.md)
