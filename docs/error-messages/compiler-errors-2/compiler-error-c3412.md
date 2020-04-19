---
title: コンパイラ エラー C3412
ms.date: 11/04/2016
f1_keywords:
- C3412
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
ms.openlocfilehash: ad241b656464746333760cfcbc134c91e49bf44e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761417"
---
# <a name="compiler-error-c3412"></a>コンパイラ エラー C3412

' template ': 現在のスコープでテンプレートを特殊化できません

テンプレートはクラススコープで特殊化できません。グローバルまたは名前空間スコープでのみ使用できます。

## <a name="example"></a>使用例

次の例では、C3412 が生成されます。

```cpp
// C3412.cpp
template <class T>
struct S {
   template <>
   struct S<int> {};   // C3412 in a class
};
```

## <a name="example"></a>使用例

次の例は、考えられる解決方法を示しています。

```cpp
// C3412b.cpp
// compile with: /c
template <class T>
struct S {};

template <>
struct S<int> {};
```
