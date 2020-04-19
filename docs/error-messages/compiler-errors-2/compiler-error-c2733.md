---
title: コンパイラエラー C2733
ms.date: 11/04/2016
f1_keywords:
- C2733
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
ms.openlocfilehash: 3ef669a49f4a3ec5a1af1a15a79f2511fa2699dd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755786"
---
# <a name="compiler-error-c2733"></a>コンパイラエラー C2733

オーバーロードされた関数 ' function ' の2番目の C リンケージは使用できません

複数のオーバーロードされた関数が C リンケージで宣言されています。 C リンケージを使用する場合、指定された関数の1つの形式のみが外部になることができます。 オーバーロードされた関数は、同じ非装飾名を持つため、C プログラムでは使用できません。

次の例では、C2733 が生成されます。

```cpp
// C2733.cpp
extern "C" {
   void F1(int);
}

extern "C" {
   void F1();   // C2733
   // try the following line instead
   // void F2();
}
```
