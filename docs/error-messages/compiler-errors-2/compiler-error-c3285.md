---
title: コンパイラ エラー C3285
ms.date: 11/04/2016
f1_keywords:
- C3285
helpviewer_keywords:
- C3285
ms.assetid: 04e8f210-d67e-4810-b153-e1efe2986c8f
ms.openlocfilehash: f5799511575617ad1705bbce50a939ee46599628
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755344"
---
# <a name="compiler-error-c3285"></a>コンパイラ エラー C3285

for each ステートメントは、型 'type' の変数で操作できません

`for each` ステートメントは、配列またはオブジェクト コレクションのそれぞれの要素に対して、埋め込みステートメントのグループを繰り返します。

詳細については、「 [for each, in](../../dotnet/for-each-in.md) 」を参照してください。

## <a name="example"></a>使用例

次の例では C3285 が生成されます。

```cpp
// C3285.cpp
// compile with: /clr
int main() {
   for each (int i in 0) {}   // C3285

   array<int> ^p = { 1, 2, 3 };
   for each (int j in p) {}   // OK
}
```
