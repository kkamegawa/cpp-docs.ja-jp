---
title: slice クラス
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice
- valarray/std::slice::size
- valarray/std::slice::start
- valarray/std::slice::stride
helpviewer_keywords:
- std::slice [C++]
- std::slice [C++], size
- std::slice [C++], start
- std::slice [C++], stride
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
ms.openlocfilehash: 830e345eb7522cef44dbf6e727a976fb79c1e081
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450355"
---
# <a name="slice-class"></a>slice クラス

親 valarray の 1 次元サブセットを定義するために使用する valarray のユーティリティ クラス。 valarray が配列内のすべての要素を持つ 2 次元行列と見なされる場合、スライスにより 2 次元配列のうち 1 次元のベクターが抽出されます。

## <a name="remarks"></a>Remarks

クラスは、[slice_array](../standard-library/slice-array-class.md) 型のオブジェクトを特徴とするパラメーターを格納します。クラスのスライスのオブジェクトが [valarray](../standard-library/valarray-class.md#op_at) **\<Type>** クラスのオブジェクトの引数として現れる場合、valarray のサブセットは間接的に構築されます。 親の valarray から選択したサブセットを指定する格納値には、以下が含まれています。

- valarray の開始インデックス。

- 合計の長さ、またはのスライスの要素の数。

- ストライド、または valarray の後続の要素のインデックス間の距離。

スライスによって定義されたセットが定数の valarray のサブセットの場合、スライスは新しい valarray です。 スライスによって定義されたセットが非定数の valarray のサブセットの場合、スライスには元の valarray に対する参照セマンティクスが含まれます。 非定数 valarray の評価メカニズムを使用すると、時間とメモリを節約できます。

valarray での操作は、スライスによって定義されたソースとターゲットのサブセットが同じでなく、すべてのインデックスが有効な場合にのみ保証されます。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[slice](#slice)|等間隔で離れ、指定した要素で開始する多数の要素で構成する `valarray` のサブセットを定義します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[size](#size)|`valarray` のスライスにある要素の数を調べます。|
|[start](#start)|`valarray` のスライスの開始インデックスを検索します。|
|[stride](#stride)|`valarray` のスライスにある要素間の距離を検索します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<valarray>

**名前空間:** std

## <a name="size"></a>  slice::size

valarray のスライスにある要素の数を調べます。

```cpp
size_t size() const;
```

### <a name="return-value"></a>戻り値

valarray のスライスにある要素の数。

### <a name="example"></a>例

```cpp
// slice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA, sizeVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   sizeVAR = vaSlice.size ( );
   cout << "The size of slice vaSlice is: "
        << sizeVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The size of the valarray is: 20.

The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The size of slice vaSlice is: 6.
```

## <a name="slice"></a>  slice::slice

等間隔で離れ、指定した要素で開始する多数の要素で構成する valarray のサブセットを定義します。

```cpp
slice();

slice(
    size_t _StartIndex,
    size_t _Len,
    size_t stride);
```

### <a name="parameters"></a>パラメーター

*StartIndex (_l)* \
サブセットの最初の要素の valarray インデックス。

*Len (_s)* \
サブセット内の要素数。

*stride*\
サブセット内の要素間の距離。

### <a name="return-value"></a>戻り値

既定のコンストラクターは、開始インデックス、長さの合計、およびストライドに対して 0 を格納します。 2番目のコンストラクターは、開始インデックスの場合は*StartIndex* 、合計長の場合は*Len* 、stride の場合は*ストライド*を格納します。

### <a name="remarks"></a>Remarks

ストライドは負となる場合があります。

### <a name="example"></a>例

```cpp
// slice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  2 * (i + 1 );

   cout << "The operand valarray va is:\n( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 1 , 7 , 3 );
   vaResult = va [ vaSlice ];

   cout << "\nThe slice of valarray va is vaResult:"
        << "\nva[slice( 1, 7, 3)] = ( ";
      for ( i = 0 ; i < 7 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
( 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 ).

The slice of valarray va is vaResult:
va[slice( 1, 7, 3)] = ( 4 10 16 22 28 34 40 ).
```

## <a name="start"></a>  slice::start

valarray のスライスの開始インデックスを検索します。

```cpp
size_t start() const;
```

### <a name="return-value"></a>戻り値

valarray のスライスの開始インデックス。

### <a name="example"></a>例

```cpp
// slice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t startVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] = i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   startVAR = vaSlice.start ( );
   cout << "The start index of slice vaSlice is: "
        << startVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The start index of slice vaSlice is: 3.
```

## <a name="stride"></a>  slice::stride

valarray のスライスにある要素間の距離を検索します。

```cpp
size_t stride() const;
```

### <a name="return-value"></a>戻り値

valarray のスライスにある要素間の距離。

### <a name="example"></a>例

```cpp
// slice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t strideVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  3 * ( i + 1 );

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 4 , 5 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 4, 5, 3)] =\n ( ";
      for ( i = 0 ; i < 5 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   strideVAR = vaSlice.stride ( );
   cout << "The stride of slice vaSlice is: "
        << strideVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45 48 51 54 57 60 ).
The slice of valarray va is vaResult = va[slice( 4, 5, 3)] =
( 15 24 33 42 51 ).
The stride of slice vaSlice is: 3.
```

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
