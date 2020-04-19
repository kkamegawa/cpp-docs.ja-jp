---
title: コンパイラの警告 (レベル 1) C4946
ms.date: 11/04/2016
f1_keywords:
- C4946
helpviewer_keywords:
- C4946
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
ms.openlocfilehash: 238e842202bfde05f41d5ab7bc4e3eb2b8b63735
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050200"
---
# <a name="compiler-warning-level-1-c4946"></a>コンパイラの警告 (レベル 1) C4946

reinterpret_cast が関連クラスの間で使用されました : 'class1' と 'class2'

関連する型の間のキャストには[reinterpret_cast](../../cpp/reinterpret-cast-operator.md)を使用しないでください。 代わりに[static_cast](../../cpp/static-cast-operator.md)を使用するか、ポリモーフィックな型の場合は[dynamic_cast](../../cpp/dynamic-cast-operator.md)を使用します。

既定では、この警告はオフになっています。 詳細については、「 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)」を参照してください。

次のコード例では、C4946 が生成されます。

```cpp
// C4946.cpp
// compile with: /W1
#pragma warning (default : 4946)
class a {
public:
   a() : m(0) {}
   int m;
};

class b : public virtual a {
};

class b2 : public virtual a {
};

class c : public b, public b2 {
};

int main() {
   c* pC = new c;
   a* pA = reinterpret_cast<a*>(pC);   // C4946
   // try the following line instead
   // a* pA = static_cast<a*>(pC);
}
```