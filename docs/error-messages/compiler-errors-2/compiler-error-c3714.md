---
title: コンパイラ エラー C3714
ms.date: 11/04/2016
f1_keywords:
- C3714
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
ms.openlocfilehash: 1078bf8a97f6cb7afeaf7046489fe262c0bb0199
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753329"
---
# <a name="compiler-error-c3714"></a>コンパイラ エラー C3714

' method ': イベントハンドラーメソッドは、ソース ' method ' と同じ呼び出し規約を指定しなければなりません

ソースイベントメソッドと同じ呼び出し規約を使用していないイベントハンドラーメソッドを定義しました。 このエラーを解決するには、イベントハンドラーメソッドに、source イベントメソッドと同じ呼び出し規約を指定します。 たとえば、次のコードでは、`handler1` の呼び出し規則を作成し、`event1` ([__cdecl](../../cpp/cdecl.md)または[__stdcall](../../cpp/stdcall.md)など) に一致させます。 両方の宣言から呼び出し規約キーワードを削除すると、問題も解決され、`event1` と `handler1` が既定で[thiscall](../../cpp/thiscall.md)呼び出し規約になります。 詳細については、「[呼び出し規約](../../cpp/calling-conventions.md)」を参照してください。

次の例では、C3714 が生成されます。

```cpp
// C3714.cpp
// compile with: /c
// processor: x86
[event_source(native)]
class CEventSrc {
public:
   __event void __cdecl event1();
   // try the following line instead
   // __event void __stdcall event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void __stdcall handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3714
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3714
   }
};
```
