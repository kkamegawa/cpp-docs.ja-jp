---
title: コンパイラの警告 (レベル 1) C4075
ms.date: 11/04/2016
f1_keywords:
- C4075
helpviewer_keywords:
- C4075
ms.assetid: 19a700b6-f210-4b9d-a2f2-76cfe39ab178
ms.openlocfilehash: b4181059a406d85514c3941ed2856d9e95673957
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626954"
---
# <a name="compiler-warning-level-1-c4075"></a>コンパイラの警告 (レベル 1) C4075

初期化子が不明な初期化領域にあります。

[#pragma init_seg](../../preprocessor/init-seg.md) が認識できないセクション名を使用しています。 コンパイラはこの **pragma** コマンドを無視します。

次の例では C4075 が生成されます。

```cpp
// C4075.cpp
// compile with: /W1
#pragma init_seg("mysegg")   // C4075

// try..
// #pragma init_seg(user)

int main() {
}
```