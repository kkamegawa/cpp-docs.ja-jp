---
title: initializer_list クラス
description: Visual Studio で Microsoft によって実装C++されている、標準ライブラリの initializer_list クラスのリファレンスです。
ms.date: 01/28/2020
f1_keywords:
- initializer_list/std::initializer_list::initializer_list
- initializer_list/std::initializer_list::begin
- initializer_list/std::initializer_list::end
- initializer_list/std::initializer_list::size
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
helpviewer_keywords:
- std::initializer_list::initializer_list
- std::initializer_list::begin
- std::initializer_list::end
- std::initializer_list::size
ms.openlocfilehash: 6be51835958a07162ce22ff9d619fb793102669f
ms.sourcegitcommit: 684181561490e0d1955cf601d222f67f09af6d00
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "76894334"
---
# <a name="initializer_list-class"></a>initializer_list クラス

すべてのメンバーが指定された型である要素の配列にアクセスできます。

## <a name="syntax"></a>構文

```cpp
template <class Type>
class initializer_list
```

### <a name="parameters"></a>パラメーター

*型*\
`initializer_list` に格納される要素のデータ型。

## <a name="remarks"></a>Remarks

`initializer_list` は、中かっこで囲んだ初期化子リストを使用して構築できます。

```cpp
initializer_list<int> i1{ 1, 2, 3, 4 };
```

関数のシグネチャで `initializer_list` が必要になる場合、コンパイラでは、中かっこで囲んだ初期化子リストが同種の要素を含んでいると、このリストは必ず `initializer_list` に変換されます。 `initializer_list`の使用方法の詳細については、「 [Uniform initialization and デリゲートコンストラクター](../cpp/uniform-initialization-and-delegating-constructors.md) 」を参照してください。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[initializer_list](#initializer_list)|`initializer_list` 型のオブジェクトを構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|`value_type`|`initializer_list` 内の要素の型。|
|`reference`|`initializer_list` 内の要素への参照を提供する型。|
|`const_reference`|`initializer_list` 内の要素への定数参照を提供する型。|
|`size_type`|`initializer_list` 内の要素の数を表す型。|
|`iterator`|`initializer_list` に反復子を提供する型。|
|`const_iterator`|`initializer_list` に定数反復子を提供する型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[begin](#begin)|`initializer_list` 内の最初の要素へのポインターを返します。|
|[end](#end)|`initializer_list` 内の最後の要素の 1 つ後ろへのポインターを返します。|
|[size](#size)|`initializer_list` 内の要素数を返します。|

## <a name="requirements"></a>要件

**ヘッダー:** \<initializer_list >

**名前空間:** std

## <a name="begin"></a>  initializer_list::begin

`initializer_list` 内の最初の要素へのポインターを返します。

```cpp
constexpr const InputIterator* begin() const noexcept;
```

### <a name="return-value"></a>戻り値

`initializer_list` の最初の要素へのポインター。 リストが空の場合、ポインターはリストの先頭および末尾と同じです。

## <a name="end"></a>  initializer_list::end

`initializer list` 内の最後の要素の 1 つ後ろへのポインターを返します。

```cpp
constexpr const InputIterator* end() const noexcept;
```

### <a name="return-value"></a>戻り値

リスト内の最後の要素の 1 つ後ろを指すポインター。 リストが空の場合は、リスト内の最初の要素へのポインターと同じになります。

## <a name="initializer_list"></a>  initializer_list::initializer_list

`initializer_list` 型のオブジェクトを構築します。

```cpp
constexpr initializer_list() noexcept;
initializer_list(const InputIterator First, const InputIterator Last);
```

### <a name="parameters"></a>パラメーター

*最初*の\
コピーする要素範囲内の最初の要素の位置。

*最後*の\
コピーする要素範囲を超える最初の要素の位置。

### <a name="remarks"></a>Remarks

`initializer_list` は、指定された型のオブジェクトの配列に基づいています。 `initializer_list` をコピーすると、同じオブジェクトを指すリストの2番目のインスタンスが作成されます。基になるオブジェクトはコピーされません。

### <a name="example"></a>使用例

```cpp
// initializer_list_class.cpp
// compile with: /EHsc
#include <initializer_list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty initializer_list c0
    initializer_list <int> c0;

    // Create an initializer_list c1 with 1 element
    initializer_list <int> c1{ 3 };

    // Create an initializer_list c2 with 5 elements
    initializer_list <int> c2{ 5, 4, 3, 2, 1 };

    // Create a copy, initializer_list c3, of initializer_list c2
    initializer_list <int> c3(c2);

    // Create a initializer_list c4 by copying the range c3[ first,  last)
    const int* c3_ptr = c3.begin();
    c3_ptr++;
    c3_ptr++;
    initializer_list <int> c4(c3.begin(), c3_ptr);

    // Move initializer_list c4 to initializer_list c5
    initializer_list <int> c5(move(c4));

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    cout << "c2 =";
    for (auto c : c2)
        cout << " " << c;
    cout << endl;

    cout << "c3 =";
    for (auto c : c3)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 3
c2 = 5 4 3 2 1
c3 = 5 4 3 2 1
c5 = 5 4
```

## <a name="size"></a>  initializer_list::size

リストの要素数を返します。

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>戻り値

リストの要素数。

## <a name="see-also"></a>関連項目

[<forward_list>](../standard-library/forward-list.md)
