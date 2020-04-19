---
title: array クラス (C++ 標準ライブラリ) |Microsoft Docs
ms.date: 11/13/2019
f1_keywords:
- array/std::array
- array/std::array::const_iterator
- array/std::array::const_pointer
- array/std::array::const_reference
- array/std::array::const_reverse_iterator
- array/std::array::difference_type
- array/std::array::iterator
- array/std::array::pointer
- array/std::array::reference
- array/std::array::reverse_iterator
- array/std::array::size_type
- array/std::array::value_type
- array/std::array::assign
- array/std::array::at
- array/std::array::back
- array/std::array::begin
- array/std::array::cbegin
- array/std::array::cend
- array/std::array::crbegin
- array/std::array::crend
- array/std::array::data
- array/std::array::empty
- array/std::array::end
- array/std::array::fill
- array/std::array::front
- array/std::array::max_size
- array/std::array::rbegin
- array/std::array::rend
- array/std::array::size
- array/std::array::swap
- array/std::array::operator=
- array/std::array::operator[]
helpviewer_keywords:
- std::array [C++]
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
- ', '
- std::array [C++], const_iterator
- std::array [C++], const_pointer
- std::array [C++], const_reference
- std::array [C++], const_reverse_iterator
- std::array [C++], difference_type
- std::array [C++], iterator
- std::array [C++], pointer
- std::array [C++], reference
- std::array [C++], reverse_iterator
- std::array [C++], size_type
- std::array [C++], value_type
- std::array [C++], assign
- std::array [C++], at
- std::array [C++], back
- std::array [C++], begin
- std::array [C++], cbegin
- std::array [C++], cend
- std::array [C++], crbegin
- std::array [C++], crend
- std::array [C++], data
- std::array [C++], empty
- std::array [C++], end
- std::array [C++], fill
- std::array [C++], front
- std::array [C++], max_size
- std::array [C++], rbegin
- std::array [C++], rend
- std::array [C++], size
- std::array [C++], swap
ms.assetid: fdfd43a5-b2b5-4b9e-991f-93bf10fb4293
ms.openlocfilehash: e93f5089e62956e7473c95eb6835046b5fe992bf
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189410"
---
# <a name="array-class-c-standard-library"></a>array クラス (C++ 標準ライブラリ)

長さ `N` の `Ty` 型の要素のシーケンスを制御するオブジェクトを記述します。 このシーケンスは、`Ty` オブジェクト内に含まれる `array<Ty, N>` の配列として格納されます。

## <a name="syntax"></a>構文

