---
title: バリアント クラス
ms.date: 04/04/2019
f1_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
helpviewer_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
ms.openlocfilehash: 9bfdf644374a0b825fd0ca02bf4164a766cb42a3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269304"
---
# <a name="variant-class"></a>バリアント クラス

値が保持していないまたは特定の時点のバリアントの任意のインスタンスが、その代替の型のいずれかの値を保持します。

## <a name="syntax"></a>構文

```cpp
template <class... Types>
    class variant
```

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[バリアント](#variant)|`variant` 型のオブジェクトを構築します。|

### <a name="functions"></a>関数

|||
|-|-|
|[emplace](#emplace)|新しい含まれている値を作成します。|
|[index](#index)|含まれている値のインデックスを返します。|
|[swap](#swap)||
|[valueless_by_exception](#emplace)|返します**false**バリアントは値を保持している場合。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator=](#op_eq)|バリアントを別のバリエーションのコピーに置き換えます。|

## <a name="emplace"></a> emplace

新しい含まれている値を作成します。

```cpp
template <class T, class... Args>
    T& emplace(Args&&...);
template <class T, class U, class... Args>
    T& emplace(initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(Args&&...);
template <size_t I, class U, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(initializer_list<U>, Args&&...);
```

## <a name="index"></a> インデックス

含まれている値のインデックスを返します。

```cpp
constexpr size_t index() const noexcept;
```

## <a name="variant"></a> バリアント

`variant` 型のオブジェクトを構築します。 また、デストラクターが含まれます。

```cpp
constexpr variant() noexcept(see below);
variant(const variant&);
variant(variant&&) noexcept(see below);
template <class T>
    constexpr variant(T&&) noexcept(see below);
template <class T, class... Args>
    constexpr explicit variant(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    constexpr explicit variant(in_place_type_t<T>, initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    constexpr explicit variant(in_place_index_t<I>, Args&&...);
template <size_t I, class U, class... Args>
    constexpr explicit variant(in_place_index_t<I>, initializer_list<U>, Args&&...);

template <class Alloc>
    variant(allocator_arg_t, const Al&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, const variant&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, variant&&);
template <class Alloc, class T>
    variant(allocator_arg_t, const Al&, T&&);
template <class Alloc, class T, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, Args&&...);
template <class Alloc, class T, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, initializer_list<U>, Args&&...);
template <class Alloc, size_t I, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, Args&&...);
template <class Alloc, size_t I, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, initializer_list<U>, Args&&...);

~variant();
```

### <a name="parameters"></a>パラメーター

*Al*\
このオブジェクトに対して使用するアロケーター クラス。

## <a name="op_eq"></a> 演算子 =

バリアントを別のバリエーションのコピーに置き換えます。

```cpp
variant& operator=(const variant&);
variant& operator=(variant&&) noexcept(see below);
template <class T>
    variant& operator=(T&&) noexcept(see below);
```

## <a name="swap"></a> スワップ

```cpp
void swap(variant&) noexcept(see below);
```

## <a name="valueless"></a> valueless_by_exception

返します**false**バリアントは値を保持している場合。

```cpp
constexpr bool valueless_by_exception() const noexcept;
```
