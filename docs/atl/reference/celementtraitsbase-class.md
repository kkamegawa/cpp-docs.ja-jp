---
title: CElementTraitsBase クラス
ms.date: 11/04/2016
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
ms.openlocfilehash: 207207d26a2c43367a00b382f80761429159a7b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259119"
---
# <a name="celementtraitsbase-class"></a>CElementTraitsBase クラス

このクラスは、既定のコピーを提供し、コレクション クラスのメソッドを移動します。

## <a name="syntax"></a>構文

```
template<typename T>
class CElementTraitsBase
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
コレクションに格納されるデータの型。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|[CElementTraitsBase::INARGTYPE](#inargtype)|コレクション クラスのオブジェクトに要素を追加するために使用するデータ型。|
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|コレクション クラスのオブジェクトから要素を取得するために使用するデータ型。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CElementTraitsBase::CopyElements](#copyelements)|コレクション クラスのオブジェクトに格納されている要素をコピーするには、このメソッドを呼び出します。|
|[CElementTraitsBase::RelocateElements](#relocateelements)|コレクション クラスのオブジェクトに格納されている要素を配置する場合に、このメソッドを呼び出します。|

## <a name="remarks"></a>Remarks

この基本クラスは、コピーおよびコレクション クラス内の要素を再配置するためのメソッドを定義します。 クラスによって使用されて、 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)、 [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)、および[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)します。

詳細については、次を参照してください。 [ATL コレクション クラス](../../atl/atl-collection-classes.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="copyelements"></a>  CElementTraitsBase::CopyElements

コレクション クラスのオブジェクトに格納されている要素をコピーするには、このメソッドを呼び出します。

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>パラメーター

*pDest*<br/>
コピー元のデータを受信する最初の要素へのポインター。

*pSrc*<br/>
コピーする最初の要素へのポインター。

*nElements*<br/>
コピーする要素の数。

### <a name="remarks"></a>Remarks

ソースと変換先の要素は重複できません。

##  <a name="inargtype"></a>  CElementTraitsBase::INARGTYPE

コレクションに要素を追加するために使用するデータ型。

```
typedef const T& INARGTYPE;
```

##  <a name="outargtype"></a>  CElementTraitsBase::OUTARGTYPE

コレクションから要素を取得するために使用するデータ型。

```
typedef T& OUTARGTYPE;
```

##  <a name="relocateelements"></a>  CElementTraitsBase::RelocateElements

コレクション クラスのオブジェクトに格納されている要素を配置する場合に、このメソッドを呼び出します。

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>パラメーター

*pDest*<br/>
再配置されたデータを受信する最初の要素へのポインター。

*pSrc*<br/>
配置する場合に、最初の要素へのポインター。

*nElements*<br/>
配置する場合に要素の数。

### <a name="remarks"></a>Remarks

このメソッドを呼び出す[memmove](../../c-runtime-library/reference/memmove-wmemmove.md)、これは、ほとんどのデータ型。 オブジェクトの移動中に、独自のメンバーへのポインターが含まれている場合は、このメソッドをオーバーライドする必要があります。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
