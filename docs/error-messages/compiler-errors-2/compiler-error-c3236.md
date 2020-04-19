---
title: コンパイラ エラー C3236
ms.date: 11/04/2016
f1_keywords:
- C3236
helpviewer_keywords:
- C3236
ms.assetid: 4ef1871f-a348-44ae-922b-1e2081de20d0
ms.openlocfilehash: a7dd94cc807b312ef4860fa0bc1d7d1d97180624
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759387"
---
# <a name="compiler-error-c3236"></a>コンパイラ エラー C3236

generic の明示的なインスタンス生成は使用できません

コンパイラでは、ジェネリック クラスを明示的にインスタンス化できません。

次の例では C3236 が生成されます。

```cpp
// C3236.cpp
// compile with: /clr
generic<class T>
public ref class X {};

generic ref class X<int>;   // C3236
```

次の例では、考えられる解決策を示しています。

```cpp
// C3236b.cpp
// compile with: /clr /c
generic<class T>
public ref class X {};
```
