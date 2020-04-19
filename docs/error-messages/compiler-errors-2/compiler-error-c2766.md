---
title: コンパイラエラー C2766
ms.date: 11/04/2016
f1_keywords:
- C2766
helpviewer_keywords:
- C2766
ms.assetid: 8032f4ca-6827-4f04-9c61-c44643c85cc4
ms.openlocfilehash: 48faee02bba18754972954a2ca464417bd552758
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759803"
---
# <a name="compiler-error-c2766"></a>コンパイラエラー C2766

明示的特殊化。' 特殊化 ' は既に定義されています

重複した明示的な特殊化は使用できません。 詳細については、「[関数テンプレートの明示的な特殊化](../../cpp/explicit-specialization-of-function-templates.md)」を参照してください。

次の例では、C2766 が生成されます。

```cpp
// C2766.cpp
// compile with: /c
template<class T>
struct A {};

template<>
struct A<int> {};

template<>
struct A<int> {};   // C2766
// try the following line instead
// struct A<char> {};
```
