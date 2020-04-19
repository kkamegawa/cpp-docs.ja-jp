---
title: コンパイラ エラー C3414
ms.date: 11/04/2016
f1_keywords:
- C3414
helpviewer_keywords:
- C3414
ms.assetid: 715f5432-b509-4f8f-84f5-e1463bac490f
ms.openlocfilehash: ee1e6913d108d0e5519eac6399ed83ac057da9e2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742939"
---
# <a name="compiler-error-c3414"></a>コンパイラ エラー C3414

' member ': インポートされたメンバー関数は定義できません

メンバーは、参照されたアセンブリでも定義されているコードで定義されています。

次の例では、C3414 が生成されます。

```cpp
// C3414a2.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

この場合、次のようになります。

```cpp
// C3414b2.cpp
// compile with: /clr
#using <C3414a2.dll>

void MyClass::Test() {    // C3414
}

System::Object::Object() {    // C3414
}
```
