---
title: vector&lt;bool&gt; クラス
ms.date: 11/04/2016
f1_keywords:
- vector<bool>
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::pointer
- vector/std::vector::flip
- vector/std::vector::swap
helpviewer_keywords:
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], pointer
- std::vector [C++], flip
- std::vector [C++], swap
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
ms.openlocfilehash: d4ae53f9a14f04d5656a13c32e75494688c5cdd0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452266"
---
# <a name="vectorltboolgt-class"></a>vector&lt;bool&gt; クラス

クラスは、 **bool**型の要素の [vector](../standard-library/vector-class.md) の部分的特殊化です。`vector<bool>` これには、特殊化によって使用される基になる型のアロケーターがあり、1ビットあたり1つの**ブール**値を格納することによって領域を最適化します。

## <a name="syntax"></a>構文

```cpp
template <class Allocator = allocator<bool>>
class vector<bool, Allocator>
```

## <a name="remarks"></a>Remarks

このクラス テンプレートの特殊化は vector と同様に動作しますが、この記事で説明する違いがあります。

**Bool**型を処理する操作は、コンテナーストレージの値に対応します。 `allocator_traits::construct` はこれらの値の構築には使用されません。

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[const_pointer](#const_pointer)|`const_iterator` のブール型要素への定数ポインターとして使用できる `vector<bool>` への typedef。|
|[const_reference](#const_reference)|**Bool**の typedef。 初期化後に、元の値への更新を確認しません。|
|[pointer](#pointer)|`iterator` のブール型要素へのポインターとして使用できる `vector<bool>` への typedef。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[flip](#flip)|`vector<bool>` 内のすべてのビットを反転させます。|
|[swap](#swap)|2 つの `vector<bool>` の要素を交換します。|
|[operator&#91;&#93;](#op_at)|指定した位置における `vector<bool>` 要素へのシミュレートされた参照を返します。|
|`at`|[vector](../standard-library/vector-class.md)::at 関数と同様に機能します。ただし、プロキシ クラス [vector\<bool>::reference](#reference_class) を使用します。 「[operator&#91;&#93;](#op_at)」も参照してください。|
|`front`|[vector](../standard-library/vector-class.md)::front 関数と同様に機能します。ただし、プロキシ クラス [vector\<bool>::reference](#reference_class) を使用します。 「[operator&#91;&#93;](#op_at)」も参照してください。|
|`back`|[vector](../standard-library/vector-class.md)::back 関数と同様に機能します。ただし、プロキシ クラス [vector\<bool>::reference](#reference_class) を使用します。 「[operator&#91;&#93;](#op_at)」も参照してください。|

### <a name="proxy-class"></a>プロキシ クラス

|||
|-|-|
|[vector\<bool> reference クラス](#reference_class)|`bool&` の動作をシミュレートするためのプロキシとして機能するクラスで、そのオブジェクトは `vector<bool>` オブジェクト内の要素 (単一ビット) への参照を提供できます。|

## <a name="requirements"></a>必要条件

**ヘッダー**: \<vector>

**名前空間:** std

## <a name="const_pointer"></a>  vector\<bool>::const_pointer

`vector<bool>` オブジェクトに格納されるシーケンスのブール要素への定数ポインターとして使用できるオブジェクトを表す型。

```cpp
typedef const_iterator const_pointer;
```

## <a name="const_reference"></a>  vector\<bool>::const_reference

`vector<bool>` オブジェクトに格納されるシーケンスのブール要素への定数参照として使用できるオブジェクトを表す型。

```cpp
typedef bool const_reference;
```

### <a name="remarks"></a>Remarks

詳細とコード例については、「[vector&lt;bool&gt;::reference::operator=](#reference_operator_eq)」を参照してください。

## <a name="flip"></a>  vector\<bool>::flip

`vector<bool>` 内のすべてのビットを反転させます。

```cpp
void flip();
```

### <a name="example"></a>例

```cpp
// vector_bool_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha; // format output for subsequent code

    vector<bool> vb = { true, false, false, true, true };
    cout << "The vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vb.flip();

    cout << "The flipped vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

## <a name="op_at"></a>  vector\<bool>::operator[]

指定した位置における `vector<bool>` 要素へのシミュレートされた参照を返します。

```cpp
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*Po*|`vector<bool>` 要素の位置。|

### <a name="return-value"></a>戻り値

インデックス付けされた要素の値を格納する [vector\<bool>::reference](#reference_class) または [vector\<bool>::const_reference](#const_reference) オブジェクト。

指定された位置がコンテナーのサイズ以上の場合、結果は未定義になります。

### <a name="remarks"></a>Remarks

コンパイルしたときに [レベルの設定] を使用した場合、ベクターの境界の外にある要素にアクセスしようとすると、実行時エラーが発生します。  詳細については、「 [Checked Iterators](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

このコード例は、`vector<bool>::operator[]` の正しい使用方法と、コメント アウトされた 2 つの一般的なコーディングの誤りを示しています。`vector<bool>::reference` が返す `vector<bool>::operator[]` オブジェクトのアドレスを取得できないため、これらの誤りによってエラーが発生します。

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;
    vector<bool> vb;

    vb.push_back(true);
    vb.push_back(false);

    //    bool* pb = &vb[1]; // conversion error - do not use
    //    bool& refb = vb[1];   // conversion error - do not use
    bool hold = vb[1];
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;

    // Note this doesn't modify hold.
    vb[1] = true;
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;
}
```

## <a name="pointer"></a>  vector\<bool>::pointer

`vector<bool>` オブジェクトに格納されるシーケンスのブール要素へのポインターとして使用できるオブジェクトを表す型。

```cpp
typedef iterator pointer;
```

## <a name="reference_class"></a>  vector\<bool>::reference クラス

`vector<bool>::reference` クラスは `bool&` をシミュレートするために [vector\<bool> クラス](../standard-library/vector-bool-class.md)によって提供されるプロキシ クラスです。

### <a name="remarks"></a>Remarks

C++ では、ネイティブにビットを直接参照しないため、シミュレートされた参照が必要です。 `vector<bool>` は、要素ごとに 1 ビットだけ使用します。このビットは、このプロキシ クラスを使用して参照できます。 ただし、参照のシミュレーションは、特定の代入が有効でないため、完全ではありません。 たとえば、`vector<bool>::reference` オブジェクトのアドレスを受け取ることができないため、[vector\<bool>::operator&#91;&#93;](#op_at) を使用する次のコードは正しくありません。

```cpp
vector<bool> vb;
//...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

###  <a name="reference_flip"></a>  vector\<bool>::reference::flip

参照先の [vector\<bool>](../standard-library/vector-bool-class.md) 要素のブール値を反転します。

```cpp
void flip();
```

#### <a name="example"></a>例

```cpp
// vector_bool_ref_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    cout << "The vector is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vector<bool>::reference vbref = vb.front();
    vbref.flip();

    cout << "The vector with first element flipped is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

```Output
The vector is:
    true false false true true
The vector with first element flipped is:
    false false false true true
```

###  <a name="reference_operator_bool"></a>  vector\<bool>::reference::operator bool

からブール型への`vector<bool>::reference`暗黙の型変換を提供します。

```cpp
operator bool() const;
```

#### <a name="return-value"></a>戻り値

vector\<bool> オブジェクトの要素のブール値。

#### <a name="remarks"></a>Remarks

`vector<bool>` オブジェクトはこの演算子では変更できません。

###  <a name="reference_operator_eq"></a>  vector\<bool>::reference::operator=

ブール値をビットに割り当てます。または参照先の要素が保持している値をビットに割り当てます。

```cpp
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```

### <a name="parameters"></a>パラメーター

*そうです*\
値がビットに割り当てられている要素の参照。

*Val*\
ビットに割り当てられるブール値。

#### <a name="example"></a>例

```cpp
// vector_bool_ref_op_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
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
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    print("The vector is: ", vb);

    // Invoke vector<bool>::reference::operator=()
    vector<bool>::reference refelem1 = vb[0];
    vector<bool>::reference refelem2 = vb[1];
    vector<bool>::reference refelem3 = vb[2];

    bool b1 = refelem1;
    bool b2 = refelem2;
    bool b3 = refelem3;
    cout << "The original value of the 1st element stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element stored in a bool: " << b3 << endl;
    cout << endl;

    refelem2 = refelem1;

    print("The vector after assigning refelem1 to refelem2 is now: ", vb);

    refelem3 = true;

    print("The vector after assigning false to refelem1 is now: ", vb);

    // The initial values are still stored in the bool variables and remained unchanged
    cout << "The original value of the 1st element still stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element still stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element still stored in a bool: " << b3 << endl;
    cout << endl;
}
```

```Output
The vector is: true false false true true
The original value of the 1st element stored in a bool: true
The original value of the 2nd element stored in a bool: false
The original value of the 3rd element stored in a bool: false

The vector after assigning refelem1 to refelem2 is now: true true false true true
The vector after assigning false to refelem1 is now: true true true true true
The original value of the 1st element still stored in a bool: true
The original value of the 2nd element still stored in a bool: false
The original value of the 3rd element still stored in a bool: false
```

## <a name="swap"></a>  vector\<bool>::swap

プロキシ クラス [vector\<bool>::reference](#reference_class) を使用してブール ベクター (`vector<bool>`) の 2 つの要素を交換する静的メンバー関数。

```cpp
static void swap(
    reference Left,
    reference Right);
```

### <a name="parameters"></a>パラメーター

*左側*\
*右*の要素と交換される要素。

*そうです*\
*左*要素と交換される要素。

### <a name="remarks"></a>Remarks

このオーバーロードは `vector<bool>` の特別なプロキシの要件をサポートします。 [vector](../standard-library/vector-class.md)::swap には、`vector<bool>::swap()` の単一引数のオーバーロードと同じ機能があります。

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
