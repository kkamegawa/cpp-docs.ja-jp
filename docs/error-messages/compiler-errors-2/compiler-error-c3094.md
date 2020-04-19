---
title: コンパイラ エラー C3094
ms.date: 11/04/2016
f1_keywords:
- C3094
helpviewer_keywords:
- C3094
ms.assetid: 10da9b7c-e72d-4013-9925-c83e1bb142db
ms.openlocfilehash: 9c9d3aaf8911e74734bb6a8ac03dfd6ebe5bc7a8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751327"
---
# <a name="compiler-error-c3094"></a>コンパイラ エラー C3094

'attribute': 匿名使用は許可されていません

属性のスコープを正しく指定しませんでした。  詳細については、「 [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では C3094 が生成されます。

```cpp
// C3094.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class)]
public ref class AAttribute : Attribute {};

[A];   // C3094

// OK
[A]
ref class x{};
```
