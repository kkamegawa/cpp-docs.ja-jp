---
title: コンパイラ エラー C2232
ms.date: 11/04/2016
f1_keywords:
- C2232
helpviewer_keywords:
- C2232
ms.assetid: 76f302b7-30a7-4a81-9a39-b4edde33b54c
ms.openlocfilehash: 78ed8970b29126bceb06ff89d12c83cb98c4b5fd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301809"
---
# <a name="compiler-error-c2232"></a>コンパイラ エラー C2232

'-> ': 左オペランドに ' class-key ' 型が含まれています。 '. ' を使用してください。

`->` 演算子の左のオペランドがポインターではありません。 クラス、構造体、または共用体にはピリオド (.) 演算子を使用します。

次の例では C2232 が生成されます。

```c
// C2232.c
struct X {
    int member;
} x, *px;
int main() {
    x->member = 0;   // C2232, x is not a pointer

    px->member = 0;
    x.member = 0;
}
```
