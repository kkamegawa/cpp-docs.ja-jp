---
title: 任意のクラス
ms.date: 04/04/2019
f1_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
helpviewer_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
ms.openlocfilehash: 050276da665ab6ed3eb53d9e65bfea06b88bcbea
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268754"
---
# <a name="any-class"></a>任意のクラス

値を持たないコンス トラクターの要件を満たす任意の型のインスタンス ストアに、クラスの状態任意のオブジェクトが呼び出されます。

格納されているインスタンスは、含まれている値と呼ばれます。 2 つの状態は、両方の値を持つありませんか、または値を持つ両方と、含まれている値が同じ場合に、同じです。

## <a name="syntax"></a>構文

```cpp
class any
```

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[any](#any)|`any` 型のオブジェクトを構築します。|

### <a name="functions"></a>関数

|||
|-|-|
|[emplace](#emplace)|任意の値を設定します。|
|[has_value](#has_value)|返します**true**がいずれかの値。|
|[reset](#reset)|Any をリセットします。|
|[swap](#swap)|交換する 2 つのオブジェクト。|
|[type](#type)|任意の型を返します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator=](#op_eq)|別のコピーのいずれかをすべて置き換えます。|

## <a name="any"></a> 任意

`any` 型のオブジェクトを構築します。 また、デストラクターが含まれます。

```cpp
constexpr any() noexcept;
any(const any& other);
any(any&& other) noexcept;
template <class T>
    any(T&& value);
template <class T, class... Args>
    explicit any(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    explicit any(in_place_type_t<T>, initializer_list<U>, Args&&...);

~any();
```

## <a name="emplace"></a> emplace

任意の値を設定します。

```cpp
template <class T, class... Args>
    decay_t<T>& emplace(Args&& ...);
template <class T, class U, class... Args>
    decay_t<T>& emplace(initializer_list<U>, Args&&...);
```

## <a name="has_value"></a> has_value

返します**true**がいずれかの値。

```cpp
bool has_value() const noexcept;
```

## <a name="op_eq"></a> 演算子 =

別のコピーのいずれかをすべて置き換えます。

```cpp
any& operator=(const any& right);
any& operator=(any&& right) noexcept;
template <class T>
    any& operator=(T&& right);
```

### <a name="parameters"></a>パラメーター

*そうです*\
いずれかのいずれかにコピーします。

## <a name="reset"></a> リセット

Any をリセットします。

```cpp
void reset() noexcept;
```

## <a name="swap"></a> スワップ

交換する 2 つのオブジェクト。

```cpp
void swap(any& rhs) noexcept;
```

## <a name="type"></a> 型

任意の型を返します。

```cpp
const type_info& type() const noexcept;
```
