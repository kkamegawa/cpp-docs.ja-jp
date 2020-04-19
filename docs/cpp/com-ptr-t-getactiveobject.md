---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: f13a42878392f63096cdfcb405f3f91cc0efe451
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498891"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Microsoft 固有の仕様**

または`CLSID` `ProgID`を指定して、オブジェクトの既存のインスタンスにアタッチします。

## <a name="syntax"></a>構文

```
HRESULT GetActiveObject(
   const CLSID& rclsid
) throw( );
HRESULT GetActiveObject(
   LPCWSTR clsidString
) throw( );
HRESULT GetActiveObject(
   LPCSTR clsidStringA
) throw( );
```

#### <a name="parameters"></a>パラメーター

*rclsid*<br/>
オブジェクト`CLSID`の。

*clsidString*<br/>
`CLSID` (" **{** `ProgID`" で始まる) またはを保持する Unicode 文字列。

*clsidStringA*<br/>
`CLSID` (" **{** `ProgID`" で始まる) またはを保持する、ANSI コードページを使用するマルチバイト文字列。

## <a name="remarks"></a>Remarks

これらのメンバー関数は、 **Getactiveobject**を呼び出して、OLE に登録されている実行中のオブジェクトへのポインターを取得し、このスマートポインターのインターフェイス型を照会します。 結果のポインターは、この `_com_ptr_t` オブジェクトの中にカプセル化されます。 `Release`は、以前にカプセル化されたポインターの参照カウントをデクリメントするために呼び出されます。 このルーチンは、成功または失敗を示す HRESULT を返します。

- **Getactiveobject (** `rclsid` **)** は、を`CLSID`指定したオブジェクトの既存のインスタンスにアタッチします。

- **Getactiveobject (** `clsidString` **)** は、 `CLSID` (" **{** " で`ProgID`始まる) またはのいずれかを保持する Unicode 文字列を指定して、オブジェクトの既存のインスタンスにアタッチします。

- **Getactiveobject (** `clsidStringA` **)** は、 `CLSID` (" **{** " で`ProgID`始まる) またはのいずれかを保持するマルチバイト文字列を指定して、オブジェクトの既存のインスタンスにアタッチします。 [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)を呼び出します。これは、文字列が OEM コードページではなく ANSI コードページに含まれていることを前提としています。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_ptr_t クラス](../cpp/com-ptr-t-class.md)