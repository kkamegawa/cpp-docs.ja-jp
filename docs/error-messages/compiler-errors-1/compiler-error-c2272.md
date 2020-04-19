---
title: コンパイラ エラー C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: fd6fdecd3a491ce5f068f4d51d413e6767aabe2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758698"
---
# <a name="compiler-error-c2272"></a>コンパイラ エラー C2272

' function ': 静的メンバー関数では、修飾子は使用できません

`static` メンバー関数は、 [const](../../cpp/const-cpp.md)や[volatile](../../cpp/volatile-cpp.md)などのメモリモデル指定子を使用して宣言されています。このような修飾子は、`static` メンバー関数では使用できません。

次の例では、C2272 が生成されます。

```cpp
// C2272.cpp
// compile with: /c
class CMyClass {
public:
   static void func1() const volatile;   // C2272  func1 is static
   void func2() const volatile;   // OK
};
```
