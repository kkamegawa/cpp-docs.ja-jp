---
title: コンパイラ エラー C2870
ms.date: 11/04/2016
f1_keywords:
- C2870
helpviewer_keywords:
- C2870
ms.assetid: 80523ee9-1fd3-4dc4-8a77-5083deb99066
ms.openlocfilehash: 3b006592723df1222d05e39b3bc9e5729efc8aa6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755032"
---
# <a name="compiler-error-c2870"></a>コンパイラ エラー C2870

' name ': 名前空間定義は、ファイルスコープで、または別の名前空間定義のすぐ下に記述する必要があります

名前空間 `name` 正しく定義されていません。 名前空間は、ファイルスコープ (すべてのブロックおよびクラスの外側) または別の名前空間内で定義する必要があります。

次の例では、C2870 が生成されます。

```cpp
// C2870.cpp
// compile with: /c
int main() {
   namespace A { int i; };   // C2870
}
```
