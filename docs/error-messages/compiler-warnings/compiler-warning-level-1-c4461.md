---
title: コンパイラの警告 (レベル 1) C4461
ms.date: 11/04/2016
f1_keywords:
- C4461
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
ms.openlocfilehash: 195e5532b6555210077e43ad3086ee3106f3e757
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966008"
---
# <a name="compiler-warning-level-1-c4461"></a>コンパイラの警告 (レベル 1) C4461

'型' : このクラスはファイナライザー 'ファイナライザー' を含んでいますが、デストラクター 'dtor' を含んでいません

既に型に含まれているファイナライザーは、削除するリソースを暗黙に指定します。 オブジェクトがスコープ外になると、ファイナライザーが型のデストラクターから明示的に呼び出されない限り、共通言語ランタイムがファイナライザーを実行するタイミングを決定します。

型にデストラクターを定義し、そのデストラクターからファイナライザーを明示的に呼び出す場合は、ファイナライザーを実行するタイミングを決定できます。

詳細については、「[デストラクターとファイナライザー](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)」を参照してください。

## <a name="example"></a>例

次の例では、C4461 が生成されます。

```cpp
// C4461.cpp
// compile with: /W1 /clr /c
ref class A {
protected:
   !A() {}   // C4461
};

// OK
ref struct B {
   ~B() {
      B::!B();
   }

   !B() {}
};
```