---
title: allocator_base クラス
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_base
- allocators/stdext::allocators::allocator_base
- allocators/stdext::allocator_base::const_pointer
- allocators/stdext::allocator_base::const_reference
- allocators/stdext::allocator_base::difference_type
- allocators/stdext::allocator_base::pointer
- allocators/stdext::allocator_base::reference
- allocators/stdext::allocator_base::size_type
- allocators/stdext::allocator_base::value_type
- allocators/stdext::allocator_base::_Charalloc
- allocators/stdext::allocator_base::_Chardealloc
- allocators/stdext::allocator_base::address
- allocators/stdext::allocator_base::allocate
- allocators/stdext::allocator_base::construct
- allocators/stdext::allocator_base::deallocate
- allocators/stdext::allocator_base::destroy
- allocators/stdext::allocator_base::max_size
helpviewer_keywords:
- stdext::allocator_base [C++]
- stdext::allocators [C++], allocator_base
- stdext::allocator_base [C++], const_pointer
- stdext::allocator_base [C++], const_reference
- stdext::allocator_base [C++], difference_type
- stdext::allocator_base [C++], pointer
- stdext::allocator_base [C++], reference
- stdext::allocator_base [C++], size_type
- stdext::allocator_base [C++], value_type
- stdext::allocator_base [C++], _Charalloc
- stdext::allocator_base [C++], _Chardealloc
- stdext::allocator_base [C++], address
- stdext::allocator_base [C++], allocate
- stdext::allocator_base [C++], construct
- stdext::allocator_base [C++], deallocate
- stdext::allocator_base [C++], destroy
- stdext::allocator_base [C++], max_size
ms.assetid: f920b45f-2a88-4bb0-8ead-b6126b426ed4
ms.openlocfilehash: cbc1a9eb9432a454ca5dc04205b9d0c7b631a430
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72690090"
---
# <a name="allocator_base-class"></a>allocator_base クラス

同期フィルターからユーザー定義のアロケーターを作成するために必要な、基底クラスと共通の関数を定義します。

## <a name="syntax"></a>構文

```cpp
template <class Type, class Sync>
class allocator_base
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Type*|アロケーターによって割り当てられた要素の型。|
|*頻度*|アロケーターの同期ポリシー。[sync_none クラス](../standard-library/sync-none-class.md)、[sync_per_container クラス](../standard-library/sync-per-container-class.md)、[sync_per_thread クラス](../standard-library/sync-per-thread-class.md)、[sync_shared クラス](../standard-library/sync-shared-class.md)のいずれかです。|

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[allocator_base](#allocator_base)|`allocator_base` 型のオブジェクトを構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[const_pointer](#const_pointer)|アロケーターによって管理されるオブジェクトの型に対する定数ポインターを提供する型。|
|[const_reference](#const_reference)|アロケーターによって管理されるオブジェクトの型に対する定数参照を提供する型。|
|[difference_type](#difference_type)|アロケーターによって管理されるオブジェクトの型に対するポインターの値の差を表すことができる符号付き整数型。|
|[pointer](#pointer)|アロケーターによって管理されるオブジェクトの型に対するポインターを提供する型。|
|[reference](#reference)|アロケーターによって管理されるオブジェクトの型に対する参照を提供する型。|
|[size_type](#size_type)|@No__t_0 型のオブジェクトが割り当てることができる任意のシーケンスの長さを表すことができる符号なし整数型。|
|[value_type](#value_type)|アロケーターによって管理される型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[_Charalloc](#charalloc)|**Char**型の配列のストレージを割り当てます。|
|[_Chardealloc](#chardealloc)|**Char**型の要素を含む配列のストレージを解放します。|
|[address](#address)|値が指定されたオブジェクトのアドレスを検索します。|
|[allocate](#allocate)|指定された要素数だけは格納できるメモリのブロックを割り当てます。|
|[construct](#construct)|指定された値で初期化され、指定されたアドレスに配置される、指定された型のオブジェクトを構築します。|
|[deallocate](#deallocate)|指定した位置で始まるストレージから、指定された数のオブジェクトを解放します。|
|[destroy](#destroy)|オブジェクトが格納されたメモリの割り当てを解除せずに、オブジェクトのデストラクターを呼び出します。|
|[max_size](#max_size)|空きメモリがすべて使用される前にクラス アロケーター オブジェクトによって割り当てることのできる、*Type* 型の要素の数を返します。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<allocators>

**名前空間:** stdext

## <a name="charalloc"></a>  allocator_base::_Charalloc

**Char**型の配列のストレージを割り当てます。

```cpp
char *_Charalloc(size_type count);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*count*|割り当てられる配列内の要素の数。|

