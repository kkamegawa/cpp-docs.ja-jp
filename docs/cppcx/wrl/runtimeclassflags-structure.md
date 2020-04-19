---
title: RuntimeClassFlags 構造体
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
ms.openlocfilehash: 4cbd3f367bc57c2eedf672422a458b67b1908fc0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403153"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags 構造体

インスタンスの型が含まれています、 [RuntimeClass](runtimeclass-class.md)します。

## <a name="syntax"></a>構文

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>パラメーター

*flags*<br/>
A [RuntimeClassType 列挙型](runtimeclasstype-enumeration.md)値。

## <a name="members"></a>メンバー

### <a name="public-constants"></a>パブリック定数

|名前|説明|
|----------|-----------------|
|[RuntimeClassFlags::value 定数](#value-constant)|含まれています、 [RuntimeClassType 列挙型](runtimeclasstype-enumeration.md)値。|

## <a name="inheritance-hierarchy"></a>継承階層

`RuntimeClassFlags`

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::wrl

## <a name="value-constant"></a>Runtimeclassflags::value 定数

含むフィールドを[RuntimeClassType 列挙型](runtimeclasstype-enumeration.md)値。

```cpp
static const unsigned int value = flags;
```
