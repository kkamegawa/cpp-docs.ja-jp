---
title: 関数テンプレートの部分的な順序付け (C++)
ms.date: 07/30/2019
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
ms.openlocfilehash: 0c4f11b4b3e02504c4786ea34441362b542959d6
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682423"
---
# <a name="partial-ordering-of-function-templates-c"></a>関数テンプレートの部分的な順序付け (C++)

関数呼び出しの引数リストと一致する複数の関数テンプレートを使用できます。 C++ では、呼び出す関数を指定するために、関数テンプレートの部分的な順序が定義されています。 順序が部分的なのは、同等に特殊化されていると見なされるテンプレートが存在するためです。

コンパイラは、使用できる最も特殊化されたテンプレート関数を一致候補から選択します。 たとえば、関数テンプレートが型`T`を受け取り、を受け取る`T*`別の関数テンプレートが使用可能な`T*`場合、そのバージョンはより特殊化されていると言います。 引数がポインター型である`T`場合は、両方とも一致する可能性があっても、ジェネリックバージョンよりも優先されます。

1 つの関数テンプレート候補がより特殊化されたかどうかを確認するには、次の手順を使用します。

1. T1 および T2 の 2 つの関数テンプレートを考えます。

1. T1 内のパラメーターを架空の一意の型 X に置き換えます。

1. T1 のパラメーター リストで、T2 がそのパラメーター リストの有効なテンプレートであるかどうかを確認します。 暗黙の変換は無視します。

1. T1 と T2 を逆にして、同じ処理を繰り返します。

1. あるテンプレートが他のテンプレートに対して有効なテンプレート引数リストであっても、逆の場合は、そのテンプレートは他のテンプレートよりも特殊化されていると見なされます。 前の手順を使用した場合、両方のテンプレートで有効な引数が相互に有効であると見なされます。これらのテンプレートは、同じように特殊化されていると見なされ、それらを使用しようとするとあいまいな呼び出しの結果になります。

1. 次の規則を使用します。

   1. 特定の型を受け取るテンプレートは、ジェネリック型引数を受け取るテンプレートよりも特殊化されます。

   1. `T*`架空の型`T` `T`は`X*`テンプレート引数の有効な引数ですが`X` 、の有効な引数ではないため、このテンプレートを使用`T*`するのは1つだけです。テンプレート引数。

   1. `const T``T`はより`T` `X`特殊化されています。 `const T` はテンプレート引数の有効な引数ですが、テンプレート引数の有効な引数ではありません。`const X`

   1. `const T*``T*`はより`T*` `X*`特殊化されています。 `const T*` はテンプレート引数の有効な引数ですが、テンプレート引数の有効な引数ではありません。`const X*`

## <a name="example"></a>例

次のサンプルは、標準で指定されているとおりに動作します。

```cpp
// partial_ordering_of_function_templates.cpp
// compile with: /EHsc
#include <iostream>

template <class T> void f(T) {
   printf_s("Less specialized function called\n");
}

template <class T> void f(T*) {
   printf_s("More specialized function called\n");
}

template <class T> void f(const T*) {
   printf_s("Even more specialized function for const T*\n");
}

int main() {
   int i =0;
   const int j = 0;
   int *pi = &i;
   const int *cpi = &j;

   f(i);   // Calls less specialized function.
   f(pi);  // Calls more specialized function.
   f(cpi); // Calls even more specialized function.
   // Without partial ordering, these calls would be ambiguous.
}
```

### <a name="output"></a>Output

```Output
Less specialized function called
More specialized function called
Even more specialized function for const T*
```

## <a name="see-also"></a>関連項目

[関数テンプレート](../cpp/function-templates.md)
