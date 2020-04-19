---
title: コンパイラ エラー C3749
ms.date: 11/04/2016
f1_keywords:
- C3749
helpviewer_keywords:
- C3749
ms.assetid: 3d26b468-4757-41b8-b5a2-78022a5295fb
ms.openlocfilehash: 75138bf8b090b7770d5bee918790efc095d76627
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761843"
---
# <a name="compiler-error-c3749"></a>コンパイラ エラー C3749

' attribute ': カスタム属性を関数内で使用することはできません

カスタム属性は関数内では使用できません。 カスタム属性の詳細については[、「」](../../windows/attributes/attribute.md)を参照してください。

## <a name="example"></a>使用例

次の例では、C3749 が生成されます。

```cpp
// C3749a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
public ref struct ABC : public Attribute {
   ABC() {}
};

void f1() { [ABC]; };  // C3749
```
