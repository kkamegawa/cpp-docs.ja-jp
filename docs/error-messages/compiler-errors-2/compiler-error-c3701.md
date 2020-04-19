---
title: コンパイラ エラー C3701
ms.date: 11/04/2016
f1_keywords:
- C3701
helpviewer_keywords:
- C3701
ms.assetid: a7faaa87-d2f5-4d6a-9a2f-5cab2d24a648
ms.openlocfilehash: 6852d130b0f10282b8c22b0053760eca120252c7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758022"
---
# <a name="compiler-error-c3701"></a>コンパイラ エラー C3701

' function ': event_source にイベントがありません

イベントメソッドのないクラスで[event_source](../../windows/event-source.md)を使用しようとしました。 このエラーを解決するには、クラスに1つ以上のイベントを追加します。

次の例では、C3701 が生成されます。

```cpp
// C3701.cpp
[ event_source(native) ]
class CEventSrc {
public:
   // uncomment the following line to resolve this C3701
   // __event void fireEvent(int i);
};   // C3701

int main() {
}
```
