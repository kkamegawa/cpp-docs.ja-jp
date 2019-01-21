---
title: CompareStringOrdinal メソッド
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
ms.openlocfilehash: c9dbbe8926036ea18210fb30928fafc40093092e
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336717"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal メソッド

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
inline INT32 CompareStringOrdinal(
   HSTRING lhs,
   HSTRING rhs)
```

### <a name="parameters"></a>パラメーター

*lhs*<br/>
比較する最初の HSTRING です。

*rhs*<br/>
比較する 2 つ目の HSTRING です。

## <a name="return-value"></a>戻り値

|[値]|条件|
|-----------|---------------|
|-1|*lhs*がより小さい*rhs*します。|
|0|*lhs* equals *rhs*します。|
|1|*lhs*がより大きい*rhs*します。|

## <a name="remarks"></a>Remarks

2 つの指定した HSTRING オブジェクトを比較し、並べ替え順序でそれらの相対位置を示す整数を返します。

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers.h

**名前空間:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>関連項目

[Microsoft::WRL::Wrappers::Details 名前空間](microsoft-wrl-wrappers-details-namespace.md)