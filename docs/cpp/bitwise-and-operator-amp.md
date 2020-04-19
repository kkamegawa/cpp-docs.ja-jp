---
title: 'ビットごとの AND 演算子: &amp;'
ms.date: 11/04/2016
f1_keywords:
- bitand
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
ms.openlocfilehash: b7d0d73802a5af7ab71e980d73eaff5c5b3c4bb8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387709"
---
# <a name="bitwise-and-operator-amp"></a>ビットごとの AND 演算子: &amp;

## <a name="syntax"></a>構文

```
expression & expression
```

## <a name="remarks"></a>Remarks

式は、他の and 式、または (以下に言及する型制限に基づき) 等価式、関係式、加算式、乗算式、メンバー式へのポインター、キャスト式、単項式、後置式、または 1 次式である場合もあります。

ビットごとの AND 演算子 (**&**) 最初のオペランドを 2 番目のオペランドの対応するビットの各ビットと比較します。 両方のビットが 1 の場合、対応する結果のビットは 1 に設定されます。 それ以外の場合は、対応する結果ビットが 0 に設定されます。

ビットごとの AND 演算子のオペランドは両方とも整数型である必要があります。 通常の算術変換は、「[標準変換](standard-conversions.md)オペランドに適用されます。

## <a name="operator-keyword-for-"></a>演算子キーワード (& a)

**Bitand**演算子と等価のテキストは、  **&** します。 アクセスする 2 つの方法がある、 **bitand**プログラムで演算子: ヘッダー ファイルをインクルード`iso646.h`、使用してコンパイル、 [/Za](../build/reference/za-ze-disable-language-extensions.md) (言語拡張を無効にする) コンパイラ オプション。

## <a name="example"></a>例

```cpp
// expre_Bitwise_AND_Operator.cpp
// compile with: /EHsc
// Demonstrate bitwise AND
#include <iostream>
using namespace std;
int main() {
   unsigned short a = 0xFFFF;      // pattern 1111 ...
   unsigned short b = 0xAAAA;      // pattern 1010 ...

   cout  << hex << ( a & b ) << endl;   // prints "aaaa", pattern 1010 ...
}
```

## <a name="see-also"></a>関連項目

[C++ の組み込み演算子、優先順位と結合規則](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C++ の組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C ビット処理演算子](../c-language/c-bitwise-operators.md)