---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: 44fc9755cd69050ea82145636f01614258943794
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500589"
---
# <a name="_com_errorerrormessage"></a>_com_error::ErrorMessage

**Microsoft 固有の仕様**

`_com_error` オブジェクトに格納された HRESULT の文字列メッセージを取得します。

## <a name="syntax"></a>構文

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>戻り値

`_com_error`オブジェクト内に記録された HRESULT の文字列メッセージを返します。 HRESULT が、マップされた16ビット[wcode](../cpp/com-error-wcode.md)の場合は、一般的な`IDispatch error #<wCode>`メッセージ "" が返されます。 メッセージがない場合、一般的なメッセージ "`Unknown error #<hresult>`" が返されます。 返される文字列は、_UNICODE マクロの状態に応じて、Unicode またはマルチバイト文字列です。

## <a name="remarks"></a>Remarks

`_com_error`オブジェクト内に記録された HRESULT の適切なシステムメッセージテキストを取得します。 システムメッセージテキストは、Win32 [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage)関数を呼び出すことによって取得されます。 返される文字列は `FormatMessage` API によって割り当てられ、`_com_error` オブジェクトが破棄されるときに解放されます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_error クラス](../cpp/com-error-class.md)