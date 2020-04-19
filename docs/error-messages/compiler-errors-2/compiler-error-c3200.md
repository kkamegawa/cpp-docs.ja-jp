---
title: コンパイラ エラー C3200
ms.date: 11/04/2016
f1_keywords:
- C3200
helpviewer_keywords:
- C3200
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
ms.openlocfilehash: 7f6b514231bcda18404e891e0acbe457c8f95146
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738779"
---
# <a name="compiler-error-c3200"></a>コンパイラ エラー C3200

' template ': テンプレートパラメーター ' parameter ' の無効なテンプレート引数です。クラステンプレートが必要です

クラステンプレートに無効な引数を渡しました。 クラステンプレートでは、パラメーターとしてテンプレートが想定されています。 次の例では、`Y<int, int> aY` を呼び出すと、C3200 が生成されます。 最初のパラメーターは、`Y<X, int> aY`などのテンプレートである必要があります。

```cpp
// C3200.cpp
template<typename T>
class X
{
};

template<template<typename U> class T1, typename T2>
class Y
{
};

int main()
{
   Y<int, int> y;   // C3200
}
```
