---
title: コンパイラ エラー C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: 0d2ea3677d883fa4843c37a41d733872b23cbba0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760674"
---
# <a name="compiler-error-c2801"></a>コンパイラ エラー C2801

' operator operator ' は静的でないメンバーでなければなりません

次の演算子は、非静的メンバーとしてのみオーバーロードできます。

- 割り当ての `=`

- クラスメンバーアクセス `->`

- 時 `[]`

- 関数呼び出し `()`

考えられる C2801 原因:

- オーバーロードされた演算子は、クラス、構造体、または共用体のメンバーではありません。

- オーバーロードされた演算子は `static`として宣言されます。

- 次の例では、C2801 が生成されます。

```cpp
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```
