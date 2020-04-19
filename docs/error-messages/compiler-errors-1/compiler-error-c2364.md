---
title: コンパイラ エラー C2364
ms.date: 11/04/2016
f1_keywords:
- C2364
helpviewer_keywords:
- C2364
ms.assetid: 4f550571-94b5-42ca-84cb-663fecbead44
ms.openlocfilehash: fb019d729bc100296742b15ba95460fe0e404673
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759881"
---
# <a name="compiler-error-c2364"></a>コンパイラ エラー C2364

' type ': カスタム属性の型が正しくありません。

カスタム属性の名前付き引数は、コンパイル時の定数に限定されます。 たとえば、整数型 (int、char など)、System:: Type ^、System:: Object ^ などです。

## <a name="example"></a>使用例

次の例では、C2364 が生成されます。

```cpp
// c2364.cpp
// compile with: /clr /c
using namespace System;

[attribute(AttributeTargets::All)]
public ref struct ABC {
public:
   // Delete the following line to resolve.
   ABC( Enum^ ) {}   // C2364
   ABC( int ) {}   // OK
};
```
