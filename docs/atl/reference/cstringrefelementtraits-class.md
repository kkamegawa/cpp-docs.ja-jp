---
title: CStringRefElementTraits クラス
ms.date: 11/04/2016
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
ms.openlocfilehash: c57fda64689a80dfa548977e56b0416641bb4360
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277410"
---
# <a name="cstringrefelementtraits-class"></a>CStringRefElementTraits クラス

このクラスは、コレクション クラスのオブジェクトに格納された文字列に関連する静的関数を提供します。 文字列オブジェクトの参照として処理します。

## <a name="syntax"></a>構文

```
template <typename T>
class CStringRefElementTraits : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
コレクションに格納されるデータの型。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CStringRefElementTraits::CompareElements](#compareelements)|2 つの文字列要素が等しいかどうかを比較する、この静的関数を呼び出します。|
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|2 つの文字列要素を比較する、この静的関数を呼び出します。|
|[CStringRefElementTraits::Hash](#hash)|指定した文字列の要素のハッシュ値を計算する、この静的関数を呼び出します。|

## <a name="remarks"></a>Remarks

このクラスは、文字列を比較し、ハッシュ値を作成するために、静的関数を提供します。 これらの関数は、文字列ベースのデータを格納するコレクション クラスを使用する場合に便利です。 異なり[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)と[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)、`CStringRefElementTraits`により、`CString`として渡される引数を**const** `CString&`参照します。

詳細については、次を参照してください。 [ATL コレクション クラス](../../atl/atl-collection-classes.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="compareelements"></a>  CStringRefElementTraits::CompareElements

2 つの文字列要素が等しいかどうかを比較する、この静的関数を呼び出します。

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>パラメーター

*element1*<br/>
最初の要素を文字列します。

*element2*<br/>
2 番目の文字列要素。

### <a name="return-value"></a>戻り値

要素が false でそれ以外の場合、等しい場合は true を返します。

##  <a name="compareelementsordered"></a>  CStringRefElementTraits::CompareElementsOrdered

2 つの文字列要素を比較する、この静的関数を呼び出します。

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>パラメーター

*str1*<br/>
最初の要素を文字列します。

*str2*<br/>
2 番目の文字列要素。

### <a name="return-value"></a>戻り値

< 0、0 の文字列が一致している場合場合*str1*がより小さい*str2*、または > 0 場合*str1*がより大きい*str2*します。 [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)メソッドは、比較を実行するために使用します。

##  <a name="hash"></a>  CStringRefElementTraits::Hash

指定した文字列の要素のハッシュ値を計算する、この静的関数を呼び出します。

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>パラメーター

*str*<br/>
文字列の要素。

### <a name="return-value"></a>戻り値

文字列の内容を使用して計算されたハッシュ値を返します。

## <a name="see-also"></a>関連項目

[CElementTraitsBase クラス](../../atl/reference/celementtraitsbase-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
