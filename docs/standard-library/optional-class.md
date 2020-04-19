---
title: 省略可能なクラス
ms.date: 11/04/2016
f1_keywords:
- optional/std::optional
- optional/std::optional::has_value
- optional/std::optional::reset
- optional/std::optional::value
- optional/std::optional::value_or
helpviewer_keywords:
- optional/std::optional
- optional/std::optional::has_value
- optional/std::optional::reset
- optional/std::optional::value
- optional/std::optional::value_or
ms.openlocfilehash: d9c4bf5356e6ff163ecdf7e1a80bc55453d59003
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689156"
---
# <a name="optional-class"></a>省略可能なクラス

クラステンプレート `optional<T>` は、格納されている*値*と呼ばれる型 `T`の値を含むことができるか、または含まれないオブジェクトを表します。

`optional<T>` のインスタンスに値が含まれている場合、格納されている値は、`optional` オブジェクトのストレージ内で、型 `T`に対して適切に配置された領域内に割り当てられます。 `optional<T>` が `bool`に変換されると、オブジェクトに値が含まれている場合、結果は `true` ます。それ以外の場合は、`false`ます。

含まれているオブジェクト型 `T` を[in_place_t](in-place-t-struct.md)または[nullopt_t](nullopt-t-structure.md)にすることはできません。 `T` は*破棄可能な*である必要があります。つまり、そのデストラクターは所有されているすべてのリソースを解放する必要があり、例外をスローしない可能性があります。

`optional` クラスは C++ 17 で新たに追加されています。

## <a name="syntax"></a>構文