```cpp
template <class Ty, std::size_t N>
class array;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|`Ty`|要素の型。|
|`N`|要素の数。|

## <a name="members"></a>メンバー

|型定義|説明|
|-|-|
|[const_iterator](#const_iterator)|被制御シーケンスの定数反復子の型です。|
|[const_pointer](#const_pointer)|要素への定数ポインターの型です。|
|[const_reference](#const_reference)|要素への定数参照の型です。|
|[const_reverse_iterator](#const_reverse_iterator)|被制御シーケンスの定数反転反復子の型です。|
|[difference_type](#difference_type)|2 つの要素間の距離を表す、符号付きの型です。|
|[iterator](#iterator)|被制御シーケンスの反復子の型です。|
|[pointer](#pointer)|要素へのポインターの型です。|
|[reference](#reference)|要素への参照の型です。|
|[reverse_iterator](#reverse_iterator)|被制御シーケンスの反転反復子の型です。|
|[size_type](#size_type)|2 つの要素間の距離を表す、符号なしの型です。|
|[value_type](#value_type)|要素の型。|

|メンバー関数|説明|
|-|-|
|[array](#array)|配列オブジェクトを構築します。|
|[assign](#assign)|公表. `fill`を使用します。)すべての要素を置換します。|
|[at](#at)|指定した位置にある要素にアクセスします。|
|[back](#back)|最後の要素にアクセスします。|
|[begin](#begin)|被制御シーケンスの先頭を指定します。|
|[cbegin](#cbegin)|配列内の最初の要素を示すランダム アクセスの定数反復子を返します。|
|[cend](#cend)|配列の末尾の次の位置を指し示すランダム アクセス定数反復子を返します。|
|[crbegin](#crbegin)|反転された配列内の最初の要素への定数反復子を返します。|
|[crend](#crend)|反転された配列内の末尾の要素への定数反復子を返します。|
|[data](#data)|最初の要素のアドレスを取得します。|
|[empty](#empty)|要素が存在するかどうかをテストします。|
|[end](#end)|被制御シーケンスの末尾を指定します。|
|[fill](#fill)|すべての要素を、指定された値に置き換えます。|
|[front](#front)|最初の要素にアクセスします。|
|[max_size](#max_size)|要素の数をカウントします。|
|[rbegin](#rbegin)|反転被制御シーケンスの先頭を指定します。|
|[rend](#rend)|反転被制御シーケンスの末尾を指定します。|
|[size](#size)|要素の数をカウントします。|
|[swap](#swap)|2 つのコンテナーのコンテンツを交換します。|

|演算子|説明|
|-|-|
|[array::operator=](#op_eq)|被制御シーケンスを置き換えます。|
|[array:: operator\[\]](#op_at)|指定した位置にある要素にアクセスします。|

## <a name="remarks"></a>コメント

この型は、既定のコンストラクター `array()` と既定代入演算子 `operator=` を持ち、`aggregate` の要件を満たします。 そのため、`array<Ty, N>` 型のオブジェクトは、集計初期化子を使用して初期化できます。 次に例を示します。

```cpp
array<int, 4> ai = { 1, 2, 3 };
```

このコードは、4 つの整数値を保持するオブジェクト `ai` を作成し、最初の 3 つの要素はそれぞれ値 1、2、3 に初期化し、4 番目の要素は 0 に初期化します。

## <a name="requirements"></a>要件

**Header:** \<array>

**名前空間:** std

## <a name="array"></a>  array::array

配列オブジェクトを構築します。

```cpp
array();

array(const array& right);
```

### <a name="parameters"></a>パラメーター

*右*\
挿入するオブジェクトまたは範囲。

### <a name="remarks"></a>コメント

既定のコンストラクター `array()` は、被制御シーケンスを初期化されない状態 (または既定の初期化された状態) のままにします。 これを使用して、初期化されていない被制御シーケンスを指定します。

コピー コンストラクター `array(const array& right)` は、被制御シーケンスをシーケンス [*right*`.begin()`, *right*`.end()`) で初期化します。 これを使用して、配列オブジェクト *right* によって制御されるシーケンスのコピーである最初の被制御シーケンスを指定します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    typedef std::array<int, 4> Myarray;

    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1(c0);

    // display contents " 0 1 2 3"
    for (const auto& it : c1)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="assign"></a>  array::assign

C++ 11 では廃止され、[fill](#fill) に置き換えられています。 すべての要素を置換します。

## <a name="at"></a>  array::at

指定した位置にある要素にアクセスします。

```cpp
reference at(size_type off);

constexpr const_reference at(size_type off) const;
```

### <a name="parameters"></a>パラメーター

*オフ*\
アクセスする要素の位置。

### <a name="remarks"></a>コメント

このメンバー関数は、制御されたシーケンスの要素への参照を*off*の位置に返します。 その位置が無効の場合、関数はクラス `out_of_range` のオブジェクトをスローします。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display odd elements " 1 3"
    std::cout << " " << c0.at(1);
    std::cout << " " << c0.at(3);
    std::cout << std::endl;

    return (0);
}
```

## <a name="back"></a>  array::back

最後の要素にアクセスします。

```cpp
reference back();

constexpr const_reference back() const;
```

### <a name="remarks"></a>コメント

このメンバー関数は、被制御シーケンスの最後の要素への参照を返します。被制御シーケンスを空にすることはできません。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    std::cout << " " << c0.back();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="begin"></a>  array::begin

被制御シーケンスの先頭を指定します。

```cpp
iterator begin() noexcept;
const_iterator begin() const noexcept;
```

### <a name="remarks"></a>コメント

メンバー関数は、シーケンスの最初の要素 (または空のシーケンスの末尾の次の位置) を示すランダム アクセス反復子を返します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::iterator it2 = c0.begin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="cbegin"></a>  array::cbegin

範囲内の最初の要素を指す**定数**反復子を返します。

