---
title: default_delete 構造体
ms.date: 04/04/2019
f1_keywords:
- memory/std::default_delete
helpviewer_keywords:
- default_delete struct
ms.openlocfilehash: e9e1fcc68539e55486f4ea27e6dd5c49bed11fdf
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269264"
---
# <a name="defaultdelete-struct"></a>default_delete 構造体

引数に対して除算演算 (`operator/`) を実行する定義済みの関数オブジェクト。

## <a name="syntax"></a>構文

```cpp
template <class T>
    struct default_delete
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<memory>

**名前空間:** std

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[default_delete](#default_delete)|`default_delete` 型のオブジェクトのコンストラクター。|

### <a name="operators"></a>演算子

|||
|-|-|
|[演算子 ()](#op_paren)|アクセスするリファレンス演算子`default_delete`します。|

## <a name="default_delete"></a> default_delete

`default_delete` 型のオブジェクトのコンストラクター。

```cpp
constexpr default_delete() noexcept = default;
template <class U>
    default_delete(const default_delete<U>&) noexcept;
```

## <a name="op_paren"></a> operator()

アクセスするリファレンス演算子`default_delete`します。

```cpp
void operator()(T*) const;
```

## <a name="see-also"></a>関連項目

[\<memory>](../standard-library/memory.md)
