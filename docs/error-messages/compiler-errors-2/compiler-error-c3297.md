---
title: コンパイラ エラー C3297
ms.date: 11/04/2016
f1_keywords:
- C3297
helpviewer_keywords:
- C3297
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
ms.openlocfilehash: 6fed01b0dcf50a657b6eb457ab8e546d0648beec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760096"
---
# <a name="compiler-error-c3297"></a>コンパイラ エラー C3297

'constraint_2':  'constraint_1' に値の制約があるために、'constraint_1' は制約として使用できません

値クラスがシールされています。 制約が値クラスの場合は、別の制約はそこから派生できません。

詳細については、「[Constraints on Generic Type Parameters (C++/CLI) (ジェネリック型パラメーターの (C++/CLI))](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)」を参照してください。

## <a name="example"></a>使用例

次の例では C3297 が生成されます。

```cpp
// C3297.cpp
// compile with: /clr /c
generic<class T, class U>
where T : value class
where U : T   // C3297
public ref struct R {};
```
