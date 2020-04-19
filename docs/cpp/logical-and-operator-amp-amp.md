---
title: '論理 AND 演算子: &amp;&amp;'
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- logical AND operator
- AND operator
- '&& operator'
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
ms.openlocfilehash: 0843ba95467c3ae0d735476de48a8195a59788f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368657"
---
# <a name="logical-and-operator-ampamp"></a>論理 AND 演算子: &amp;&amp;

## <a name="syntax"></a>構文

```
expression && expression
```

## <a name="remarks"></a>Remarks

論理 AND 演算子 (**&&**) 両方のオペランドが TRUE の場合は、ブール値 TRUE を返すし、それ以外の場合は FALSE を返します。 オペランドは型に暗黙的に変換**bool**前に、evaluation、および結果の種類では**bool**します。 論理 AND には左から右方向の結合規則があります。

論理 AND 演算子のオペランドが同じ型である必要はありませんが、整数型またはポインター型である必要があります。 オペランドは一般に関係式または等価式です。

最初のオペランドが完全に評価され、すべての副作用が完了した後で、論理 AND 式の評価が続行されます。

2 番目のオペランドは、最初のオペランドが true (ゼロ以外) と評価された場合にのみ、評価されます。 この評価により、論理 AND 式が false の場合に 2 番目のオペランドに不要な評価が行われないようになっています。 このショート サーキット評価を使用して、次の例に示すように、null ポインターの逆参照を防止できます。

```cpp
char *pch = 0;
...
(pch) && (*pch = 'a');
```

`pch` が null (0) であれば、式の右側は評価されません。 したがって、null ポインターを使用した代入が発生することはありません。

## <a name="operator-keyword-for-"></a>演算子キーワード (& a) (& a)

**と**演算子と等価のテキストは、  **&&** します。 アクセスする 2 つの方法がある、**と**プログラムで演算子: ヘッダー ファイルをインクルード`iso646.h`、使用してコンパイル、 [/Za](../build/reference/za-ze-disable-language-extensions.md) (言語拡張を無効にする) コンパイラ オプション。

## <a name="example"></a>例

```cpp
// expre_Logical_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate logical AND
#include <iostream>

using namespace std;

int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b && b < c yields "
         << (a < b && b < c) << endl
         << "The false expression "
         << "a > b && b < c yields "
         << (a > b && b < c) << endl;
}
```

## <a name="see-also"></a>関連項目

[C++ の組み込み演算子の優先順位と結合規則](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C++ の組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 論理演算子](../c-language/c-logical-operators.md)