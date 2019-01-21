---
title: BoolStruct 構造体
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
- internal/Microsoft::WRL::Details::BoolStruct::Member
helpviewer_keywords:
- Microsoft::WRL::Details::BoolStruct structure
- Microsoft::WRL::Details::BoolStruct::Member data member
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
ms.openlocfilehash: cdec425e317585abbd9730447e2c4fbb19b8250a
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336725"
---
# <a name="boolstruct-structure"></a>BoolStruct 構造体

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Remarks

`BoolStruct`構造体を定義するかどうかを`ComPtr`インターフェイスのオブジェクトの有効期間を管理します。 `BoolStruct` 内部で使用される、 [BoolType()](comptr-class.md#operator-microsoft-wrl-details-booltype)演算子。

## <a name="members"></a>メンバー

### <a name="public-data-members"></a>パブリック データ メンバー

名前                          | 説明
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[Boolstruct::member](#member) | 指定します、 [ComPtr](comptr-class.md)またはインターフェイスのオブジェクトの有効期間の管理ではないです。

## <a name="inheritance-hierarchy"></a>継承階層

`BoolStruct`

## <a name="requirements"></a>必要条件

**ヘッダー:** internal.h

**名前空間:** Microsoft::WRL::Details

## <a name="member"></a>Boolstruct::member

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
int Member;
```

### <a name="remarks"></a>Remarks

指定します、 [ComPtr](comptr-class.md)またはインターフェイスのオブジェクトの有効期間の管理ではないです。
