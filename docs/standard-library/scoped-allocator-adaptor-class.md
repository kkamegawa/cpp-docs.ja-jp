---
title: scoped_allocator_adaptor クラス
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::scoped_allocator_adaptor
- scoped_allocator/std::scoped_allocator_adaptor::rebind Struct
- scoped_allocator/std::scoped_allocator_adaptor::allocate
- scoped_allocator/std::scoped_allocator_adaptor::construct
- scoped_allocator/std::scoped_allocator_adaptor::deallocate
- scoped_allocator/std::scoped_allocator_adaptor::destroy
- scoped_allocator/std::scoped_allocator_adaptor::inner_allocator
- scoped_allocator/std::scoped_allocator_adaptor::max_size
- scoped_allocator/std::scoped_allocator_adaptor::outer_allocator
- scoped_allocator/std::scoped_allocator_adaptor::select_on_container_copy_construction
helpviewer_keywords:
- std::scoped_allocator_adaptor
- std::scoped_allocator_adaptor::allocate
- std::scoped_allocator_adaptor::construct
- std::scoped_allocator_adaptor::deallocate
- std::scoped_allocator_adaptor::destroy
- std::scoped_allocator_adaptor::inner_allocator
- std::scoped_allocator_adaptor::max_size
- std::scoped_allocator_adaptor::outer_allocator
- std::scoped_allocator_adaptor::select_on_container_copy_construction
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
ms.openlocfilehash: 6ba135d0c3a69293415d1c46d70679d9f8bc8a37
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686556"
---
# <a name="scoped_allocator_adaptor-class"></a>scoped_allocator_adaptor クラス

アロケーターの入れ子を表します。

## <a name="syntax"></a>構文

```cpp
template <class Outer, class... Inner>
class scoped_allocator_adaptor;
```

## <a name="remarks"></a>Remarks

クラステンプレートは、1つまたは複数のアロケーターの入れ子をカプセル化します。 このような各クラスは、`outer_allocator_type` 型の最も外側のアロケーターである `Outer` のシノニムを持ちます。これは、`scoped_allocator_adaptor` オブジェクトのパブリック ベースです。 `Outer` はコンテナーで使用されるメモリの割り当てに使用されます。 このアロケーター基本オブジェクトへの参照を取得するには、`outer_allocator` を呼び出します。

入れ子の残りの部分には `inner_allocator_type` 型が含まれます。 内部のアロケーターを使用して、コンテナー内の要素にメモリを割り当てます。 格納されているこの型のオブジェクトへの参照を取得するには、`inner_allocator` を呼び出します。 `Inner...` が空ではない場合、`inner_allocator_type` は型 `scoped_allocator_adaptor<Inner...>` を持ち、`inner_allocator` はメンバー オブジェクトを指定します。 それ以外の場合、`inner_allocator_type` は型 `scoped_allocator_adaptor<Outer>` を持ち、`inner_allocator` はオブジェクト全体を指定します。

入れ子は、必要に応じて、最も内側のカプセル化されたアロケーターをレプリケートする任意の深さがあるかのように動作します。

表示されるインターフェイスの一部ではないいくつかの概念は、このクラステンプレートの動作を説明するのに役立ちます。 *最も外側のアロケーター*は、コンストラクトのすべての呼び出しを仲介し、メソッドを破棄します。 再帰関数 `OUTERMOST(X)` で効率的に定義されます。ここで `OUTERMOST(X)` は、次のいずれかです。

- `X.outer_allocator()` が整形式である場合、`OUTERMOST(X)` は `OUTERMOST(X.outer_allocator())` です。

- それ以外の場合、`OUTERMOST(X)` は `X` です。

説明のために 3 つの型が定義されています。

|[種類]|説明|
|----------|-----------------|
|`Outermost`|`OUTERMOST(*this)` の型。|
|`Outermost_traits`|`allocator_traits<Outermost>`|
|`Outer_traits`|`allocator_traits<Outer>`|

### <a name="constructors"></a>コンストラクター

|名|説明|
|----------|-----------------|
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|`scoped_allocator_adaptor` オブジェクトを構築します。|

### <a name="typedefs"></a>Typedef

|名|説明|
|----------|-----------------|
|`const_pointer`|この型は、アロケーター `Outer` に関連付けられている `const_pointer` のシノニムです。|
|`const_void_pointer`|この型は、アロケーター `Outer` に関連付けられている `const_void_pointer` のシノニムです。|
|`difference_type`|この型は、アロケーター `Outer` に関連付けられている `difference_type` のシノニムです。|
|`inner_allocator_type`|この型は、入れ子になったアダプター `scoped_allocator_adaptor<Inner...>` の型のシノニムです。|
|`outer_allocator_type`|この型は、基本アロケーター `Outer` の型のシノニムです。|
|`pointer`|この型は、アロケーター `Outer` に関連付けられている `pointer` のシノニムです。|
|`propagate_on_container_copy_assignment`|`Outer_traits::propagate_on_container_copy_assignment` が true を保持するか、または `inner_allocator_type::propagate_on_container_copy_assignment` が true を保持する場合にのみ、この型は true を保持します。|
|`propagate_on_container_move_assignment`|`Outer_traits::propagate_on_container_move_assignment` が true を保持するか、または `inner_allocator_type::propagate_on_container_move_assignment` が true を保持する場合にのみ、この型は true を保持します。|
|`propagate_on_container_swap`|`Outer_traits::propagate_on_container_swap` が true を保持するか、または `inner_allocator_type::propagate_on_container_swap` が true を保持する場合にのみ、この型は true を保持します。|
|`size_type`|この型は、アロケーター `Outer` に関連付けられている `size_type` のシノニムです。|
|`value_type`|この型は、アロケーター `Outer` に関連付けられている `value_type` のシノニムです。|
|`void_pointer`|この型は、アロケーター `Outer` に関連付けられている `void_pointer` のシノニムです。|

