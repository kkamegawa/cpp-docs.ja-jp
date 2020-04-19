---
title: is_final クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_final
helpviewer_keywords:
- is_final
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
ms.openlocfilehash: 14efbeb33193cc674c6e766b880e89d9b76d140a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452652"
---
# <a name="isfinal-class"></a>is_final クラス

型が `final` でマークされたクラス型であるかどうかをテストします。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct is_final;
```

### <a name="parameters"></a>パラメーター

*\T*\
照会する型。

## <a name="remarks"></a>Remarks

型*T*がとマーク`final`されたクラス型である場合、型述語のインスタンスは true を保持します。それ以外の場合は、false を保持します。 *T*がクラス型の場合は、完全な型である必要があります。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)\
[final 指定子](../cpp/final-specifier.md)
