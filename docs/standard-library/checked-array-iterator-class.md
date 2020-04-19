---
title: checked_array_iterator クラス
ms.date: 03/27/2019
f1_keywords:
- iterator/checked_array_iterator
- iterator/stdext::checked_array_iterator::difference_type
- iterator/stdext::checked_array_iterator::pointer
- iterator/stdext::checked_array_iterator::reference
- iterator/stdext::checked_array_iterator::base
helpviewer_keywords:
- stdext::checked_array_iterator [C++], difference_type
- stdext::checked_array_iterator [C++], pointer
- stdext::checked_array_iterator [C++], reference
- stdext::checked_array_iterator [C++], base
ms.assetid: 7f07185e-d588-4ae3-9c4f-84ec4aa25a28
ms.openlocfilehash: 68ee602c44a8515e1d41f04a4bd0fbb7edc924b7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452309"
---
# <a name="checkedarrayiterator-class"></a>checked_array_iterator クラス

`checked_array_iterator` クラスを使用すると、配列またはポインターをチェックを行う反復子に変換できます。 チェックを行わないポインター警告をグローバルに抑制する代わりに、チェック機能を提供し、これらの警告を管理するのに適した方法として、このクラスを生のポインターまたは配列のラッパーとして使用します ([make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator) 関数を使用)。 必要に応じて、このクラスのチェックを行わないバージョンである [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md) を使用できます。

> [!NOTE]
> このクラスは、標準 C++ ライブラリの Microsoft 拡張機能です。 この関数を使用して実装されるコードは、Microsoft 拡張機能をサポートしない C++ 標準ビルド環境には移植できません。 このクラスを使用する必要がないコードを記述する方法を示す例については、次の 2 番目の例を参照してください。

## <a name="syntax"></a>構文

```cpp
template <class _Iterator>
class checked_array_iterator;
```

## <a name="remarks"></a>Remarks

このクラスは、[stdext](../standard-library/stdext-namespace.md) 名前空間で定義されます。

チェックを行う反復子機能の詳細とコード例については、「[チェックを行う反復子](../standard-library/checked-iterators.md)」をご覧ください。

## <a name="example"></a>例

次の例は、チェックを行う配列反復子を定義および使用する方法を示しています。

コピー先がコピーされるすべての要素を保持するほど十分大きくない場合に、たとえば次のように行を変更した場合、

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 5));
```

から

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 4));
```

ランタイム エラーが発生します。

```cpp
// compile with: /EHsc /W4 /MTd
#include <algorithm>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[]={0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b, 5));

   cout << "(";
   for (int i = 0 ; i < 5 ; i++)
      cout << " " << b[i];
   cout << " )" << endl;

   // constructor example
   checked_array_iterator<int*> checked_out_iter(b, 5);
   copy(a, a + 5, checked_out_iter);

   cout << "(";
   for (int i = 0 ; i < 5 ; i++)
      cout << " " << b[i];
   cout << " )" << endl;
}
/* Output:
( 0 1 2 3 4 )
( 0 1 2 3 4 )
*/
```

## <a name="example"></a>例

C++ 標準ライブラリ アルゴリズムを使用する場合の `checked_array_iterator` クラスの必要性を回避するため、動的に割り当てられた配列の代わりに `vector` を使用することを検討してください。 この方法を次の例に示します。

```cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    std::vector<int> v(10);
    int *arr = new int[10];
    for (int i = 0; i < 10; ++i)
    {
        v[i] = i;
        arr[i] = i;
    }

    // std::copy(v.begin(), v.end(), arr); will result in
    // warning C4996. To avoid this warning while using int *,
    // use the Microsoft extension checked_array_iterator.
    std::copy(v.begin(), v.end(),
              stdext::checked_array_iterator<int *>(arr, 10));

    // Instead of using stdext::checked_array_iterator and int *,
    // consider using std::vector to encapsulate the array. This will
    // result in no warnings, and the code will be portable.
    std::vector<int> arr2(10);    // Similar to int *arr = new int[10];
    std::copy(v.begin(), v.end(), arr2.begin());

    for (int j = 0; j < arr2.size(); ++j)
    {
        cout << " " << arr2[j];
    }
    cout << endl;

    return 0;
}
/* Output:
0 1 2 3 4 5 6 7 8 9
*/
```

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[checked_array_iterator](#checked_array_iterator)|基になる反復子の既定の `checked_array_iterator` または `checked_array_iterator` を構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[difference_type](#difference_type)|同じコンテナー内の要素を参照する 2 つの `checked_array_iterator` の違いを提供する型。|
|[pointer](#pointer)|`checked_array_iterator` によってアドレス指定される要素へのポインターを提供する型。|
|[reference](#reference)|`checked_array_iterator` によってアドレス指定される要素への参照を提供する型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[base](#base)|その `checked_array_iterator` から基になる反復子を復元します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator==](#op_eq_eq)|2 つの `checked_array_iterator` が等しいかどうかをテストします。|
|[operator!=](#op_neq)|2 つの `checked_array_iterator` が等しくないかどうかをテストします。|
|[operator<](#op_lt)|演算子の左側の `checked_array_iterator` オブジェクトが右側の `checked_array_iterator` オブジェクトより小さいかどうかをテストします。|
|[operator>](#op_gt)|演算子の左側の `checked_array_iterator` オブジェクトが右側の `checked_array_iterator` オブジェクトより大きいかどうかをテストします。|
|[operator<=](#op_lt_eq)|演算子の左側の `checked_array_iterator` が右側の `checked_array_iterator` 以下かどうかをテストします。|
|[operator>=](#op_gt_eq)|演算子の左側の `checked_array_iterator` が右側の `checked_array_iterator` 以上かどうかをテストします。|
|[operator*](#op_star)|`checked_array_iterator` がアドレス指定する要素を返します。|
|[operator->](#op_arrow)|`checked_array_iterator` によってアドレス指定される要素へのポインターを返します。|
|[operator++](#op_add_add)|`checked_array_iterator` を次の要素にインクリメントします。|
|[operator--](#operator--)|`checked_array_iterator` を直前の要素にデクリメントします。|
|[operator+=](#op_add_eq)|指定したオフセットを `checked_array_iterator` に追加します。|
|[operator+](#op_add)|反復子にオフセットを追加し、新しいオフセット位置に挿入された要素をアドレス指定する新しい `checked_array_iterator` アドレスを返します。|
|[operator-=](#operator-_eq)|指定したオフセットを `checked_array_iterator` からデクリメントします。|
|[operator-](#operator-)|反復子からオフセットをデクリメントし、新しいオフセット位置に挿入された要素をアドレス指定する新しい `checked_array_iterator` アドレスを返します。|
|[operator&#91;&#93;](#op_at)|`checked_array_iterator` によってアドレス指定される要素からの要素のオフセットへの参照を返します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<iterator>

**名前空間:** stdext

## <a name="base"></a>  checked_array_iterator::base

その `checked_array_iterator` から基になる反復子を復元します。

```cpp
_Iterator base() const;
```

### <a name="remarks"></a>Remarks

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// checked_array_iterators_base.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main() {
   using namespace std;

   int V1[10];

   for (int i = 0; i < 10 ; i++)
      V1[i] = i;

   int* bpos;

   stdext::checked_array_iterator<int*> rpos(V1, 10);
   rpos++;

   bpos = rpos.base ( );
   cout << "The iterator underlying rpos is bpos & it points to: "
        << *bpos << "." << endl;
}
/* Output:
The iterator underlying rpos is bpos & it points to: 1.
*/
```

## <a name="checked_array_iterator"></a>  checked_array_iterator::checked_array_iterator

基になる反復子の既定の `checked_array_iterator` または `checked_array _iterator` を構築します。

```cpp
checked_array_iterator();

checked_array_iterator(
    ITerator ptr,
    size_t size,
    size_t index = 0);
```

### <a name="parameters"></a>パラメーター

*ポインター*\
配列データへのポインター。

*幅*\
配列のサイズ。

*化*\
(省略可能) 反復子を初期化するための配列内の要素。  既定では、反復子は、配列内の最初の要素に初期化されます。

### <a name="remarks"></a>Remarks

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// checked_array_iterators_ctor.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << " ";
   cout << endl;

   checked_array_iterator<int*> checked_output_iterator(b,5);
   copy (a, a + 5, checked_output_iterator);
   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << " ";
   cout << endl;

   checked_array_iterator<int*> checked_output_iterator2(b,5,3);
   cout << *checked_output_iterator2 << endl;
}
/* Output:
0 1 2 3 4
0 1 2 3 4
3
*/
```

## <a name="difference_type"></a>  checked_array_iterator::difference_type

同じコンテナー内の要素を参照する 2 つの `checked_array_iterator` の違いを提供する型。

```cpp
typedef typename iterator_traits<_Iterator>::difference_type difference_type;
```

### <a name="remarks"></a>Remarks

`checked_array_iterator` の異なる型は、反復子の異なる型と同じです。

コード サンプルについては、[checked_array_iterator::operator[]](#op_at) を参照してください。

詳細については、「[チェックを行う反復子](../standard-library/checked-iterators.md)」を参照してください。

## <a name="op_eq_eq"></a>  checked_array_iterator::operator==

2 つの `checked_array_iterator` が等しいかどうかをテストします。

```cpp
bool operator==(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>パラメーター

*そうです*\
等しいかどうかを確認する対象の `checked_array_iterator`。

### <a name="remarks"></a>Remarks

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// checked_array_iterators_opeq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 == checked_output_iterator)
      cout << "checked_array_iterators are equal" << endl;
   else
      cout << "checked_array_iterators are not equal" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 == checked_output_iterator)
      cout << "checked_array_iterators are equal" << endl;
   else
      cout << "checked_array_iterators are not equal" << endl;
}
/* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*/
```

## <a name="op_neq"></a>  checked_array_iterator::operator!=

2 つの `checked_array_iterator` が等しくないかどうかをテストします。

```cpp
bool operator!=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>パラメーター

*そうです*\
等しくないかどうかを確認する対象の `checked_array_iterator`。

### <a name="remarks"></a>Remarks

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// checked_array_iterators_opneq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 != checked_output_iterator)
      cout << "checked_array_iterators are not equal" << endl;
   else
      cout << "checked_array_iterators are equal" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 != checked_output_iterator)
      cout << "checked_array_iterators are not equal" << endl;
   else
      cout << "checked_array_iterators are equal" << endl;
}
/* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*/
```

## <a name="op_lt"></a>  checked_array_iterator::operator&lt;

演算子の左側の `checked_array_iterator` オブジェクトが右側の `checked_array_iterator` オブジェクトより小さいかどうかをテストします。

```cpp
bool operator<(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>パラメーター

*そうです*\
等しくないかどうかを確認する対象の `checked_array_iterator`。

### <a name="remarks"></a>Remarks

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// checked_array_iterators_oplt.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 < checked_output_iterator)
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 < checked_output_iterator)
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;
}
/* Output:
checked_output_iterator2 is not less than checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*/
```

## <a name="op_gt"></a>  checked_array_iterator::operator&gt;

演算子の左側の `checked_array_iterator` オブジェクトが右側の `checked_array_iterator` オブジェクトより大きいかどうかをテストします。

```cpp
bool operator>(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>パラメーター

*そうです*\
比較対象の `checked_array_iterator`。

### <a name="remarks"></a>Remarks

コード サンプルについては、[checked_array_iterator::operator&lt;](#op_lt) を参照してください。

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

## <a name="op_lt_eq"></a>  checked_array_iterator::operator&lt;=

演算子の左側の `checked_array_iterator` が右側の `checked_array_iterator` 以下かどうかをテストします。

```cpp
bool operator<=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>パラメーター

*そうです*\
比較対象の `checked_array_iterator`。

### <a name="remarks"></a>Remarks

コード サンプルについては、 [checked_array_iterator::operator&gt;=](#op_gt_eq) を参照してください。

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

## <a name="op_gt_eq"></a>  checked_array_iterator::operator&gt;=

演算子の左側の `checked_array_iterator` が右側の `checked_array_iterator` 以上かどうかをテストします。

```cpp
bool operator>=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>パラメーター

*そうです*\
比較対象の `checked_array_iterator`。

### <a name="remarks"></a>Remarks

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// checked_array_iterators_opgteq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 >= checked_output_iterator)
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 >= checked_output_iterator)
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
}
/* Output:
checked_output_iterator2 is greater than or equal to checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*/
```

## <a name="op_star"></a>  checked_array_iterator::operator*

`checked_array_iterator` がアドレス指定する要素を返します。

```cpp
reference operator*() const;
```

### <a name="return-value"></a>戻り値

`checked_array_iterator` によってアドレス指定される要素の値。

### <a name="remarks"></a>Remarks

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// checked_array_iterator_pointer.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   pair<int, int> c[1];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << endl;

    c[0].first = 10;
    c[0].second = 20;

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*>::pointer p = &(*checked_output_iterator);
   checked_array_iterator<pair<int, int>*> chk_c(c, 1);
   checked_array_iterator<pair<int, int>*>::pointer p_c = &(*chk_c);

   cout << "b[0] = " << *p << endl;
   cout << "c[0].first = " << p_c->first << endl;
}
/* Output:
0
1
2
3
4
b[0] = 0
c[0].first = 10
*/
```

## <a name="op_arrow"></a>  checked_array_iterator::operator-&gt;

`checked_array_iterator` によってアドレス指定される要素へのポインターを返します。

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>戻り値

`checked_array_iterator` によってアドレス指定される要素へのポインター。

### <a name="remarks"></a>Remarks

コード サンプルについては、[checked_array_iterator::pointer](#pointer) を参照してください。

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

## <a name="op_add_add"></a>  checked_array_iterator::operator++

`checked_array_iterator` を次の要素にインクリメントします。

```cpp
checked_array_iterator& operator++();

checked_array_iterator<_Iterator> operator++(int);
```

### <a name="return-value"></a>戻り値

最初の演算子は、プリインクリメントされた `checked_array_iterator` を返し、2 番目のポストインクリメント演算子は、インクリメントされた `checked_array_iterator` のコピーを返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// checked_array_iterators_op_plus_plus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   ++checked_output_iterator;
   cout << *checked_output_iterator << endl;
   checked_output_iterator++;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
3
77
*/
```

## <a name="operator--"></a>  checked_array_iterator::operator--

`checked_array_iterator` を直前の要素にデクリメントします。

```cpp
checked_array_iterator<_Iterator>& operator--();

checked_array_iterator<_Iterator> operator--(int);
```

### <a name="return-value"></a>戻り値

最初の演算子はプリデクリメントされた `checked_array_iterator` を返し、2 番目のポストデクリメント演算子は、デクリメントされた `checked_array_iterator` のコピーを返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// checked_array_iterators_op_minus_minus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator++;
   cout << *checked_output_iterator << endl;
   checked_output_iterator--;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
3
6
*/
```

## <a name="op_add_eq"></a>  checked_array_iterator::operator+=

指定したオフセットを `checked_array_iterator` に追加します。

```cpp
checked_array_iterator<_Iterator>& operator+=(difference_type _Off);
```

### <a name="parameters"></a>パラメーター

*オフ (_r)* \
反復子をインクリメントするオフセット。

### <a name="return-value"></a>戻り値

`checked_array_iterator` によってアドレス指定される要素への参照。

### <a name="remarks"></a>Remarks

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// checked_array_iterators_op_plus_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator += 3;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
199
*/
```

## <a name="op_add"></a>  checked_array_iterator::operator+

反復子にオフセットを追加し、新しいオフセット位置に挿入された要素をアドレス指定する新しい `checked_array_iterator` アドレスを返します。

```cpp
checked_array_iterator<_Iterator> operator+(difference_type _Off) const;
```

### <a name="parameters"></a>パラメーター

*オフ (_r)* \
`checked_array_iterator` に追加するオブジェクト。

### <a name="return-value"></a>戻り値

オフセット要素を指す `checked_array_iterator`。

### <a name="remarks"></a>Remarks

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// checked_array_iterators_op_plus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator = checked_output_iterator + 3;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
199
*/
```

## <a name="operator-_eq"></a>  checked_array_iterator::operator-=

指定したオフセットを `checked_array_iterator` からデクリメントします。

```cpp
checked_array_iterator<_Iterator>& operator-=(difference_type _Off);
```

### <a name="parameters"></a>パラメーター

*オフ (_r)* \
反復子をインクリメントするオフセット。

### <a name="return-value"></a>戻り値

`checked_array_iterator` によってアドレス指定される要素への参照。

### <a name="remarks"></a>Remarks

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// checked_array_iterators_op_minus_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   checked_output_iterator += 3;
   cout << *checked_output_iterator << endl;
   checked_output_iterator -= 2;
   cout << *checked_output_iterator << endl;
}
/* Output:
199
3
*/
```

## <a name="operator-"></a>  checked_array_iterator::operator-

反復子からオフセットをデクリメントし、新しいオフセット位置に挿入された要素をアドレス指定する新しい `checked_array_iterator` アドレスを返します。

```cpp
checked_array_iterator<_Iterator> operator-(difference_type _Off) const;

difference_type operator-(const checked_array_iterator& right) const;
```

### <a name="parameters"></a>パラメーター

*オフ (_r)* \
`checked_array_iterator` からデクリメントされるオフセット。

### <a name="return-value"></a>戻り値

オフセット要素を指す `checked_array_iterator`。

### <a name="remarks"></a>Remarks

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

## <a name="op_at"></a>  checked_array_iterator::operator[]

`checked_array_iterator` によってアドレス指定される要素からの要素のオフセットへの参照を返します。

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>パラメーター

*オフ (_r)* \
`checked_array_iterator` アドレスからのオフセット。

### <a name="return-value"></a>戻り値

オフセット要素への参照。

### <a name="remarks"></a>Remarks

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// checked_array_iterators_op_diff.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   int V1[10];

   for (int i = 0; i < 10 ; i++)
      V1[i] = i;

   // Declare a difference type for a parameter
   stdext::checked_array_iterator<int*>::difference_type diff = 2;

   stdext::checked_array_iterator<int*> VChkIter(V1, 10);

   stdext::checked_array_iterator<int*>::reference refrpos = VChkIter [diff];

   cout << refrpos + 1 << endl;
}
/* Output:
3
*/
```

## <a name="pointer"></a>  checked_array_iterator::pointer

`checked_array_iterator` によってアドレス指定される要素へのポインターを提供する型。

```cpp
typedef typename iterator_traits<_Iterator>::pointer pointer;
```

### <a name="remarks"></a>Remarks

コード サンプルについては、 [checked_array_iterator::operator*](#op_star) を参照してください。

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

## <a name="reference"></a>  checked_array_iterator::reference

`checked_array_iterator` によってアドレス指定される要素への参照を提供する型。

```cpp
typedef typename iterator_traits<_Iterator>::reference reference;
```

### <a name="remarks"></a>Remarks

コード サンプルについては、[checked_array_iterator::operator[]](#op_at) を参照してください。

詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

## <a name="see-also"></a>関連項目

[\<iterator>](../standard-library/iterator.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
