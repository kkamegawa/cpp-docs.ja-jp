---
title: ArgTraitsHelper 構造体
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
- event/Microsoft::WRL::Details::ArgTraitsHelper::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraitsHelper structure
- Microsoft::WRL::Details::ArgTraitsHelper::args constant
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
ms.openlocfilehash: fbba6d96106cc95910ccd9d0029cb3e9c254d7d3
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337358"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper 構造体

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template<typename TDelegateInterface>
struct ArgTraitsHelper;
```

### <a name="parameters"></a>パラメーター

*TDelegateInterface*<br/>
デリゲートのインターフェイスです。

## <a name="remarks"></a>Remarks

定義のデリゲート引数の一般的な特性に役立ちます。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

名前         | 説明
------------ | ------------------------------------------------------
`methodType` | `decltype(&TDelegateInterface::Invoke)` と同義。
`Traits`     | `ArgTraits<methodType>` と同義。

### <a name="public-constants"></a>パブリック定数

名前                           | 説明
------------------------------ | ---------------------------------------------------------------------------------------------------------------------
[Argtraitshelper::args](#args) | により、 [argtraits::args](#args)パラメーターの数のカウントを保持、`Invoke`デリゲート インターフェイスのメソッド。

## <a name="inheritance-hierarchy"></a>継承階層

`ArgTraitsHelper`

## <a name="requirements"></a>必要条件

**ヘッダー:** event.h

**名前空間:** Microsoft::WRL::Details

## <a name="args"></a>Argtraitshelper::args

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
static const int args = Traits::args;
```

### <a name="remarks"></a>Remarks

により、`ArgTraitsHelper::args`パラメーターの数のカウントを保持、`Invoke`デリゲート インターフェイスのメソッド。
