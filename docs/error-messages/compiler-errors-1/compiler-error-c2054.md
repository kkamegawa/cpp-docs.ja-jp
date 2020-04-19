---
title: コンパイラエラー C2054
ms.date: 11/04/2016
f1_keywords:
- C2054
helpviewer_keywords:
- C2054
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
ms.openlocfilehash: e7d90d684c1d95f540f6357bf61ee7c6f889ad3f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302056"
---
# <a name="compiler-error-c2054"></a>コンパイラエラー C2054

'識別子'の後に'('が必要です。

関数識別子は、末尾にかっこが必要なコンテキストで使用されます。

このエラーは、複雑な初期化で等号 (=) を省略することによって発生することがあります。

次の例では、C2054 が生成されます。

```c
// C2054.c
int array1[] { 1, 2, 3 };   // C2054, missing =
```

解決方法:

```c
// C2054b.c
int main() {
   int array2[] = { 1, 2, 3 };
}
```
