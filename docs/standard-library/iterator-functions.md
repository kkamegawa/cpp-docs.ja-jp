---
title: '&lt;iterator&gt; 関数'
ms.date: 11/04/2016
f1_keywords:
- xutility/std::advance
- xutility/std::back_inserter
- xutility/std::begin
- xutility/std::cbegin
- xutility/std::cend
- xutility/std::distance
- xutility/std::end
- xutility/std::front_inserter
- xutility/std::inserter
- xutility/std::make_checked_array_iterator
- xutility/std::make_move_iterator
- xutility/std::make_unchecked_array_iterator
- xutility/std::next
- xutility/std::prev
ms.assetid: 4a57c9a3-7e36-411f-8655-e0be2eec88e7
helpviewer_keywords:
- std::advance [C++]
- std::back_inserter [C++]
- std::begin [C++]
- std::cbegin [C++]
- std::cend [C++]
- std::distance [C++]
- std::end [C++]
- std::front_inserter [C++]
- std::inserter [C++]
- std::make_checked_array_iterator [C++]
- std::make_move_iterator [C++]
- std::make_unchecked_array_iterator [C++]
- std::next [C++]
- std::prev [C++]
ms.openlocfilehash: 69f1007f0c7f587e81313f5de97947410bf243df
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244035"
---
# <a name="ltiteratorgt-functions"></a>&lt;iterator&gt; 関数

## <a name="advance"></a> 高度な

指定された位置の番号によって反復子をインクリメントします。

```cpp
template <class InputIterator, class Distance>
    void advance(InputIterator& InIt, Distance Off);
```

### <a name="parameters"></a>パラメーター

*InIt*\
インクリメントされる、入力反復子の要件を満たしている必要がある反復子。

*オフ*\
反復子の差の型に変換可能で、反復子の位置を進めるインクリメントの数を指定する整数型。

### <a name="remarks"></a>Remarks

進む範囲は非特異である必要があり、反復子が逆参照可能であるか、末尾を超える必要があります。

場合、 `InputIterator` 、双方向反復子の型の要件を満たす*オフ*負の値があります。 場合`InputIterator`は、入力または前方反復子型*オフ*負でない必要があります。

Advance 関数が一定の複雑さと`InputIterator`がランダム アクセス反復子の要件を満たす線形の複雑さを持ち、可能性はそれ以外の場合、します。

### <a name="example"></a>例

```cpp
// iterator_advance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = 1 ; i < 9 ; ++i )
   {
      L.push_back ( i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 4 );
   cout << "LPOS is advanced 4 steps forward to point"
        << " to the fifth element: "
        << *LPOS << "." << endl;

   advance ( LPOS , -3 );
   cout << "LPOS is moved 3 steps back to point to the "
        << "2nd element: " << *LPOS << "." << endl;
}
```

```Output
The list L is: ( 1 2 3 4 5 6 7 8 ).
The iterator LPOS initially points to the first element: 1.
LPOS is advanced 4 steps forward to point to the fifth element: 5.
LPOS is moved 3 steps back to point to the 2nd element: 2.
```

## <a name="back_inserter"></a> back_inserter

指定されたコンテナーの後ろに要素を挿入できる反復子を作成します。

```cpp
template <class Container>
back_insert_iterator<Container> back_inserter(Container& _Cont);
```

### <a name="parameters"></a>パラメーター

*_Cont*\
後方挿入の実行対象となるコンテナー。

### <a name="return-value"></a>戻り値

A`back_insert_iterator`コンテナー オブジェクトに関連付けられた *_Cont*します。

### <a name="remarks"></a>Remarks

C++ 標準ライブラリでは、引数は、メンバー関数 `push_back` が含まれる [deque クラス](../standard-library/deque-class.md)、[list クラス](../standard-library/list-class.md)、[vector クラス](../standard-library/vector-class.md)の 3 つのシーケンス コンテナーのいずれかを参照する必要があります。

### <a name="example"></a>例

