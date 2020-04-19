---
title: length_error クラス
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::length_error
helpviewer_keywords:
- length_error class
ms.assetid: d53c46c5-4626-400d-bd76-bf3e1e0f64ae
ms.openlocfilehash: c88b9e3af5d00a3d2c0b3146783b0babe9d0a01a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447595"
---
# <a name="lengtherror-class"></a>length_error クラス

このクラスは、生成を試みたオブジェクトが長すぎて指定できないことを通知するためにスローされる例外すべてに対する基底クラスとして機能します。

## <a name="syntax"></a>構文

```cpp
class length_error : public logic_error {
public:
    explicit length_error(const string& message);

    explicit length_error(const char *message);

};
```

## <a name="remarks"></a>Remarks

[what](../standard-library/exception-class.md) によって返される値は、**message**`.`[data](../standard-library/basic-string-class.md#data) のコピーです。

## <a name="example"></a>例

```cpp
// length_error.cpp
// compile with: /EHsc /GR /MDd
#include <vector>
#include <iostream>

using namespace std;

template<class  T>
class stingyallocator : public allocator< T>
{
public:
   template <class U>
      struct rebind { typedef stingyallocator<U> other; };
   _SIZT max_size( ) const
   {
         return 10;
   };

};

int main( )
{
   try
   {
      vector<int, stingyallocator< int > > myv;
      for ( int i = 0; i < 11; i++ ) myv.push_back( i );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught vector<T> too long
Type class std::length_error
*/
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<stdexcept>

**名前空間:** std

## <a name="see-also"></a>関連項目

[logic_error クラス](../standard-library/logic-error-class.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
