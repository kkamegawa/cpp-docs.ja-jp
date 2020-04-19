---
title: _com_error::operator =
ms.date: 11/04/2016
f1_keywords:
- _com_error::operator=
helpviewer_keywords:
- _com_error [C++]
ms.assetid: b9cc4094-d055-450c-b45a-0a95317488f8
ms.openlocfilehash: 1c68d10c8f82f5d5ed7f6286ba15437941c0ac6b
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222496"
---
# <a name="comerroroperator-"></a>_com_error::operator =

**Microsoft 固有の仕様**

既存の `_com_error` オブジェクトを別のオブジェクトに割り当てます。

## <a name="syntax"></a>構文

```
_com_error& operator = (
   const _com_error& that
) throw ( );
```

#### <a name="parameters"></a>パラメーター

*それ*<br/>
`_com_error` オブジェクト。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_error クラス](../cpp/com-error-class.md)