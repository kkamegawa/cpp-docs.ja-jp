---
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: f2fc84be53d95754d21c30eaea8dd981447453d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154930"
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Microsoft 固有の仕様**

16 ビット マップ*wCode* HRESULT の 32 ビットにします。

## <a name="syntax"></a>構文

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>パラメーター

*WCode*<br/>
16 ビット*wCode* HRESULT の 32 ビットにマップします。

## <a name="return-value"></a>戻り値

16 ビットからマップされた 32 ビット HRESULT *wCode*します。

## <a name="remarks"></a>Remarks

参照してください、 [WCode](../cpp/com-error-wcode.md)メンバー関数。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error クラス](../cpp/com-error-class.md)