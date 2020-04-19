---
title: コンパイラ エラー C2908
ms.date: 11/04/2016
f1_keywords:
- C2908
helpviewer_keywords:
- C2908
ms.assetid: 49cd2a21-cad8-4ba0-9a0b-3a0190d9344c
ms.openlocfilehash: ca07ef3c8240e6a55137e07bccbfc61ca8d96636
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750560"
---
# <a name="compiler-error-c2908"></a>コンパイラ エラー C2908

明示的特殊化。' template ' は既にインスタンス化されています

プライマリテンプレートの特殊化は、明示的な特殊化の前に発生します。

次の例では、C2908 が生成されます。

```cpp
// C2908.cpp
// compile with: /c
template<class T> class X {};

void f() {
X<int> x;   //specialization and instantiation
            //of X<int>
}

template<> class X<int> {}  // C2908, explicit specialization
```