```cpp
const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>戻り値

範囲の最初の要素、または空の範囲の末尾の次の位置 (空の範囲の場合は `cbegin() == cend()`) を指す**const**ランダムアクセス反復子。

### <a name="remarks"></a>コメント

`cbegin` の戻り値で範囲内の要素を変更することはできません。

`begin()` メンバー関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常は、次の例に示すように [auto](../cpp/auto-cpp.md) 型推論キーワードと共に使用します。 この例では、`begin()` と `cbegin()`をサポートする任意の種類の変更可能な (非**定数**) コンテナーとして `Container` を検討してください。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  array::cend

範囲内の最後の要素の次の位置を指す**定数**反復子を返します。

```cpp
const_iterator cend() const noexcept;
```

### <a name="return-value"></a>戻り値

範囲の末尾の次の位置を指し示すランダム アクセス反復子。

### <a name="remarks"></a>コメント

`cend` は、反復子が範囲の末尾を超えたかどうかをテストするために使用されます。

`end()` メンバー関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常は、次の例に示すように [auto](../cpp/auto-cpp.md) 型推論キーワードと共に使用します。 この例では、`end()` と `cend()`をサポートする任意の種類の変更可能な (非**定数**) コンテナーとして `Container` を検討してください。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend` によって返された値は逆参照しないでください。

## <a name="const_iterator"></a>  array::const_iterator

被制御シーケンスの定数反復子の型です。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>コメント

