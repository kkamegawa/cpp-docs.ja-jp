---
title: indirect_array クラス
ms.date: 11/04/2016
f1_keywords:
- valarray/std::indirect_array
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
ms.openlocfilehash: 6be0c5153cbc94d09b414fc9e14fa498c7a4cfa7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687921"
---
# <a name="indirect_array-class"></a>indirect_array クラス

親 valarray のインデックスのサブセットを指定することによって定義されたサブセット配列間の演算を提供することによって、valarray のサブセットであるオブジェクトをサポートする、内部の補助クラステンプレート。

## <a name="syntax"></a>構文

## <a name="remarks"></a>Remarks

クラスは、クラス[valarray](../standard-library/valarray-class.md)  **\<Type >** の `va` オブジェクトへの参照、および `valarray<size_t>` オブジェクトから選択する要素のシーケンスを記述するクラス `valarray<Type>` のオブジェクト `xa` を格納するオブジェクトを表します。

@No__t_0 オブジェクトを構築するには `va[xa]` フォームの式を記述する必要があります。 クラス indirect_array のメンバー関数は、`valarray<Type>` に対して定義されている対応する関数シグネチャのように動作します。ただし、選択された要素のシーケンスのみが影響を受けます。

シーケンスは xa で構成さ**れます。** 要素の[サイズ](../standard-library/valarray-class.md#size)を変更します。ここで、要素 `I` は `va` 内のインデックス**xa**[`I`] になります。

## <a name="example"></a>例:

```cpp
// indirect_array.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      va [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 2 )
      va [ i ] =  -1;

   cout << "The initial operand valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   // Select 2nd, 4th & 6th elements
   // and assign a value of 10 to them
   valarray<size_t> indx ( 3 );
   indx [0] = 2;
   indx [1] = 4;
   indx [2] = 6;
   va[indx] = 10;

   cout << "The modified operand valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;
}
```

### <a name="output"></a>出力

```cpp
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).
```

## <a name="requirements"></a>［要件］

**ヘッダー:** \<valarray>

**名前空間:** std

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
