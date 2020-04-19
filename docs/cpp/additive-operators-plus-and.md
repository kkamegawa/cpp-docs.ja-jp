---
title: '加法演算子: + および -'
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- operators [C++], addition
- subtraction operator [C++], additive operators
- + operator [C++], additive operators
- additive operators [C++]
- arithmetic operators [C++], additive operators
- '- operator [C++], additive operators in C++'
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
ms.openlocfilehash: be9e1830ea44223aa46ad9a7f5c6cee6734fa9e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385051"
---
# <a name="additive-operators--and--"></a>加法演算子: + および -

## <a name="syntax"></a>構文

```
expression + expression
expression - expression
```

## <a name="remarks"></a>Remarks

加法演算子を次に示します。

- 加算 ( **+** )

- 減算 ( **-** )

これらの二項演算子の結合規則は、左から右方向です。

加法演算子は、数値型またはポインター型のオペランドを受け取ります。 加算 ( **+** ) 演算子の結果はオペランドの合計になります。 減算 ( **-** ) 演算子の結果は、オペランド間の差です。 オペランドの一方または両方がポインターの場合、これらのオペランドは関数ではなくオブジェクトのポインターである必要があります。 両方のオペランドがポインターの場合、両方とも同じ配列のオブジェクトへのポインターでない限り意味がありません。

加法演算子はオペランドとして *数値*、*整数*、および*スカラー*型を受け取ります。 次の表にこれらの定義を示します。

### <a name="types-used-with-additive-operators"></a>加法演算子と併用される型

|型|説明|
|----------|-------------|
|*数値*|整数型および浮動型はまとめて "数値" 型と呼ばれます。|
|*整数*|すべてのサイズ (long、short) の char 型と int 型、および列挙型は "整数" 型です。|
|*スカラー*|スカラー オペランドは、数値型またはポインター型のオペランドです。|

これらの演算子の有効な組み合わせは以下のとおりです。

*算術* + *算術*

*スカラー* + *整数*

*整数* + *スカラー*

*算術* - *算術*

*スカラー* - *スカラー*

加算と減算が同等の操作ではないことに注意してください。

両方のオペランドが算術型である場合は、[標準変換](standard-conversions.md)で取り上げられている変換処理が適用され結果は変換後の型になります。

## <a name="example"></a>例

```cpp
// expre_Additive_Operators.cpp
// compile with: /EHsc
#include <iostream>
#define SIZE 5
using namespace std;
int main() {
   int i = 5, j = 10;
   int n[SIZE] = { 0, 1, 2, 3, 4 };
   cout  << "5 + 10 = " << i + j << endl
         << "5 - 10 = " << i - j << endl;

   // use pointer arithmetic on array

   cout << "n[3] = " << *( n + 3 ) << endl;
}
```

## <a name="pointer-addition"></a>ポインターの加算

加算演算のオペランドの片方がオブジェクトの配列へのポインターである場合、もう一方のオペランドは整数型である必要があります。 結果は、元のポインターと同じ型のポインターで、他の配列要素をポイントします。 後述するコードでこの概念を説明します。

```cpp
short IntArray[10]; // Objects of type short occupy 2 bytes
short *pIntArray = IntArray;

for( int i = 0; i < 10; ++i )
{
    *pIntArray = i;
    cout << *pIntArray << "\n";
    pIntArray = pIntArray + 1;
}
```

整数値 1 が `pIntArray` に追加されますが、これは "アドレスに 1 を追加する" ことを意味しません。そうではなく、2 バイト (または `sizeof( int )`) 移動するように、"配列内の次のオブジェクトを指すようにポインターを調整する" ことを意味します。

> [!NOTE]
>  `pIntArray = pIntArray + 1` のような形式のコードは、C++ プログラムではあまり見られません。インクリメントを行う場合は、`pIntArray++` または `pIntArray += 1` のような形式を使用することをお勧めします。

## <a name="pointer-subtraction"></a>ポインターの減算

両方のオペランドがポインターの場合、減算の結果は、オペランド間の (配列要素内の) 差になります。 減算式には、符号付き整数型 `ptrdiff_t` の結果が得られます (標準インクルードファイル\<stddef.h> で定義されている)。

それが 2 番目のオペランドに限って、オペランドの 1 つは整数型にできます。 減算の結果は、元のポインターと同じ型です。 減算の値は (*n* - *i*) 番目の配列要素へのポインターを指します (ここでいう *n* は元のポインターが指している要素、*i* は 2 番目のオペランドの整数値)。

## <a name="see-also"></a>関連項目

[二項演算子を含む式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ の組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 加法演算子](../c-language/c-additive-operators.md)
