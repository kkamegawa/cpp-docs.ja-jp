---
title: コンパイラ エラー C3299
ms.date: 11/04/2016
f1_keywords:
- C3299
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
ms.openlocfilehash: 148433f0d959985eb5a874f588f8cbf9d377e8b7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735958"
---
# <a name="compiler-error-c3299"></a>コンパイラ エラー C3299

'member_function': 制約を指定できません。それらは基本メソッドから継承されています

汎用的なメンバー関数をオーバーライドする場合は、制約句を指定できません (制約を繰り返すことは、制約が継承されないことを意味します)。

オーバーライドするジェネリック関数の制約句が継承されます。

詳細については、「[Constraints on Generic Type Parameters (C++/CLI) (ジェネリック型パラメーターの (C++/CLI))](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)」を参照してください。

## <a name="example"></a>使用例

次の例では C3299 が生成されます。

```cpp
// C3299.cpp
// compile with: /clr /c
public ref struct R {
   generic<class T>
   where T : R
   virtual void f();
};

public ref struct S : R {
   generic<class T>
   where T : R   // C3299
   virtual void f() override;
};
```
