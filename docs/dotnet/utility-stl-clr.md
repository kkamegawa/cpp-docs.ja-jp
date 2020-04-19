---
title: utility (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/utility>
- cliext::pair
- cliext::pair::pair
- cliext::pair::first
- cliext::pair::first_type
- cliext::pair::second
- cliext::pair::second_type
- cliext::pair::swap
- cliext::make_pair
- cliext::pair::operator=
- cliext::pair::operator==
- cliext::pair::operator>=
- cliext::pair::operator>
- cliext::pair::operator!=
- cliext::pair::operator<=
- cliext::pair::operator<
helpviewer_keywords:
- <utility> header [STL/CLR]
- utility header [STL/CLR]
- <cliext/utility> header [STL/CLR]
- first member [STL/CLR]
- first_type member [STL/CLR]
- second member [STL/CLR]
- second_type member [STL/CLR]
- swap member [STL/CLR]
- make_pair function [STL/CLR]
- pair class [STL/CLR]
- pair member [STL/CLR]
- operator== member [STL/CLR]
- operator= member [STL/CLR]
- operator>= member [STL/CLR]
- operator> member [STL/CLR]
- operator!= member [STL/CLR]
- operator<= member [STL/CLR]
- operator< member [STL/CLR]
ms.assetid: fb48cb75-d5ef-47ce-b526-bf60dc86c552
ms.openlocfilehash: 1a884a75fbc3ba979402c94c67d2915863a847e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384466"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

STL/CLR のヘッダーを含める`<cliext/utility>`テンプレート クラスを定義する`pair`といくつかのサポート テンプレート関数。

## <a name="syntax"></a>構文

```cpp
#include <utility>
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<cliext ユーティリティ/>

**Namespace:** cliext

## <a name="declarations"></a>宣言

|クラス|説明|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|要素のペアをラップします。|

|演算子|説明|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|ペアには、比較と等しくなります。|
|[operator!= (pair) (STL/CLR)](#op_neq)|非等値比較をペアリングします。|
|[operator< (pair) (STL/CLR)](#op_lt)|ペアの比較よりも小さい。|
|[演算子\<= (ペア) (STL/CLR)](#op_lteq)|以下のペアの比較。|
|[operator> (pair) (STL/CLR)](#op_gt)|ペアの比較よりも大きい。|
|[operator>= (pair) (STL/CLR)](#op_gteq)|ペアより大きいまたは等しい比較します。|

|関数|説明|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|値のペアからのペアを作成します。|

## <a name="members"></a>メンバー

## <a name="pair"></a> ペア (STL/CLR)
テンプレート クラスは、値のペアをラップするオブジェクトを表します。

### <a name="syntax"></a>構文

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>パラメーター

*Value1*<br/>
最初のラップされた値の型。

*Value2*<br/>
2 番目のラップされた値の型。

## <a name="members"></a>メンバー

|型定義|説明|
|---------------------|-----------------|
|[pair::first_type (STL/CLR)](#first_type)|最初のラップされた値の型。|
|[pair::second_type (STL/CLR)](#second_type)|2 番目のラップされた値の型。|

|メンバー オブジェクト|説明|
|-------------------|-----------------|
|[pair::first (STL/CLR)](#first)|最初の格納されている値。|
|[pair::second (STL/CLR)](#second)|2 つ目には、値が格納されています。|

|メンバー関数|説明|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|ペア オブジェクトを構築します。|
|[pair::swap (STL/CLR)](#swap)|2 つのペアの内容を交換します。|

|演算子|説明|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|ストアド値のペアを置き換えます。|

## <a name="remarks"></a>Remarks

オブジェクトは、値のペアを格納します。 2 つの値を 1 つのオブジェクトに結合するのにには、このテンプレート クラスを使用します。 オブジェクトではまた、 `cliext::pair` (ここで説明) のみマネージ型のストア; 非管理対象のペアを格納する型を使用して`std::pair`で宣言された`<utility>`します。

## <a name="first"></a> pair::first (STL/CLR)

最初のラップされた値。

### <a name="syntax"></a>構文

```cpp
Value1 first;
```

### <a name="remarks"></a>Remarks

オブジェクトは、最初のラップされた値を格納します。

### <a name="example"></a>例

```cpp
// cliext_pair_first.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="first_type"></a> pair::first_type (STL/CLR)

最初のラップされた値の型。

### <a name="syntax"></a>構文

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>Remarks

型はテンプレート パラメーターのシノニム*Value1*します。

### <a name="example"></a>例

```cpp
// cliext_pair_first_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="op_as"></a> pair::operator = (STL/CLR)

ストアド値のペアを置き換えます。

### <a name="syntax"></a>構文

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>パラメーター

*right*<br/>
ペアをコピーします。

### <a name="remarks"></a>Remarks

メンバー演算子コピー*右*、オブジェクトを返します`*this`します。 ストアドの値のペアのコピーに置き換えるストアド値のペアを使用する*右*します。

### <a name="example"></a>例

```cpp
// cliext_pair_operator_as.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

// assign to a new pair
    cliext::pair<wchar_t, int> c2;
    c2 = c1;
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);
    return (0);
    }