### <a name="structs"></a>構造体

|名|説明|
|----------|-----------------|
|[scoped_allocator_adaptor::rebind 構造体](#rebind_struct)|`scoped_allocator_adaptor\<Other, Inner...>` のシノニムとして `Outer::rebind\<Other>::other` 型を定義します。|

### <a name="methods"></a>メソッド

|名|説明|
|----------|-----------------|
|[allocate](#allocate)|`Outer` アロケーターを使用してメモリを割り当てます。|
|[construct](#construct)|オブジェクトを構築します。|
|[deallocate](#deallocate)|外側のアロケーターを使用してオブジェクトの割り当てを解除します。|
|[destroy](#destroy)|指定したオブジェクトを破棄します。|
|[inner_allocator](#inner_allocator)|`inner_allocator_type` 型の格納されているオブジェクトへの参照を取得します。|
|[max_size](#max_size)|外側のアロケーターが割り当てることができるオブジェクトの最大数を指定します。|
|[outer_allocator](#outer_allocator)|`outer_allocator_type` 型の格納されているオブジェクトへの参照を取得します。|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|対応するアロケーターごとに `select_on_container_copy_construction` を呼び出すことによって、格納されている各アロケーター オブジェクトが初期化された新しい `scoped_allocator_adaptor` オブジェクトを作成します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator=](#op_as)||
|[operator==](#op_eq_eq)||
|[operator!=](#op_noeq)||

## <a name="requirements"></a>［要件］

**ヘッダー:** \<scoped_allocator>

**名前空間:** std

## <a name="allocate"></a>scoped_allocator_adaptor:: allocate

`Outer` アロケーターを使用してメモリを割り当てます。

```cpp
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```

### <a name="parameters"></a>パラメーター

*カウント*\
十分な記憶域を割り当てる要素の数。

*ヒント*\
要求の前に割り当てられたオブジェクトのアドレスを見つけることによって、アロケーター オブジェクトを支援できるポインター。

### <a name="return-value"></a>戻り値

最初のメンバー関数は `Outer_traits::allocate(outer_allocator(), count)` を返します。 2 番目のメンバー関数は `Outer_traits::allocate(outer_allocator(), count, hint)` を返します。

## <a name="construct"></a>scoped_allocator_adaptor:: construct

オブジェクトを構築します。

```cpp
template <class Ty, class... Atypes>
void construct(Ty* ptr, Atypes&&... args);

template <class Ty1, class Ty2, class... Atypes1, class... Atypes2>
void construct(pair<Ty1, Ty2>* ptr, piecewise_construct_t,
    tuple<Atypes1&&...>
first, tuple<Atypes1&&...> second);

template <class Ty1, class Ty2>
void construct(pair<Ty1, Ty2>* ptr);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr,
    class Uy1&& first, class Uy2&& second);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, const pair<Uy1, Uy2>& right);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, pair<Uy1, Uy2>&& right);
```

### <a name="parameters"></a>パラメーター

*ptr* \
オブジェクトが構築されるメモリの場所へのポインター。

*args* \
引数リスト。

*最初*の \
ペアの最初の型のオブジェクト。

*2 番目*の \
ペアの 2 番目の型のオブジェクト。

*右*\
移動またはコピーされる既存のオブジェクト。

### <a name="remarks"></a>Remarks

最初のメソッドは `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)` を呼び出すことによってオブジェクトを*ptr*に構築します。 `xargs...` は次のいずれかになります。

- `uses_allocator<Ty, inner_allocator_type>` が false を保持する場合、`xargs...` は `args...` です。

- `uses_allocator<Ty, inner_allocator_type>` が true を保持し、`is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` が true を保持する場合、`xargs...` は `allocator_arg, inner_allocator(), args...` です。

- `uses_allocator<Ty, inner_allocator_type>` が true を保持し、`is_constructible<Ty, args..., inner_allocator()>` が true を保持する場合、`xargs...` は `args..., inner_allocator()` です。

2番目のメソッドは、`Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)` を呼び出すことによって、 *ptr*にペアオブジェクトを構築します。この場合、`xargs...` は上記のリストのように変更され、`Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`、上記の一覧のように `xargs...` が変更 `first...` されます。

3 番目のメソッドの動作は `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)` と同じです。

4 番目のメソッドの動作は `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))` と同じです。

5 番目のメソッドの動作は `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))` と同じです。

6 番目のメソッドの動作は `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))` と同じです。

## <a name="deallocate"></a>scoped_allocator_adaptor::d eallocate

外側のアロケーターを使用してオブジェクトの割り当てを解除します。

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>パラメーター

*ptr* \
割り当て解除されるオブジェクトの開始位置へのポインター。

*カウント*\
割り当て解除するオブジェクトの数。

## <a name="destroy"></a>scoped_allocator_adaptor::d estroy

指定したオブジェクトを破棄します。

```cpp
template <class Ty>
void destroy(Ty* ptr)
```

### <a name="parameters"></a>パラメーター

*ptr* \
破棄するオブジェクトへのポインター。

### <a name="return-value"></a>戻り値

`Outermost_traits::destroy(OUTERMOST(*this), ptr)`

## <a name="inner_allocator"></a>scoped_allocator_adaptor::inner_allocator

`inner_allocator_type` 型の格納されているオブジェクトへの参照を取得します。

```cpp
inner_allocator_type& inner_allocator() noexcept;
const inner_allocator_type& inner_allocator() const noexcept;
```

### <a name="return-value"></a>戻り値

`inner_allocator_type` 型の格納されているオブジェクトへの参照。

## <a name="max_size"></a>scoped_allocator_adaptor::max_size

外側のアロケーターが割り当てることができるオブジェクトの最大数を指定します。

```cpp
size_type max_size();
```

### <a name="return-value"></a>戻り値

`Outer_traits::max_size(outer_allocator())`

## <a name="a-nameop_as--scoped_allocator_adaptoroperator"></a><a name="op_as"> scoped_allocator_adaptor:: operator =

```cpp
scoped_allocator_adaptor& operator=(const scoped_allocator_adaptor&) = default;
scoped_allocator_adaptor& operator=(scoped_allocator_adaptor&&) = default;
```

## <a name="a-nameop_eq_eq--scoped_allocator_adaptoroperator"></a><a name="op_eq_eq"> scoped_allocator_adaptor:: operator = =

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator==(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="a-nameop_noeq--scoped_allocator_adaptoroperator"></a><a name="op_noeq"> scoped_allocator_adaptor:: operator! =

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator!=(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="outer_allocator"></a>scoped_allocator_adaptor::outer_allocator

`outer_allocator_type` 型の格納されているオブジェクトへの参照を取得します。

```cpp
outer_allocator_type& outer_allocator() noexcept;
const outer_allocator_type& outer_allocator() const noexcept;
```

### <a name="return-value"></a>戻り値

`outer_allocator_type` 型の格納されているオブジェクトへの参照。

## <a name="rebind_struct"></a>  scoped_allocator_adaptor::rebind 構造体

`scoped_allocator_adaptor\<Other, Inner...>` のシノニムとして `Outer::rebind\<Other>::other` 型を定義します。

構造体の再バインド {typedef Other_traits:: 再バインド \<Other > Other_alloc; typedef scoped_allocator_adaptor \<Other_alloc, Inner...> その他;};

## <a name="scoped_allocator_adaptor"></a>  scoped_allocator_adaptor::scoped_allocator_adaptor コンストラクター

`scoped_allocator_adaptor` オブジェクトを構築します。 には、デストラクターも含まれています。

```cpp
scoped_allocator_adaptor();

scoped_allocator_adaptor(const scoped_allocator_adaptor& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
const scoped_allocator_adaptor<Outer2, Inner...>& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
scoped_allocator_adaptor<Outer2, Inner...>&& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(Outer2&& al,
    const Inner&... rest) noexcept;

~scoped_allocator_adaptor();
```

### <a name="parameters"></a>パラメーター

*右*\
既存の `scoped_allocator_adaptor`。

*al* \
外側のアロケーターとして使用する既存のアロケーター。

*rest* \
内側のアロケーターとして使用するアロケーターのリスト。

### <a name="remarks"></a>Remarks

1 番目のコンストラクターは、格納されているアロケーター オブジェクトを既定で構築します。 次の3つの各コンストラクターは、対応するオブジェクトから、格納されているアロケーターオブジェクトを*右側*に構築します。 最後のコンストラクターは、引数リストの対応する引数から、格納されているアロケーター オブジェクトを構築します。

## <a name="select_on_container_copy_construction"></a>scoped_allocator_adaptor::select_on_container_copy_construction

対応するアロケーターごとに `select_on_container_copy_construction` を呼び出すことによって、格納されている各アロケーター オブジェクトが初期化された新しい `scoped_allocator_adaptor` オブジェクトを作成します。

```cpp
scoped_allocator_adaptor select_on_container_copy_construction();
```

### <a name="return-value"></a>戻り値

このメソッドは、実質的に `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())` を返します。 結果は、対応するアロケーター *al*の `al.select_on_container_copy_construction()` を呼び出すことによって、格納されている各アロケーターオブジェクトを初期化した新しい `scoped_allocator_adaptor` オブジェクトになります。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)
