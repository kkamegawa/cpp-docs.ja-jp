---
title: add_cv クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_cv
helpviewer_keywords:
- add_cv class
- add_cv
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
ms.openlocfilehash: 0cc63558ea392976bd6a3c5a43735c592e4606b4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456595"
---
# <a name="addcv-class"></a>add_cv クラス

型から**const volatile**型を作成します。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct add_cv;

template <class T>
using add_cv_t = typename add_cv<T>::type;
```

### <a name="parameters"></a>パラメーター

*\T*\
変更する型。

## <a name="remarks"></a>Remarks

変更後`add_cv<T>`の型のインスタンスに`type`は、 [add_volatile](../standard-library/add-volatile-class.md)と[add_const](../standard-library/add-const-class.md)の両方によって変更された*t*と等価のメンバー **typedef**があります。ただし、既に cv 修飾子があるか、参照であるか、またはプロシージャ.

`add_cv_t<T>` ヘルパー型は、`add_cv<T>` メンバー typedef `type` にアクセスするショートカットです。

## <a name="example"></a>例

```cpp
// add_cv.cpp
// compile by using: cl /EHsc /W4 add_cv.cpp
#include <type_traits>
#include <iostream>

struct S {
    void f() {
        std::cout << "invoked non-cv-qualified S.f()" << std::endl;
    }
    void f() const {
        std::cout << "invoked const S.f()" << std::endl;
    }
    void f() volatile {
        std::cout << "invoked volatile S.f()" << std::endl;
    }
    void f() const volatile {
        std::cout << "invoked const volatile S.f()" << std::endl;
    }
};

template <class T>
void invoke() {
    T t;
    ((T *)&t)->f();
}

int main()
{
    invoke<S>();
    invoke<std::add_const<S>::type>();
    invoke<std::add_volatile<S>::type>();
    invoke<std::add_cv<S>::type>();
}
```

```Output
invoked non-cv-qualified S.f()
invoked const S.f()
invoked volatile S.f()
invoked const volatile S.f()
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[remove_const クラス](../standard-library/remove-const-class.md)\
[remove_volatile クラス](../standard-library/remove-volatile-class.md)
