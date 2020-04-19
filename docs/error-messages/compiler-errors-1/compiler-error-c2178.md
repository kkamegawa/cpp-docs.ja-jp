---
title: コンパイラエラー C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: 85cac4919c048c30a3ed1ff5573a3c14b77da0bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737193"
---
# <a name="compiler-error-c2178"></a>コンパイラエラー C2178

'*identifier*' を '*指定*子 ' 指定子と共に宣言することはできません

宣言で `mutable` 指定子が使用されましたが、このコンテキストでは指定子は許可されていません。

`mutable` 指定子は、クラスのデータメンバーの名前にのみ適用できます。また、`const` または `static`として宣言された名前には適用できません。また、参照メンバーには適用できません。

## <a name="example"></a>使用例

次の例では、C2178 の発生方法とその修正方法を示しています。

```cpp
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