この型は、被制御シーケンスの定数ランダム アクセス反復子として使用できるオブジェクトを表します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for (MyArray::const_iterator it1 = c0.begin();
        it1 != c0.end();
        ++it1) {
        std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::const_iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
it1: 0 1 2 3
it2: 0
```

## <a name="const_pointer"></a>  array::const_pointer

要素への定数ポインターの型です。

```cpp
typedef const Ty *const_pointer;
```

### <a name="remarks"></a>コメント

この型は、シーケンスの要素への定数ポインターとして使用できるオブジェクトを表します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="const_reference"></a>  array::const_reference

要素への定数参照の型です。

```cpp
typedef const Ty& const_reference;
```

### <a name="remarks"></a>コメント

この型は、被制御シーケンスの要素への定数参照として使用できるオブジェクトを表します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="const_reverse_iterator"></a>  array::const_reverse_iterator

被制御シーケンスの定数反転反復子の型です。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>コメント

この型は、被制御シーケンスの定数反転反復子として使用できるオブジェクトを表します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="crbegin"></a>  array::crbegin

反転された配列内の最初の要素への定数反復子を返します。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>戻り値

反転された配列の最初の要素を指すか、反転されていない配列の最後の要素だったものを指す、定数逆順ランダム アクセス反復子。

### <a name="remarks"></a>コメント

戻り値が `crbegin` の場合、配列オブジェクトは変更できません。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::iterator v1_Iter;
   array<int, 2>::const_reverse_iterator v1_rIter;

   v1_Iter = v1.begin( );
   cout << "The first element of array is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed array is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of array is 1.
The first element of the reversed array is 2.
```

## <a name="crend"></a>  array::crend

逆順の配列内の最後の要素の次の位置を指す定数反復子を返します。

```cpp
const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>戻り値

逆順の配列内の最後の要素の次の位置 (通常の順序の配列内の最初の要素の前の位置) を指す定数逆順ランダム アクセス反復子。

### <a name="remarks"></a>コメント

`crend` は、[array::cend](#cend) が配列で使用されるときと同様の方法により、逆順の配列で使用されます。

戻り値が (適切にデクリメントされた) `crend` の場合、配列オブジェクトは変更できません。

`crend` を使用して、逆順反復子が配列の末尾に達したかどうかをテストできます。

`crend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

int main( )
{
   using namespace std;
   array<int, 2> v1 = {1, 2};
   array<int, 2>::const_reverse_iterator v1_rIter;

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="data"></a>  array::data

最初の要素のアドレスを取得します。

```cpp
Ty *data();

const Ty *data() const;
```

### <a name="remarks"></a>コメント

メンバー関数は、被制御シーケンス内の最初の要素のアドレスを返します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::pointer ptr = c0.data();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="difference_type"></a>  array::difference_type

2 つの要素間の距離を表す、符号付きの型です。

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>コメント

符号付き整数型は、被制御シーケンス内にある 2 つの要素のアドレスの違いを表すことのできるオブジェクトを記述します。 これは `std::ptrdiff_t` 型のシノニムです。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display distance first-last " -4"
    Myarray::difference_type diff = c0.begin() - c0.end();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
-4
```

## <a name="empty"></a>  array::empty

要素が存在しないかどうかをテストします。

```cpp
constexpr bool empty() const;
```

### <a name="remarks"></a>コメント

`N == 0` の場合にのみ、メンバー関数は true を返します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display whether c0 is empty " false"
    std::cout << std::boolalpha << " " << c0.empty();
    std::cout << std::endl;

    std::array<int, 0> c1;

    // display whether c1 is empty " true"
    std::cout << std::boolalpha << " " << c1.empty();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
false
true
```

## <a name="end"></a>  array::end

被制御シーケンスの末尾を指定します。

```cpp
reference end();

const_reference end() const;
```

### <a name="remarks"></a>コメント

このメンバー関数は、シーケンスの最後を越えたところを示すランダム アクセス反復子を返します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::iterator it2 = c0.end();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="fill"></a>  array::fill

配列を消去し、空の配列に指定された要素をコピーします。

```cpp
void fill(const Type& val);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*val*|配列に挿入される要素の値。|

### <a name="remarks"></a>コメント

`fill` は、配列の各要素を、指定された値に置き換えます。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

int main()
{
    using namespace std;
    array<int, 2> v1 = { 1, 2 };

    cout << "v1 = ";
    for (const auto& it : v1)
    {
        std::cout << " " << it;
    }
    cout << endl;

    v1.fill(3);
    cout << "v1 = ";
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    cout << endl;
}
```

## <a name="front"></a>  array::front

最初の要素にアクセスします。

```cpp
reference front();

constexpr const_reference front() const;
```

### <a name="remarks"></a>コメント

このメンバー関数は、被制御シーケンスの最初の要素への参照を返します。被制御シーケンスを空にすることはできません。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    std::cout << " " << c0.front();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="iterator"></a>  array::iterator

被制御シーケンスの反復子の型です。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>コメント

この型は、被制御シーケンスのランダム アクセス反復子として使用できるオブジェクトを表します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> MyArray;

int main()
{
    MyArray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    std::cout << "it1:";
    for (MyArray::iterator it1 = c0.begin();
        it1 != c0.end();
        ++it1) {
        std::cout << " " << *it1;
    }
    std::cout << std::endl;

    // display first element " 0"
    MyArray::iterator it2 = c0.begin();
    std::cout << "it2:";
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
it1: 0 1 2 3

it2: 0
```

## <a name="max_size"></a>  array::max_size

要素の数をカウントします。

```cpp
constexpr size_type max_size() const;
```

### <a name="remarks"></a>コメント

このメンバー関数は、`N` を返します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display (maximum) size " 4"
    std::cout << " " << c0.max_size();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="op_at"></a>  array::operator[]

指定した位置にある要素にアクセスします。

```cpp
reference operator[](size_type off);

constexpr const_reference operator[](size_type off) const;
```

### <a name="parameters"></a>パラメーター

*オフ*\
アクセスする要素の位置。

### <a name="remarks"></a>コメント

このメンバー関数は、制御されたシーケンスの要素への参照を*off*の位置に返します。 その位置が無効な場合、動作は定義されません。

また、**配列**の要素への参照を取得するために使用できる非メンバーの[get](array-functions.md#get)関数もあります。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display odd elements " 1 3"
    std::cout << " " << c0[1];
    std::cout << " " << c0[3];
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
1 3
```

## <a name="op_eq"></a>  array::operator=

被制御シーケンスを置き換えます。

```cpp
array<Value> operator=(array<Value> right);
```

### <a name="parameters"></a>パラメーター

*右*\
コピーするコンテナー。

### <a name="remarks"></a>コメント

メンバー演算子は、制御されたシーケンスの対応する要素に*right*の各要素を代入し、`*this`を返します。 このメソッドを使用して、被制御シーケンスを*右側*の被制御シーケンスのコピーで置き換えます。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1;
    c1 = c0;

    // display copied contents " 0 1 2 3"
        // display contents " 0 1 2 3"
    for (auto it : c1)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="pointer"></a>  array::pointer

要素へのポインターの型です。

```cpp
typedef Ty *pointer;
```

### <a name="remarks"></a>コメント

この型は、シーケンスの要素へのポインターとして使用できるオブジェクトを表します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::pointer ptr = &*c0.begin();
    std::cout << " " << *ptr;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="rbegin"></a>  array::rbegin

反転被制御シーケンスの先頭を指定します。

```cpp
reverse_iterator rbegin()noexcept;
const_reverse_iterator rbegin() const noexcept;
```

### <a name="remarks"></a>コメント

このメンバー関数は、被制御シーケンスの最後を越えたところを示す反転反復子を返します。 したがって、反転シーケンスの先頭を指定します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::const_reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="reference"></a>  array::reference

要素への参照の型です。

```cpp
typedef Ty& reference;
```

### <a name="remarks"></a>コメント

この型は、被制御シーケンスの要素への参照として機能するオブジェクトを表します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::reference ref = *c0.begin();
    std::cout << " " << ref;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="rend"></a>  array::rend

反転被制御シーケンスの末尾を指定します。

```cpp
reverse_iterator rend()noexcept;
const_reverse_iterator rend() const noexcept;
```

### <a name="remarks"></a>コメント

メンバー関数は、シーケンスの最初の要素 (または空のシーケンスの末尾の次の位置) を示す反転反復子を返します。 したがって、反転シーケンスの末尾を指定します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display first element " 0"
    Myarray::const_reverse_iterator it2 = c0.rend();
    std::cout << " " << *--it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0
```

## <a name="reverse_iterator"></a>  array::reverse_iterator

被制御シーケンスの反転反復子の型です。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>コメント

この型は、被制御シーケンスの反転反復子として使用できるオブジェクトを表します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display last element " 3"
    Myarray::reverse_iterator it2 = c0.rbegin();
    std::cout << " " << *it2;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
3
```

## <a name="size"></a>  array::size

要素の数をカウントします。

```cpp
constexpr size_type size() const;
```

### <a name="remarks"></a>コメント

このメンバー関数は、`N` を返します。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display size " 4"
    std::cout << " " << c0.size();
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="size_type"></a>  array::size_type

2 つの要素間の距離を表す、符号なしの型です。

```cpp
typedef std::size_t size_type;
```

### <a name="remarks"></a>コメント

符号なし整数型は、被制御シーケンスの長さを表すことができるオブジェクトを表します。 これは `std::size_t` 型のシノニムです。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display distance last-first " 4"
    Myarray::size_type diff = c0.end() - c0.begin();
    std::cout << " " << diff;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4
```

## <a name="swap"></a>  array::swap

この配列の内容を別の配列と交換します。

```cpp
void swap(array& right);
```

### <a name="parameters"></a>パラメーター

*右*\
コンテンツを交換する配列。

### <a name="remarks"></a>コメント

このメンバー関数は、`*this` と*right*の間で被制御シーケンスを交換します。 さまざまな要素の割り当てを実行し、`N` に比例してコンストラクターを呼び出します。

2つの**配列**インスタンスをスワップするために使用できる非メンバー[スワップ](array-functions.md#swap)関数もあります。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    Myarray c1 = { 4, 5, 6, 7 };
    c0.swap(c1);

    // display swapped contents " 4 5 6 7"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    swap(c0, c1);

    // display swapped contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
0 1 2 3
```

## <a name="value_type"></a>  array::value_type

要素の型。

```cpp
typedef Ty value_type;
```

### <a name="remarks"></a>コメント

この型は、テンプレート パラメーター `Ty`のシノニムです。

### <a name="example"></a>例

```cpp
#include <array>
#include <iostream>

typedef std::array<int, 4> Myarray;
int main()
{
    Myarray c0 = { 0, 1, 2, 3 };

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        std::cout << " " << it;
    }
    std::cout << std::endl;

    // display contents " 0 1 2 3"
    for (const auto& it : c0)
    {
        Myarray::value_type val = it;
        std::cout << " " << val;
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="see-also"></a>参照

[\<array>](../standard-library/array.md)
