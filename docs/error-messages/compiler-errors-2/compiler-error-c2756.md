---
title: コンパイラエラー C2756
ms.date: 11/04/2016
f1_keywords:
- C2756
helpviewer_keywords:
- C2756
ms.assetid: 42eb988d-4043-4dee-8fd4-596949f69a55
ms.openlocfilehash: f9b3ea261db825f00004a2f447636c15d2d0d52e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759543"
---
# <a name="compiler-error-c2756"></a>コンパイラエラー C2756

'template type': 既定のテンプレート引数は部分的特殊化では使用できません

部分的特殊化用のテンプレートに既定の引数を含めることはできません。

次の例では、C2756 を生成し、その修正方法を示しています。

```cpp
// C2756.cpp
template <class T>
struct S {};

template <class T=int>
// try the following line instead
// template <class T>
struct S<T*> {};   // C2756
```
