---
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: d89503e822d92bf6a1fcb2b6bb658d532af32c5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155047"
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode

**Microsoft 固有の仕様**

16 ビットに 32 ビットの HRESULT をマップ`wCode`します。

## <a name="syntax"></a>構文

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>パラメーター

*hr*<br/>
16 ビットにマップする 32 ビット HRESULT`wCode`します。

## <a name="return-value"></a>戻り値

16 ビット`wCode`32 ビット HRESULT からマップされます。

## <a name="remarks"></a>Remarks

参照してください[_com_error::wcode](../cpp/com-error-wcode.md)詳細についてはします。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error クラス](../cpp/com-error-class.md)