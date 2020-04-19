---
title: is_nothrow_default_constructible クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_default_constructible
helpviewer_keywords:
- is_nothrow_default_constructible
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
ms.openlocfilehash: 76b58800a454f42f6b5b6fcea23df161c37564b2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455930"
---
# <a name="isnothrowdefaultconstructible-class"></a>is_nothrow_default_constructible クラス

スローしない既定コンストラクターが型に存在するかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct is_nothrow_default_constructible;
```

### <a name="parameters"></a>パラメーター

*~* \
照会する型。

## <a name="remarks"></a>Remarks

型が nothrow の既定のコンストラクター*を持つ場合*、型の述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。 型述語のインスタンスは `is_nothrow_constructible<Ty>` と同じです。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
