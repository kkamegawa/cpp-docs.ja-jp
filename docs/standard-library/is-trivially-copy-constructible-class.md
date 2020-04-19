---
title: is_trivially_copy_constructible クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
ms.openlocfilehash: f8c4026da424e77b57555dd4c342c9ac7a386591
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447986"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible クラス

型に自明なコピー コンストラクターが含まれるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>パラメーター

*\T*\
照会する型。

## <a name="remarks"></a>Remarks

型*T*が自明なコピーコンストラクターを持つクラスである場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。

クラス*t*のコピーコンストラクターは、暗黙的に宣言されている場合は単純です *。クラス t*には仮想関数も仮想基底もありません。クラス*t*のすべての直接基底に自明なコピーコンストラクター、すべての非静的データメンバーのクラスが含まれます。クラス型のに自明なコピーコンストラクターがあり、クラスの型配列のすべての非静的データメンバーのクラスに自明なコピーコンストラクターが含まれています。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
