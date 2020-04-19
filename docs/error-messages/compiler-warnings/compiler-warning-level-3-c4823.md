---
title: コンパイラの警告 (レベル 3) C4823
ms.date: 11/04/2016
f1_keywords:
- C4823
helpviewer_keywords:
- C4823
ms.assetid: 8a77560d-dcea-4cae-aebb-8ebf1b4cef85
ms.openlocfilehash: a96877252b0b7699f5e4033f8e695f4d9016a6c9
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541260"
---
# <a name="compiler-warning-level-3-c4823"></a>コンパイラの警告 (レベル 3) C4823

' function ': 固定ポインターを使用しますが、アンワインドセマンティクスは有効ではありません。 /EHa の使用を検討する

ブロックスコープ内で宣言されているピンポインターによって指されているマネージヒープ上のオブジェクトの固定を解除するために、コンパイラはローカルクラスのデストラクターの動作をシミュレートします。 "偽装" は、固定ポインターにポインターを nullifies するデストラクターを持っています。 例外をスローした後にデストラクターの呼び出しを有効にするには、オブジェクトのアンワインドを有効にする必要があります。これは、 [/ehsc](../../build/reference/eh-exception-handling-model.md)を使用して実行できます。

また、手動でオブジェクトの固定を解除し、警告を無視することもできます。

## <a name="example"></a>使用例

次の例では、C4823 が生成されます。

```cpp
// C4823.cpp
// compile with: /clr /W3 /EHa-
using namespace System;

ref struct G {
   int m;
};

void f(G ^ pG) {
   try {
      pin_ptr<int> p = &pG->m;
      // manually unpin, ignore warning
      // p = nullptr;
      throw gcnew Exception;
   }
   catch(Exception ^) {}
}   // C4823 warning

int main() {
   f( gcnew G );
}
```
