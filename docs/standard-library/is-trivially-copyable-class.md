---
title: is_trivially_copyable クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copyable
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
ms.openlocfilehash: d3062ae311b63be76ba07185f4f8173afa4229cc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459749"
---
# <a name="istriviallycopyable-class"></a>is_trivially_copyable クラス

型が自明にコピー可能な型であるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct is_trivially_copyable;
```

### <a name="parameters"></a>パラメーター

*\T*\
照会する型。

## <a name="remarks"></a>Remarks

型*T*が普通にコピー可能な型である場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。 自明にコピー可能な型とは、自明でないコピー操作、移動操作、デストラクターが含まれない型のことです。 通常、ビット単位のコピーとして実装可能なコピー操作は自明であるとみなされます。 組み込みの型と自明にコピー可能な型の配列は、両方とも自明にコピー可能です。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
