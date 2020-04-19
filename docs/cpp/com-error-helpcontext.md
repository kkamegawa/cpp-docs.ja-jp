---
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: a421a7fd7fa0817c74dac66946e28928b2ad82dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155086"
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext

**Microsoft 固有の仕様**

`IErrorInfo::GetHelpContext` 関数を呼び出します。

## <a name="syntax"></a>構文

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>戻り値

結果を返します`IErrorInfo::GetHelpContext`の`IErrorInfo`内オブジェクトに記録された、`_com_error`オブジェクト。 ない場合は`IErrorInfo`オブジェクトが記録されますが、0 を返します。

## <a name="remarks"></a>Remarks

呼び出すときの失敗、`IErrorInfo::GetHelpContext`メソッドは無視されます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_error クラス](../cpp/com-error-class.md)