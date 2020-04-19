---
title: '&lt;allocators&gt; マクロ'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::ALLOCATOR_DECL
- allocators/std::CACHE_CHUNKLIST
- allocators/std::CACHE_FREELIST
- allocators/std::CACHE_SUBALLOC
- allocators/std::SYNC_DEFAULT
ms.assetid: 9cb5ee07-1ff9-4594-ae32-3c8c6efb511a
helpviewer_keywords:
- std::ALLOCATOR_DECL [C++]
- std::CACHE_CHUNKLIST [C++]
- std::CACHE_FREELIST [C++]
- std::CACHE_SUBALLOC [C++]
- std::SYNC_DEFAULT [C++]
ms.openlocfilehash: 5355661e370daf8826541c036f7301e5c25788d7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72690054"
---
# <a name="ltallocatorsgt-macros"></a>&lt;allocators&gt; マクロ

||||
|-|-|-|
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|

## <a name="allocator_decl"></a>  ALLOCATOR_DECL

アロケータークラステンプレートを生成します。

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>Remarks

マクロを使用すると、テンプレート定義 `template <class Type> class name {.....}` および特殊化 `template <> class name<void> {.....}` が生成されます。これにより、同期フィルター `sync` と、`cache` 型のキャッシュを使用するアロケータークラステンプレートが定義されます。

再バインドをコンパイルできるコンパイラの場合、作成されるテンプレート定義は次のようになります。

```cpp
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };
```

再バインドをコンパイルできないコンパイラの場合、作成されるテンプレート定義は次のようになります。

```cpp
template <class Type<class name
    : public stdext::allocators::allocator_base<Type,
    sync<stdext::allocators::rts_alloc<cache>>>
{
public:
    name() {}
    template <class Other>
    name(const name<Other>&) {}
    template <class Other>
    name& operator= (const name<Other>&)
    {
        return *this;
    }
};
```

## <a name="cache_chunklist"></a>  CACHE_CHUNKLIST

`stdext::allocators::cache_chunklist<sizeof(Type)>` を生成します。

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>Remarks

## <a name="cache_freelist"></a>  CACHE_FREELIST

`stdext::allocators::cache_freelist<sizeof(Type), max>` を生成します。

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>Remarks

## <a name="cache_suballoc"></a>  CACHE_SUBALLOC

`stdext::allocators::cache_suballoc<sizeof(Type)>` を生成します。

```cpp
#define CACHE_SUBALLOC <cache_class>
```

### <a name="remarks"></a>Remarks

## <a name="sync_default"></a>  SYNC_DEFAULT

同期フィルターを生成します。

```cpp
#define SYNC_DEFAULT <sync_template>
```

### <a name="remarks"></a>Remarks

コンパイラがシングル スレッド アプリケーションとマルチ スレッド アプリケーションの両方のコンパイルをサポートしている場合、マクロはシングル スレッド アプリケーションには `stdext::allocators::sync_none` を生成し、それ以外の場合は `stdext::allocators::sync_shared` を生成します。

## <a name="see-also"></a>関連項目

[\<allocators>](../standard-library/allocators-header.md)