### <a name="return-value"></a>戻り値

割り当てられたオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、再バインドをコンパイルできないコンパイラでコンパイルした場合に、コンテナーによって使用されます。 この関数は、同期フィルターの `allocate` 関数への呼び出しの結果を返すことで、ユーザー定義のアロケーターに `_Charalloc` を実装します。

## <a name="chardealloc"></a>  allocator_base::_Chardealloc

**Char**型の要素を含む配列のストレージを解放します。

```cpp
void _Chardealloc(void* ptr, size_type count);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*ptr*|記憶域から割り当てを解除される最初のオブジェクトへのポインター。|
|*count*|記憶域から割り当てを解除されるオブジェクトの数。|

### <a name="remarks"></a>Remarks

このメンバー関数は、再バインドをコンパイルできないコンパイラでコンパイルした場合に、コンテナーによって使用されます。 この関数は、同期フィルターの `deallocate` 関数を呼び出すことで、ユーザー定義のアロケーターに `_Chardealloc` を実装します。 ポインター ptr は、同じサイズと型の配列オブジェクトを割り当てる `*this` と等しいことを比較するアロケーター オブジェクトに対し、`_Charalloc` を呼び出すことで、既に返されているはずです。 `_Chardealloc` は例外をスローしません。

## <a name="address"></a>  allocator_base::address

値が指定されたオブジェクトのアドレスを検索します。

```cpp
pointer address(reference val);

const_pointer address(const_reference val);
```

### <a name="parameters"></a>パラメーター

*val* \
アドレスが検索対象となっているオブジェクトの const 値または nonconst 値。

### <a name="return-value"></a>戻り値

見つかった const 値または nonconst 値のそれぞれのオブジェクトに対する const ポインターまたは nonconst ポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、`&val` を返すことで、ユーザー定義のアロケーターに実装されます。

## <a name="allocate"></a>  allocator_base::allocate

指定された要素数だけは格納できるメモリのブロックを割り当てます。

```cpp
template <class Other>
pointer allocate(size_type _Nx, const Other* _Hint = 0);

pointer allocate(size_type _Nx);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Nx (_s)*|割り当てられる配列内の要素の数。|
|*_Hint*|このパラメーターは無視されます。|

### <a name="return-value"></a>戻り値

割り当てられたオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

メンバー関数は、`_Nx == 1` の場合、Type `*` 型の同期フィルターの `allocate` 関数への呼び出しの結果を返すことで、ユーザー定義のアロケーターにメモリ割り当てを実装します。それ以外の場合は、`operator new(_Nx * sizeof(Type))` への呼び出しの結果を返すことで、Type `*` 型にキャストします。

## <a name="allocator_base"></a>  allocator_base::allocator_base

`allocator_base` 型のオブジェクトを構築します。

