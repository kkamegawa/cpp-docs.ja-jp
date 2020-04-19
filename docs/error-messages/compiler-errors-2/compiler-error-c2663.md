---
title: コンパイラエラー C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: f07b63202d8f171dfb69f4bb294b392152b9290b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756033"
---
# <a name="compiler-error-c2663"></a>コンパイラエラー C2663

' function ': 数値オーバーロードに ' this ' ポインターの有効な変換がありません

コンパイラは、`this` をメンバー関数のいずれかのオーバーロードされたバージョンに変換できませんでした。

このエラーは、`const` オブジェクトで非`const` メンバー関数を呼び出すことによって発生することがあります。  考えられる解決策は次のとおりです。

1. オブジェクト宣言から `const` を削除します。

1. メンバー関数のオーバーロードのいずれかに `const` を追加します。

次の例では、C2663 が生成されます。

```cpp
// C2663.cpp
struct C {
   void f() volatile {}
   void f() {}
};

struct D {
   void f() volatile;
   void f() const {}
};

const C *pcc;
const D *pcd;

int main() {
   pcc->f();    // C2663
   pcd->f();    // OK
}
```