```

```Output
[x, 3]
[x, 3]
```

## <a name="pair_pair"></a> pair::pair (STL/CLR)

ペア オブジェクトを構築します。

### <a name="syntax"></a>構文

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>パラメーター

*right*<br/>
ペアを格納します。

*Val1*<br/>
最初の値を格納します。

*Val2*<br/>
2 番目の値を格納します。

### <a name="remarks"></a>Remarks

コンス トラクター。

`pair();`

既定で構築される値を持つストアドのペアを初期化します。

コンス トラクター。

`pair(pair<Value1, Value2>% right);`

ストアドのペアを初期化します`right.` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md)と`right.` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md)します。

`pair(pair<Value1, Value2>^ right);`

ストアドのペアを初期化します`right->` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md)と`right>` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md)します。

コンス トラクター。

`pair(Value1 val1, Value2 val2);`

ストアドのペアを初期化します*val1*と*val2*します。

### <a name="example"></a>例

```cpp
// cliext_pair_construct.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
// construct an empty container
    cliext::pair<wchar_t, int> c1;
    System::Console::WriteLine("[{0}, {1}]",
        c1.first == L'\0' ? "\\0" : "??", c1.second);

// construct with a pair of values
    cliext::pair<wchar_t, int> c2(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

// construct by copying another pair
    cliext::pair<wchar_t, int> c3(c2);
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);

// construct by copying a pair handle
    cliext::pair<wchar_t, int> c4(%c3);
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);

    return (0);
    }
```

```Output
[\0, 0]
[x, 3]
[x, 3]
[x, 3]
```

## <a name="second"></a> pair::second (STL/CLR)

2 番目のラップされた値。

### <a name="syntax"></a>構文

```cpp
Value2 second;
```

### <a name="remarks"></a>Remarks

オブジェクトは、2 番目のラップされた値を格納します。

### <a name="example"></a>例

```cpp
// cliext_pair_second.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="second_type"></a> pair::second_type (STL/CLR)

2 番目のラップされた値の型。

### <a name="syntax"></a>構文

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>Remarks

型はテンプレート パラメーターのシノニム*Value2*します。

### <a name="example"></a>例

```cpp
// cliext_pair_second_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="swap"></a> pair::swap (STL/CLR)

2 つのペアの内容を交換します。

### <a name="syntax"></a>構文

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>パラメーター

*right*<br/>
コンテンツを交換するペア。

### <a name="remarks"></a>Remarks

メンバー関数は、ストアドの間の値のペアを交換する`*this`と*右*します。

### <a name="example"></a>例

```cpp
// cliext_pair_swap.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    cliext::deque<wchar_t> d2(5, L'x');
    Mycoll c2(%d2);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x x x x x
