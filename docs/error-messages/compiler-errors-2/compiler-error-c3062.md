---
title: コンパイラ エラー C3062
ms.date: 11/04/2016
f1_keywords:
- C3062
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
ms.openlocfilehash: 9b1fbc8f4ca2ce3434a30e833f4741bc17015bbb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749530"
---
# <a name="compiler-error-c3062"></a>コンパイラ エラー C3062

' enum ': 基になる型が ' type ' であるため、列挙子には値が必要です

列挙型の基になる型を指定できます。 ただし、一部の型では、各列挙子に値を代入する必要があります。

列挙型の詳細については、「 [enum class](../../extensions/enum-class-cpp-component-extensions.md)」を参照してください。

次の例では、C3062 が生成されます。

```cpp
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```
