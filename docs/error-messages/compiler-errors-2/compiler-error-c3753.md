---
title: コンパイラ エラー C3753
ms.date: 11/04/2016
f1_keywords:
- C3753
helpviewer_keywords:
- C3753
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
ms.openlocfilehash: 2970c4851d3e5cbbe9952c12a71c913c5e3ac656
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755331"
---
# <a name="compiler-error-c3753"></a>コンパイラ エラー C3753

ジェネリックプロパティは使用できません

ジェネリックパラメーターリストは、マネージクラス、構造体、または関数でのみ使用できます。

詳細については、「[ジェネリック](../../extensions/generics-cpp-component-extensions.md)と[プロパティ](../../extensions/property-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3753 が生成されます。

```cpp
// C3753.cpp
// compile with: /clr /c
ref struct A {
   generic <typename T>
   property int i;   // C3753 error
};
```
