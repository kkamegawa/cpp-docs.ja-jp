---
title: is_error_condition_enum クラス
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_condition_enum
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
ms.openlocfilehash: c40f8f6eb93a33098cfbcf8133f08c56285abb43
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452604"
---
# <a name="iserrorconditionenum-class"></a>is_error_condition_enum クラス

[error_condition](../standard-library/error-condition-class.md) をテストする型述語を表します。

## <a name="syntax"></a>構文

```cpp
template <_Enum>
    class is_error_condition_enum;
```

## <a name="remarks"></a>Remarks

型 `_Enum` が型 `error_condition` のオブジェクトを格納するのに適した列挙型の値である場合、この[型述語](../standard-library/type-traits.md)のインスタンスは true を保持します。

ユーザー定義型のこの型に特殊化を追加できます。

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
