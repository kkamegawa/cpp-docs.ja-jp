---
title: _variant_t::ChangeType
ms.date: 11/04/2016
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
ms.openlocfilehash: 319c4fde808932e86021ee59b051261c43ca2edd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166205"
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType

**Microsoft 固有の仕様**

型を変更、`_variant_t`オブジェクトを指定された`VARTYPE`します。

## <a name="syntax"></a>構文

```
void ChangeType(
   VARTYPE vartype,
   const _variant_t* pSrc = NULL
);
```

#### <a name="parameters"></a>パラメーター

*vartype*<br/>
`VARTYPE`この`_variant_t`オブジェクト。

*pSrc*<br/>
変換する `_variant_t` オブジェクトへのポインター。 この値が NULL の場合は、変換が適切に実行されます。

## <a name="remarks"></a>Remarks

このメンバー関数に変換する`_variant_t`オブジェクトを指定された`VARTYPE`します。 場合*pSrc*が NULL の場合、変換が行われる場所、それ以外の場合にこの`_variant_t`からオブジェクトをコピー *pSrc*変換と。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_variant_t クラス](../cpp/variant-t-class.md)