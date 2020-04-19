---
title: is_pod クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_pod
helpviewer_keywords:
- is_pod class
- is_pod
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
ms.openlocfilehash: 1249e9a3689d4b91334e545ba294c28984898035
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455759"
---
# <a name="ispod-class"></a>is_pod クラス

型が POD かどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct is_pod;
```

### <a name="parameters"></a>パラメーター

*\T*\
照会する型。

## <a name="remarks"></a>Remarks

`is_pod<T>::value`*T*型が Plain Old DATA (POD) の場合、は**true**になります。 それ以外の場合は**false**になります。

演算型、列挙型、ポインター型、およびメンバーへのポインター型は、POD です。

POD 型の cv-qualified バージョンは、それ自体が POD 型です。

POD の配列は、それ自体が POD です。

すべての非静的データ メンバーが POD である構造体または共用体は、次に該当する場合、それ自体が POD です。

- ユーザーが宣言したコンストラクターを持たない。

- 非静的なプライベートまたはプロテクト データ メンバーを持たない。

- 基底クラスを持たない。

- 仮想関数を持たない。

- 参照型の非静的データ メンバーを持たない。

- ユーザー定義のコピー代入演算子を持たない。

- ユーザー定義のデストラクターを持たない。

したがって、POD 型の構造体や配列を含む POD 型の構造体や配列を再帰的に構築できます。

## <a name="example"></a>例

```cpp
// std__type_traits__is_pod.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial {
    int val;
};

struct throws {
    throws() {}  // User-declared ctor, so not POD

    int val;
};

int main() {
    std::cout << "is_pod<trivial> == " << std::boolalpha
        << std::is_pod<trivial>::value << std::endl;
    std::cout << "is_pod<int> == " << std::boolalpha
        << std::is_pod<int>::value << std::endl;
    std::cout << "is_pod<throws> == " << std::boolalpha
        << std::is_pod<throws>::value << std::endl;

    return (0);
}
```

```Output
is_pod<trivial> == true
is_pod<int> == true
is_pod<throws> == false
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
