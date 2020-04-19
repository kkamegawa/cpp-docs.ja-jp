---
title: _variant_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
ms.openlocfilehash: 510267c7ab00fe22a93dc01342def5fc262ddb04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166219"
---
# <a name="varianttattach"></a>_variant_t::Attach

**Microsoft 固有の仕様**

アタッチを`VARIANT`オブジェクトを **_variant_t**オブジェクト。

## <a name="syntax"></a>構文

```
void Attach(VARIANT& varSrc);
```

#### <a name="parameters"></a>パラメーター

*varSrc*<br/>
A`VARIANT`オブジェクトにアタッチされる **_variant_t**オブジェクト。

## <a name="remarks"></a>Remarks

所有権を取得、`VARIANT`によってカプセル化しています。 このメンバー関数は、既存のカプセル化を解放`VARIANT`をコピーし、指定された`VARIANT`、設定とその`VARTYPE`VT_EMPTY を確認するにそのリソースのみ解放できますが、 **_variant_t**デストラクターです。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_variant_t クラス](../cpp/variant-t-class.md)