---
title: コンパイラの警告 (レベル 1) C4216
ms.date: 11/04/2016
f1_keywords:
- C4216
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
ms.openlocfilehash: 69559348a27151a22b11cae8d821110d923cd803
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627339"
---
# <a name="compiler-warning-level-1-c4216"></a>コンパイラの警告 (レベル 1) C4216

非標準の拡張機能が使用されています: float long

既定の Microsoft 拡張機能 (/Ze) では、**float long**は**double**として扱われます。 ANSI 互換 ([/za](../../build/reference/za-ze-disable-language-extensions.md)) ではありません。 互換性を維持するには、 **double**を使用します。 次の例では、C4216 が生成されます。

```cpp
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```