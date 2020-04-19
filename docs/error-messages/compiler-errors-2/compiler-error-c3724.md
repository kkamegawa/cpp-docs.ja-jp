---
title: コンパイラ エラー C3724
ms.date: 11/04/2016
f1_keywords:
- C3724
helpviewer_keywords:
- C3724
ms.assetid: cab8aba7-14fc-406f-8cc6-32744c8f31c1
ms.openlocfilehash: b107137652c4efde43fdfe9c991240767eb5ced7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752978"
---
# <a name="compiler-error-c3724"></a>コンパイラ エラー C3724

イベントでマルチスレッドを使用するには \<windows .h > を #include する必要があります

イベントでマルチスレッドを使用する場合は、windows .h ファイルが必要です。 このエラーを修正するには、イベントソースとイベントレシーバーが定義されているファイルの先頭に `#include <windows.h>` を追加します。

```cpp
// C3724.cpp
// uncomment the following line to resolve
// #include <windows.h>

[event_source(native), threading(apartment)]
class CEventSrc {
public:
   __event void event1();   // C3724
};

[event_receiver(native)]
class CEventRec {
public:
   void handler1() {
   }

   void HookEvents(CEventSrc* pSrc) {
      __hook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }
};

int main() {
}
```
