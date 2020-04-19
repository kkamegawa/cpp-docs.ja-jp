---
title: コンパイラ エラー C3909
ms.date: 11/04/2016
f1_keywords:
- C3909
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
ms.openlocfilehash: 69613a1058bd5178ea4c03931664dd00bad7a101
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748997"
---
# <a name="compiler-error-c3909"></a>コンパイラ エラー C3909

aWinRT またはマネージイベントの宣言は、WinRT またはマネージ型で発生する必要があります

Windows ランタイム イベントまたはマネージド イベントがネイティブ型内で宣言されました。 このエラーを修正するには、Windows ランタイム型またはマネージド型内でイベントを宣言します。

詳細については、「 [event](../../extensions/event-cpp-component-extensions.md)」を参照してください。

次の例では、C3909 を生成し、その修正方法を示しています。

```cpp
// C3909.cpp
// compile with: /clr /c
delegate void H();
class X {
   event H^ E;   // C3909 - use ref class X instead
};

ref class Y {
   static event H^ E {
      void add(H^) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```
