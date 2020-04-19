---
title: コンパイラ エラー C3213
ms.date: 11/04/2016
f1_keywords:
- C3213
helpviewer_keywords:
- C3213
ms.assetid: 1f079e36-b3e9-40f8-8e95-08eeba3adc82
ms.openlocfilehash: c172ebbc133690eabe5ca25e4427c2c22e8221bf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756202"
---
# <a name="compiler-error-c3213"></a>コンパイラ エラー C3213

基底クラス 'base_type' のアクセス可能性が 'derived_type' よりも小さい

アセンブリから参照できる型は、公開されている基底クラスを使用する必要があります。

次の例では C3213 が生成されます。

```cpp
// C3213.cpp
// compile with: /clr
private ref struct privateG {
public:
   int i;
};

public ref struct publicG {
public:
   int i;
};

public ref struct V : public privateG {   // C3213
public:
   int j;
};

public ref struct W: public publicG {   // OK
public:
   int j;
};
```
