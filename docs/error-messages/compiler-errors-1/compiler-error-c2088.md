---
title: コンパイラエラー C2088
ms.date: 11/04/2016
f1_keywords:
- C2088
helpviewer_keywords:
- C2088
ms.assetid: b93f7094-185b-423d-8bb9-507cd757dbf5
ms.openlocfilehash: 1f798774a7735a6aceb0bf75b3c6da9ccb1e4a72
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301978"
---
# <a name="compiler-error-c2088"></a>コンパイラエラー C2088

' operator ': ' class-key ' に対して無効です。

演算子が構造体または共用体に対して定義されていません。 このエラーは、C コードに対してのみ有効です。

次の例では、C2088 が3回生成されます。

```c
// C2088.c
struct S {
   int m_i;
} s;

int main() {
   int i = s * 1;   // C2088
   struct S s2 = +s;   // C2088
   s++;   // C2088
}
```
