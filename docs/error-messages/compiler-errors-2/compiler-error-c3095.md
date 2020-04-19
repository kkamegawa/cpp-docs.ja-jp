---
title: コンパイラ エラー C3095
ms.date: 11/04/2016
f1_keywords:
- C3095
helpviewer_keywords:
- C3095
ms.assetid: cde725be-0936-40f6-9e57-e1d7d0710f83
ms.openlocfilehash: 1630def4fb2b22c948b3a33b081227d91351bf35
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756826"
---
# <a name="compiler-error-c3095"></a>コンパイラ エラー C3095

'attribute': 属性を繰り返して使用できません

複数回出現する属性がターゲットに適用されないように、いくつかの属性が宣言されます。

詳細については、「 [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では C3095 が生成されます。

```cpp
// C3095.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All, AllowMultiple=false)]
public ref class Attr : public Attribute {
public:
   Attr(int t) : m_t(t) {}
   const int m_t;
};

[AttributeUsage(AttributeTargets::All, AllowMultiple=true)]
public ref class Attr2 : public Attribute {
public:
   Attr2(int t) : m_t(t) {}
   const int m_t;
};

[Attr(10)]   // C3095
[Attr(11)]
ref class A {};

[Attr2(10)]   // OK
[Attr2(11)]
ref class B {};
```