```cpp
// iterator_back_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 0 ; i < 3 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Insertions can be done with template function
   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 30;
   backiter++;
*backiter = 40;

   // Alternatively, insertions can be done with the
   // back_insert_iterator member function
   back_inserter ( vec ) = 500;
   back_inserter ( vec ) = 600;

   cout << "After the insertions, the vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The initial vector vec is: ( 0 1 2 ).
After the insertions, the vector vec is: ( 0 1 2 30 40 500 600 ).
```

## <a name="begin"></a> 開始

指定されたコンテナーの最初の要素への反復子を取得します。

```cpp
template <class Container>
auto begin(Container& cont)  `
   -> decltype(cont.begin());

template <class Container>
auto begin(const Container& cont)   `
   -> decltype(cont.begin());

template <class Ty, class Size>
Ty *begin(Ty (& array)[Size]);
```

### <a name="parameters"></a>パラメーター

*続き*\
コンテナー。

*配列*\
`Ty` 型のオブジェクトの配列。

### <a name="return-value"></a>戻り値

最初の 2 つのテンプレート関数は、`cont.begin()` を返します。 最初の関数は定数ではなく、2 番目の関数は定数です。

3 番目のテンプレート関数を返します*配列*します。

### <a name="example"></a>例

さらに、より一般的な動作が必要な場合は、コンテナーのメンバーである `begin()` の代わりにこのテンプレート関数を使用することをお勧めします。

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <functional>
#include <iostream>
#include <iterator>
#include <vector>

template <typename C> void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(begin(c), end(c), std::greater<>());
}

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        std::cout << e << " ";
    }

    std::cout << "\n";
}

