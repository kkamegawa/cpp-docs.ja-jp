---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 13ddf57e0bdbdbcc0c5b487e879e14b000de3ad0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393936"
---
# <a name="_bstr_tcopy"></a>_bstr_t::copy

**Microsoft 固有の仕様**

カプセル化された `BSTR` のコピーを生成します。

## <a name="syntax"></a>構文

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>パラメーター

*fCopy*<br/>
TRUE の場合、**copy**格納されているのコピーを返します`BSTR`それ以外の場合、**copy**実際の BSTR を返します。

## <a name="remarks"></a>Remarks

カプセル化された `BSTR` オブジェクトの新しく割り当てられたコピーを返します。

## <a name="example"></a>例

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_bstr_t クラス](../cpp/bstr-t-class.md)