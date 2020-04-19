---
title: is_trivially_copy_assignable クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
ms.openlocfilehash: c0019257a032d3becc268513336ed59e58a2e1d5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447994"
---
# <a name="istriviallycopyassignable-class"></a>is_trivially_copy_assignable クラス

型が自明なコピー代入演算子を持つかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>パラメーター

*\T*\
照会する型。

## <a name="remarks"></a>Remarks

型*T*が自明なコピー代入演算子を持つクラスである場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。

クラス*t*の割り当てコンストラクターは、暗黙的に指定されている場合 *、クラス t*に仮想関数がない場合、クラス*t*に仮想基底クラスがない場合、クラス型のすべての非静的データメンバーのクラスに自明な代入が含まれます。演算子、およびクラスの型配列のすべての非静的データメンバーのクラスに自明な代入演算子があります。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
