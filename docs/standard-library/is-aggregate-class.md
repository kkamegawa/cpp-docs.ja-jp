---
title: is_aggregate クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_aggregate
helpviewer_keywords:
- is_aggregate
ms.openlocfilehash: 89749e2b4c0e6aaf00de074718cfb598333bc739
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456702"
---
# <a name="isaggregate-class"></a>is_aggregate クラス

型が `aggregate` でマークされたクラス型であるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct is_aggregate;
```

### <a name="parameters"></a>パラメーター

*\T*\
照会する型。

## <a name="remarks"></a>Remarks

型*T*がとマーク`aggregate`されたクラス型である場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。 *T*がクラス型の場合は、完全な型である必要があります。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