x x x x x
a b c
```

## <a name="make_pair"></a> make_pair (STL/CLR)

ように、`pair`の値のペアから。

### <a name="syntax"></a>構文

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>パラメーター

*Value1*<br/>
最初のラップされた値の型。

*Value2*<br/>
2 番目のラップされた値の型。

*first*<br/>
最初の値をラップします。

*second*<br/>
2 番目の値をラップします。

### <a name="remarks"></a>Remarks

このテンプレート関数は `pair<Value1, Value2>(first, second)` を返します。 使用して構築する、`pair<Value1, Value2>`の値のペアからオブジェクト。

### <a name="example"></a>例

```cpp
// cliext_make_pair.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    c1 = cliext::make_pair(L'y', 4);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    return (0);
    }
```

```Output
[x, 3]
[y, 4]
```

## <a name="op_neq"></a> 演算子! = (ペア) (STL/CLR)

非等値比較をペアリングします。

### <a name="syntax"></a>構文

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のペア。

*right*<br/>
比較する右のペア。

### <a name="remarks"></a>Remarks

演算子関数を返します`!(left == right)`します。 テストに使用するかどうか*左*順序付けされていないと同じ*右*2 つのペアが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_pair_operator_ne.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] != [x 3] is {0}",
        c1 != c1);
    System::Console::WriteLine("[x 3] != [x 4] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] != [x 3] is False
[x 3] != [x 4] is True
```

## <a name="op_lt"></a> 演算子&lt;(ペア) (STL/CLR)

ペアの比較よりも小さい。

### <a name="syntax"></a>構文

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のペア。

*right*<br/>
比較する右のペア。

### <a name="remarks"></a>Remarks

演算子関数を返します`left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`します。 テストに使用するかどうか*左*が順序付け、前に*右*2 つのペアが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_pair_operator_lt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] < [x 3] is {0}",
        c1 < c1);
    System::Console::WriteLine("[x 3] < [x 4] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] < [x 3] is False
[x 3] < [x 4] is True
```

## <a name="op_lteq"></a> 演算子&lt;= (ペア) (STL/CLR)

以下のペアの比較。

### <a name="syntax"></a>構文

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のペア。

*right*<br/>
比較する右のペア。

### <a name="remarks"></a>Remarks

演算子関数を返します`!(right < left)`します。 テストに使用するかどうか*左*後に順序付けされていない*右*2 つのペアが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_pair_operator_le.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] <= [x 3] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[x 4] <= [x 3] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] <= [x 3] is True
[x 4] <= [x 3] is False
```

## <a name="op_eq"></a> 演算子 (ペア) (STL/CLR) = =

ペアには、比較と等しくなります。

### <a name="syntax"></a>構文

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のペア。

*right*<br/>
比較する右のペア。

### <a name="remarks"></a>Remarks

演算子関数を返します`left.first ==` `right.first &&` `left.second ==` `right.second`します。 テストに使用するかどうか*左*が同じ順序付け*右*2 つのペアが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_pair_operator_eq.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] == [x 3] is {0}",
        c1 == c1);
    System::Console::WriteLine("[x 3] == [x 4] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] == [x 3] is True
[x 3] == [x 4] is False
```

## <a name="op_gt"></a> 演算子&gt;(ペア) (STL/CLR)

ペアの比較よりも大きい。

### <a name="syntax"></a>構文

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のペア。

*right*<br/>
比較する右のペア。

### <a name="remarks"></a>Remarks

演算子関数を返します`right` `<` `left`します。 テストに使用するかどうか*左*が後に順序付け*右*2 つのペアが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_pair_operator_gt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] > [x 3] is {0}",
        c1 > c1);
    System::Console::WriteLine("[x 4] > [x 3] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] > [x 3] is False
[x 4] > [x 3] is True
```

## <a name="op_gteq"></a> 演算子&gt;= (ペア) (STL/CLR)

ペアより大きいまたは等しい比較します。

### <a name="syntax"></a>構文

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のペア。

*right*<br/>
比較する右のペア。

### <a name="remarks"></a>Remarks

演算子関数を返します`!(left < right)`します。 テストに使用するかどうか*左*する前に順序付けされていない*右*2 つのペアが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_pair_operator_ge.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] >= [x 3] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[x 3] >= [x 4] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] >= [x 3] is True
[x 3] >= [x 4] is False
```