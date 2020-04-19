---
title: __asm ブロックでの演算子の使用
ms.date: 08/30/2018
helpviewer_keywords:
- brackets [ ]
- brackets [ ], __asm blocks
- __asm keyword [C++], operators
- square brackets [ ], __asm blocks
- operators [C++], using in __asm blocks
- square brackets [ ]
ms.assetid: a26ccfd4-40ae-4a61-952f-c417982aa8dd
ms.openlocfilehash: a871c19942252bf6a1a4901f8854b7b759700cd9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166504"
---
# <a name="using-operators-in-__asm-blocks"></a>__asm ブロックでの演算子の使用

**Microsoft 固有の仕様**

`__asm`ブロックがなど、C または C++ の特定の演算子を使用することはできません、 **<<** 演算子。 しかし、演算子、共有 C および MASM など、\*演算子は、アセンブリ言語の演算子として解釈されます。 たとえば、外部、`__asm`ブロック、角かっこ ( **[]** ) C は、配列内の要素のサイズを自動的にスケーリング配列の添字を囲むとして解釈されます。 内で、`__asm`ブロック、任意のデータ オブジェクトまたはラベル (配列だけでなく) から、スケールなしのバイト オフセットを生成 MASM インデックス演算子として出現します。 次のコードは、違いを示しています。

```cpp
int array[10];

__asm mov array[6], bx ;  Store BX at array+6 (not scaled)

array[6] = 0;         /* Store 0 at array+24 (scaled) */
```

最初に参照される`array`スケールされていないが、2 つ目は。 使用することに注意してください、**TYPE**定数に基づいてスケーリングを実現するために演算子。 たとえば、次のステートメントは同等です。

```cpp
__asm mov array[6 * TYPE int], 0 ; Store 0 at array + 24

array[6] = 0;                   /* Store 0 at array + 24 */
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__asm ブロックでの C または C++ の使用](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>