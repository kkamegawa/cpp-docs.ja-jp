---
title: '&lt;new&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 80123bc35422984ef92bdba6da45052d3461b1d7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245153"
---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt; typedefs

## <a name="hardware_constructive_interference_size"></a> hardware_constructive_interference_size

```cpp
inline constexpr size_t hardware_constructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Remarks

この数は、最大の同時実行スレッドがテンポラルの局所性とアクセスの 2 つのオブジェクトによって占有される連続したメモリのサイズをお勧めします。 ディレクトリを選択するには少なくとも`alignof(max_align_t)`します。

### <a name="example"></a>例

```cpp
struct together { 
    atomic<int> dog;
    int puppy;
};

struct kennel {
    // Other data members...
    alignas(sizeof(together)) together pack;
    // Other data members...
};

static_assert(sizeof(together) <= hardware_constructive_interference_size);
```

## <a name="hardware_destructive_interference_size"></a> hardware_destructive_interference_size

```cpp
inline constexpr size_t hardware_destructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Remarks

この数は、実装で導入された競合によって追加のパフォーマンスの低下を回避するために、2 つの同時にアクセスされるオブジェクト間の最小推奨されるオフセットです。 ディレクトリを選択するには少なくとも`alignof(max_align_t)`します。

### <a name="example"></a>例

```cpp
struct keep_apart {
    alignas(hardware_destructive_interference_size) atomic<int> cat;
    alignas(hardware_destructive_interference_size) atomic<int> dog;
};
```

## <a name="new_handler"></a> new_handler

新しいハンドラーとして使用するのに適した関数を指す型。

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Remarks

この種類のハンドラー関数を呼び出して**演算子 new**または`operator new[]`追加の記憶域の要求を満たすことができない場合。

### <a name="example"></a>例

`new_handler` を戻り値として使用する例については、「[set_new_handler](../standard-library/new-functions.md#set_new_handler)」をご覧ください。
