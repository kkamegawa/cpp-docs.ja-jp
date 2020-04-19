---
title: コンパイラの警告 (レベル 1) C4145
ms.date: 11/04/2016
f1_keywords:
- C4145
helpviewer_keywords:
- C4145
ms.assetid: 0440777a-cca2-4159-aff5-e67a254ad64a
ms.openlocfilehash: a6ae6145749842c01e720f5af1fe2b3ee438a5ba
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624990"
---
# <a name="compiler-warning-level-1-c4145"></a>コンパイラの警告 (レベル 1) C4145

'expression1' : switch ステートメントの制御式と関係する式 ; 式 'expression2' は、case 式と見なされます

`switch` ステートメントで、関係式をその制御式として使用した結果、 **case** ステートメントにブール値が返されます。 *expression2*を意図していましたか。

## <a name="example"></a>例

次の例では C4145 が生成されます。

```cpp
// C4145.cpp
// compile with: /W1
int main() {
   int i = 0;
   switch(i == 1) {   // C4145, use i instead of i == 1 to resolve
      case 1:
         break;
      default:
         break;
   }
}
```