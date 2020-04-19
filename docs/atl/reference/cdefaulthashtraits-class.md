---
title: CDefaultHashTraits クラス
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: a51b4460d7fcdf778fce24b6e404b75190f598f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245834"
---
# <a name="cdefaulthashtraits-class"></a>CDefaultHashTraits クラス

このクラスは、ハッシュ値を計算するための静的関数を提供します。

## <a name="syntax"></a>構文

```
template<typename T>
class CDefaultHashTraits
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
コレクションに格納されるデータの型。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDefaultHashTraits::Hash](#hash)|(静的)指定された要素のハッシュ値を計算するには、この関数を呼び出します。|

## <a name="remarks"></a>Remarks

このクラスには、指定された要素のハッシュ値を返す 1 つの静的関数が含まれています。 このクラスは、によって使用されて、 [CDefaultElementTraits クラス](../../atl/reference/cdefaultelementtraits-class.md)します。

詳細については、次を参照してください。 [ATL コレクション クラス](../../atl/atl-collection-classes.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="hash"></a>  CDefaultHashTraits::Hash

指定された要素のハッシュ値を計算するには、この関数を呼び出します。

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>パラメーター

*要素*<br/>
要素。

### <a name="return-value"></a>戻り値

ハッシュ値を返します。

### <a name="remarks"></a>Remarks

既定のハッシュ アルゴリズムは非常に単純: 戻り値は、要素数。 複雑なアルゴリズムが必要な場合は、この関数をオーバーライドします。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
