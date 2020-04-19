---
title: コンパイラの警告 (レベル 1) C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: 831789f5295fcf91e83de3bd0bba12c8429e9fa3
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966237"
---
# <a name="compiler-warning-level-1-c4584"></a>コンパイラの警告 (レベル 1) C4584

' class1 ': 基底クラス ' class2 ' は既に ' class3 ' の基底クラスです

定義したクラスは2つのクラスから継承します。1つは他方のクラスを継承します。 (例:

```cpp
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

この場合、クラス C に対して警告が発行されます。これは、クラス a とクラス B の両方を継承し、クラス A からも継承するためです。この警告は、これらの基本クラスのメンバーの使用を完全に修飾する必要があること、または参照しているクラスメンバーがあいまいであるためにコンパイラエラーが生成されることを示す通知として機能します。