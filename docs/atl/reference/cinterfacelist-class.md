---
title: CInterfaceList クラス
ms.date: 11/04/2016
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
ms.openlocfilehash: e740d891e279bb29eeef898de52698dc3f04fc67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258638"
---
# <a name="cinterfacelist-class"></a>CInterfaceList クラス

このクラスは、COM インターフェイス ポインターのリストを構築するときに役立つメソッドを提供します。

## <a name="syntax"></a>構文

```
template<class I, const IID* piid =& __uuidof(I)>
class CInterfaceList
   : public CAtlList<ATL::CComQIPtr<I, piid>,
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
|[CInterfaceList::CInterfaceList](#cinterfacelist)|インターフェイスの一覧のコンス トラクター。|

## <a name="remarks"></a>Remarks

このクラスは、コンス トラクターおよび COM インターフェイス ポインターのリストを作成するための派生メソッドを提供します。 使用[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)配列が必要な場合。

詳細については、次を参照してください。 [ATL コレクション クラス](../../atl/atl-collection-classes.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CAtlList](../../atl/reference/catllist-class.md)

`CInterfaceList`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="cinterfacelist"></a>  CInterfaceList::CInterfaceList

インターフェイスの一覧のコンス トラクター。

```
CInterfaceList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>パラメーター

*nBlockSize*<br/>
既定値は 10 でのブロック サイズ。

### <a name="remarks"></a>Remarks

ブロック サイズは、新しい要素が必要なときに割り当てられたメモリ量の測定です。 ブロック サイズの増加はメモリ割り当てルーチンの呼び出しを減らすためがより多くのリソースを使用します。

## <a name="see-also"></a>関連項目

[CAtlList クラス](../../atl/reference/catllist-class.md)<br/>
[CComQIPtr クラス](../../atl/reference/ccomqiptr-class.md)<br/>
[CComQIPtrElementTraits クラス](../../atl/reference/ccomqiptrelementtraits-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
