---
title: コンパイラ エラー C3612
ms.date: 11/04/2016
f1_keywords:
- C3612
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
ms.openlocfilehash: 499c31b0c02bd72695cd6118612609a70316f0ae
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755747"
---
# <a name="compiler-error-c3612"></a>コンパイラ エラー C3612

' type ': シールドクラスを抽象クラスにすることはできません

`value` を使用して定義された型は既定でシールされます。基底クラスのすべてのメソッドを実装しない限り、クラスは抽象クラスです。 シールされた抽象クラスは基底クラスにすることも、インスタンス化することもできません。

詳細については、「[クラスと構造体](../../extensions/classes-and-structs-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3612 が生成されます。

```cpp
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```
