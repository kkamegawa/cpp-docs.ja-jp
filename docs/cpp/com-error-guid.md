---
title: _com_error::GUID
ms.date: 11/04/2016
f1_keywords:
- _com_error::GUID
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
ms.openlocfilehash: 905b67577a65b81be0b4d18c7513652dd8c5f055
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155060"
---
# <a name="comerrorguid"></a>_com_error::GUID

**Microsoft 固有の仕様**

`IErrorInfo::GetGUID` 関数を呼び出します。

## <a name="syntax"></a>構文

```
GUID GUID( ) const throw( );
```

## <a name="return-value"></a>戻り値

結果を返します`IErrorInfo::GetGUID`の`IErrorInfo`内オブジェクトに記録された、`_com_error`オブジェクト。 ない場合は`IErrorInfo`返しますオブジェクトが記録されて、`GUID_NULL`します。

## <a name="remarks"></a>Remarks

呼び出すときの失敗、`IErrorInfo::GetGUID`メソッドは無視されます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_error クラス](../cpp/com-error-class.md)