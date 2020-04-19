---
title: is_nothrow_constructible クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_constructible
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
ms.openlocfilehash: 7ec4fc3ef5d9a799d5d77124870fbb337061c94c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455992"
---
# <a name="isnothrowconstructible-class"></a>is_nothrow_constructible クラス

指定された引数型の使用時に型を構築できるかどうか、およびスローしないと判明しているかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>パラメーター

*\T*\
照会する型。

*Value*\
*T*のコンストラクターで一致する引数の型。

## <a name="remarks"></a>Remarks

型の述語のインスタンスは、型*T*が*引数の型*を引数として使用して構築可能であり、コンストラクターがコンパイラによってスローされない場合に true を保持します。それ以外の場合は、false を保持します。 型*T*は、変数定義`T t(std::declval<Args>()...);`が整形式である場合に構築可能です。 *T*と*Args*内のすべての型は、完全な型、 **void**、または不明なバインドの配列である必要があります。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
