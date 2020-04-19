---
title: _com_error::Description
ms.date: 11/04/2016
f1_keywords:
- _com_error::Description
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
ms.openlocfilehash: a517c40e9adfbda2d790ce41a48ccf8658bcd3e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155112"
---
# <a name="comerrordescription"></a>_com_error::Description

**Microsoft 固有の仕様**

`IErrorInfo::GetDescription` 関数を呼び出します。

## <a name="syntax"></a>構文

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>戻り値

結果を返します`IErrorInfo::GetDescription`の`IErrorInfo`内オブジェクトに記録された、`_com_error`オブジェクト。 結果の `BSTR` は `_bstr_t` オブジェクトにカプセル化されます。 ない場合は`IErrorInfo`が記録されると、空を返します`_bstr_t`します。

## <a name="remarks"></a>Remarks

呼び出し、`IErrorInfo::GetDescription`関数を取得します`IErrorInfo`内に記録された、`_com_error`オブジェクト。 呼び出すときの失敗、`IErrorInfo::GetDescription`メソッドは無視されます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_error クラス](../cpp/com-error-class.md)