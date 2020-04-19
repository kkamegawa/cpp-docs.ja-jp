---
title: コンパイラ エラー C3282
ms.date: 11/04/2016
f1_keywords:
- C3282
helpviewer_keywords:
- C3282
ms.assetid: bac2ac89-c360-4c24-bb81-c20c62ece9ba
ms.openlocfilehash: a119f8a9482d3f49c98873fee6f54b434416ee48
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757580"
---
# <a name="compiler-error-c3282"></a>コンパイラ エラー C3282

ジェネリックパラメーターリストは、マネージまたは WinRTclasses、構造体、または関数でのみ使用できます

ジェネリック パラメーター リストが正しく使用されていません。  詳細については、「[ジェネリック](../../extensions/generics-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では C3282 を生成し、その修正方法を示しています。

```cpp
// C3282.cpp
// compile with: /clr /c
generic <typename T> int x;   // C3282

ref struct GC0 {
   generic <typename T> int x;   // C3282
};

// OK
generic <typename T>
ref class M {};
```
