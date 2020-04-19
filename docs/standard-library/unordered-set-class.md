---
title: unordered_set クラス
ms.date: 11/04/2016
f1_keywords:
- unordered_set/std::unordered_set
- unordered_set/std::unordered_set::allocator_type
- unordered_set/std::unordered_set::const_iterator
- unordered_set/std::unordered_set::const_local_iterator
- unordered_set/std::unordered_set::const_pointer
- unordered_set/std::unordered_set::const_reference
- unordered_set/std::unordered_set::difference_type
- unordered_set/std::unordered_set::hasher
- unordered_set/std::unordered_set::iterator
- unordered_set/std::unordered_set::key_equal
- unordered_set/std::unordered_set::key_type
- unordered_set/std::unordered_set::local_iterator
- unordered_set/std::unordered_set::pointer
- unordered_set/std::unordered_set::reference
- unordered_set/std::unordered_set::size_type
- unordered_set/std::unordered_set::value_type
- unordered_set/std::unordered_set::begin
- unordered_set/std::unordered_set::bucket
- unordered_set/std::unordered_set::bucket_count
- unordered_set/std::unordered_set::bucket_size
- unordered_set/std::unordered_set::cbegin
- unordered_set/std::unordered_set::cend
- unordered_set/std::unordered_set::clear
- unordered_set/std::unordered_set::count
- unordered_set/std::unordered_set::emplace
- unordered_set/std::unordered_set::emplace_hint
- unordered_set/std::unordered_set::empty
- unordered_set/std::unordered_set::end
- unordered_set/std::unordered_set::equal_range
- unordered_set/std::unordered_set::erase
- unordered_set/std::unordered_set::find
- unordered_set/std::unordered_set::get_allocator
- unordered_set/std::unordered_set::hash
- unordered_set/std::unordered_set::insert
- unordered_set/std::unordered_set::key_eq
- unordered_set/std::unordered_set::load_factor
- unordered_set/std::unordered_set::max_bucket_count
- unordered_set/std::unordered_set::max_load_factor
- unordered_set/std::unordered_set::max_size
- unordered_set/std::unordered_set::rehash
- unordered_set/std::unordered_set::size
- unordered_set/std::unordered_set::swap
- unordered_set/std::unordered_set::unordered_set
- unordered_set/std::unordered_set::operator=
- unordered_set/std::unordered_set::hash_function
helpviewer_keywords:
- std::unordered_set
- std::unordered_set::allocator_type
- std::unordered_set::const_iterator
- std::unordered_set::const_local_iterator
- std::unordered_set::const_pointer
- std::unordered_set::const_reference
- std::unordered_set::difference_type
- std::unordered_set::hasher
- std::unordered_set::iterator
- std::unordered_set::key_equal
- std::unordered_set::key_type
- std::unordered_set::local_iterator
- std::unordered_set::pointer
- std::unordered_set::reference
- std::unordered_set::size_type
- std::unordered_set::value_type
- std::unordered_set::begin
- std::unordered_set::bucket
- std::unordered_set::bucket_count
- std::unordered_set::bucket_size
- std::unordered_set::cbegin
- std::unordered_set::cend
- std::unordered_set::clear
- std::unordered_set::count
- std::unordered_set::emplace
- std::unordered_set::emplace_hint
- std::unordered_set::empty
- std::unordered_set::end
- std::unordered_set::equal_range
- std::unordered_set::erase
- std::unordered_set::find
- std::unordered_set::get_allocator
- std::unordered_set::hash
- std::unordered_set::insert
- std::unordered_set::key_eq
- std::unordered_set::load_factor
- std::unordered_set::max_bucket_count
- std::unordered_set::max_load_factor
- std::unordered_set::max_size
- std::unordered_set::rehash
- std::unordered_set::size
- std::unordered_set::swap
- std::unordered_set::unordered_set
- std::unordered_set::operator=
- std::unordered_set::allocator_type
- std::unordered_set::const_iterator
- std::unordered_set::const_local_iterator
- std::unordered_set::const_pointer
- std::unordered_set::const_reference
- std::unordered_set::difference_type
- std::unordered_set::hasher
- std::unordered_set::iterator
- std::unordered_set::key_equal
- std::unordered_set::key_type
- std::unordered_set::local_iterator
- std::unordered_set::pointer
- std::unordered_set::reference
- std::unordered_set::size_type
- std::unordered_set::value_type
- std::unordered_set::begin
- std::unordered_set::bucket
- std::unordered_set::bucket_count
- std::unordered_set::bucket_size
- std::unordered_set::cbegin
- std::unordered_set::cend
- std::unordered_set::clear
- std::unordered_set::count
- std::unordered_set::emplace
- std::unordered_set::emplace_hint
- std::unordered_set::empty
- std::unordered_set::end
- std::unordered_set::equal_range
- std::unordered_set::erase
- std::unordered_set::find
- std::unordered_set::get_allocator
- std::unordered_set::hash_function
- std::unordered_set::insert
- std::unordered_set::key_eq
- std::unordered_set::load_factor
- std::unordered_set::max_bucket_count
- std::unordered_set::max_load_factor
- std::unordered_set::max_size
- std::unordered_set::rehash
- std::unordered_set::size
- std::unordered_set::swap
ms.assetid: ac08084e-05a7-48c0-9ae4-d40c529922dd
ms.openlocfilehash: 1aebb30649d138b22c5b9dae95662f84a6bf39f2
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684100"
---
# <a name="unordered_set-class"></a>unordered_set クラス

