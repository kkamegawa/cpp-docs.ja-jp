---
title: CDefaultCharTraits クラス
ms.date: 11/04/2016
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
ms.openlocfilehash: fe599ee0e84c393bed656b7304fd13d55ce95a50
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258742"
---
# <a name="cdefaultchartraits-class"></a>CDefaultCharTraits クラス

このクラスは、大文字と小文字を変換するための 2 つの静的関数を提供します。

## <a name="syntax"></a>構文

```
template <typename T>
class CDefaultCharTraits
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
コレクションに格納されるデータの型。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDefaultCharTraits::CharToLower](#chartolower)|(静的)文字を大文字に変換するには、この関数を呼び出します。|
|[CDefaultCharTraits::CharToUpper](#chartoupper)|(静的)文字を小文字に変換するには、この関数を呼び出します。|

## <a name="remarks"></a>Remarks

このクラスには、クラスによって使用されている関数[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcoll.h

##  <a name="chartolower"></a>  CDefaultCharTraits::CharToLower

文字を小文字に変換するには、この関数を呼び出します。

```
static wchar_t CharToLower(wchar_t x);
static char CharToLower(char x);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
小文字に変換する文字。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]

##  <a name="chartoupper"></a>  CDefaultCharTraits::CharToUpper

文字を大文字に変換するには、この関数を呼び出します。

```
static wchar_t CharToUpper(wchar_t x);
static char CharToUpper(char x);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
大文字に変換する文字。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
