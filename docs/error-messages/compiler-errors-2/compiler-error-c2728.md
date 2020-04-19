---
title: コンパイラエラー C2728
ms.date: 11/04/2016
f1_keywords:
- C2728
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
ms.openlocfilehash: ac9efa88fc4ab17a656172c44de2e49e82108108
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755669"
---
# <a name="compiler-error-c2728"></a>コンパイラエラー C2728

'type': ネイティブ配列はこの型を含むことはできません

配列作成の構文が、マネージドまたは WinRT オブジェクトの配列の作成に使用されました。 ネイティブ配列の構文を使用して、マネージドまたは WinRT オブジェクトの配列を作成することはできません。

詳細については、「 [配列](../../extensions/arrays-cpp-component-extensions.md)」を参照してください。

次の例では、C2728 を生成し、その修正方法を示しています。

```cpp
// C2728.cpp
// compile with: /clr

int main() {
   int^ arr[5];   // C2728

   // try the following line instead
   array<int>^arr2;
}
```
