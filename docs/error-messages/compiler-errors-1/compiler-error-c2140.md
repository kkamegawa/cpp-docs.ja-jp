---
title: コンパイラ エラー C2140
ms.date: 11/04/2016
f1_keywords:
- C2140
helpviewer_keywords:
- C2140
ms.assetid: d44a0500-002c-4632-9e5e-c71c3a473ec4
ms.openlocfilehash: 0329872ff0baee595bf32486a53d6abf91d208d4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756527"
---
# <a name="compiler-error-c2140"></a>コンパイラ エラー C2140

' type ': ジェネリック型パラメーターに依存する型は、コンパイラの組み込み型の特徴である ' 特徴 ' に対する引数として許可されていません

型の特徴に無効な型指定子が渡されました。

詳細については、「[型の特徴のコンパイラ サポート](../../extensions/compiler-support-for-type-traits-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C2140 が生成されます。

```cpp
// C2140.cpp
// compile with: /clr /c
template <class T>

struct is_polymorphic {
   static const bool value = __is_polymorphic(T);
};

class x {};

generic <class T>
ref class C {
   void f() {
      System::Console::WriteLine(__is_polymorphic(T));   // C2140
      System::Console::WriteLine(is_polymorphic<T>::value);   // C2140

      System::Console::WriteLine(__is_polymorphic(x));   // OK
      System::Console::WriteLine(is_polymorphic<x>::value);   // OK
   }
};
```
