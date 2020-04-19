---
title: コンパイラ エラー C2196
ms.date: 11/04/2016
f1_keywords:
- C2196
helpviewer_keywords:
- C2196
ms.assetid: fd2f6a58-48ce-4e58-96f8-e37720feb8e7
ms.openlocfilehash: ec677e14b856f4b8a572006d61668ef089e42834
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758516"
---
# <a name="compiler-error-c2196"></a>コンパイラ エラー C2196

case の値 'value' は既に使用されています。

switch ステートメントで、同じ case 値を複数回使用します。

次の例では C2196 が生成されます。

```cpp
// C2196.cpp
int main() {
   int i = 0;
   switch( i ) {
   case 0:
      break;
   case 0:   // C2196
   // try the following line instead
   // case 1:
      break;
   }
}
```
