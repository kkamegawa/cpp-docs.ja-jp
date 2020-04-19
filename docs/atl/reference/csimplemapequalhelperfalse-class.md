---
title: CSimpleMapEqualHelperFalse クラス
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
ms.openlocfilehash: 9c4241049ad323047f06c0b29f946521f2c02167
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277904"
---
# <a name="csimplemapequalhelperfalse-class"></a>CSimpleMapEqualHelperFalse クラス

このクラスのヘルパーは、 [CSimpleMap](../../atl/reference/csimplemap-class.md)クラス。

## <a name="syntax"></a>構文

```
template <class TKey, class TVal>
class CSimpleMapEqualHelperFalse
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|(静的)2 つのキーの等価性をテストします。|
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|(静的)False を返します。|

## <a name="remarks"></a>Remarks

この特性クラスを補足するため、`CSimpleMap`クラス。 含まれる 2 つの要素を比較するためのメソッドを提供します、`CSimpleMap`オブジェクト、具体的には 2 つの値の要素またはキーの 2 つの要素。

値の比較は、常に false を返すし、さらが呼び出されます`ATLASSERT`引数が参照されている場合は false。 等しいかどうかテストが十分に定義されていない場合、このクラスは、ほとんどのメソッドに対して正常に動作しなどの比較に依存する方法を明確に定義された方法で失敗する可能性がキー/値ペアを含むマップを[CSimpleMap:。FindVal](../../atl/reference/csimplemap-class.md#findval)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsimpcoll.h

##  <a name="isequalkey"></a>  CSimpleMapEqualHelperFalse::IsEqualKey

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

### <a name="remarks"></a>Remarks

このメソッドを呼び出す[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)します。

##  <a name="isequalvalue"></a>  CSimpleMapEqualHelperFalse::IsEqualValue

false を返します。

```
static bool IsEqualValue(const TVal&, const TVal&);
```

### <a name="return-value"></a>戻り値

false を返します。

### <a name="remarks"></a>Remarks

このメソッドは常に false を返し、呼び出されます`ATLASSERT`引数が参照されている場合は false。 目的は、`CSimpleMapEqualHelperFalse::IsEqualValue`を強制的に比較を使用して、等しいかどうかテストが適切に定義されていないときに、明確に定義された方法で失敗するメソッド。

## <a name="see-also"></a>関連項目

[CSimpleMapEqualHelper クラス](../../atl/reference/csimplemapequalhelper-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
