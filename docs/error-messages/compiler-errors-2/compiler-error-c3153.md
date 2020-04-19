---
title: コンパイラ エラー C3153
ms.date: 11/04/2016
f1_keywords:
- C3153
helpviewer_keywords:
- C3153
ms.assetid: d775d97e-2480-484f-81f1-88406b10f947
ms.openlocfilehash: 54fa7de8eb3df8d4b3695544c5285cc202275492
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745917"
---
# <a name="compiler-error-c3153"></a>コンパイラ エラー C3153

' interface ': インターフェイスのインスタンスを作成することはできません。

インターフェイスをインスタンス化することはできません。 インターフェイスのメンバーを使用するには、インターフェイスからクラスを派生させ、インターフェイスメンバーを実装してから、メンバーを使用します。

次の例では、C3153 が生成されます。

```cpp
// C3153.cpp
// compile with: /clr
interface class A {
};

int main() {
   A^ a = gcnew A;   // C3153
}
```