クラステンプレートは、`const Key` 型の要素の可変長シーケンスを制御するオブジェクトを表します。 このシーケンスは、ハッシュ関数によって、"バケット" と呼ばれる一列に並んだサブシーケンスに分割され、弱い順序付けがなされます。 各バケット内では、比較関数によって要素間の大小関係が決定されます。 各要素には、並べ替えキーと値という、2 つの側面があります。 このシーケンスは、すべてのバケットの長さがおおよそ等しければ、シーケンス内の要素数にかかわらず一定の演算回数 (定数時間) で、任意の要素を検索、挿入、削除できるような方法で表現されます。 最悪のケースは、すべての要素が 1 つのバケットに集められたときです。演算の回数は、シーケンス内の要素数に比例して増えることになります (線形時間)。 要素を挿入しても反復子の有効性は失われません。また、要素を削除した場合は、削除された要素を指す反復子だけが無効化されます。

## <a name="syntax"></a>構文

```cpp
template <
   class Key,
   class Hash = std::hash<Key>,
   class Pred = std::equal_to<Key>,
   class Alloc = std::allocator<Key>>
class unordered_set;
```

### <a name="parameters"></a>パラメーター

*キー* \
キーの型。

*ハッシュ*\
ハッシュ関数のオブジェクト型。

*Pred* \
等価比較関数のオブジェクト型。

*Alloc* \
アロケーター クラス。