```cpp
allocator_base();

template <class Other>
allocator_base(const allocator_base<Other, Sync>& right);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*right*|コピーするアロケーター オブジェクト。|

### <a name="remarks"></a>Remarks

1 つ目のコンストラクターは、[allocator_base](../standard-library/allocator-base-class.md) インスタンスを構築します。 2 番目のコンストラクターは、`allocator_base<Type, _Sync>` インスタンス `a`、`allocator_base<Type, Sync>(allocator_base<Other, Sync>(a)) == a` などのいずれかに対し、`allocator_base` インスタンスを構築します。

## <a name="const_pointer"></a>  allocator_base::const_pointer

アロケーターによって管理されるオブジェクトの型に対する定数ポインターを提供する型。

```cpp
typedef const Type *const_pointer;
```

## <a name="const_reference"></a>  allocator_base::const_reference

アロケーターによって管理されるオブジェクトの型に対する定数参照を提供する型。

```cpp
typedef const Type& const_reference;
```

## <a name="construct"></a>  allocator_base::construct

指定された値で初期化され、指定されたアドレスに配置される、指定された型のオブジェクトを構築します。

```cpp
void construct(pointer ptr, const Type& val);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*ptr*|オブジェクトが構築される場所へのポインター。|
|*val*|構築されるオブジェクトが初期化される値。|

### <a name="remarks"></a>Remarks

このメンバー関数は、`new((void*)ptr Type(val)` を呼び出すことで、ユーザー定義のアロケーターに実装されます。

## <a name="deallocate"></a>  allocator_base::deallocate

指定した位置で始まるストレージから、指定された数のオブジェクトを解放します。

```cpp
void deallocate(pointer ptr, size_type _Nx);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*ptr*|記憶域から割り当てを解除される最初のオブジェクトへのポインター。|
|*Nx (_s)*|記憶域から割り当てを解除されるオブジェクトの数。|

### <a name="remarks"></a>Remarks

このメンバー関数は、`_Nx == 1` の場合は同期フィルター `Sync` で `deallocate(ptr)` を呼び出すことで、それ以外の場合は `operator delete(_Nx * ptr)` を呼び出すことで、ユーザー定義のアロケーターに実装されます。

## <a name="destroy"></a>  allocator_base::destroy

オブジェクトが格納されたメモリの割り当てを解除せずに、オブジェクトのデストラクターを呼び出します。

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*ptr*|破棄するオブジェクトのアドレスを指定するポインター。|

### <a name="remarks"></a>Remarks

このメンバー関数は、`ptr->~Type()` を呼び出すことで、ユーザー定義のアロケーターに実装されます。

## <a name="difference_type"></a>  allocator_base::difference_type

アロケーターによって管理されるオブジェクトの型に対するポインターの値の差を表すことができる符号付き整数型。

```cpp
typedef std::ptrdiff_t difference_type;
```

## <a name="max_size"></a>  allocator_base::max_size

空きメモリがすべて使用される前にクラス アロケーター オブジェクトによって割り当てることのできる、型 `Type` の要素の数を返します。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

割り当てることができる要素の数。

### <a name="remarks"></a>Remarks

このメンバー関数は、`0 < (size_t)-1 / sizeof(Type)` の場合は `(size_t)-1 / sizeof(Type)` を返すことで、それ以外は `1` を返すことで、ユーザー定義のアロケーターに実装されます。

## <a name="pointer"></a>  allocator_base::pointer

アロケーターによって管理されるオブジェクトの型に対するポインターを提供する型。

```cpp
typedef Type *pointer;
```

## <a name="reference"></a>  allocator_base::reference

アロケーターによって管理されるオブジェクトの型に対する参照を提供する型。

```cpp
typedef Type& reference;
```

## <a name="size_type"></a>  allocator_base::size_type

@No__t_0 型のオブジェクトが割り当てることができる任意のシーケンスの長さを表すことができる符号なし整数型。

```cpp
typedef std::size_t size_type;
```

## <a name="value_type"></a>  allocator_base::value_type

アロケーターによって管理される型。

```cpp
typedef Type value_type;
```

## <a name="see-also"></a>関連項目

[\<allocators>](../standard-library/allocators-header.md)
