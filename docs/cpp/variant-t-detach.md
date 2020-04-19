---
title: _variant_t::Detach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
ms.openlocfilehash: 8426c80af04b2c0906af150ea3e91304335e9f69
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500558"
---
# <a name="_variant_tdetach"></a>_variant_t::Detach

**Microsoft 固有の仕様**

`VARIANT` この`_variant_t`オブジェクトからカプセル化されたオブジェクトをデタッチします。

## <a name="syntax"></a>構文

```
VARIANT Detach( );
```

## <a name="return-value"></a>戻り値

カプセル化`VARIANT`された。

## <a name="remarks"></a>Remarks

カプセル化`VARIANT`されたを抽出して`_variant_t`返した後、このオブジェクトを破棄せずにクリアします。 このメンバー関数は、 `VARIANT`をカプセル化から削除`VARTYPE`し、 `_variant_t`このオブジェクトのを VT_EMPTY に設定します。 [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) 関数を呼び出すことによって`VARIANT`返されたを解放します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_variant_t クラス](../cpp/variant-t-class.md)