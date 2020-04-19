---
title: is_trivially_move_constructible クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_constructible
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
ms.openlocfilehash: 279da956eaff21c39c6e5ca563f26989105f7e74
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448358"
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible クラス

型に自明な移動コンストラクターが存在するかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>パラメーター

*~* \
照会する型。

## <a name="remarks"></a>Remarks

型*Ty*が自明な移動コンストラクターを持つクラスである場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。

クラス*Ty*の移動コンストラクターは、次のような場合に自明です。

暗黙的に宣言されている

そのパラメーターの型が暗黙的な宣言のものと同じである

クラス*Ty*に仮想関数がありません。

クラス*Ty*に仮想基底がありません

クラスに揮発性の非静的データ メンバーがない

*クラスの*すべての直接基底に自明な移動コンストラクターがある

クラス型のすべての非静的データ メンバーのクラスに自明な移動コンストラクターがある

クラスの型配列のすべての非静的データ メンバーのクラスに自明な移動コンストラクターがある

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
