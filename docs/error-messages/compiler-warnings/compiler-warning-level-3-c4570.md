---
title: コンパイラの警告 (レベル 3) C4570
ms.date: 11/04/2016
f1_keywords:
- C4570
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
ms.openlocfilehash: 13767cdbd34c72953568181c15ad33119bf5179a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991930"
---
# <a name="compiler-warning-level-3-c4570"></a>コンパイラの警告 (レベル 3) C4570

' type ': は抽象として明示的に宣言されていませんが、抽象関数を含んでいます

[抽象](../../extensions/abstract-cpp-component-extensions.md)関数を含む型は、それ自体が abstract としてマークされている必要があります。

## <a name="example"></a>使用例

次の例では、C4570 が生成されます。

```cpp
// C4570.cpp
// compile with: /clr /W3 /c
ref struct X {   // C4570
// try the following line instead
// ref class X abstract {
   virtual void f() abstract;
};
```
