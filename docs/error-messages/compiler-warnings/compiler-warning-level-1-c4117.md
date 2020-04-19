---
title: コンパイラの警告 (レベル 1) C4117
ms.date: 11/04/2016
f1_keywords:
- C4117
helpviewer_keywords:
- C4117
ms.assetid: c45aa281-4cc1-4dfd-bd32-bd7a60ddd577
ms.openlocfilehash: 97fd5703a744448db87634e313678cf4e824df7f
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626284"
---
# <a name="compiler-warning-level-1-c4117"></a>コンパイラの警告 (レベル 1) C4117

マクロ名 'name' は予約されています。"Command" は無視されます

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. 定義済みマクロを定義するか未定義にしようとしています。

1. プリプロセッサ演算子 **defined**を定義するか未定義にしようとしています。

次の例では C4117 が生成されます。

```cpp
// C4117.cpp
// compile with: /W1
#define __FILE__ test         // C4117. __FILE__ is a predefined macro
#define ValidMacroName test   // ok

int main() {
}
```