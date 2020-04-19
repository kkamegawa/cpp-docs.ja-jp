---
title: pop_macro プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.pop_macro
- pop_macro_CPP
helpviewer_keywords:
- pop_macro pragma
- pragmas, pop_macro
ms.assetid: 3b5489d0-69ba-4c66-b572-2748af0f12bb
ms.openlocfilehash: f9e097d139e1df5c9ba09ad9ca99f0cfe6bbbfb3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218285"
---
# <a name="pop_macro-pragma"></a>pop_macro プラグマ

*マクロ名*マクロの値を、このマクロのスタックの一番上にある値に設定します。

## <a name="syntax"></a>構文

> **#pragma pop_macro (** "*マクロ名*" **)**

## <a name="remarks"></a>Remarks

**Pop_macro**を実行する前に、 [push_macro](../preprocessor/push-macro.md)の*マクロ名*を発行する必要があります。

## <a name="example"></a>例

```cpp
// pragma_directives_pop_macro.cpp
// compile with: /W1
#include <stdio.h>
#define X 1
#define Y 2

int main() {
   printf("%d",X);
   printf("\n%d",Y);
   #define Y 3   // C4005
   #pragma push_macro("Y")
   #pragma push_macro("X")
   printf("\n%d",X);
   #define X 2   // C4005
   printf("\n%d",X);
   #pragma pop_macro("X")
   printf("\n%d",X);
   #pragma pop_macro("Y")
   printf("\n%d",Y);
}
```

```Output
1
2
1
2
1
3
```

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
