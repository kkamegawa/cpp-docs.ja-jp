---
title: コンパイラ エラー C2270
ms.date: 11/04/2016
f1_keywords:
- C2270
helpviewer_keywords:
- C2270
ms.assetid: b52c068e-0b61-42e7-b775-4d57b3ddcba0
ms.openlocfilehash: 67dc970ffb5dac218072ff98046f88c31a9c2db9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758724"
---
# <a name="compiler-error-c2270"></a>コンパイラ エラー C2270

' function ': 修飾子は、非メンバー関数では使用できません

非メンバー関数は、 [const](../../cpp/const-cpp.md)、 [volatile](../../cpp/volatile-cpp.md)、または別のメモリモデル修飾子で宣言されています。

次の例では、C2270 が生成されます。

```cpp
// C2270.cpp
// compile with: /c
void func1(void) const;   // C2270, nonmember function

void func2(void);

class CMyClass {
public:
   void func2(void) const;
};
```