int main() {
    std::vector<int> v = { 11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(v);
    reverse_sort(v);
    print(v);

    std::cout << "--\n";

    int arr[] = { 23, 70, 35, 106, 53, 160, 80, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(arr);
    reverse_sort(arr);
    print(arr);
}
```

```Output
11 34 17 52 26 13 40 20 10 5 16 8 4 2 1
52 40 34 26 20 17 16 13 11 10 8 5 4 2 1
--
23 70 35 106 53 160 80 40 20 10 5 16 8 4 2 1
160 106 80 70 53 40 35 23 20 16 10 8 5 4 2 1
```

`reverse_sort` 関数は、通常の配列に加えて、任意の種類のコンテナーをサポートします。これは、メンバーではないバージョンの `begin()` を呼び出すためです。 コンテナーのメンバーである `reverse_sort` を使用するために `begin()` がコーディングされた場合、次のようになります。

```cpp
template <typename C>
void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(c.begin(), c.end(), std::greater<>());

}
```

その後、配列を渡すと、このコンパイラ エラーが発生します。

```Output
error C2228: left of '.begin' must have class/struct/union
```

## <a name="cbegin"></a> cbegin

指定されたコンテナーの最初の要素への const 反復子を取得します。

```cpp
template <class Container>
auto cbegin(const Container& cont)
   -> decltype(cont.begin());
```

### <a name="parameters"></a>パラメーター

*続き*\
コンテナーまたは initializer_list。

### <a name="return-value"></a>戻り値

定数 `cont.begin()`。

### <a name="remarks"></a>Remarks

この関数はすべての C++ 標準ライブラリ コンテナーと [initializer_list](../standard-library/initializer-list-class.md) を使用します。

`begin()` テンプレート関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常は、次の例に示すように [auto](../cpp/auto-cpp.md) 型推論キーワードと共に使用します。 例では、検討してください。`Container`に変更可能な (非**const**) コンテナーまたは`initializer_list`をサポートする任意の種類`begin()`と`cbegin()`します。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a> cend

指定されたコンテナーの最後の要素の後ろにある要素への定数反復子を取得します。

```cpp
template <class Container>
auto cend(const Container& cont)
   -> decltype(cont.end());
```

### <a name="parameters"></a>パラメーター

*続き*\
コンテナーまたは initializer_list。

### <a name="return-value"></a>戻り値

定数 `cont.end()`。

### <a name="remarks"></a>Remarks

この関数はすべての C++ 標準ライブラリ コンテナーと [initializer_list](../standard-library/initializer-list-class.md) を使用します。

[end()](../standard-library/iterator-functions.md#end) テンプレート関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常は、次の例に示すように [auto](../cpp/auto-cpp.md) 型推論キーワードと共に使用します。 例では、検討してください。`Container`に変更可能な (非**const**) コンテナーまたは`initializer_list`をサポートする任意の種類`end()`と`cend()`します。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

## <a name="crbegin"></a> crbegin

```cpp
template <class C> constexpr auto crbegin(const C& c) -> decltype(std::rbegin(c));
```

## <a name="crend"></a> crend

```cpp
template <class C> constexpr auto crend(const C& c) -> decltype(std::rend(c));
```

## <a name="data"></a> データ

```cpp
template <class C> constexpr auto data(C& c) -> decltype(c.data());
template <class C> constexpr auto data(const C& c) -> decltype(c.data());
template <class T, size_t N> constexpr T* data(T (&array)[N]) noexcept;
template <class E> constexpr const E* data(initializer_list<E> il) noexcept;
```

## <a name="distance"></a> 距離

2 つの反復子によってアドレス指定された位置の間のインクリメント数を決定します。

```cpp
template <class InputIterator>
typename iterator_traits<InputIterator>::difference_type distance(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>パラメーター

*まずは*\
2 番目の反復子からの距離を特定する 1 番目の反復子。

*前の*\
1 番目の反復子からの距離を特定する 2 番目の反復子。

### <a name="return-value"></a>戻り値

時間を数*最初*等しくなるまで増加する必要があります*最後*します。

### <a name="remarks"></a>Remarks

Distance 関数が一定の複雑さと`InputIterator`がランダム アクセス反復子の要件を満たす線形の複雑さを持ち、可能性はそれ以外の場合、します。

### <a name="example"></a>例

```cpp
// iterator_distance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 7 );
   cout << "LPOS is advanced 7 steps forward to point "
        << " to the eighth element: "
        << *LPOS << "." << endl;

   list<int>::difference_type Ldiff ;
   Ldiff = distance ( L.begin ( ) , LPOS );
   cout << "The distance from L.begin( ) to LPOS is: "
        << Ldiff << "." << endl;
}
```

```Output
The list L is: ( -2 0 2 4 6 8 10 12 14 16 ).
The iterator LPOS initially points to the first element: -2.
LPOS is advanced 7 steps forward to point  to the eighth element: 12.
The distance from L.begin( ) to LPOS is: 7.
```

## <a name="empty"></a> 空

```cpp
template <class C> constexpr auto empty(const C& c) -> decltype(c.empty());
template <class T, size_t N> constexpr bool empty(const T (&array)[N]) noexcept;
template <class E> constexpr bool empty(initializer_list<E> il) noexcept;
```

## <a name="end"></a> 終わり

指定されたコンテナーの最後の要素の後ろにある要素への反復子を取得します。

```cpp
template <class Container>
auto end(Container& cont)
   -> decltype(cont.end());

template <class Container>
auto end(const Container& cont)
   -> decltype(cont.end());

template <class Ty, class Size>
Ty *end(Ty (& array)[Size]);
```

### <a name="parameters"></a>パラメーター

*続き*\
コンテナー。

*配列*\
`Ty` 型のオブジェクトの配列。

### <a name="return-value"></a>戻り値

最初の 2 つのテンプレート関数は `cont.end()` を返します (最初は非定数で、2 番目は定数です)。

3 番目のテンプレート関数は `array + Size` を返します。

### <a name="remarks"></a>Remarks

コード例については、[begin](../standard-library/iterator-functions.md#begin) を参照してください。

## <a name="front_inserter"></a> front_inserter

指定されたコンテナーの前に要素を挿入できる反復子を作成します。

```cpp
template <class Container>
front_insert_iterator<Container> front_inserter(Container& _Cont);
```

### <a name="parameters"></a>パラメーター

*_Cont*\
先頭に要素が挿入されるコンテナー オブジェクト。

### <a name="return-value"></a>戻り値

A`front_insert_iterator`コンテナー オブジェクトに関連付けられた *_Cont*します。

### <a name="remarks"></a>Remarks

front_insert_iterator クラスのメンバー関数 [front_insert_iterator](../standard-library/front-insert-iterator-class.md#front_insert_iterator) も使用できます。

C++ 標準ライブラリでは、引数は、メンバー関数 `push_back` が含まれる [deque クラス](../standard-library/deque-class.md)または "list クラス" の 2 つのシーケンス コンテナーのいずれかを参照する必要があります。

### <a name="example"></a>例

```cpp
// iterator_front_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template function to insert an element
   front_insert_iterator< list < int> > Iter(L);
*Iter = 100;

   // Alternatively, you may use the front_insert member function
   front_inserter ( L ) = 200;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
( -1 0 1 2 3 4 5 6 7 8 ).
After the front insertions, the list L is:
( 200 100 -1 0 1 2 3 4 5 6 7 8 ).
```

## <a name="inserter"></a> inserter

使用できるようにするヘルパー テンプレート関数`inserter(_Cont, _Where)`の代わりに`insert_iterator<Container>(_Cont, _Where)`します。

```cpp
template <class Container>
insert_iterator<Container>
inserter(
    Container& _Cont,
    typename Container::iterator _Where);
```

### <a name="parameters"></a>パラメーター

*_Cont*\
新しい要素が追加されるコンテナー。

*_Where*\
挿入位置を指定する反復子。

### <a name="remarks"></a>Remarks

テンプレート関数を返します[insert_iterator](../standard-library/insert-iterator-class.md#insert_iterator)`<Container>(_Cont, _Where)`します。

### <a name="example"></a>例

```cpp
// iterator_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = 2 ; i < 5 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template version to insert an element
   insert_iterator<list <int> > Iter( L, L.begin ( ) );
*Iter = 1;

   // Alternatively, using the member function to insert an element
   inserter ( L, L.end ( ) ) = 500;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
( 20 30 40 ).
After the insertions, the list L is:
( 1 20 30 40 500 ).
```

## <a name="make_checked_array_iterator"></a> make_checked_array_iterator

他のアルゴリズムで使用できる [checked_array_iterator](../standard-library/checked-array-iterator-class.md) を作成します。

> [!NOTE]
> この関数は、標準 C++ ライブラリの Microsoft 拡張機能です。 この関数を使用して実装されるコードは、Microsoft 拡張機能をサポートしない C++ 標準ビルド環境には移植できません。

```cpp
template <class Iter>
checked_array_iterator<Iter>
    make_checked_array_iterator(
Iter Ptr,
    size_t Size,
    size_t Index = 0);
```

### <a name="parameters"></a>パラメーター

*ptr*\
コピー先配列へのポインター。

*サイズ*\
ターゲット配列のサイズ。

*インデックス*\
配列のインデックス (省略可能)。

### <a name="return-value"></a>戻り値

`checked_array_iterator` のインスタンス。

### <a name="remarks"></a>Remarks

`make_checked_array_iterator` 関数は `stdext` 名前空間で定義されています。

この関数は、生のポインター (通常、境界オーバーランに関する問題の原因となる) を受け取り、チェックを行う [checked_array_iterator](../standard-library/checked-array-iterator-class.md) クラスでポインターをラップします。 そのクラスはチェック済みとしてマークされるので、C++ 標準ライブラリはそれについて警告を表示しません。 詳細およびコード例については、「[チェックを行う反復子](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

次の例では、[ベクター](../standard-library/vector-class.md)が作成され、10 個の項目が設定されます。 ベクターのコンテンツはコピー アルゴリズムで配列にコピーされ、`make_checked_array_iterator` を使用してコピー先が指定されます。 その後、境界チェックの意図的な違反によって、デバッグのアサーション エラーがトリガーされます。

```cpp
// make_checked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_checked_array_iterator
#include <memory> // std::make_unique
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const size_t dest_size = 10;
    // Old-school but not exception safe, favor make_unique<int[]>
    // int* dest = new int[dest_size];
    unique_ptr<int[]> updest = make_unique<int[]>(dest_size);
    int* dest = updest.get(); // get a raw pointer for the demo

    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    // Add another element to the vector to force an overrun.
    v.push_back(10);
    // The next line causes a debug assertion when it executes.
    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));
}
```

## <a name="make_move_iterator"></a> make_move_iterator

指定した反復子を `stored` 反復子として含む `move iterator` を作成します。

```cpp
template <class Iterator>
move_iterator<Iterator>
make_move_iterator(const Iterator& _It);
```

### <a name="parameters"></a>パラメーター

*_It*\
新しい move 反復子に格納する反復子。

### <a name="remarks"></a>Remarks

テンプレート関数を返します`move_iterator``<Iterator>(_It)`します。

## <a name="make_unchecked_array_iterator"></a> make_unchecked_array_iterator

他のアルゴリズムで使用できる [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md) を作成します。

> [!NOTE]
> この関数は、標準 C++ ライブラリの Microsoft 拡張機能です。 この関数を使用して実装されるコードは、Microsoft 拡張機能をサポートしない C++ 標準ビルド環境には移植できません。

```cpp
template <class Iter>
unchecked_array_iterator<Iter>
    make_unchecked_array_iterator(Iter Ptr);
```

### <a name="parameters"></a>パラメーター

*ptr*\
コピー先配列へのポインター。

### <a name="return-value"></a>戻り値

`unchecked_array_iterator` のインスタンス。

### <a name="remarks"></a>Remarks

`make_unchecked_array_iterator` 関数は `stdext` 名前空間で定義されています。

この関数は生のポインターを受け取り、チェックを行わず何も最適化しないクラスにラップしますが、[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) などのコンパイラ警告も抑制します。 したがって、これは未チェックのポインターの警告を処理するのに適した方法であり、警告がグローバルに抑制されることも、チェックのコストが発生することもありません。 詳細およびコード例については、「[チェックを行う反復子](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

次の例では、[ベクター](../standard-library/vector-class.md)が作成され、10 個の項目が設定されます。 ベクターのコンテンツはコピー アルゴリズムで配列にコピーされ、`make_unchecked_array_iterator` を使用してコピー先が指定されます。

```cpp
// make_unchecked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_unchecked_array_iterator
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const size_t dest_size = 10;
    int *dest = new int[dest_size];
    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    // COMPILER WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun will trigger undefined behavior)
    copy(v.begin(), v.end(), stdext::make_unchecked_array_iterator(dest));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    delete[] dest;
}
```

## <a name="next"></a> 次に

指定された回数を繰り返し、新しい反復子の位置を返します。

```cpp
template <class InputIterator>
InputIterator next(
    InputIterator first,
    typename iterator_traits<InputIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>パラメーター

*まずは*\
現在位置を返します。

*_Off*\
反復する回数。

### <a name="return-value"></a>戻り値

反復処理後の新しい反復子の位置を返します *_Off*時間。

### <a name="remarks"></a>Remarks

テンプレート関数を返します`next`インクリメント *_Off*回

## <a name="prev"></a> [前へ]

指定された回数を逆方向に繰り返し、新しい反復子の位置を返します。

```cpp
template <class BidirectionalIterator>
BidirectionalIterator prev(
    BidirectionalIterator first,
    typename iterator_traits<BidirectionalIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>パラメーター

*まずは*\
現在位置を返します。

*_Off*\
反復する回数。

### <a name="remarks"></a>Remarks

このテンプレート関数は、`off` 回デクリメントされた `next` を返します。

## <a name="rbegin"></a> rbegin

```cpp
template <class C> constexpr auto rbegin(C& c) -> decltype(c.rbegin());
template <class C> constexpr auto rbegin(const C& c) -> decltype(c.rbegin());
```

## <a name="rend"></a> rend

```cpp
template <class C> constexpr auto rend(C& c) -> decltype(c.rend());
template <class C> constexpr auto rend(const C& c) -> decltype(c.rend());
```

## <a name="size"></a> サイズ

```cpp
template <class C> constexpr auto size(const C& c) -> decltype(c.size());
template <class T, size_t N> constexpr size_t size(const T (&array)[N]) noexcept;
```
