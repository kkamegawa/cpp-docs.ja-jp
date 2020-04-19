---
title: CInterfaceArray クラス
ms.date: 11/04/2016
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
ms.openlocfilehash: 2e8714bf40e99a1014d7cd6de82cddb13cbbb9cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258872"
---
# <a name="cinterfacearray-class"></a>CInterfaceArray クラス

このクラスは、COM インターフェイス ポインターの配列を構築するときに役立つメソッドを提供します。

## <a name="syntax"></a>構文

```
template <class I, const IID* piid=& __uuidof(I)>
class CInterfaceArray :
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```

#### <a name="parameters"></a>パラメーター

*I*<br/>
COM インターフェイスを格納するポインターの種類を指定します。

*piid*<br/>
ポインターの IID を*は*します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|インターフェイスの配列のコンス トラクター。|

## <a name="remarks"></a>Remarks

このクラスは、コンス トラクターおよび COM インターフェイス ポインターの配列を作成するための派生メソッドを提供します。 使用[CInterfaceList](../../atl/reference/cinterfacelist-class.md)一覧が必要な場合。

詳細については、次を参照してください。 [ATL コレクション クラス](../../atl/atl-collection-classes.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

`CAtlArray`

`CInterfaceArray`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="cinterfacearray"></a>  CInterfaceArray::CInterfaceArray

コンストラクターです。

```
CInterfaceArray() throw();
```

### <a name="remarks"></a>Remarks

スマート ポインターの配列を初期化します。

## <a name="see-also"></a>関連項目

[CAtlArray クラス](../../atl/reference/catlarray-class.md)<br/>
[CComQIPtr クラス](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits クラス](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
