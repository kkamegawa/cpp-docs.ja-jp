---
title: tuple_size クラス
ms.date: 11/04/2016
f1_keywords:
- tuple_size
- std::tuple_size
- utility/std::tuple_size
helpviewer_keywords:
- std::tuple_size
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
ms.openlocfilehash: 361545bee020d6c3624d1d45743abcb9c2b4ac85
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688850"
---
# <a name="tuple_size-class"></a>tuple_size クラス

`tuple` を含む要素の数を報告します。

## <a name="syntax"></a>構文

```cpp
// TEMPLATE STRUCT tuple_size
template <class Tuple>
   struct tuple_size;

// number of elements in array
template <class Elem, size_t Size>
   struct tuple_size<array<Elem, Size>>
      : integral_constant<size_t, Size>;

// size of pair
template <class T1, class T2>
   struct tuple_size<pair<T1, T2>>
      : integral_constant<size_t, 2>

// size of tuple
template <class... Types>
   struct tuple_size<tuple<Types...>>
      : integral_constant<size_t, sizeof...(Types)>;

// size of const tuple
template <class Tuple>
   struct tuple_size<const Tuple>;

// size of volatile tuple
template <class Tuple>
   struct tuple_size<volatile Tuple>;

// size of const volatile tuple
template <class Tuple>
   struct tuple_size<const volatile Tuple>;
```

```cpp
template <class T> inline constexpr size_t tuple_size_v = tuple_size<T>::value;
```

### <a name="parameters"></a>パラメーター

*タプル*の \
タプルの型。

*Elem* \
配列要素の型。

@No__t_1*サイズ*
配列のサイズ。

*T1* \
ペアの最初のメンバーの型。

*T2* \
ペアの 2 番目のメンバーの型。

*型*\
タプル要素の型。

## <a name="remarks"></a>Remarks

クラステンプレートには、タプル型の*タプル*の範囲を値として持つ整数定数式であるメンバー `value` があります。

配列のテンプレート特殊化には、*値が配列のサイズである*整数定数式である `value` メンバーが含まれています。

ペアのテンプレート特殊化には、2 を値として持つ整数定数式であるメンバー `value` が含まれます。

## <a name="example"></a>例

```cpp
#include <tuple>
#include <iostream>

using namespace std;

typedef tuple<int, double, int, double> MyTuple;
int main()
{
    MyTuple c0(0, 1.5, 2, 3.7);

    // display contents "0 1 2 3"
    cout << get<0>(c0);
    cout << " " << get<1>(c0);
    cout << " " << get<2>(c0);
    cout << " " << get<3>(c0) << endl;

    // display size "4"
    cout << " " << tuple_size<MyTuple>::value << endl;
}
```

```Output
0 1.5 2 3.7
4
```

## <a name="requirements"></a>［要件］

**ヘッダー:** \<tuple>

**ヘッダー:** \<array> (配列の特殊化用)

**ヘッダー:** \<utility> (ペアの特殊化用)

**名前空間:** std
