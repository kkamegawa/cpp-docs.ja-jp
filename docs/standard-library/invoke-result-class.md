---
title: invoke_result クラス
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::invoke_result
- type_traits/std::invoke_result_t
- type_traits/std::invoke_result::type
helpviewer_keywords:
- std::invoke_result
- std::invoke_result_t
- std::invoke_result::type
ms.openlocfilehash: a5f67935bde103cf10c1bd9948ac1388f5221322
ms.sourcegitcommit: f38f770bfda1c174d2b81fabda7c893b15bd83a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77473884"
---
# <a name="invoke_result-class"></a>invoke_result クラス

コンパイル時に指定された引数の型を受け取る呼び出し可能な型の戻り値の型を決定します。 C++ 17 で追加されました。

## <a name="syntax"></a>構文

```cpp
template <class Callable, class... Args>
   struct invoke_result<Callable(Args...)>;

// Helper type
template<class Callable, class... Args>
   using invoke_result_t = typename invoke_result<Callable, Args...>::type;
```

### <a name="parameters"></a>パラメーター

*呼び出し*可能\
照会する呼び出し可能型。

*Args*\
照会する呼び出し可能型の引数リストの種類。

## <a name="remarks"></a>コメント

このテンプレートを使用して、コンパイル時に*呼び出し*可能な (*args*...) の結果の種類を決定します。*呼び出し*可能な引数と、 *args*内のすべての型は、完全な型、不明な配列、または cv で修飾された `void`です。 クラステンプレートの `type` メンバーは、引数*Args*... を使用して呼び出されたときに、*呼び出し*元の戻り値の型に名前を指定します。`type` メンバーは、引数*Args*を使用して呼び出されたときに*呼び出し*可能な場合にのみ定義されます...未評価のコンテキスト。 それ以外の場合、クラステンプレートには `type`メンバーがなく、コンパイル時に特定の引数の型に対して SFINAE テストを行うことができます。

## <a name="requirements"></a>要件

**ヘッダー:** \<type_traits >

**名前空間:** std

## <a name="see-also"></a>参照

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)
