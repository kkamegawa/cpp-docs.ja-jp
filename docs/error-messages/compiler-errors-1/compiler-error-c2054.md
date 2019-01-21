---
title: コンパイラ エラー C2054
ms.date: 11/04/2016
f1_keywords:
- C2054
helpviewer_keywords:
- C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
ms.openlocfilehash: 7366995f8930b4733ccff73aef38ebcf65a0c120
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575657"
---
# <a name="compiler-error-c2054"></a>コンパイラ エラー C2054

'識別子'の後に'('が必要です。

関数識別子は、末尾のかっこを必要とするコンテキストで使用されます。

このエラーは、複雑な初期化の等号 (=) を省略することで発生することができます。

次の例では、C2054 が生成されます。

```
// C2054.c
int array1[] { 1, 2, 3 };   // C2054, missing =
```

考えられる解決方法:

```
// C2054b.c
int main() {
   int array2[] = { 1, 2, 3 };
}
```
