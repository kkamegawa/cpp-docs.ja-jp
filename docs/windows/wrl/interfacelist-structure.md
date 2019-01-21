---
title: InterfaceList 構造体
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: 70565081338f953abb65d2cdc7c5f1eb869f75e5
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337438"
---
# <a name="interfacelist-structure"></a>InterfaceList 構造体

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
インターフェイス名。再帰的なリストの先頭のインターフェイス。

*U*<br/>
インターフェイス名。再帰的なリストの残りのインターフェイスです。

## <a name="remarks"></a>Remarks

インターフェイスの再帰的な一覧を作成するために使用します。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|`FirstT`|テンプレート パラメーターのシノニム*T*します。|
|`RestT`|テンプレート パラメーターのシノニム*U*します。|

## <a name="inheritance-hierarchy"></a>継承階層

`InterfaceList`

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::WRL::Details

## <a name="see-also"></a>関連項目

[Microsoft::WRL::Details 名前空間](microsoft-wrl-details-namespace.md)