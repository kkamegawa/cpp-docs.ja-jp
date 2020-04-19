---
title: unique_ptr クラス
ms.date: 11/04/2016
f1_keywords:
- memory/std::unique_ptr
- memory/std::unique_ptr::deleter_type
- memory/std::unique_ptr::element_type
- memory/std::unique_ptr::pointer
- memory/std::unique_ptr::get
- memory/std::unique_ptr::get_deleter
- memory/std::unique_ptr::release
- memory/std::unique_ptr::reset
- memory/std::unique_ptr::swap
helpviewer_keywords:
- std::unique_ptr [C++]
- std::unique_ptr [C++], deleter_type
- std::unique_ptr [C++], element_type
- std::unique_ptr [C++], pointer
- std::unique_ptr [C++], get
- std::unique_ptr [C++], get_deleter
- std::unique_ptr [C++], release
- std::unique_ptr [C++], reset
- std::unique_ptr [C++], swap
ms.assetid: acdf046b-831e-4a4a-83aa-6d4ee467db9a
ms.openlocfilehash: 3aff30e2e23feb85c6b93d79ddd4552849d3ba05
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243474"
---
# <a name="uniqueptr-class"></a>unique_ptr クラス

所有されているオブジェクトまたは配列へのポインターを格納します。 このオブジェクトと配列は、この `unique_ptr` によってのみ所有されます。 このオブジェクトと配列は、`unique_ptr` が破棄されたときに破棄されます。

## <a name="syntax"></a>構文

```cpp
class unique_ptr {
public:
    unique_ptr();
    unique_ptr(nullptr_t Nptr);
    explicit unique_ptr(pointer Ptr);
    unique_ptr(pointer Ptr,
        typename conditional<is_reference<Del>::value, Del,
        typename add_reference<const Del>::type>::type Deleter);
    unique_ptr(pointer Ptr,
        typename remove_reference<Del>::type&& Deleter);
    unique_ptr(unique_ptr&& Right);
    template <class T2, Class Del2>
    unique_ptr(unique_ptr<T2, Del2>&& Right);
    unique_ptr(const unique_ptr& Right) = delete;
    unique_ptr& operator=(const unique_ptr& Right) = delete;
};

//Specialization for arrays:
template <class T, class D>
class unique_ptr<T[], D> {
public:
    typedef pointer;
    typedef T element_type;
    typedef D deleter_type;
    constexpr unique_ptr() noexcept;
    template <class U>
    explicit unique_ptr(U p) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    unique_ptr(unique_ptr&& u) noexcept;
    constexpr unique_ptr(nullptr_t) noexcept : unique_ptr() { }     template <class U, class E>
        unique_ptr(unique_ptr<U, E>&& u) noexcept;
    ~unique_ptr();
    unique_ptr& operator=(unique_ptr&& u) noexcept;
    template <class U, class E>
    unique_ptr& operator=(unique_ptr<U, E>&& u) noexcept;
    unique_ptr& operator=(nullptr_t) noexcept;
    T& operator[](size_t i) const;

    pointer get() const noexcept;
    deleter_type& get_deleter() noexcept;
    const deleter_type& get_deleter() const noexcept;
    explicit operator bool() const noexcept;
    pointer release() noexcept;
    void reset(pointer p = pointer()) noexcept;
    void reset(nullptr_t = nullptr) noexcept;
    template <class U>
    void reset(U p) noexcept = delete;
    void swap(unique_ptr& u) noexcept;  // disable copy from lvalue unique_ptr(const unique_ptr&) = delete;
    unique_ptr& operator=(const unique_ptr&) = delete;
};
```

### <a name="parameters"></a>パラメーター

*そうです*\
`unique_ptr`。

*関数*\
`rvalue` 型の `std::nullptr_t`。

*ptr*\
`pointer`。

*削除子*\
`deleter` にバインドされている `unique_ptr` 関数。

## <a name="exceptions"></a>例外

例外は `unique_ptr` で生成されません。

## <a name="remarks"></a>Remarks

`unique_ptr` クラスは、`auto_ptr` に代わるものであり、C++ 標準ライブラリ コンテナーの要素として使用できます。

