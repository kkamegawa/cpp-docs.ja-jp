---
title: コンパイラ エラー C2500
ms.date: 11/04/2016
f1_keywords:
- C2500
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
ms.openlocfilehash: 152546fce8f3ee63f8b95595bff052f18cd4ebda
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746969"
---
# <a name="compiler-error-c2500"></a>コンパイラ エラー C2500

' identifier1 ': ' identifier2 ' は既に直接基底クラスです

クラスまたは構造体が基底クラスのリストに複数回出現します。

直接ベースは、基本リストに記載されています。 間接基本は、基本リスト内のいずれかのクラスの基本クラスです。

クラスは、直接基底クラスとして複数回指定することはできません。 クラスは、間接的な基底クラスとして複数回使用できます。

次の例では、C2500 が生成されます。

```cpp
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```
