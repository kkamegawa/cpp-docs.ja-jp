---
title: add_pointer クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_pointer
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
ms.openlocfilehash: 759867a542aa128755ba31e090984eb5b3fe6963
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456555"
---
# <a name="addpointer-class"></a>add_pointer クラス

指定された型から型へのポインターを作成します。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct add_pointer;

template <class T>
using add_pointer_t = typename add_pointer<T>::type;
```

### <a name="parameters"></a>パラメーター

*\T*\
変更する型。

## <a name="remarks"></a>Remarks

このメンバー **typedef** `type`は、と同じ型`remove_reference<T>::type*`に名前を付けます。 エイリアス`add_pointer_t`は、メンバー **typedef** `type`にアクセスするためのショートカットです。

参照からポインターを作成することは無効であるため、`add_pointer` は型へのポインターを作成する前に、指定された型から参照を削除します (存在する場合)。 その結果、型が参照であるかどうかを気にすることなく、型を `add_pointer` で使用できます。

## <a name="example"></a>例

次の例では、型の `add_pointer` がその型へのポインターと同じであることを示します。

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_pointer_t<int> *p = (int **)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_pointer_t<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_pointer_t<int> == int *
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[remove_pointer クラス](../standard-library/remove-pointer-class.md)
