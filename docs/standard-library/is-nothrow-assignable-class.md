---
title: is_nothrow_assignable クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_assignable
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
ms.openlocfilehash: 9ee8b5f97c92b6eb378db40f93696e5e6c554205
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456021"
---
# <a name="isnothrowassignable-class"></a>is_nothrow_assignable クラス

型*の値*を型*に*割り当てることができるかどうかをテストし、割り当てがスローしないことがわかっていることを確認します。

## <a name="syntax"></a>構文

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>パラメーター

*宛先*\
代入を受け取るオブジェクトの型。

*差出人*\
値を渡すオブジェクトの型。

## <a name="remarks"></a>Remarks

式 `declval<To>() = declval<From>()` は正しい形式である必要があり、スローしないことがコンパイラに判明している必要があります。 と*の*両方で、完全な型、 **void**、または不明なバインドの配列を指定する必要があります。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
