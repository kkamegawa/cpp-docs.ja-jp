---
title: デバイスコンテキストのグローバル関数
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
ms.openlocfilehash: d225bd0cd996fd908479b5a93aad81ea0428900b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496101"
---
# <a name="device-context-global-functions"></a>デバイスコンテキストのグローバル関数

この関数は、特定のデバイスのデバイスコンテキストを作成します。

|||
|-|-|
|[AtlCreateTargetDC](#atlcreatetargetdc)|デバイスコンテキストを作成します。|

##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC

[DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)構造体で指定されたデバイスのデバイスコンテキストを作成します。

```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```

### <a name="parameters"></a>パラメーター

*hdc*<br/>
からデバイスコンテキストの既存のハンドル、または NULL。

*ptd*<br/>
からターゲットデバイスに関する`DVTARGETDEVICE`情報を格納している構造体へのポインター。

### <a name="return-value"></a>戻り値

で指定されたデバイスのデバイスコンテキストを示すハンドルを`DVTARGETDEVICE`返します。 デバイスが指定されていない場合は、既定の表示デバイスへのハンドルを返します。

### <a name="remarks"></a>Remarks

構造体が NULL で、 *hdc*が null の場合、は既定の表示デバイスのデバイスコンテキストを作成します。

*Hdc*が null でなく、 *ptd*が null の場合、関数は既存の*hdc*を返します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

## <a name="see-also"></a>関連項目

[関数](../../atl/reference/atl-functions.md)
