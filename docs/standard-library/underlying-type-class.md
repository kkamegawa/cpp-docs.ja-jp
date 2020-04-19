---
title: underlying_type クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: ea4768d78047112a7584ca49b0e4487fad55a970
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688842"
---
# <a name="underlying_type-class"></a>underlying_type クラス

列挙型の基になる整数型を生成します。

## <a name="syntax"></a>構文

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>パラメーター

*T* \
変更する型。

## <a name="remarks"></a>Remarks

クラステンプレートの `type` メンバー typedef は、 *t*が列挙型である場合*に、基*になる整数型の名前を指定します。それ以外の場合は、`type` メンバー typedef は存在しません。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
