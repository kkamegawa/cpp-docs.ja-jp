---
title: コンパイラ エラー C3400
ms.date: 11/04/2016
f1_keywords:
- C3400
helpviewer_keywords:
- C3400
ms.assetid: d44169a8-73b6-4766-b406-b3a6c93f2a4d
ms.openlocfilehash: cb4b9d03e10155383f2c58cca07253ae69c2c69a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737505"
---
# <a name="compiler-error-c3400"></a>コンパイラ エラー C3400

'constraint_1' と 'constraint_2' を含む、循環制約の依存関係です

コンパイラが循環制約を検出しました。

詳細については、「[Constraints on Generic Type Parameters (C++/CLI) (ジェネリック型パラメーターの (C++/CLI))](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)」を参照してください。

## <a name="example"></a>使用例

次の例では C3400 が生成されます。

```cpp
// C3400.cpp
// compile with: /clr /c
generic<class T, class U>
where T : U
where U : T   // C3400
public ref struct R {};
```
