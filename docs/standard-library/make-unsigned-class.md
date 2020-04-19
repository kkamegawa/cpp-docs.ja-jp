---
title: make_unsigned クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_unsigned
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
ms.openlocfilehash: 4c0224bd5fd7dc8c6589ae474bb9acb9a8f09cf6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456324"
---
# <a name="makeunsigned-class"></a>make_unsigned クラス

サイズが型以上の型または最小の符号なしの型を作成します。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*T*|変更する型。|

## <a name="remarks"></a>Remarks

型修飾子のインスタンスは、が true を保持している場合`is_unsigned<T>`は T である修飾型を保持します。 それ以外の場合は、`sizeof (T) <= sizeof (ST)` である最小の符号付きの型 `ST` になります。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
