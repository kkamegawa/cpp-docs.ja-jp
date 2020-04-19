---
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: aec4df98413bf34ac1e2966d012bb905edd4775e
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857932"
---
# <a name="__noop"></a>__noop

**Microsoft 固有の仕様**

`__noop` 組み込みは、関数を無視する必要があることを指定します。 引数リストは解析されますが、引数のコードは生成されません。 これは、可変個の引数を受け取るグローバルデバッグ関数で使用することを目的としています。

コンパイラは、コンパイル時に組み込みの `__noop` を0に変換します。

## <a name="example"></a>使用例

次のコードは、`__noop`を使用する方法を示しています。

```cpp
// compiler_intrinsics__noop.cpp
// compile with or without /DDEBUG
#include <stdio.h>

#if DEBUG
   #define PRINT   printf_s
#else
   #define PRINT   __noop
#endif

int main() {
   PRINT("\nhello\n");
}
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[キーワード](../cpp/keywords-cpp.md)
