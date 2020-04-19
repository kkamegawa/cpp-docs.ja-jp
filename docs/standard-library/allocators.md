---
title: アロケーター
ms.date: 11/04/2016
helpviewer_keywords:
- allocators
- C++ Standard Library, allocators
ms.assetid: ac95023b-9e7d-49f5-861a-bf7a9a340746
ms.openlocfilehash: cb1b0e0d1466d4af5ba255bdf3d00b11cd921fd6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457541"
---
# <a name="allocators"></a>アロケーター

アロケーターは、C++ 標準ライブラリでコンテナーに格納された要素の割り当ておよび解放を処理するために使用されます。 std::array を除くすべての C++ 標準ライブラリのコンテナーは、`allocator<Type>` 型のテンプレート パラメーターを持ちます。この `Type` はコンテナー要素の型を表しています。 たとえば、vector クラスは次のように宣言されます。

```cpp
template <
    class Type,
    class Allocator = allocator<Type>
>
class vector
```

C++ 標準ライブラリでは、アロケーターの既定の実装が提供されます。 C++11 以降では、既定のアロケーターがより小さなインターフェイスを公開するように更新されています。この新しいアロケーターは、*最小アロケーター*と呼ばれています。 特に、最小アロケーターの `construct()` メンバーは、パフォーマンスを大幅に改善できる移動セマンティクスをサポートしています。 ほとんどの場合、この既定のアロケーターがあれば十分です。 C++11 では、`std::function`、`shared_ptr, allocate_shared()`、`basic_string` など、すべての標準ライブラリの型、およびアロケーター型のパラメーターを受け取る関数が、最小アロケーターをサポートしています。  既定のアロケーターの詳細については、「[allocator クラス](../standard-library/allocator-class.md)」を参照してください。

## <a name="writing-your-own-allocator-c11"></a>独自のアロケーターの記述 (C++ 11)

既定のアロケーターは、 **new**と**delete**を使用してメモリの割り当てと割り当て解除を行います。 メモリの割り当てに、共有メモリなど、別の方法を使用する場合は、独自のアロケーターを作成する必要があります。 対象が C++ 11 で、かつ新しいカスタム アロケーターを作成する必要がある場合、可能であれば最小アロケーターを作成することをお勧めします。 既に旧式のアロケーターを実装している場合でも、自動的に提供される、より効率的な `construct()` メソッドを利用するため、それを*最小アロケーター*に変更することを検討してください。

最小アロケーターは、必要な定型句が大幅に少なくなっているため、すべての処理を担う `allocate` と `deallocate` メンバー関数に集中することができます。 最小アロケーターを作成する場合は、次の例に示すものを除き、いずれのメンバーも実装しないでください。

1. 変換コピー コンストラクター (例を参照)

1. operator==

1. operator!=

1. allocate

1. deallocate

提供される C++ 11 の既定の `construct()` メンバーは、完全転送を行い、移動セマンティクスを可能にします。多くの場合において旧バージョンよりはるかに効率的です。

> [!WARNING]
> コンパイル時には、C++ 標準ライブラリが allocator_traits を使用して明示的に指定されたメンバーを検出し、存在しないすべてのメンバーの既定の実装を提供します。 アロケーターに対して allocator_traits の特殊化を指定して、このメカニズムを妨げることがないように注意してください。

次の例に、`malloc` および `free` を使用するアロケーターの最小限の実装を示します。 新しい例外型である `std::bad_array_new_length` を使用している点に注目してください。配列のサイズが 0 未満か、または最大許容サイズより大きい場合に、これがスローされます。

```cpp
#pragma once
#include <stdlib.h> //size_t, malloc, free
#include <new> // bad_alloc, bad_array_new_length
#include <memory>
template <class T>
struct Mallocator
{
    typedef T value_type;
    Mallocator() noexcept {} //default ctor not required by C++ Standard Library

    // A converting copy constructor:
    template<class U> Mallocator(const Mallocator<U>&) noexcept {}
    template<class U> bool operator==(const Mallocator<U>&) const noexcept
    {
        return true;
    }
    template<class U> bool operator!=(const Mallocator<U>&) const noexcept
    {
        return false;
    }
    T* allocate(const size_t n) const;
    void deallocate(T* const p, size_t) const noexcept;
};

template <class T>
T* Mallocator<T>::allocate(const size_t n) const
{
    if (n == 0)
    {
        return nullptr;
    }
    if (n > static_cast<size_t>(-1) / sizeof(T))
    {
        throw std::bad_array_new_length();
    }
    void* const pv = malloc(n * sizeof(T));
    if (!pv) { throw std::bad_alloc(); }
    return static_cast<T*>(pv);
}

template<class T>
void Mallocator<T>::deallocate(T * const p, size_t) const noexcept
{
    free(p);
}
```

## <a name="writing-your-own-allocator-c03"></a>独自のアロケーターの記述 (C++ 03)

C++ 03 では、C++ 標準ライブラリのコンテナーで使用されるアロケーターは次の型定義を実装する必要があります。

|||
|-|-|
|`const_pointer`|`rebind`|
|`const_reference`|`reference`|
|`difference_type`|`size_type`|
|`pointer`|`value_type`|

さらに、C++ 標準ライブラリのコンテナーで使用されるアロケーターは次のメソッドを実装する必要があります。

|||
|-|-|
|コンストラクター|`deallocate`|
|コピー コンストラクター|`destroy`|
|デストラクターです。|`max_size`|
|`address`|`operator==`|
|`allocate`|`operator!=`|
|`construct`||

これらの型定義およびメソッドの詳細については、「[allocator クラス](../standard-library/allocator-class.md)」を参照してください。

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
