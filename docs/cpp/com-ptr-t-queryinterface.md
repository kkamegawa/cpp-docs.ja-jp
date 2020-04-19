---
title: _com_ptr_t::QueryInterface
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::QueryInterface
- _com_ptr_t.QueryInterface
helpviewer_keywords:
- QueryInterface method [C++]
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
ms.openlocfilehash: 42953c92e4cf31b5ccd02dd51811fc1fdeedbcaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399279"
---
# <a name="comptrtqueryinterface"></a>_com_ptr_t::QueryInterface

**Microsoft 固有の仕様**

呼び出し、 **QueryInterface**のメンバー関数`IUnknown`カプセル化されたインターフェイス ポインター。

## <a name="syntax"></a>構文

```
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType*& p
) throw ( );
template<typename _InterfaceType> HRESULT QueryInterface (
   const IID& iid,
   _InterfaceType** p
) throw( );
```

#### <a name="parameters"></a>パラメーター

*iid*<br/>
`IID` インターフェイス ポインター。

*p*<br/>
生のインターフェイス ポインター。

## <a name="remarks"></a>Remarks

呼び出し`IUnknown::QueryInterface`指定してカプセル化されたインターフェイス ポインターで`IID`で、結果として得られる生のインターフェイス ポインターを返します*p*します。 このルーチンは、成功または失敗を示す HRESULT を返します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_ptr_t クラス](../cpp/com-ptr-t-class.md)