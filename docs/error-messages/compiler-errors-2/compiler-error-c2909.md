---
title: コンパイラ エラー C2909
ms.date: 11/04/2016
f1_keywords:
- C2909
helpviewer_keywords:
- C2909
ms.assetid: 1c9df8ae-925d-4002-a5f8-a71413c45f9e
ms.openlocfilehash: 6c9a40bd271fa04146193e8315e205e293e8a34d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750482"
---
# <a name="compiler-error-c2909"></a>コンパイラ エラー C2909

'identifier': 関数テンプレートの明示的なインスタンス化には戻り値の型が必要です

関数テンプレートの明示的なインスタンス化では、戻り値の型の明示的な指定が必要です。 暗黙の戻り値型の仕様は機能しません。

次の例では C2909 が生成されます。

```cpp
// C2909.cpp
// compile with: /c
template<class T> int f(T);
template f<int>(int);         // C2909
template int f<int>(int);   // OK
```
