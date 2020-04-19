---
title: '方法: Gcnew 値型を作成し、使用して暗黙的なボックス化を使用してください。'
ms.date: 11/04/2016
helpviewer_keywords:
- gcnew keyword [C++], creating value types
- boxing, implicit
- value types, creating
ms.assetid: ceb48841-d6bd-47be-a167-57f44c961603
ms.openlocfilehash: c67f8e0b9511f4ed1610e72e4a7df41c949b1d27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387163"
---
# <a name="how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing"></a>方法: Gcnew 値型を作成し、使用して暗黙的なボックス化を使用してください。

使用して[gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md)値の型が管理され、ガベージ コレクション ヒープに配置することができます、ボックス化された値の型を作成します。

## <a name="example"></a>例

```
// vcmcppv2_explicit_boxing4.cpp
// compile with: /clr
public value class V {
public:
   int m_i;
   V(int i) : m_i(i) {}
};

public ref struct TC {
   void do_test(V^ v) {
      if (v != nullptr)
         ;
      else
         ;
   }
};

int main() {
   V^ v = gcnew V(42);
   TC^ tc = gcnew TC;
   tc->do_test(v);
}
```

## <a name="see-also"></a>関連項目

[ボックス化](../extensions/boxing-cpp-component-extensions.md)
