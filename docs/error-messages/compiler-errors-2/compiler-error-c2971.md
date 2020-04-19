---
title: コンパイラ エラー C2971
ms.date: 11/04/2016
f1_keywords:
- C2971
helpviewer_keywords:
- C2971
ms.assetid: fdb5467b-9a41-41ef-ac20-2e9428d5a4fc
ms.openlocfilehash: 9912224c5c871f9bae2c6d22f0d38f5f88c983a9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743290"
---
# <a name="compiler-error-c2971"></a>コンパイラ エラー C2971

' class ': テンプレートパラメーター ' param ': ' arg ': ローカル変数を非型引数として使用することはできません

ローカル変数の名前またはアドレスをテンプレート引数として使用することはできません。

次の例では、C2971 が生成されます。

```cpp
// C2971.cpp
template <int *pi>
class Y {};

int global_var = 0;

int main() {
   int local_var = 0;
   Y<&local_var> aY;   // C2971
   // try the following line instead
   // Y<&global_var> aY;
}
```
