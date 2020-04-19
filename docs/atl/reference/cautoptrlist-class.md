---
title: CAutoPtrList クラス
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
ms.openlocfilehash: 2558c522f7903e8d59363cd77d1a86027f6a7511
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260280"
---
# <a name="cautoptrlist-class"></a>CAutoPtrList クラス

このクラスは、スマート ポインターのリストを構築するときに役立つメソッドを提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<typename E>
class CAutoPtrList :
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>パラメーター

*E*<br/>
ポインター型。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|コンストラクターです。|

## <a name="remarks"></a>Remarks

このクラスは、コンス トラクターを提供し、メソッドからの派生[CAtlList](../../atl/reference/catllist-class.md)と[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)スマート ポインターを格納するリスト オブジェクトの作成を支援します。 クラスは、 [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) array オブジェクトと同様の機能を提供します。

詳細については、次を参照してください。 [ATL コレクション クラス](../../atl/atl-collection-classes.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CAtlList](../../atl/reference/catllist-class.md)

`CAutoPtrList`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="cautoptrlist"></a>  CAutoPtrList::CAutoPtrList

コンストラクターです。

```
CAutoPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>パラメーター

*nBlockSize*<br/>
既定値は 10 でのブロック サイズ。

### <a name="remarks"></a>Remarks

ブロック サイズは、新しい要素が必要なときに割り当てられたメモリ量の測定です。 ブロック サイズの増加はメモリ割り当てルーチンの呼び出しを減らすためがより多くのリソースを使用します。

## <a name="see-also"></a>関連項目

[CAtlList クラス](../../atl/reference/catllist-class.md)<br/>
[CAutoPtrElementTraits クラス](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
