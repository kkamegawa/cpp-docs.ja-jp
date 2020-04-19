---
title: CD2DRectF クラス
ms.date: 11/04/2016
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
ms.openlocfilehash: 9b91cfaec3827a61152c4116b56e817a436606be
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682399"
---
# <a name="cd2drectf-class"></a>CD2DRectF クラス

`D2D1_RECT_F`のラッパー。

## <a name="syntax"></a>構文

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DRectF:: CD2DRectF](#cd2drectf)|オーバーロードされます。 オブジェクトから`CD2DRectF` `D2D1_RECT_F`オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CD2DRectF::IsNull](#isnull)|式に有効なデータが含まれていない (NULL) かどうかを示す**ブール**値を返します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CD2DRectF:: operator CRect](#operator_crect)|を`CD2DRectF`オブジェクト`CRect`に変換します。|

## <a name="inheritance-hierarchy"></a>継承階層

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget

##  <a name="cd2drectf"></a>  CD2DRectF::CD2DRectF

CRect オブジェクトから CD2DRectF オブジェクトを構築します。

```
CD2DRectF(const CRect& rect);
CD2DRectF(const D2D1_RECT_F& rect);
CD2DRectF(const D2D1_RECT_F* rect);

CD2DRectF(
    FLOAT fLeft = 0.,
    FLOAT fTop = 0.,
    FLOAT fRight = 0.,
    FLOAT fBottom = 0.);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
ソース四角形

*fLeft*<br/>
ソースの左座標

*fTop*<br/>
基になる上座標

*fRight*<br/>
ソースの右座標

*下*<br/>
基になる下座標

##  <a name="isnull"></a>  CD2DRectF::IsNull

式に有効なデータが含まれていない (Null) かどうかを示すブール値を返します。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>戻り値

四角形の上、左、下、および右の値がすべて0に等しい場合は TRUE。それ以外の場合は FALSE。

##  <a name="operator_crect"></a>CD2DRectF:: operator CRect

CD2DRectF を CRect オブジェクトに変換します。

```
operator CRect();
```

### <a name="return-value"></a>戻り値

D2D rectangle の現在の値。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
