---
title: _ReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _ReturnAddress
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
ms.openlocfilehash: 2a830ff1e8a2c9551dec52cf10a3d5cf126bde3b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218053"
---
# <a name="_returnaddress"></a>_ReturnAddress

**Microsoft 固有の仕様**

組み込み`_ReturnAddress`は、呼び出し元に制御が戻った後に実行される呼び出し元関数の命令のアドレスを提供します。

次のプログラムをビルドし、デバッガーでステップスルーします。 プログラムをステップ実行するときに、から`_ReturnAddress`返されたアドレスをメモしておきます。 次に、 `_ReturnAddress`が使用さ[れた関数から制御が戻った直後に、「方法:[逆アセンブル]](/visualstudio/debugger/how-to-use-the-disassembly-window)ウィンドウを使用して、次に実行される命令のアドレスがから`_ReturnAddress`返されたアドレスと一致することを確認します。

インライン展開などの最適化は、返信先アドレスに影響を与える可能性があります。 たとえば、以下のサンプルプログラムが[/ob1](../build/reference/ob-inline-function-expansion.md)でコンパイルされると`inline_func` 、は呼び出し元の関数`main`にインライン化されます。 したがって、および`_ReturnAddress` `inline_func` `main`からへの呼び出しでは、それぞれ同じ値が生成されます。

[/clr](../build/reference/clr-common-language-runtime-compilation.md) `_ReturnAddress`でコンパイルされたプログラムでを使用する場合、 `_ReturnAddress`呼び出しを含む関数はネイティブ関数としてコンパイルされます。 を含む`_ReturnAddress`関数へのマネージ呼び出しとしてコンパイルさ`_ReturnAddress`れた関数が、予期したとおりに動作しないことがあります。

## <a name="requirements"></a>必要条件

**ヘッダーファイル**\<>

## <a name="example"></a>例

```cpp
// compiler_intrinsics__ReturnAddress.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_ReturnAddress)

__declspec(noinline)
void noinline_func(void)
{
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());
}

__forceinline
void inline_func(void)
{
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());
}

int main(void)
{
   noinline_func();
   inline_func();
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());

   return 0;
}
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[キーワード](../cpp/keywords-cpp.md)
