---
title: コンパイラの警告 (レベル 4) C4127
ms.date: 10/16/2019
f1_keywords:
- C4127
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
ms.openlocfilehash: bef825f546573b878c415c385e1a2a2286e08db4
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444906"
---
# <a name="compiler-warning-level-4-c4127"></a>コンパイラの警告 (レベル 4) C4127

> 条件式が定数です。

## <a name="remarks"></a>Remarks

**If**ステートメントまたは**while**ループの制御式が定数に評価されます。 慣用的なの一般的な使用方法により、Visual Studio 2015 update 3 以降では、1や**true**などの自明な定数は、式の演算の結果でない限り、警告をトリガーしません。

ループが途中で終了するため**に while**ループの制御式が定数である場合は、 **while**ループを**for**ループに置き換えることを検討してください。 **For**ループの初期化、終了テスト、およびループインクリメントを省略すると、`while(1)` と同じようにループが無限に**なるため、for ステートメントの**本体からループを終了できます。

## <a name="example"></a>例

次の例は、C4127 が生成される2つの方法を示しています。また、for ループを使用して警告を回避する方法を示しています。

```cpp
// C4127.cpp
// compile with: /W4
#include <stdio.h>
int main() {
   if (true) {}           // OK in VS2015 update 3 and later
   if (1 == 1) {}         // C4127
   while (42) { break; }  // C4127

   // OK
   for ( ; ; ) {
      printf("test\n");
      break;
   }
}
```

この警告は、条件式でコンパイル時定数が使用されている場合にも生成されます。


```cpp
#include <string>

using namespace std;

template<size_t S, class T>
void MyFunc()
{
   if (sizeof(T) >= S) // C4127. "Consider using 'if constexpr' statement instead"
   {
   }
}

class Foo
{
   int i;
   string s;
};

int main()
{
   Foo f;
   MyFunc<4, Foo>();
}
```