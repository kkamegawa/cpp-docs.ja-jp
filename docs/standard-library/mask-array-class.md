---
title: mask_array クラス
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 12398203d61f2c3ea155b5f6e6e7b118d4a13c75
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689404"
---
# <a name="mask_array-class"></a>mask_array クラス

サブセット配列間の演算を提供することにより、ブール式で指定された親 valarrays のサブセットであるオブジェクトをサポートする、内部の補助クラステンプレート。

## <a name="syntax"></a>構文

## <a name="remarks"></a>Remarks

クラスは、[クラス valarray](../standard-library/valarray-class.md)  **\<Type >** の `va` オブジェクトへの参照、`ba` および選択する要素のシーケンスを記述するクラス[valarray \<bool >](../standard-library/valarray-bool-class.md)のオブジェクトへの参照を格納するオブジェクトを表します。`valarray<Type>` オブジェクトからです。

@No__t_0 オブジェクトを構築するには、 [va&#91;ba&#93;](../standard-library/valarray-class.md#op_at)という形式の式を記述する必要があります。 クラス mask_array のメンバー関数は、`valarray<Type>` に対して定義されている対応する関数シグネチャのように動作します。ただし、選択された要素のシーケンスのみが影響を受けます。

シーケンスは、最大 `ba.size` の要素で構成されます。 要素 *J* は **ba**[ *J*] が true である場合にのみ含まれます。 したがって、シーケンス内には `ba` に true 要素があるのと同じ数の要素があります。 @No__t_0 が `ba` の最下位の true 要素のインデックスである場合、 **va**[`I`] は選択されたシーケンスの要素0です。

## <a name="example"></a>例

```cpp
// mask_array.cpp
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

   // Use masked subsets to assign a value of 10
   // to all elements grrater than 3 in value
   va [va > 3 ] = 10;
   cout << "The modified operand valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;
}
```

### <a name="output"></a>出力

```Output
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 2 -1 10 -1 10 -1 10 -1).
```

## <a name="requirements"></a>［要件］

**ヘッダー:** \<valarray>

**名前空間:** std

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
