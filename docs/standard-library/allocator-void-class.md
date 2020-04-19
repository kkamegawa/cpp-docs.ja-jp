---
title: allocator&lt;void&gt; クラス
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: c8d787fe03dfe6f67fb8e228308ec74b6e7f620a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688531"
---
# <a name="allocatorltvoidgt-class"></a>allocator&lt;void&gt; クラス

**Void**型へのクラステンプレートアロケーターの特殊化。このコンテキストで意味を持つ型を定義します。

## <a name="syntax"></a>構文

```cpp
template <>
class allocator<void> {
    typedef void *pointer;
    typedef const void *const_pointer;
    typedef void value_type;
    template <class Other>
    struct rebind;
    allocator();
    allocator(const allocator<void>&);

    template <class Other>
    allocator(const allocator<Other>&);

    template <class Other>
    allocator<void>& operator=(const allocator<Other>&);
};
```

## <a name="remarks"></a>Remarks

クラスは、 **void**型に対してクラステンプレート[アロケーター](../standard-library/allocator-class.md)を明示的に特殊化します。 コンストラクターと代入演算子は、クラステンプレートと同じように動作しますが、次の型のみを定義します。

- [const_pointer](../standard-library/allocator-class.md#const_pointer)

- [pointer](../standard-library/allocator-class.md#pointer)

- [value_type](../standard-library/allocator-class.md#value_type)

- 入れ子になったクラステンプレートを再[バインド](../standard-library/allocator-class.md#rebind)します。
