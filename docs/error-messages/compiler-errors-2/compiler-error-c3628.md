---
title: コンパイラ エラー C3628
ms.date: 11/04/2016
f1_keywords:
- C3628
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
ms.openlocfilehash: 9976cb2425f8f855ffb2903c07de22822c781e20
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755825"
---
# <a name="compiler-error-c3628"></a>コンパイラ エラー C3628

' base class ': マネージクラスまたは WinRTclasses は、パブリック継承のみをサポートしています

マネージクラスまたは WinRT クラスを[プライベート](../../cpp/private-cpp.md)または[プロテクト](../../cpp/protected-cpp.md)基底クラスとして使用しようとしました。 マネージクラスまたは WinRT クラスは、[パブリック](../../cpp/public-cpp.md)アクセスを持つ基底クラスとしてのみ使用できます。

次の例は C3628 を生成し、その修正方法を示しています。

```cpp
// C3628a.cpp
// compile with: /clr
ref class B {
};

ref class D : private B {   // C3628

// The following line resolves the error.
// ref class D : public B {
};

int main() {
}
```