## <a name="members"></a>メンバー

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[allocator_type](#allocator_type)|ストレージを管理するためのアロケーターの型です。|
|[const_iterator](#const_iterator)|被制御シーケンスの定数反復子の型です。|
|[const_local_iterator](#const_local_iterator)|被制御シーケンスの定数バケット反復子の型です。|
|[const_pointer](#const_pointer)|要素への定数ポインターの型です。|
|[const_reference](#const_reference)|要素への定数参照の型です。|
|[difference_type](#difference_type)|2 つの要素間の距離を表す、符号付きの型です。|
|[hasher](#hasher)|ハッシュ関数の型です。|
|[Iterator](#iterator)|被制御シーケンスの反復子の型です。|
|[key_equal](#key_equal)|比較関数の型です。|
|[key_type](#key_type)|順序付けキーの型です。|
|[local_iterator](#local_iterator)|被制御シーケンスのバケット反復子の型です。|
|[pointer](#pointer)|要素へのポインターの型です。|
|[reference](#reference)|要素への参照の型です。|
|[size_type](#size_type)|2 つの要素間の距離を表す、符号なしの型です。|
|[value_type](#value_type)|要素の型。|

### <a name="functions"></a>関数

|||
|-|-|
|[begin](#begin)|被制御シーケンスの先頭を指定します。|
|[つぶし](#bucket)|キー値のバケット番号を取得します。|
|[bucket_count](#bucket_count)|バケット数を取得します。|
|[bucket_size](#bucket_size)|バケットのサイズを取得します。|
|[cbegin](#cbegin)|被制御シーケンスの先頭を指定します。|
|[cend](#cend)|被制御シーケンスの末尾を指定します。|
|[clear](#clear)|すべての要素を削除します。|
|[count](#count)|指定したキーに一致する要素の数を検索します。|
|[emplace](#emplace)|構築された要素を適切な場所に追加します。|
|[emplace_hint](#emplace_hint)|構築された要素を適切な場所にヒントと一緒に追加します。|
|[empty](#empty)|要素が存在しないかどうかをテストします。|
|[end](#end)|被制御シーケンスの末尾を指定します。|
|[equal_range](#equal_range)|指定したキーに一致する範囲を検索します。|
|[erase](#erase)|指定した位置にある要素を削除します。|
|[find](#find)|指定したキーに一致する要素を検索します。|
|[get_allocator](#get_allocator)|格納されているアロケーター オブジェクトを取得します。|
|[hash_function](#hash)|格納されているハッシュ関数オブジェクトを取得します。|
|[insert](#insert)|要素を追加します。|
|[key_eq](#key_eq)|格納されている比較関数オブジェクトを取得します。|
|[load_factor](#load_factor)|バケットごとの平均要素数をカウントします。|
|[max_bucket_count](#max_bucket_count)|最大バケット数を取得します。|
|[max_load_factor](#max_load_factor)|バケットあたりの最大要素数を取得または設定します。|
|[max_size](#max_size)|被制御シーケンスの最大サイズを取得します。|
|[rehash](#rehash)|ハッシュ テーブルをリビルドします。|
|[size](#size)|要素の数をカウントします。|
|[swap](#swap)|2 つのコンテナーのコンテンツを交換します。|
|[unordered_set](#unordered_set)|コンテナー オブジェクトを構築します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[unordered_set::operator=](#op_eq)|ハッシュ テーブルをコピーします。|

## <a name="remarks"></a>Remarks

オブジェクトは、格納されている2つのオブジェクト ( [unordered_set:: key_equal](#key_equal)型の比較関数オブジェクトと、 [unordered_set:: hasher](#hasher)型のハッシュ関数オブジェクト) を呼び出すことによって、制御するシーケンスを並べ替えます。 最初に格納されたオブジェクトにアクセスするには、メンバー関数[unordered_set:: key_eq](#key_eq) `()`; を呼び出します。また、メンバー関数[unordered_set:: hash_function](#hash) `()` を呼び出して、2番目に格納されているオブジェクトにアクセスします。 具体的には、`X` 型のすべての値 `Y` と `Key` について、`key_eq()(X, Y)` が呼び出され、2 つの引数値の大小関係が等しい場合は true が返されます。`hash_function()(keyval)` の呼び出しからは、`size_t` 型の値の分布が生成されます。 クラステンプレート[Unordered_multiset クラス](../standard-library/unordered-multiset-class.md)とは異なり、`unordered_set` 型のオブジェクトでは、被制御シーケンスの任意の2つの要素に対して `key_eq()(X, Y)` が常に false になります。 キーの重複は許されません。

このオブジェクトには、さらに、適切とされるバケットあたりの最大平均要素数を指定する最大テーブル占有率が格納されます。 要素を挿入すると、 [unordered_set:: `()` load_factor](#load_factor)が最大テーブル占有率を超える場合、コンテナーはバケット数を増やし、必要に応じてハッシュテーブルを再構築します。

被制御シーケンスにおける要素の実際の順序は、ハッシュ関数、比較関数、挿入の順序、最大テーブル占有率、現在のバケット数などによって異なります。 通常、被制御シーケンス内の要素の順序を予測することはできません。 ただし、被制御シーケンス内で同じ大小関係を持った一連の要素は必ず隣接して存在します。

オブジェクトは、 [unordered_set:: allocator_type](#allocator_type)型の格納されているアロケーターオブジェクトを介して制御するシーケンスのストレージを割り当て、解放します。 このようなアロケーターオブジェクトは、`allocator` 型のオブジェクトと同じ外部インターフェイスを持つ必要があります。 コンテナー オブジェクトを代入しても、格納されているアロケーター オブジェクトはコピーされない点に注意してください。

## <a name="allocator_type"></a>  unordered_set::allocator_type

ストレージを管理するためのアロケーターの型です。

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `Alloc` のシノニムです。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_allocator_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Myset c1;

    Myset::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
    << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="begin"></a>初め

被制御シーケンスまたはバケットの先頭を指定します。

```cpp
iterator begin();

const_iterator begin() const;

local_iterator begin(size_type nbucket);

const_local_iterator begin(size_type nbucket) const;
```

### <a name="parameters"></a>パラメーター

*nbucket* \
バケット番号。

### <a name="remarks"></a>Remarks

最初の 2 つのメンバー関数は、シーケンスの最初の要素 (または空のシーケンスの末尾の次の位置) を示す前方反復子を返します。 最後の2つのメンバー関数は、バケット*nbucket*の最初の要素 (または空のバケットの末尾の次の位置) を示す前方反復子を返します。

### <a name="example"></a>例

```cpp
// unordered_set_begin.cpp
// compile using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>

using namespace std;

typedef unordered_set<char> MySet;

int main()
{
    MySet c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents using range-based for
    for (auto it : c1) {
    cout << "[" << it << "] ";
    }

    cout << endl;

    // display contents using explicit for
    for (MySet::const_iterator it = c1.begin(); it != c1.end(); ++it) {
        cout << "[" << *it << "] ";
    }

    cout << std::endl;

    // display first two items
    MySet::iterator it2 = c1.begin();
    cout << "[" << *it2 << "] ";
    ++it2;
    cout << "[" << *it2 << "] ";
    cout << endl;

    // display bucket containing 'a'
    MySet::const_local_iterator lit = c1.begin(c1.bucket('a'));
    cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[a] [b] [c]
[a] [b] [c]
[a] [b]
[a]
```

## <a name="bucket"></a>つぶし

キー値のバケット番号を取得します。

```cpp
size_type bucket(const Key& keyval) const;
```

### <a name="parameters"></a>パラメーター

*keyval* \
マップするキー値。

### <a name="remarks"></a>Remarks

このメンバー関数は、キー値*keyval*に現在対応しているバケット番号を返します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_bucket.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // display buckets for keys
    Myset::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
    << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="bucket_count"></a>bucket_count

バケット数を取得します。

```cpp
size_type bucket_count() const;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、現在のバケット数を返します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_bucket_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="bucket_size"></a>bucket_size

バケットのサイズを取得します。

```cpp
size_type bucket_size(size_type nbucket) const;
```

### <a name="parameters"></a>パラメーター

*nbucket* \
バケット番号。

### <a name="remarks"></a>Remarks

このメンバー関数は、バケット数*nbucket*のサイズを返します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_bucket_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // display buckets for keys
    Myset::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
    << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="cbegin"></a>cbegin

範囲内の最初の要素を指す**定数**反復子を返します。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>戻り値

範囲の最初の要素、または空の範囲の末尾の次の位置 (空の範囲の場合は `cbegin() == cend()`) を指す、**定数**前方アクセス反復子。

### <a name="remarks"></a>Remarks

`cbegin` の戻り値で範囲内の要素を変更することはできません。

`begin()` メンバー関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常は、次の例に示すように [auto](../cpp/auto-cpp.md) 型推論キーワードと共に使用します。 この例では、`begin()` と `cbegin()` をサポートする任意の種類の変更可能な (非**定数**) コンテナーとして `Container` を検討してください。

```cpp
auto i1 = Container.begin();
// i1 isContainer<T>::iterator
auto i2 = Container.cbegin();

// i2 isContainer<T>::const_iterator
```

## <a name="cend"></a>cend

範囲内の最後の要素の次の位置を指す**定数**反復子を返します。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>戻り値

範囲の末尾の次の位置を指し示す**定数**前方アクセス反復子。

### <a name="remarks"></a>Remarks

`cend` は、反復子が範囲の末尾を超えたかどうかをテストするために使用されます。

`end()` メンバー関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常は、次の例に示すように [auto](../cpp/auto-cpp.md) 型推論キーワードと共に使用します。 この例では、`end()` と `cend()` をサポートする任意の種類の変更可能な (非**定数**) コンテナーとして `Container` を検討してください。

```cpp
auto i1 = Container.end();
// i1 isContainer<T>::iterator
auto i2 = Container.cend();

// i2 isContainer<T>::const_iterator
```

`cend` によって返された値は逆参照しないでください。

## <a name="clear"></a>クリア

すべての要素を削除します。

```cpp
void clear();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、 [unordered_set:: erase](#erase) `(` [unordered_set:: begin](#begin) `(),` [unordered_set:: end](#end) `())` を呼び出します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_clear.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
size == 0
empty() == true
[e] [d]
size == 2
empty() == false
```

## <a name="const_iterator"></a>const_iterator

被制御シーケンスの定数反復子の型です。

```cpp
typedef T1 const_iterator;
```

### <a name="remarks"></a>Remarks

この型は、被制御シーケンスの定数前方反復子として使用できるオブジェクトを表します。 ここでは、実装定義型 `T1`のシノニムとして記述されています。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_const_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
    std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="const_local_iterator"></a>const_local_iterator

被制御シーケンスの定数バケット反復子の型です。

```cpp
typedef T5 const_local_iterator;
```

### <a name="remarks"></a>Remarks

この型は、バケットの定数前方反復子として使用できるオブジェクトを表します。 ここでは、実装定義型 `T5`のシノニムとして記述されています。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_const_local_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a]
```

## <a name="const_pointer"></a>const_pointer

要素への定数ポインターの型です。

```cpp
typedef Alloc::const_pointer const_pointer;
```

### <a name="remarks"></a>Remarks

この型は、被制御シーケンスの要素への定数ポインターとして使用できるオブジェクトを表します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_const_pointer.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::const_pointer p = &*it;
        std::cout << "[" << *p << "] ";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="const_reference"></a>const_reference

要素への定数参照の型です。

```cpp
typedef Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Remarks

この型は、被制御シーケンスの要素への定数参照として使用できるオブジェクトを表します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_const_reference.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::const_reference ref = *it;
        std::cout << "[" << ref << "] ";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="count"></a>数

指定したキーに一致する要素の数を検索します。

```cpp
size_type count(const Key& keyval) const;
```

### <a name="parameters"></a>パラメーター

*keyval* \
検索対象のキー値。

### <a name="remarks"></a>Remarks

このメンバー関数は、 [unordered_set:: equal_range](#equal_range) `(keyval)` で区切られた範囲内の要素の数を返します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
count('A') == 0
count('b') == 1
count('C') == 0
```

## <a name="difference_type"></a>difference_type

2 つの要素間の距離を表す、符号付きの型です。

```cpp
typedef T3 difference_type;
```

### <a name="remarks"></a>Remarks

符号付き整数型は、被制御シーケンス内にある 2 つの要素のアドレスの違いを表すことのできるオブジェクトを記述します。 ここでは、実装定義型 `T3`のシノニムとして記述されています。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_difference_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // compute positive difference
    Myset::difference_type diff = 0;
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference
    diff = 0;
    for (Myset::const_iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
end()-begin() == 3
begin()-end() == -3
```

## <a name="emplace"></a>emplace

インプレースで構築された (コピーまたは移動操作が実行されない) 要素を挿入します。

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
Args&&... args);
```

### <a name="parameters"></a>パラメーター

*args* \
値が同じ順序付けになる要素が unordered_set にまだ含まれていない場合に、unordered_set に挿入される要素を構築するために転送される引数。

### <a name="return-value"></a>戻り値

挿入が行われた場合は**bool**コンポーネントが true を返す `pair`。 `unordered_set` に既に順序の値が同じキーを持つ要素が含まれており、その反復子コンポーネントが新しい要素が挿入されたアドレスを返す場合は false です。または要素が既に配置されています。

このメンバー関数によって返されたペア `pr` の反復子コンポーネントにアクセスするには `pr.first` を使用し、この反復子を逆参照するには `*(pr.first)` を使用します。 このメンバー関数によって返されるペア `pr` の**bool**コンポーネントにアクセスするには、`pr.second` を使用します。

### <a name="remarks"></a>Remarks

この関数では、反復子や参照は無効になりません。

挿入時、例外がスローされたが、コンテナーのハッシュ関数ではエラーが発生しなかった場合、コンテナーは変更されません。 ハッシュ関数で例外がスローされた場合、結果は未定義になります。

コード例については、「 [set:: emplace](../standard-library/set-class.md#emplace)」を参照してください。

## <a name="emplace_hint"></a>emplace_hint

インプレースで構築された (コピーまたは移動操作が実行されない) 要素を、配置ヒントと一緒に挿入します。

```cpp
template <class... Args>
iterator emplace_hint(
const_iteratorwhere,
Args&&... args);
```

### <a name="parameters"></a>パラメーター

*args* \
挿入される要素が unordered_set にまだ含まれていない場合、一般的には、キーが同じ順序付けになる要素が unordered_set にまだ含まれていない場合に、unordered_set に挿入される要素を構築するために転送される引数。

*\*
正しい挿入ポイントの検索を開始する場所に関するヒント。

### <a name="return-value"></a>戻り値

新しく挿入される要素を指す反復子。

要素が既に存在するために挿入が失敗した場合は、既存の要素を指す反復子を返します。

### <a name="remarks"></a>Remarks

この関数では、反復子や参照は無効になりません。

挿入時、例外がスローされたが、コンテナーのハッシュ関数ではエラーが発生しなかった場合、コンテナーは変更されません。 ハッシュ関数で例外がスローされた場合、結果は未定義になります。

コード例については、「[set::emplace_hint](../standard-library/set-class.md#emplace_hint)」をご覧ください。

## <a name="empty"></a>指定

要素が存在しないかどうかをテストします。

```cpp
bool empty() const;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスが空の場合に true を返します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_empty.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
size == 0
empty() == true
[e] [d]
size == 2
empty() == false
```

## <a name="end"></a>終わり

被制御シーケンスの末尾を指定します。

```cpp
iterator end();

const_iterator end() const;

local_iterator end(size_type nbucket);

const_local_iterator end(size_type nbucket) const;
```

### <a name="parameters"></a>パラメーター

*nbucket* \
バケット番号。

### <a name="remarks"></a>Remarks

最初の 2 つのメンバー関数は、シーケンスの末尾の次を示す前方反復子を返します。 最後の2つのメンバー関数は、バケット*nbucket*の末尾の次の位置を示す前方反復子を返します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_end.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect last two items "[a] [b] "
    Myset::iterator it2 = c1.end();
    --it2;
    std::cout << "[" << *it2 << "] ";
    --it2;
    std::cout << "[" << *it2 << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.end(c1.bucket('a'));
    --lit;
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a] [b]
[a]
```

## <a name="equal_range"></a>equal_range

指定したキーに一致する範囲を検索します。

```cpp
std::pair<iterator, iterator>
equal_range(const Key& keyval);

std::pair<const_iterator, const_iterator>
equal_range(const Key& keyval) const;
```

### <a name="parameters"></a>パラメーター

*keyval* \
検索対象のキー値。

### <a name="remarks"></a>Remarks

@No__t_1 このメンバー関数は、 *keyval*と同等の順序付けを持つ被制御シーケンスの要素だけを区切る反復子のペア `X` を返します。 そのような要素が存在しない場合は、どちらの反復子も `end()`です。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_equal_range.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // display results of failed search
    std::pair<Myset::iterator, Myset::iterator> pair1 =
    c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << "[" << *pair1.first << "] ";
    std::cout << std::endl;

    // display results of successful search
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << "[" << *pair1.first << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
equal_range('x'):
equal_range('b'): [b]
```

## <a name="erase"></a>消去

unordered_set 内の要素または要素範囲を指定した位置から削除するか、指定したキーと一致する要素を削除します。

```cpp
iterator erase(const_iterator Where);

iterator erase(const_iterator First, const_iterator Last);

size_type erase(const key_type& Key);
```

### <a name="parameters"></a>パラメーター

*@No__t_1*
削除される要素の位置。

*最初*の \
削除される最初の要素の位置。

*最後*の \
削除される最後の要素の次の位置。

*キー* \
削除される要素のキー値。

### <a name="return-value"></a>戻り値

最初の 2 つのメンバー関数では、削除された要素の後にある最初の残存要素を指定する双方向反復子、またはこのような要素が存在しない場合は unordered_set の最後の要素を指定する双方向反復子が返されます。

3 番目のメンバー関数では、unordered_set から削除された要素の数が返されます。

### <a name="remarks"></a>Remarks

コード例については、「[set::erase](../standard-library/set-class.md#erase)」をご覧ください。

## <a name="find"></a>探す

指定したキーに一致する要素を検索します。

```cpp
const_iterator find(const Key& keyval) const;
```

### <a name="parameters"></a>パラメーター

*keyval* \
検索対象のキー値。

### <a name="remarks"></a>Remarks

このメンバー関数は、 [unordered_set:: equal_range](#equal_range) `(keyval).first` を返します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_find.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // try to find and fail
    std::cout << "find('A') == "
    << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed
    Myset::iterator it = c1.find('b');
    std::cout << "find('b') == "
    << std::boolalpha << (it != c1.end())
    << ": [" << *it << "] " << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
find('A') == false
find('b') == true: [b]
```

## <a name="get_allocator"></a>get_allocator

格納されているアロケーター オブジェクトを取得します。

```cpp
Alloc get_allocator() const;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、格納されているアロケーター オブジェクトを返します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_get_allocator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Myset c1;

    Myset::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
    << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="hash"></a>hash_function

格納されているハッシュ関数オブジェクトを取得します。

```cpp
Hash hash_function() const;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、格納されているハッシュ関数オブジェクトを返します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_hash_function.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="hasher"></a>hasher

ハッシュ関数の型です。

```cpp
typedef Hash hasher;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `Hash` のシノニムです。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_hasher.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="insert"></a>insert

unordered_set に要素または要素範囲を挿入します。

```cpp
// (1) single element
pair<iterator, bool> insert(const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool> insert(ValTy&& Val);

// (3) single element with hint
iterator insert(const_iterator Where, const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(const_iterator Where, ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(InputIterator First, InputIterator Last);

// (6) initializer list
void insert(initializer_list<value_type> IList);
```

### <a name="parameters"></a>パラメーター

*Val* \
キーが同じ順序付けになる要素が unordered_set にまだ含まれていない場合に、unordered_set に挿入される要素の値。

*@No__t_1*
正しい挿入ポイントの検索を開始する場所

*Valty* \
Unordered_set が[value_type](../standard-library/map-class.md#value_type)の要素を構築するために使用できる引数の型を指定し、引数として*Val*を完全に転送するテンプレートパラメーター。

*最初*の \
コピーされる最初の要素の位置。

*最後*の \
コピーされる最後の要素の次の位置。

*InputIterator* \
[入力反復子](../standard-library/input-iterator-tag-struct.md)の要件を満たすテンプレート関数の引数。この反復子は、[value_type](../standard-library/map-class.md#value_type) オブジェクトの構築に使用できる型の要素を指し示します。

*IList* \
要素のコピー元の [initializer_list](../standard-library/initializer-list.md)。

### <a name="return-value"></a>戻り値

単一要素のメンバー関数 (1) と (2) は、ペアを返します。この[ペア](../standard-library/pair-structure.md)の**bool**コンポーネントは、挿入が行われた場合は true になり、順序の値が同じキーを持つ要素が unordered_set に既に含まれている場合は false になります。 戻り値のペアの反復子コンポーネントは、 **bool**コンポーネントが true の場合は新しく挿入された要素を指し、 **bool**コンポーネントが false の場合は既存の要素を指します。

単一要素とヒントのメンバー関数 (3) と (4) は、unordered_set に挿入された新しい要素の位置を指す反復子を返します。ただし、同じキーを持つ要素が既に存在する場合、この反復子は既存の要素を指します。

### <a name="remarks"></a>Remarks

この関数では、反復子、ポインター、参照は無効になりません。

要素を 1 つだけ挿入するとき、例外がスローされたが、コンテナーのハッシュ関数ではエラーが発生しなかった場合、コンテナーの状態は変更されません。 ハッシュ関数で例外がスローされた場合、結果は未定義になります。 複数の要素を挿入するときに例外がスローされた場合、コンテナーの状態は未指定ですが、有効な状態になっています。

単一要素のメンバー関数によって返される `pair` `pr` の反復子コンポーネントにアクセスするには `pr.first` を使用します。返されたペア内で反復子を逆参照するには、`*pr.first` を使用して、要素を指定します。 **Bool**コンポーネントにアクセスするには、`pr.second` を使用します。 例については、この記事で後ほど説明するサンプル コードを参照してください。

コンテナーの [value_type](../standard-library/map-class.md#value_type) はそのコンテナーに属する typedef であり、set の場合、`unordered_set<V>::value_type` は `const V` 型です。

範囲のメンバー関数 (5) は、unordered_set に要素値のシーケンスを挿入します。このシーケンスは、`[First, Last)` の範囲の反復子によってアドレス指定された各要素に対応します。したがって、 *Last*は挿入されません。 コンテナーのメンバー関数 `end()` は、コンテナー内にある最後の要素の直後の位置を参照します。たとえば、ステートメント `s.insert(v.begin(), v.end());` は、`v` のすべての要素を `s` に挿入しようとします。 範囲内で一意の値を持つ要素だけが挿入されますが、値が重複する要素は無視されます。 拒否される要素を確認するには、1 つの要素が指定された `insert` を使用します。

初期化子リストのメンバー関数 (6) は、 [initializer_list](../standard-library/initializer-list.md)を使用して unordered_set に要素をコピーします。

インプレースで構築された (つまり、コピーまたは移動操作が実行されない) 要素の挿入については、「[set::emplace](../standard-library/set-class.md#emplace)」および「[set::emplace_hint](../standard-library/set-class.md#emplace_hint)」を参照してください。

コード例については、「 [set:: insert](../standard-library/set-class.md#insert)」を参照してください。

## <a name="iterator"></a>反

Unordered_set 内の要素を読み取ることができる定数[前方反復子](../standard-library/forward-iterator-tag-struct.md)を提供する型。

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>例

**反復子**の宣言方法や使用方法の例については、 [begin](../standard-library/set-class.md#begin)の例を参照してください。

## <a name="key_eq"></a>key_eq

格納されている比較関数オブジェクトを取得します。

```cpp
Pred key_eq() const;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、格納されている比較関数オブジェクトを返します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_key_eq.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
    << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
    << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
}
```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="key_equal"></a>key_equal

比較関数の型です。

```cpp
typedef Pred key_equal;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `Pred` のシノニムです。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_key_equal.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
    << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
    << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
}
```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="key_type"></a>key_type

順序付けキーの型です。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `Key` のシノニムです。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_key_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // add a value and reinspect
    Myset::key_type key = 'd';
    Myset::value_type val = key;
    c1.insert(val);

    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[d] [c] [b] [a]
```

## <a name="load_factor"></a>load_factor

バケットごとの平均要素数をカウントします。

```cpp
float load_factor() const;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、バケットごとの平均要素数 `(float)` [unordered_set::size](#size)`() / (float)`[unordered_set::bucket_count](#bucket_count)`()` を返します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_load_factor.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="local_iterator"></a>local_iterator

バケット反復子の型。

```cpp
typedef T4 local_iterator;
```

### <a name="remarks"></a>Remarks

この型は、バケットの前方反復子として使用できるオブジェクトを表します。 ここでは、実装定義型 `T4`のシノニムとして記述されています。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_local_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << "[" << *lit << "] ";

    return (0);
}
```

```Output
[c] [b] [a]
[a]
```

## <a name="max_bucket_count"></a>max_bucket_count

最大バケット数を取得します。

```cpp
size_type max_bucket_count() const;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、現在許可されているバケットの最大数を返します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_max_bucket_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="max_load_factor"></a>max_load_factor

バケットあたりの最大要素数を取得または設定します。

```cpp
float max_load_factor() const;

void max_load_factor(float factor);
```

### <a name="parameters"></a>パラメーター

*要因*\
新しい最大テーブル占有率。

### <a name="remarks"></a>Remarks

1 つ目のメンバー関数は、格納されている最大テーブル占有率を返します。 2番目のメンバー関数は、格納されている最大占有率を*係数*に置き換えます。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_max_load_factor.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
    << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
    << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1
```

## <a name="max_size"></a>max_size

被制御シーケンスの最大サイズを取得します。

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、オブジェクトが制御できる最も長いシーケンスの長さを返します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_max_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    std::cout << "max_size() == " << c1.max_size() << std::endl;

    return (0);
}
```

```Output
max_size() == 4294967295
```

## <a name="op_eq"></a>operator =

ハッシュ テーブルをコピーします。

```cpp
unordered_set& operator=(const unordered_set& right);

unordered_set& operator=(unordered_set&& right);
```

### <a name="parameters"></a>パラメーター

*右*\
@No__t_1 にコピーされる[unordered_set](../standard-library/unordered-set-class.md) 。

### <a name="remarks"></a>Remarks

@No__t_0 内の既存の要素を消去した後、 *`operator=` の内容*を `unordered_set` にコピーまたは移動します。

### <a name="example"></a>例

```cpp
// unordered_set_operator_as.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

int main( )
{
    using namespace std;
    unordered_set<int> v1, v2, v3;
    unordered_set<int>::iterator iter;

    v1.insert(10);

    cout << "v1 = " ;
    for (iter = v1.begin(); iter != v1.end(); iter++)
        cout << *iter << " ";
    cout << endl;

    v2 = v1;
    cout << "v2 = ";
    for (iter = v2.begin(); iter != v2.end(); iter++)
        cout << *iter << " ";
    cout << endl;

    // move v1 into v2
    v2.clear();
    v2 = move(v1);
    cout << "v2 = ";
    for (iter = v2.begin(); iter != v2.end(); iter++)
        cout << *iter << " ";
    cout << endl;
}
```

## <a name="pointer"></a>pointer

要素へのポインターの型です。

```cpp
typedef Alloc::pointer pointer;
```

### <a name="remarks"></a>Remarks

この型は、被制御シーケンスの要素へのポインターとして機能するオブジェクトを表します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_pointer.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::key_type key = *it;
        Myset::pointer p = &key;
        std::cout << "[" << *p << "] ";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="reference"></a>「

要素への参照の型です。

```cpp
typedef Alloc::reference reference;
```

### <a name="remarks"></a>Remarks

この型は、被制御シーケンスの要素への参照として使用できるオブジェクトを表します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_reference.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::key_type key = *it;
        Myset::reference ref = key;
        std::cout << "[" << ref << "] ";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
```

## <a name="rehash"></a>rehash

ハッシュ テーブルをリビルドします。

```cpp
void rehash(size_type nbuckets);
```

### <a name="parameters"></a>パラメーター

*nbuckets* \
要求されたバケット数。

### <a name="remarks"></a>Remarks

このメンバー関数は、バケットの数を少なくとも*nbuckets*に変更し、必要に応じてハッシュテーブルを再構築します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_rehash.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_load_factor() == 0.1
```

## <a name="size"></a>幅

要素の数をカウントします。

```cpp
size_type size() const;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスの長さを返します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents "[e] [d] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
size == 0
empty() == true

[e] [d]
size == 2
empty() == false
```

## <a name="size_type"></a>size_type

2 つの要素間の距離を表す、符号なしの型です。

```cpp
typedef T2 size_type;
```

### <a name="remarks"></a>Remarks

符号なし整数型は、被制御シーケンスの長さを表すことができるオブジェクトを表します。 ここでは、実装定義型 `T2`のシノニムとして記述されています。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_size_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;
    Myset::size_type sz = c1.size();

    std::cout << "size == " << sz << std::endl;

    return (0);
}
```

```Output
size == 0
```

## <a name="swap"></a>フォト

2 つのコンテナーのコンテンツを交換します。

```cpp
void swap(unordered_set& right);
```

### <a name="parameters"></a>パラメーター

*右*\
交換先のコンテナー。

### <a name="remarks"></a>Remarks

このメンバー関数は、`*this` と*right*の間で被制御シーケンスを交換します。 [Unordered_set:: get_allocator](#get_allocator) `() == right.get_allocator()` の場合は、一定の時間内に実行されます。 `Tr` 型の格納された特性オブジェクトをコピーした結果としてのみ例外をスローし、次の要素を指定する参照、ポインター、または反復子を無効にしません。2つの被制御シーケンス。 それ以外の場合、2 つの被制御シーケンス内の要素数に比例した回数、要素の割り当てとコンストラクター呼び出しが実行されます。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_swap.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    Myset c2;

    c2.insert('d');
    c2.insert('e');
    c2.insert('f');

    c1.swap(c2);

    // display contents "[f] [e] [d] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    swap(c1, c2);

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[f] [e] [d]
[c] [b] [a]
```

## <a name="unordered_set"></a>unordered_set

コンテナー オブジェクトを構築します。

```cpp
unordered_set(const unordered_set& Right);

explicit unordered_set(
    size_typebucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());

unordered_set(unordered_set&& Right);

unordered_set(initializer_list<Type> IList);

unordered_set(initializer_list<Type> IList, size_typebucket_count);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash,
    const Comp& Comp);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash,
    const Comp& Comp,
    const Allocator& Al);

template <class InputIterator>
unordered_set(
    InputIteratorfirst,
    InputIteratorlast,
    size_typebucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());
```

### <a name="parameters"></a>パラメーター

*InputIterator* \
反復子の型。

*Al* \
格納するアロケーター オブジェクト。

*Comp* \
格納する比較関数オブジェクト。

*ハッシュ*\
格納するハッシュ関数オブジェクト。

*bucket_count* \
最小バケット数。

*右*\
コピーするコンテナー。

*IList* \
コピーする要素を含む initializer_list。

### <a name="remarks"></a>Remarks

1つ目のコンストラクターは、 *Right*によって制御されるシーケンスのコピーを指定します。 2 つ目のコンストラクターは、空の被制御シーケンスのコピーを指定します。 3番目のコンストラクターは、4番目のコンストラクターを*右*に移動することによってシーケンスのコピーを指定し、initializer_list を使用してコピーする要素を指定します。 9 つ目のコンストラクターは、要素値 `[first, last)` のシーケンスを挿入します。

さらに、格納された複数の値を初期化する処理が実行されます。この処理は、すべてのコンストラクターに共通です。 コピーコンストラクターの場合、値は*Right*から取得されます。 それ以外の場合:

バケットの最小数は、引数*bucket_count*(存在する場合) です。それ以外の場合は、実装定義の値 `N0` としてここで説明されている既定値になります。

ハッシュ関数オブジェクトは、引数*ハッシュ*(存在する場合) です。それ以外の場合は `Hash()` になります。

比較関数オブジェクトは、引数*Comp*(存在する場合) です。それ以外の場合は `Comp()` になります。

アロケーターオブジェクトは、引数*Al*(存在する場合) です。それ以外の場合は、`Alloc()` ます。

## <a name="value_type"></a>value_type

要素の型。

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Remarks

この型は、被制御シーケンス内の要素を示します。

### <a name="example"></a>例

```cpp
// std__unordered_set__unordered_set_value_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents "[c] [b] [a] "
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    // add a value and reinspect
    Myset::key_type key = 'd';
    Myset::value_type val = key;
    c1.insert(val);

    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << "[" << *it << "] ";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[d] [c] [b] [a]
```
