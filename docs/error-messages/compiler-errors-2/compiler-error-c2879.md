---
title: コンパイラ エラー C2879
ms.date: 11/04/2016
f1_keywords:
- C2879
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
ms.openlocfilehash: 6c7238faf94a2493894534ae5684634b65bb4342
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736296"
---
# <a name="compiler-error-c2879"></a>コンパイラ エラー C2879

' symbol ': 名前空間エイリアスの定義により、既存の名前空間に代替名を指定することはできません

名前空間以外のシンボルに対して[名前空間エイリアス](../../cpp/namespaces-cpp.md#namespace_aliases)を作成することはできません。

次の例では、C2879 が生成されます。

```cpp
// C2879.cpp
int main() {
   int i;
   namespace A = i;   // C2879 i is not a namespace
}
```
