---
title: '前置インクリメント演算子と前置デクリメント演算子: ++ および --'
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- ++ operator [C++], prefix increment operators
- operators [C++], decrement
- -- operator [C++], prefix decrement operators [C++]
- operators [C++], increment
- decrement operators [C++], syntax
- decrement operators [C++]
ms.assetid: 45ea7fc7-f279-4be9-a216-1d9a0ef9eb7b
ms.openlocfilehash: deb8acc6c6a68c9a97f2f0efbdc4084b4937df46
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392103"
---
# <a name="prefix-increment-and-decrement-operators--and---"></a>前置インクリメント演算子と前置デクリメント演算子: ++ および --

## <a name="syntax"></a>構文

```
++ unary-expression
-- unary-expression
```

## <a name="remarks"></a>Remarks

前置インクリメント演算子 ( **++** ) そのオペランドの値に 1 つを追加します。 このインクリメントされた値は、式の結果。 オペランドの種類が左辺値である必要があります**const**します。 結果は、オペランドと同じ型の左辺値です。

前置デクリメント演算子 ( **--** ) は、オペランドが 1 だけデクリメントし、結果はこのデクリメントされた値にする点を除いて、前置インクリメント演算子に似ています。

**Visual Studio 2017 バージョン 15.3 以降**(で使用可能な[/std:c++17](../build/reference/std-specify-language-standard-version.md))。型のインクリメントまたはデクリメント演算子のオペランドができない可能性があります**bool**します。

前置および後置インクリメントおよびデクリメント演算子は、オペランドに影響します。 これらの主要な違いは、式の評価でインクリメントまたはデクリメントが発生する順序です。 (詳細については、次を参照してください[後置インクリメント演算子と前置デクリメント演算子](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)。)。前置形式では、値が式評価で使用される前にインクリメントまたはデクリメントが発生するため、式の値はオペランドの値と異なります。 後置形式では、値が式評価で使用された後にインクリメントまたはデクリメントが発生するため、式の値はオペランドの値と同じになります。 たとえば、次のプログラムでは、"`++i = 6`" と出力されます。

```cpp
// expre_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   int i = 5;
   cout << "++i = " << ++i << endl;
}
```

整数または浮動小数点型のオペランドは、整数値 1 ずつインクリメントまたはデクリメントされます。 結果の型は、オペランドの型と同じです。 ポインター型のオペランドは、アドレス指定するオブジェクトのサイズだけインクリメントまたはデクリメントされます。 インクリメントされたポインターは、次のオブジェクトを指します。デクリメントされたポインターは、前のオブジェクトを指します。

ため、インクリメントおよびデクリメント演算子があるでインクリメントまたはデクリメント演算子を含む式を使用して、副作用を[プリプロセッサ マクロ](../preprocessor/macros-c-cpp.md)望ましくない結果を持つことができます。 次の例について考えます。

```cpp
// expre_Increment_and_Decrement_Operators2.cpp
#define max(a,b) ((a)<(b))?(b):(a)

int main()
{
   int i = 0, j = 0, k;
   k = max( ++i, j );
}
```

マクロは次のように展開されます。

```cpp
k = ((++i)<(j))?(j):(++i);
```

`i` が `j` 以上であるか、`j` より 1 少ない場合、2 回インクリメントされます。

> [!NOTE]
>  C++ のインライン関数は、ここで説明したような副作用をなくし、言語でより完全な型チェックを実行できるため、多くの場合、マクロよりも適しています。

## <a name="see-also"></a>関連項目

[単項演算子を含む式](../cpp/expressions-with-unary-operators.md)<br/>
[C++ の組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[前置インクリメント演算子と前置デクリメント演算子](../c-language/prefix-increment-and-decrement-operators.md)