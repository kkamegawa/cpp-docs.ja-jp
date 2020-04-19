---
title: オブジェクトの状態マクロ
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
ms.openlocfilehash: dc50825d6b6e74dc263a097e86d8ea0d42989825
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495314"
---
# <a name="object-status-macros"></a>オブジェクトの状態マクロ

このマクロは、ActiveX コントロールに属するフラグを設定します。

|||
|-|-|
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|OLEMISC フラグを設定するために ATL ActiveX コントロールで使用されます。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS

OLEMISC フラグを設定するために ATL ActiveX コントロールで使用されます。

```
DECLARE_OLEMISC_STATUS( miscstatus )
```

### <a name="parameters"></a>パラメーター

*間違った状態*<br/>
すべての該当する OLEMISC フラグ。

### <a name="remarks"></a>Remarks

このマクロは、ActiveX コントロールの OLEMISC フラグを設定するために使用されます。 詳細については、 [IOleObject:: Get誤 Cstatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus)を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]

## <a name="see-also"></a>関連項目

[[マクロ]](../../atl/reference/atl-macros.md)
