---
title: コンパイラの警告 (レベル 3) C4534
ms.date: 11/04/2016
f1_keywords:
- c4534
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
ms.openlocfilehash: 7d8ff442e84aa7563b1787e5a030297c034e1871
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992063"
---
# <a name="compiler-warning-level-3-c4534"></a>コンパイラの警告 (レベル 3) C4534

既定の引数により、' constructor ' はクラス ' class ' の既定のコンストラクターになりません

アンマネージクラスは、既定値を持つパラメーターを持つコンストラクターを持つことができ、コンパイラはこれを既定のコンストラクターとして使用します。 `value` キーワードでマークされたクラスは、パラメーターの既定値を持つコンストラクターを既定のコンストラクターとして使用しません。

詳細については、「[クラスと構造体](../../extensions/classes-and-structs-cpp-component-extensions.md)」を参照してください。

次の例では、C4534 が生成されます。

```cpp
// C4534.cpp
// compile with: /W3 /clr /WX
value class MyClass {
public:
   int ii;
   MyClass(int i = 9) {   // C4534, will not be the default constructor
      i++;
   }
};

int main() {
   MyClass ^ xx = gcnew MyClass;
   xx->ii = 0;
}
```
