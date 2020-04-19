---
title: GetModuleBase 関数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 4d8c8467b7aeb9c21bf5f4ee19c60e6e60880688
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398395"
---
# <a name="getmodulebase-function"></a>GetModuleBase 関数

取得、 [ModuleBase](modulebase-class.md)の参照カウントをインクリメントおよびデクリメントするため、ポインター、 [RuntimeClass](runtimeclass-class.md)オブジェクト。

## <a name="syntax"></a>構文

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>戻り値

`ModuleBase` オブジェクトへのポインター。

## <a name="remarks"></a>Remarks

この関数は、インクリメントおよびデクリメントを内部的に使用されますオブジェクト参照をカウントします。

この関数を使用して、呼び出すことによって参照カウントを制御することができます[modulebase::incrementobjectcount](modulebase-class.md#incrementobjectcount)と[modulebase::decrementobjectcount](modulebase-class.md#decrementobjectcount)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::wrl

## <a name="see-also"></a>関連項目

[Microsoft::WRL 名前空間](microsoft-wrl-namespace.md)