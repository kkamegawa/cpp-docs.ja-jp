---
title: コンパイラエラー C2601
ms.date: 11/04/2016
f1_keywords:
- C2601
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
ms.openlocfilehash: 87b5afe2133bb737a8f9c855b0652c2f50ca27ec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740521"
---
# <a name="compiler-error-c2601"></a>コンパイラエラー C2601

' function ': ローカル関数の定義が正しくありません。

コードは関数内で関数を定義しようとします。

または、C2601 エラーの場所の前に、ソースコードに余分な中かっこが含まれている可能性があります。

次の例では、C2601 が生成されます。

```cpp
// C2601.cpp
int main() {
   int i = 0;

   void funcname(int j) {   // C2601
      j++;
   }
}
```
