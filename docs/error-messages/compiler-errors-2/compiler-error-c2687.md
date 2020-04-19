---
title: コンパイラエラー C2687
ms.date: 11/04/2016
f1_keywords:
- C2687
helpviewer_keywords:
- C2687
ms.assetid: 1d24b24a-cd0f-41cc-975c-b08dcfb7f402
ms.openlocfilehash: f3e728033a3230d628242aab341377be2f6670ca
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760258"
---
# <a name="compiler-error-c2687"></a>コンパイラエラー C2687

' type ': 例外宣言を ' void ' にしたり、不完全な型、ポインター、または不完全な型への参照を意味したりすることはできません

型を例外宣言の一部として使用するには、型が void ではなく定義されている必要があります。

次の例では、C2687 が生成されます。

```cpp
// C2687.cpp
class C;

int main() {
   try {}
   catch (C) {}   // C2687 error
}
```

解決方法:

```cpp
// C2687b.cpp
// compile with: /EHsc
class C {};

int main() {
   try {}
   catch (C) {}
}
```
