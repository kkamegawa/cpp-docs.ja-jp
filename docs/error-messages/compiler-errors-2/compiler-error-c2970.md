---
title: コンパイラ エラー C2970
ms.date: 11/04/2016
f1_keywords:
- C2970
helpviewer_keywords:
- C2970
ms.assetid: 21d90348-20d3-438c-b278-efdbfb93a7d2
ms.openlocfilehash: af30ccc4a71c51d042d6f7807a648a1eef066a70
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742666"
---
# <a name="compiler-error-c2970"></a>コンパイラ エラー C2970

' class ': テンプレートパラメーター ' param ': ' arg ': 内部リンケージを持つオブジェクトを含む式を非型引数として使用することはできません

静的変数の名前またはアドレスをテンプレート引数として使用することはできません。 テンプレートクラスには、コンパイル時に評価できる const 値が必要です。

次の例では、C2970 が生成されます。

```cpp
// C2970.cpp
// compile with: /c
static int si;
// could declare nonstatic to resolve all errors
// int si;

template <int i>
class X {};

template <int *pi>
class Y {};

X<si> anX;   // C2970 cannot use static variable in templates

// this would also work
const int i = 10;
X<i> anX2;
```
