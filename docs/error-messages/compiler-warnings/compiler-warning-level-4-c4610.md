---
title: コンパイラの警告 (レベル 4) C4610
ms.date: 11/04/2016
f1_keywords:
- C4610
helpviewer_keywords:
- C4610
ms.assetid: 23c1a16c-9ca9-4bf6-9911-a72b785560c2
ms.openlocfilehash: 1cf8b9bd3194d03f5cb57a32ac78bfe82962d07c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990689"
---
# <a name="compiler-warning-level-4-c4610"></a>コンパイラの警告 (レベル 4) C4610

オブジェクト ' class ' はインスタンス化できません。ユーザー定義のコンストラクターが必要です

クラスには、ユーザー定義または既定のコンストラクターがありません。 インスタンス化は実行されません。 次の例では、C4610 が生成されます。

```cpp
// C4610.cpp
// compile with: /W4
struct A {
   int &j;

   A& A::operator=( const A& );
};   // C4610

/* use this structure definition to resolve the warning
struct B {
   int &k;

   B(int i = 0) : k(i) {
   }

   B& B::operator=( const B& );
} b;
*/

int main() {
}
```
