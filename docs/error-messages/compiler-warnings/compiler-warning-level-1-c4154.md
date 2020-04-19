---
title: コンパイラの警告 (レベル 1) C4154
ms.date: 11/04/2016
f1_keywords:
- C4154
helpviewer_keywords:
- C4154
ms.assetid: 4511afeb-e893-4cc6-83b6-4c7a0477f76b
ms.openlocfilehash: 3f0d56f6ae4b4ca92bc330d72176266e3196ea6a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625024"
---
# <a name="compiler-warning-level-1-c4154"></a>コンパイラの警告 (レベル 1) C4154

配列式の削除ポインターへの変換が指定されました

配列に対して `delete` を使用することはできないため、コンパイラは配列をポインターに変換します。

## <a name="example"></a>例

```cpp
// C4154.cpp
// compile with: /c /W1
int main() {
   int array[ 10 ];
   delete array;   // C4154 can't delete stack object

   int *parray2 = new int [10];
   int (&array2)[10] = (int(&)[10]) parray2;
   delete [] array2;   // C4154

   // try the following line instead
   delete [] &array2;
}
```