```cpp
template <class T>
class optional
{
    using value_type = T;
};

template<class T> optional(T) -> optional<T>;
```

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
| **コンストラクターとデストラクター** | |
|[optional](#optional) | `optional` 型のオブジェクトを構築します。 |
|[~ 省略可能](#optional-destructor) | `optional`型のオブジェクトを破棄します。 |
| **代入** | |
| [operator=](#op_eq) | `optional` を別の `optional`のコピーで置き換えます。 |
| [emplace](#op_eq) | 引数を指定して、格納されている値を初期化します。 |
| **Swap** | |
| [swap](#swap) | 含まれている値または空の状態を別の `optional`と交換します。 |
| **オブザーバー** | |
| [has_value](#has_value) | `optional` オブジェクトに値が含まれているかどうかを返します。 |
| [値](#value) | 格納されている値を返します。 |
| [value_or](#value_or) | 含まれている値を返します。値が存在しない場合は、代替のを返します。 |
| [operator->](#op_as) | `optional` オブジェクトの格納されている値を参照します。 |
| [operator*](#op_mem) | `optional` オブジェクトの格納されている値を参照します。 |
| [operator bool](#op_bool) | `optional` オブジェクトに値が含まれているかどうかを返します。 |
| **修飾子** | |
| [reset](#reset) | 格納されている値をすべて破棄することによって、`optional` をリセットします。 |

## <a name="has_value"></a>has_value

```cpp
constexpr bool has_value() const noexcept;
```

## <a name="optional"></a>省略可能なコンストラクター

`optional` 型のオブジェクトを構築します。

```cpp
constexpr optional() noexcept;
constexpr optional(nullopt_t nullopt) noexcept;
constexpr optional(const optional& rhs);
constexpr optional(optional&& rhs) noexcept;

template <class... Args>
constexpr explicit optional(in_place_t, Args&&... args);

template <class U, class... Args>
constexpr explicit optional(in_place_t, initializer_list<U> i_list, Args&&... args);

template <class U = T>
explicit constexpr optional(U&& rhs);

template <class U>
explicit optional(const optional<U>& rhs);

template <class U>
explicit optional(optional<U>&& rhs);
```

### <a name="parameters"></a>パラメーター

*rhs*\
格納されている値をコピーまたは移動する `optional`。

*i_list*\
格納されている値を構築する初期化子リスト。

*args*\
格納されている値を構築する引数リスト。

### <a name="remarks"></a>コメント

`constexpr optional() noexcept;`
`constexpr optional(nullopt_t nullopt) noexcept;` これらのコンストラクターは、値を含まない `optional` を構築します。

コピーコンストラクター `constexpr optional(const optional& rhs);`、引数の格納されている値から、格納されている値を初期化します。 `is_copy_constructible_v<T>` が true の場合を除き、**削除済み**として定義されています。 `is_trivially_copy_constructible_v<T>` が true の場合は簡単です。

移動コンストラクター `constexpr optional(optional&& rhs) noexcept;`、含まれている値を引数の値から移動して、格納されている値を初期化します。 `is_move_constructible_v<T>` が true の場合を除き、オーバーロードの解決には関与しません。 `is_trivially_move_constructible_v<T>` が真である場合、これは簡単です。

`template <class... Args> constexpr explicit optional(in_place_t, Args&&... args);` Direct は、引数 `std::forward<Args>(args)`を使用する場合と同様に、格納されている値を初期化します。 使用する `T` コンストラクターが `constexpr`場合、このコンストラクターは `constexpr` ます。 `is_constructible_v<T, Args...>` が true でない限り、オーバーロードの解決には関与しません。

`template <class U, class... Args> constexpr explicit optional(in_place_t, initializer_list<U> i_list, Args&&... args);` Direct は、引数 `i_list, std::forward<Args>(args)`を使用する場合と同様に、格納されている値を初期化します。 使用する `T` コンストラクターが `constexpr`場合、このコンストラクターは `constexpr` ます。 `is_constructible_v<T, initializer_list<U>&, Args&&...>` が true でない限り、オーバーロードの解決には関与しません。

`template <class U = T> explicit constexpr optional(U&& rhs);` Direct は、`std::forward<U>(v)`を使用する場合と同様に、格納されている値を初期化します。 使用する `T` コンストラクターが `constexpr`場合、このコンストラクターは `constexpr` ます。 `is_constructible_v<T, U&&>` が true で、`is_same_v<remove_cvref_t<U>, in_place_t>` と `is_same_v<remove_cvref_t<U>, optional>` が false でない限り、オーバーロードの解決には関与しません。

*rhs*に値が含まれている場合は、引数の格納されている値から、格納されている値を直接初期化します。 `template <class U> explicit optional(const optional<U>& rhs);` `is_constructible_v<T, const U&>` が true ではなく、`is_constructible_v<T, optional<U>&>`、`is_constructible_v<T, optional<U>&&>`、`is_constructible_v<T, const optional<U>&>`、`is_constructible_v<T, const optional<U>&&>`、`is_convertible_v<optional<U>&, T>`、`is_convertible_v<optional<U>&&, T>`、`is_convertible_v<const optional<U>&, T>`、および `is_convertible_v<const optional<U>&&, T>` がすべて false である場合を除き、オーバーロードの解決には関与しません。

`template <class U> explicit optional(optional<U>&& rhs);` に値が*含まれている場合*は、`std::move(*rhs)`を使用する場合と同様に、格納されている値を直接初期化します。 `is_constructible_v<T, U&&>` が true ではなく、`is_constructible_v<T, optional<U>&>`、`is_constructible_v<T, optional<U>&&>`、`is_constructible_v<T, const optional<U>&>`、`is_constructible_v<T, const optional<U>&&>`、`is_convertible_v<optional<U>&, T>`、`is_convertible_v<optional<U>&&, T>`、`is_convertible_v<const optional<U>&, T>`、および `is_convertible_v<const optional<U>&&, T>` がすべて false である場合を除き、オーバーロードの解決には関与しません。

## <a name="optional-destructor"></a>~ 省略可能なデストラクター

非普通の破棄可能なに含まれている値が存在する場合は、そのデストラクターを呼び出して破棄します。

```cpp
~optional();
```

### <a name="remarks"></a>コメント

`T` が非常に破棄可能なの場合、`optional<T>` も普通の破棄可能なになります。

## <a name="op_eq"></a>operator =

`optional` の含まれている値を、含まれている別の `optional` 値からコピーまたは移動した値に置き換えます。

```cpp
optional& operator=(nullopt_t) noexcept;
optional& operator=(const optional& rhs);
optional& operator=(optional&&) noexcept( /* see below */ );

template <class U = T>
    optional& operator=(U&&);

template <class U>
optional& operator=(const optional<U>&);

template <class U>
    optional& operator=(optional<U>&&);

template <class... Args>
T& emplace(Args&&...);

template <class U, class... Args>
T& emplace(initializer_list<U>, Args&&...);
```

## <a name="op_as"></a>演算子->

`optional` オブジェクトの格納されている値を逆参照します。

```cpp
constexpr const T* operator->() const;
constexpr T* operator->();
```

## <a name="op_mem"></a>operator

`optional` オブジェクトの格納されている値を逆参照します。

```cpp
constexpr const T& operator*() const&;
constexpr T& operator*() &;
constexpr T&& operator*() &&;
constexpr const T&& operator*() const&&;
```

## <a name="op_bool"></a>bool 演算子

`optional` オブジェクトに格納されている値があるかどうかを報告します。

```cpp
constexpr explicit operator bool() const noexcept;
```

## <a name="reset"></a>解除

実質的に、は、含まれているオブジェクトのデストラクターを呼び出し、初期化されていない状態に設定します。

```cpp
void reset() noexcept;
```

## <a name="swap"></a>フォト

```cpp
template<class T>
void swap(optional<T>&, optional<T>&) noexcept;
```

## <a name="value"></a>数値

```cpp
constexpr const T& value() const&;
constexpr T& value() &;
constexpr T&& value() &&;
constexpr const T&& value() const&&;
```

## <a name="value_or"></a>value_or

```cpp
template <class U>
    constexpr T value_or(U&&) const&;
template <class U>
    constexpr T value_or(U&&) &&;
```

## <a name="see-also"></a>参照

[\<オプションの >](optional.md)
