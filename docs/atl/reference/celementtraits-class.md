---
title: CElementTraits クラス
ms.date: 11/04/2016
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
helpviewer_keywords:
- CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
ms.openlocfilehash: 646b445aed93c9041932c60442f61792f5e1a7e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245769"
---
# <a name="celementtraits-class"></a>CElementTraits クラス

このクラスは、移動、コピー、比較、およびハッシュ演算のメソッドや関数を提供するコレクション クラスによって使用されます。

## <a name="syntax"></a>構文

```
template<typename T>
class CElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
コレクションに格納されるデータの型。

## <a name="remarks"></a>Remarks

このクラスは、移動、コピー、比較、およびコレクション クラスのオブジェクトに格納されているハッシュの要素の既定の静的関数およびメソッドを提供します。 `CElementTraits` コレクション クラスでこれらの操作の既定のプロバイダーとして指定された[CAtlArray](../../atl/reference/catlarray-class.md)、 [CAtlList](../../atl/reference/catllist-class.md)、 [CRBMap](../../atl/reference/crbmap-class.md)、 [CRBMultiMap](../../atl/reference/crbmultimap-class.md)、および[CRBTree](../../atl/reference/crbtree-class.md)します。

単純なデータ型の場合は、既定の実装で十分ですが、関数およびメソッドをユーザーが指定した実装でオーバーライドする必要がありますより複雑なオブジェクトを格納するコレクション クラスを使用する場合。

詳細については、次を参照してください。 [ATL コレクション クラス](../../atl/atl-collection-classes.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

## <a name="see-also"></a>関連項目

[CDefaultElementTraits クラス](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
