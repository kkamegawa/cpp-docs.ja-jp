---
title: コンパイラの警告 (レベル 3) C4316
ms.date: 11/04/2016
f1_keywords:
- C4316
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
ms.openlocfilehash: 5f895a231c8b32d76e4ccd3c15ffae5717d8017f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402048"
---
# <a name="compiler-warning-level-3-c4316"></a>コンパイラの警告 (レベル 3) C4316

ヒープで割り当てられているオブジェクトが、この型にアラインされていない可能性があります。

`operator new` を使用して割り当てられたオブジェクトがオーバーアラインされている場合は、このオブジェクトにアラインメントが指定されていない可能性があります。 オーバーライド[new 演算子](../../c-runtime-library/operator-new-crt.md)と[delete 演算子](../../c-runtime-library/operator-delete-crt.md)のアラインされた割り当てルーチンを使用するようオーバーア ラインされた型: たとえば、 [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md)と[_aligned_free](../../c-runtime-library/reference/aligned-free.md)します。 次の例では、C4316 が生成されます。

```cpp
// C4316.cpp
// Test: cl /W3 /c C4316.cpp

__declspec(align(32)) struct S {}; // C4324

int main() {
    new S; // C4316
}
```