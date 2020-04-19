---
title: コンパイラ エラー C2164
ms.date: 11/04/2016
f1_keywords:
- C2164
helpviewer_keywords:
- C2164
ms.assetid: 55df5024-68a8-45a8-ae6c-e6dba35318a2
ms.openlocfilehash: 74c4f0e24f21f21d7a7015a20cb0e27ac635c467
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301913"
---
# <a name="compiler-error-c2164"></a>コンパイラ エラー C2164

' function ': 組み込み関数が宣言されていません。

`intrinsic` プラグマは宣言されていない関数を使用します ( **/Oi**でのみ発生します)。 または、コンパイラの組み込みの1つがヘッダーファイルを含めずに使用されました。

次の例では、C2164 が生成されます。

```c
// C2164.c
// compile with: /c
// processor: x86
// Uncomment the following line to resolve.
// #include "xmmintrin.h"
void b(float *p) {
   _mm_load_ss(p);   // C2164
}
```
