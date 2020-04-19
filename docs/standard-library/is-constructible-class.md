---
title: is_constructible クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: dc0596ac7a3fc2bcbcbe49f5fa4b20a971e5e445
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452862"
---
# <a name="isconstructible-class"></a>is_constructible クラス

指定した引数型の使用時に型を構築できるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>パラメーター

*\T*\
照会する型。

*Value*\
*T*のコンストラクターで一致する引数の型。

## <a name="remarks"></a>Remarks

型の述語のインスタンスは、型*T*が引数の型を使用して構築可能である場合は*true を保持*し、それ以外の場合は false を保持します。 型*T*は、変数定義`T t(std::declval<Args>()...);`が整形式である場合に構築可能です。 *T*と*Args*内のすべての型は、完全な型、 **void**、または不明なバインドの配列である必要があります。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
