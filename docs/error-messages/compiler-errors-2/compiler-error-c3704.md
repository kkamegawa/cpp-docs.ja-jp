---
title: コンパイラ エラー C3704
ms.date: 11/04/2016
f1_keywords:
- C3704
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
ms.openlocfilehash: 11e5792344b6f8fba6183f4ab87e1799db803b46
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757944"
---
# <a name="compiler-error-c3704"></a>コンパイラ エラー C3704

' function ': vararg メソッドはイベントを発生させることができません

Vararg メソッドで[__event](../../cpp/event.md)を使用しようとしました。 このエラーを解決するには、次のコードサンプルに示すように、`fireEvent(int i, ...)` 呼び出しを `fireEvent(int i)` 呼び出しに置き換えます。

次の例では、C3704 が生成されます。

```cpp
// C3704.cpp
[ event_source(native) ]
class CEventSrc {
   public:
      __event void fireEvent(int i, ...);   // C3704
      // try the following line instead:
      // __event void fireEvent(int i);
};

int main() {
}
```
