---
title: EnableIf 構造体
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::EnableIf
helpviewer_keywords:
- EnableIf structure
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
ms.openlocfilehash: daaba919acaa35615af56831f9458831c3d35427
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398525"
---
# <a name="enableif-structure"></a>EnableIf 構造体

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template <bool b, typename T = void>
struct EnableIf;

template <typename T>
struct EnableIf<true, T>;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
型。

*b*<br/>
ブール式。

## <a name="remarks"></a>Remarks

最初のテンプレート パラメーターが評価された場合は、2 番目のテンプレート パラメーターで指定された型のデータ メンバーを定義**true**します。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|`type`|場合テンプレート パラメーター *b*に評価される**true**、部分的特殊化は、データ メンバーを定義します。`type`型`T`します。|

## <a name="inheritance-hierarchy"></a>継承階層

`EnableIf`

## <a name="requirements"></a>必要条件

**ヘッダー:** internal.h

**名前空間:** Microsoft::WRL::Details

## <a name="see-also"></a>関連項目

[Microsoft::WRL::Details 名前空間](microsoft-wrl-details-namespace.md)