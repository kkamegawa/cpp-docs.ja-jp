---
title: result_of クラス
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
ms.openlocfilehash: ab575ac31936e7003f19fc2ceb3c5b1727d0728c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688995"
---
# <a name="result_of-class"></a>result_of クラス

指定された引数型を受け取る呼び出し可能型の戻り値の型を決定します。 C++ 14 では非推奨となりました。

## <a name="syntax"></a>構文

```cpp
template<class>
struct result_of; // Causes a static assert

template <class Fn, class... ArgTypes>
struct result_of<Fn(ArgTypes...)>;

// Helper type
template<class T>
   using result_of_t = typename result_of<T>::type;
```

### <a name="parameters"></a>パラメーター

*Fn* \
照会する呼び出し可能型。

*Argtypes* \
照会する呼び出し可能型の引数リストの種類。

## <a name="remarks"></a>Remarks

このテンプレートを使用して、コンパイル時に `Fn` の結果の型 (`ArgTypes`) を決定します。ここで、 *Fn*は呼び出し可能な型、関数への参照、または*argtypes*の型の引数リストを使用して呼び出される呼び出し可能な型への参照です。 未評価の式 `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` が整形式である場合、クラステンプレートの `type` メンバーは `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` の結果の型に名前を指定します。 それ以外の場合、クラステンプレートには `type` メンバーがありません。 型*Fn*とパラメーターパックの*argtypes*のすべての型は、完全な型、 **void**、または不明なバインドの配列である必要があります。 C++ 17 で[invoke_result](invoke-result-class.md)を使用することは推奨されていません。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[invoke_result クラス](invoke-result-class.md)
