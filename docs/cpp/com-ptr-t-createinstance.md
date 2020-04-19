---
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: 82b180b3f40683495ed2cfa284bdae8e1afaef9e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498662"
---
# <a name="_com_ptr_tcreateinstance"></a>_com_ptr_t::CreateInstance

**Microsoft 固有の仕様**

または`CLSID` `ProgID`を指定して、オブジェクトの新しいインスタンスを作成します。

## <a name="syntax"></a>構文

```
HRESULT CreateInstance(
   const CLSID& rclsid,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCWSTR clsidString,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCSTR clsidStringA,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
```

#### <a name="parameters"></a>パラメーター

*rclsid*<br/>
オブジェクト`CLSID`の。

*clsidString*<br/>
`CLSID` (" **{** `ProgID`" で始まる) またはを保持する Unicode 文字列。

*clsidStringA*<br/>
`CLSID` (" **{** `ProgID`" で始まる) またはを保持する、ANSI コードページを使用するマルチバイト文字列。

*dwClsContext*<br/>
実行可能コードを実行するコンテキスト。

*pOuter*<br/>
[集計](../atl/aggregation.md)の不明な外部。

## <a name="remarks"></a>Remarks

これらのメンバー関数は、`CoCreateInstance` を呼び出して新しい COM オブジェクトを作成し、このスマート ポインターのインターフェイス型を照会します。 結果のポインターは、この `_com_ptr_t` オブジェクトの中にカプセル化されます。 `Release`は、以前にカプセル化されたポインターの参照カウントをデクリメントするために呼び出されます。 このルーチンは、成功または失敗を示す HRESULT を返します。

- **CreateInstance (** *rclsid* **、** *dwClsContext* **)** を指定したオブジェクトの実行中の新しいインスタンスを作成します`CLSID`。

- **CreateInstance (** *clsidString* **、** *dwClsContext* **)** 指定したオブジェクトの実行中の新しいインスタンスを作成します。保持する Unicode 文字列、 `CLSID` (以降では" **{** ") または`ProgID`します。

- **CreateInstance (** *clsidStringA* **、** *dwClsContext* **)** 指定したオブジェクトの実行中の新しいインスタンスを作成します。いずれかを保持するマルチバイト文字の文字列を`CLSID`(以降では" **{** ") または`ProgID`します。 [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)を呼び出します。これは、文字列が OEM コードページではなく ANSI コードページに含まれていることを前提としています。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_ptr_t クラス](../cpp/com-ptr-t-class.md)