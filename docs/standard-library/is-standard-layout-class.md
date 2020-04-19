---
title: is_standard_layout クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_standard_layout
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
ms.openlocfilehash: 4f999eaa4a5c1ea7e9672a5efdc6000a4d3d9759
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457408"
---
# <a name="isstandardlayout-class"></a>is_standard_layout クラス

型が標準レイアウト型であるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct is_standard_layout;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*Ty*|照会する型|

## <a name="remarks"></a>Remarks

型*Ty*がメモリ内にメンバーオブジェクトの標準レイアウトを持つクラスである場合、この型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
