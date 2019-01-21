---
title: Microsoft::WRL::Wrappers::Details 名前空間
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details
- internal/Microsoft::WRL::Details
- async/Microsoft::WRL::Details
- corewrappers/Microsoft::WRL::Wrappers::Details
- client/Microsoft::WRL::Details
- module/Microsoft::WRL::Details
- event/Microsoft::WRL::Details
helpviewer_keywords:
- Details namespace
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
ms.openlocfilehash: d02b19863ffa14e0edb3b1a96dceb936037743d3
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336832"
---
# <a name="microsoftwrlwrappersdetails-namespace"></a>Microsoft::WRL::Wrappers::Details 名前空間

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
namespace Microsoft::WRL::Wrappers::Details;
```

## <a name="members"></a>メンバー

### <a name="classes"></a>クラス

|名前|説明|
|----------|-----------------|
|[SyncLockT クラス](synclockt-class.md)|排他的に使用できる型を表すか、リソースの所有権を共有します。|
|[SyncLockWithStatusT クラス](synclockwithstatust-class.md)|排他的に使用できる型を表すか、リソースの所有権を共有します。|

### <a name="methods"></a>メソッド

|名前|説明|
|----------|-----------------|
|[CompareStringOrdinal メソッド](comparestringordinal-method.md)|指定した 2 つ比較`HSTRING`オブジェクトし、並べ替え順序においてそれらの相対位置を示す整数を返します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers.h

**名前空間:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>関連項目

[Microsoft::WRL::Wrappers 名前空間](microsoft-wrl-wrappers-namespace.md)