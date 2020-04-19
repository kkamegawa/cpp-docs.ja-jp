---
title: __int8、__int16、__int32、__int64
ms.date: 10/09/2018
f1_keywords:
- __int8_cpp
- __int16_cpp
- __int32_cpp
- __int64_cpp
- __int8
- __int16
- __int32
- __int64
- _int8
- _int16
- _int32
- _int64
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
ms.openlocfilehash: 4e793f23581f7dc62a39fcd8c5c504fb5a2ccbc9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301471"
---
# <a name="__int8-__int16-__int32-__int64"></a>__int8、__int16、__int32、__int64

**Microsoft 固有の仕様**

Microsoft C/C++ の機能では、サイズ設定された整数型をサポートします。 **__Int**<em>n</em>型指定子を使用して、8ビット、16ビット、32ビット、または64ビットの整数変数を宣言できます。 *n*は8、16、32、または64です。

次の例は、サイズ設定された整数のこれらの型のそれぞれに 1 つの変数を宣言しています。

```cpp
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

**__Int8**、 **__int16**、および **__int32**型は、同じサイズを持つ ANSI 型のシノニムであり、複数のプラットフォームで同じように動作する移植性のあるコードを記述する場合に便利です。 **__Int8**データ型は**char**型と同義で、 **__int16**は**short**型と同義であり、 **__int32**は**int**型と同義です。 **__Int64**型は**long long**型と同義です。

以前のバージョンとの互換性を維持するために、 **_int8**、 **_int16**、 **_int32**、および **_int64**は、コンパイラオプション[/za __int8 言語拡張を無効にする)](../build/reference/za-ze-disable-language-extensions.md)が指定されていない限り、 **__int16**、 **__int32**、 **__int64**、および **\(** のシノニムになります。

## <a name="example"></a>使用例

次の例では、__int*xx*パラメーターが**int**に昇格されることを示しています。

```cpp
// sized_int_types.cpp

#include <stdio.h>

void func(int i) {
    printf_s("%s\n", __FUNCTION__);
}

int main()
{
    __int8 i8 = 100;
    func(i8);   // no void func(__int8 i8) function
                // __int8 will be promoted to int
}
```

```Output
func
```

**END Microsoft 固有の仕様**

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)<br/>
[組み込みの型](../cpp/fundamental-types-cpp.md)<br/>
[データ型の範囲](../cpp/data-type-ranges.md)<br/>
