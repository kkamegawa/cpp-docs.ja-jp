---
title: コンパイラエラー C3106
ms.date: 11/04/2016
f1_keywords:
- C3106
helpviewer_keywords:
- C3106
ms.assetid: 39d97a32-0905-4702-87d3-7f8ce473fb93
ms.openlocfilehash: 85aef1937ccbdbbbc335e4166fab11aa982b1839
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755838"
---
# <a name="compiler-error-c3106"></a>コンパイラエラー C3106

' attribute ': 名前のない引数は名前付き引数の前に指定しなければなりません

名前のない引数は、名前付き引数の前に属性に渡す必要があります。

詳細については、「 [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3106 が生成されます。

```cpp
// C3106.cpp
// compile with: /c
[module(name="MyLib", dll)];   // C3106
[module(dll, name="MyLib")];   // OK
```
