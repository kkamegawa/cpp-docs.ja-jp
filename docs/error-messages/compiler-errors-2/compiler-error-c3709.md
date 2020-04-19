---
title: コンパイラ エラー C3709
ms.date: 11/04/2016
f1_keywords:
- C3709
helpviewer_keywords:
- C3709
ms.assetid: d5576b04-2f93-420a-8f3e-8b8e987e8dab
ms.openlocfilehash: 47320c79dbbfc2152c126c80d1eb8c061f3ceb3a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757918"
---
# <a name="compiler-error-c3709"></a>コンパイラ エラー C3709

' function ': __hook/\_でイベントを指定する構文が正しくありません _unhook

[__Hook](../../cpp/hook.md)または[__unhook](../../cpp/unhook.md)でイベントソースを指定する場合、最初のパラメーターは有効なイベントメソッドである必要があり、2番目のパラメーターは、(メソッドではなく) 有効なイベントソースオブジェクトである必要があります。

次の例では、C3709 が生成されます。

```cpp
// C3709.cpp
// compile with: /LD
[event_source(native)]
class CEventSrc
{
public:
   __event void event1();
};

[event_receiver(native)]
class CEventRec
{
public:
   void handler1()
   {
   }

   void HookEvents(CEventSrc* pSrc)
   {
      __hook(bad, pSrc, CEventRec::handler1);   // C3709
      // Try the following line instead:
      // __hook(&CEventSrc::event1, pSrc, CEventRec::handler1);
   }

   void UnhookEvents(CEventSrc* pSrc)
   {
      __unhook(&CEventSrc::event1, pSrc, CEventRec::handler1);
   }
};
```