効率的に `unique_ptr` の新しいインスタンスを作成するには、[make_unique](../standard-library/memory-functions.md#make_unique) ヘルパー関数を使用します。

`unique_ptr` は一意にリソースを管理します。 `unique_ptr` オブジェクトは null ポインターを所有または保存するオブジェクトへのポインターを格納します。 1 つのリソースは、1 つの `unique_ptr` オブジェクトによってのみ所有されます。特定のリソースを所有する `unique_ptr` オブジェクトが破棄された時点で、リソースが解放されます。 `unique_ptr` オブジェクトを移動することはできますが、コピーすることはできません。詳細については、「[右辺値参照宣言子: &&](../cpp/rvalue-reference-declarator-amp-amp.md)」を参照してください。

特定の `deleter` に対するリソースの割り当てを認識する、`Del` 型の格納された `unique_ptr` オブジェクトを呼び出すことによって、リソースが解放されます。 既定の`deleter``default_delete<T>`がでリソースを指すことを前提としています`ptr`使用が割り当てられた`new`、呼び出すことによって解放できることと`delete _Ptr`します。 (部分的特殊化 `unique_ptr<T[]>` は `new[]` で割り当てられた配列オブジェクトを管理します。また、delete[] `deleter` の呼び出しに特化した既定の `default_delete<T[]>` `ptr` があります)。

所有されたリソースに対する格納されたポインター、`stored_ptr` には、`pointer` 型があります。 これは、定義されている場合は `Del::pointer`、定義されていない場合は `T *` です。 `deleter` がステートレスである場合、格納された `stored_deleter` オブジェクトである `deleter` はオブジェクト内の領域を使用しません。 `Del` が参照型である場合があることに注意してください。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[unique_ptr](#unique_ptr)|`unique_ptr` には、7 種類のコンストラクターがあります。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[deleter_type](#deleter_type)|テンプレート パラメーター `Del` のシノニム。|
|[element_type](#element_type)|テンプレート パラメーター `T` のシノニム。|
|[pointer](#pointer)|定義されている場合は `Del::pointer` のシノニム、それ以外の場合は `T *` のシノニム。|

### <a name="functions"></a>関数

|||
|-|-|
|[get](#get)|`stored_ptr` を返します。|
|[get_deleter](#get_deleter)|`stored_deleter` への参照を返します。|
|[release](#release)|`pointer()` を `stored_ptr` に格納し、以前の内容を返します。|
|[reset](#reset)|現在所有されているリソースを解放し、新しいリソースを受け取ります。|
|[swap](#swap)|指定された `deleter` を使用して、リソースと `unique_ptr` を交換します。|

### <a name="operators"></a>演算子

|||
|-|-|
|**operator bool**|演算子に変換できる型の値を返します**bool**します。 変換の結果**bool**は**true**とき`get() != pointer()`それ以外の場合、 **false**します。|
|`operator->`|このメンバー関数は、`stored_ptr` を返します。|
|`operator*`|このメンバー関数は、`*stored_ptr` を返します。|
|[operator=](#unique_ptr_operator_eq)|現在の `unique_ptr` に `unique_ptr` (または `pointer-type`) の値を割り当てます。|

### <a name="deleter_type"></a> deleter_type

この型は、テンプレート パラメーター `Del` のシノニムです。

```cpp
typedef Del deleter_type;
```

#### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `Del` のシノニムです。

### <a name="element_type"></a> element_type

この型は、テンプレート パラメーター `Type` のシノニムです。

```cpp
typedef Type element_type;
```

#### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `Ty` のシノニムです。

### <a name="get"></a> 取得

`stored_ptr` を返します。

```cpp
pointer get() const;
```

#### <a name="remarks"></a>Remarks

このメンバー関数は、`stored_ptr` を返します。

### <a name="get_deleter"></a> get_deleter

`stored_deleter` への参照を返します。

```cpp
Del& get_deleter();

const Del& get_deleter() const;
```

#### <a name="remarks"></a>Remarks

このメンバー関数は、`stored_deleter` への参照を返します。

### <a name="unique_ptr_operator_eq"></a> 演算子 =

指定された `unique_ptr` のアドレスを現在のアドレスに割り当てます。

```cpp
unique_ptr& operator=(unique_ptr&& right);
template <class U, Class Del2>
unique_ptr& operator=(unique_ptr<Type, Del>&& right);
unique_ptr& operator=(pointer-type);
```

#### <a name="parameters"></a>パラメーター

現在の `unique_ptr` に値を割り当てるために使用される `unique_ptr` 参照。

#### <a name="remarks"></a>Remarks

このメンバー関数は `reset(right.release())` を呼び出し、`right.stored_deleter` を `stored_deleter` に移動し、`*this` を返します。

### <a name="pointer"></a> ポインター

定義されている場合は `Del::pointer` のシノニム、それ以外の場合は `Type *` のシノニム。

```cpp
typedef T1 pointer;
```

#### <a name="remarks"></a>Remarks

この型は、定義されている場合は `Del::pointer` の同意語、それ以外の場合は `Type *` の同意語です。

### <a name="release"></a> リリース

呼び出し元に返される、格納されたポインターの所有権を解放し、格納されているポインター値に設定**nullptr**します。

```cpp
pointer release();
```

#### <a name="remarks"></a>Remarks

`release` を使用して、`unique_ptr` が保存した生のポインターの所有権を引き継ぎます。 呼び出し元は、返されたポインターの削除を担当します。 `unique-ptr` は、既定で構築される空の状態に設定します。 `unique_ptr` を呼び出した後に、互換性のある型の別のポインターを `release` に割り当てることができます。

#### <a name="example"></a>例

この例は、返されたオブジェクトに release の呼び出し元が対応する方法を示しています。

```cpp
// stl_release_unique.cpp
// Compile by using: cl /W4 /EHsc stl_release_unique.cpp
#include <iostream>
#include <memory>

struct Sample {
   int content_;
   Sample(int content) : content_(content) {
      std::cout << "Constructing Sample(" << content_ << ")" << std::endl;
   }
   ~Sample() {
      std::cout << "Deleting Sample(" << content_ << ")" << std::endl;
   }
};

void ReleaseUniquePointer() {
   // Use make_unique function when possible.
   auto up1 = std::make_unique<Sample>(3);
   auto up2 = std::make_unique<Sample>(42);

   // Take over ownership from the unique_ptr up2 by using release
   auto ptr = up2.release();
   if (up2) {
      // This statement does not execute, because up2 is empty.
      std::cout << "up2 is not empty." << std::endl;
   }
   // We are now responsible for deletion of ptr.
   delete ptr;
   // up1 deletes its stored pointer when it goes out of scope.
}

int main() {
   ReleaseUniquePointer();
}
```

```Output
Constructing Sample(3)
Constructing Sample(42)
Deleting Sample(42)
Deleting Sample(3)
```

### <a name="reset"></a> リセット

ポインター パラメーターの所有権を取得してから、格納されている元のポインターを削除します。 新しいポインターは、元の格納されたポインターと同じ場合`reset`ポインターを削除し、格納されたポインター設定**nullptr**します。

```cpp
void reset(pointer ptr = pointer());
void reset(nullptr_t ptr);
```

#### <a name="parameters"></a>パラメーター

*ptr*\
所有権を取得するリソースへのポインター。

#### <a name="remarks"></a>Remarks

使用`reset`、格納されている変更[ポインター](#pointer)によって所有されている、`unique_ptr`に*ptr*し、元の格納されているポインターを削除します。 `unique_ptr` が空でなかった場合、`reset` は元の格納されているポインターについて [get_deleter](#get_deleter) が返すデリーター関数を呼び出します。

`reset`まず新しいポインターを格納*ptr*、元の格納されたポインターを削除しますが可能性があります`reset`を今すぐ削除*ptr*元と同じである場合格納されたポインター。

### <a name="swap"></a> スワップ

2 つの `unique_ptr` オブジェクト間でポインターを交換します。

```cpp
void swap(unique_ptr& right);
```

#### <a name="parameters"></a>パラメーター

*そうです*\
ポインターを交換するために使用される `unique_ptr`。

#### <a name="remarks"></a>Remarks

このメンバー関数は、`stored_ptr` を `right.stored_ptr` と交換し、`stored_deleter` を `right.stored_deleter` と交換します。

### <a name="unique_ptr"></a> unique_ptr

`unique_ptr` には、7 種類のコンストラクターがあります。

```cpp
unique_ptr();

unique_ptr(nullptr_t);
explicit unique_ptr(pointer ptr);

unique_ptr(
    Type* ptr,
    typename conditional<
    is_reference<Del>::value,
    Del,
    typename add_reference<const Del>::type>::type _Deleter);

unique_ptr(pointer ptr, typename remove_reference<Del>::type&& _Deleter);
unique_ptr(unique_ptr&& right);
template <class Ty2, Class Del2>
    unique_ptr(unique_ptr<Ty2, Del2>&& right);
```

#### <a name="parameters"></a>パラメーター

*ptr*\
割り当てられるリソースへのポインター、`unique_ptr`します。

*_Deleter*\
`unique_ptr` に割り当てられる `deleter`。

*そうです*\
新しく構築された `unique_ptr` に対する `unique_ptr` フィールドの割り当て元となる `unique_ptr` への `rvalue reference`。

#### <a name="remarks"></a>Remarks

最初の 2 つのコンストラクターはリソースを管理しないオブジェクトを構築します。 3 番目のコンス トラクター ストア*ptr*で`stored_ptr`します。 4 番目のコンス トラクター ストア*ptr*で`stored_ptr`と`deleter`で`stored_deleter`します。

5 番目のコンス トラクター ストア*ptr*で`stored_ptr`移動`deleter`に`stored_deleter`します。 6 番目と 7 番目のコンストラクターは `stored_ptr` に `right.release()` を格納し、`stored_deleter` に `right.get_deleter()` を移動します。

### <a name="dtorunique_ptr"></a> ~ unique_ptr

`unique_ptr` のデストラクターで、`unique_ptr` オブジェクトを破棄します。

```cpp
~unique_ptr();
```

#### <a name="remarks"></a>Remarks

このデストラクターは `get_deleter()(stored_ptr)` を呼び出します。
