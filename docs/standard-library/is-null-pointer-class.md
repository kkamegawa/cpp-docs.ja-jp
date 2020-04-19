---
title: is_null_pointer クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_null_pointer
helpviewer_keywords:
- is_null_pointer
ms.assetid: f3b3601b-f162-4803-a6e9-dabf5c3876cc
ms.openlocfilehash: b306753146a51bde842b55e4f36d3c1afa82591d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455845"
---
# <a name="isnullpointer-class"></a>is_null_pointer クラス

型が std::nullptr_t であるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct is_null_pointer;
```

### <a name="parameters"></a>パラメーター

*\T*\
照会する型。

## <a name="remarks"></a>Remarks

型が`std::nullptr_t` *T*の場合、型の述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
