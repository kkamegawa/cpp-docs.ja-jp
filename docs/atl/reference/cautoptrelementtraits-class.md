---
title: CAutoPtrElementTraits クラス
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
ms.openlocfilehash: d217441048403b0ff5361f8049b76367174812f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246742"
---
# <a name="cautoptrelementtraits-class"></a>CAutoPtrElementTraits クラス

このクラスは、スマート ポインターのコレクションを作成するときに、メソッド、静的関数、および便利な typedef を提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<typename T>
class CAutoPtrElementTraits
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
ポインター型。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|コレクション クラスのオブジェクトに要素を追加するために使用するデータ型。|
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|コレクション クラスのオブジェクトから要素を取得するために使用するデータ型。|

## <a name="remarks"></a>Remarks

このクラスは、スマート ポインターを格納しているコレクション クラスのオブジェクトを作成するときに役立つ方法、静的関数、および typedef を提供します。 クラスは、 [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)と[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)から派生`CAutoPtrElementTraits`します。 使用して、スマート ポインターのコレクションを構築するには、ベクター型の new と delete 演算子が必要な場合[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)代わりにします。

## <a name="inheritance-hierarchy"></a>継承階層

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoPtrElementTraits`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="inargtype"></a>  CAutoPtrElementTraits::INARGTYPE

コレクション クラスのオブジェクトに要素を追加するために使用するデータ型。

```
typedef CAutoPtr<T>& INARGTYPE;
```

##  <a name="outargtype"></a>  CAutoPtrElementTraits::OUTARGTYPE

コレクション クラスのオブジェクトから要素を取得するために使用するデータ型。

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>関連項目

[CDefaultElementTraits クラス](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
