---
title: コンパイラ エラー C2584
ms.date: 11/04/2016
f1_keywords:
- C2584
helpviewer_keywords:
- C2584
ms.assetid: 836e2c0a-86c0-4742-b432-beb0191ad20e
ms.openlocfilehash: 2c3b10ecd6808ccd864ecf877fe9f1d0e9f30a3a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748633"
---
# <a name="compiler-error-c2584"></a>コンパイラ エラー C2584

' Class ': direct base ' Base2 ' にアクセスできません。' Base1 ' のベースが既にあります

`Class` は `Base1`から直接派生しています。 `Base2` も `Base1`から派生します。 `Base1` は既に直接基底クラスであるため、`Class` を `Base2` から派生させることはできません。これは `Base1` から間接的に継承することを意味します。

## <a name="example"></a>使用例

次の例では、C2584 が生成されます。

```cpp
// C2584.cpp
// compile with: /c
struct A1 {
   virtual int MyFunction();
};

struct A2 {
    virtual int MyFunction();
};

struct B1: public virtual A1, virtual A2 {
    virtual int MyFunction();
};

struct B2: public virtual A2, virtual A1 {
    virtual int MyFunction();
};

struct C: virtual B1, B2 {
    virtual int MyFunction();
};

struct Z : virtual B2, virtual C {   // C2584
// try the following line insted
// struct Z : virtual C {
    virtual int MyFunction();
};
```
