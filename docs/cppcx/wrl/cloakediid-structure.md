---
title: CloakedIid 構造体
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: 10dc2af1897147045382e8463b6602fa015fc899
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398720"
---
# <a name="cloakediid-structure"></a>CloakedIid 構造体

示します、 `RuntimeClass`、`Implements`と`ChainInterfaces`テンプレートの指定したインターフェイスが IID リストにアクセスできないことです。

## <a name="syntax"></a>構文

```cpp
template<typename T>
struct CloakedIid : T;
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
インターフェイスが非表示 (クロークされています)。

## <a name="remarks"></a>Remarks

方法の例を次に**CloakedIid**使用:`struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`します。

## <a name="inheritance-hierarchy"></a>継承階層

`T`

`CloakedIid`

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::wrl

## <a name="see-also"></a>関連項目

[Microsoft::WRL 名前空間](microsoft-wrl-namespace.md)