---
title: コンパイラ エラー C2457
ms.date: 11/04/2016
f1_keywords:
- C2457
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
ms.openlocfilehash: a08ac9f9cfbc332b90ad16c663349ee227427278
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347104"
---
# <a name="compiler-error-c2457"></a>コンパイラ エラー C2457

> '*マクロ*': 定義済みマクロが関数本体の外部で表示できません。

定義済みのマクロを使用しようとしています。 [ &#95;&#95;関数&#95;&#95;](../../preprocessor/predefined-macros.md)、グローバル空間内。

## <a name="example"></a>例

次の例では、C2457 を生成し、また正しい使用法を示します。

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```