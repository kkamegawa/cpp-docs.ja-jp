---
title: CSimpleMapEqualHelper クラス
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: c614cbb11376c5ae338762c0feaa54c8f1bb3e27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277932"
---
# <a name="csimplemapequalhelper-class"></a>CSimpleMapEqualHelper クラス

このクラスのヘルパーは、 [CSimpleMap](../../atl/reference/csimplemap-class.md)クラス。

## <a name="syntax"></a>構文

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>パラメーター

*TKey*<br/>
重要な要素です。

*TVal*<br/>
値の要素。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(静的)2 つのキーの等価性をテストします。|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(静的)2 つの値が等しいかどうかをテストします。|

## <a name="remarks"></a>Remarks

この特性クラスを補足するため、`CSimpleMap`クラス。 2 つを比較するためのメソッドを提供`CSimpleMap`object 要素 (具体的には、キーと値コンポーネント) の等価性。 既定では、キーと値が比較されます**operator==()** が必要な追加機能を提供するこのクラスをオーバーライドできますが、マップに独自の等値演算子の複合データ型が含まれている場合。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsimpcoll.h

##  <a name="isequalkey"></a>  CSimpleMapEqualHelper::IsEqualKey

2 つのキーの等価性をテストします。

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>パラメーター

*k1*<br/>
最初のキー。

*k2*<br/>
2 番目のキー。

### <a name="return-value"></a>戻り値

キーが false でそれ以外の場合、等しい場合は true を返します。

##  <a name="isequalvalue"></a>  CSimpleMapEqualHelper::IsEqualValue

2 つの値が等しいかどうかをテストします。

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>パラメーター

*v1*<br/>
最初の値。

*v2*<br/>
2 番目の値。

### <a name="return-value"></a>戻り値

値が false でそれ以外の場合、等しい場合は true を返します。

## <a name="see-also"></a>関連項目

[CSimpleMapEqualHelperFalse クラス](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
