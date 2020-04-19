---
title: add_rvalue_reference クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_rvalue_reference
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
ms.openlocfilehash: 64694f2428c1dd536df4d242a17f3f011cfb290c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456533"
---
# <a name="addrvaluereference-class"></a>add_rvalue_reference クラス

テンプレート パラメーターがオブジェクトまたは関数の型の場合に、その右辺値参照型を作成します。 それ以外の場合、参照縮小のセマンティクスのため、型はテンプレート パラメーターと同じです。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```

### <a name="parameters"></a>パラメーター

*\T*\
変更する型。

## <a name="remarks"></a>Remarks

クラスには、という`type`名前のメンバーがあります。これは、テンプレートパラメーター T への右辺値参照の型のエイリアスです。  `add_rvalue_reference`参照の縮小のセマンティクスは、非オブジェクト型と非関数型*t* `T&&`の場合、 *t*です。たとえば、 *T*が左辺値参照型`add_rvalue_reference<T>::type`の場合、は右辺値参照ではなく左辺値参照型です。

便宜上、 \<type_traits > は、の`add_rvalue_reference`メンバーの`type`エイリアス`add_rvalue_reference_t`であるヘルパーテンプレートを定義します。

## <a name="example"></a>例

このコード例では、static_assert を使用して、右辺値参照型を `add_rvalue_reference` と`add_rvalue_reference_t` を使用して作成する方法、および左辺値参照型での `add_rvalue_reference` の結果を右辺値参照ではなく左辺値参照型に縮小する方法を示します。

```cpp
// ex_add_rvalue_reference.cpp
// Build by using: cl /EHsc /W4 ex_add_rvalue_reference.cpp
#include <type_traits>
#include <iostream>
#include <string>

using namespace std;
int main()
{
    static_assert(is_same<add_rvalue_reference<string>::type, string&&>::value,
        "Expected add_rvalue_reference_t<string> to be string&&");
    static_assert(is_same<add_rvalue_reference_t<string*>, string*&&>::value,
        "Expected add_rvalue_reference_t<string*> to be string*&&");
    static_assert(is_same<add_rvalue_reference<string&>::type, string&>::value,
        "Expected add_rvalue_reference_t<string&> to be string&");
    static_assert(is_same<add_rvalue_reference_t<string&&>, string&&>::value,
        "Expected add_rvalue_reference_t<string&&> to be string&&");
    cout << "All static_assert tests of add_rvalue_reference passed." << endl;
    return 0;
}

/*Output:
All static_assert tests of add_rvalue_reference passed.
*/
```

## <a name="requirements"></a>必要条件

ヘッダー: \<type_traits >

名前空間: std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[add_lvalue_reference クラス](../standard-library/add-lvalue-reference-class.md)\
[is_rvalue_reference クラス](../standard-library/is-rvalue-reference-class.md)
