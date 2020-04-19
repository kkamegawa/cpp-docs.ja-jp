---
title: CD2DPointF クラス
ms.date: 11/04/2016
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
ms.openlocfilehash: b8fe808c3147fa52c5041e2988822ace0ba60896
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396341"
---
# <a name="cd2dpointf-class"></a>CD2DPointF クラス

`D2D1_POINT_2F`のラッパー。

## <a name="syntax"></a>構文

```
class CD2DPointF : public D2D1_POINT_2F;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DPointF::CD2DPointF](#cd2dpointf)|オーバーロードされます。 構築、`CD2DPointF`オブジェクトから`D2D1_POINT_2F`オブジェクト。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CD2DPointF::operator CPoint](#operator_cpoint)|変換`CD2DPointF`に`CPoint`オブジェクト。|

## <a name="inheritance-hierarchy"></a>継承階層

`D2D1_POINT_2F`

`CD2DPointF`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="cd2dpointf"></a>  CD2DPointF::CD2DPointF

CPoint オブジェクトから CD2DPointF オブジェクトを構築します。

```
CD2DPointF(const CPoint& pt);
CD2DPointF(const D2D1_POINT_2F& pt);
CD2DPointF(const D2D1_POINT_2F* pt);
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```

### <a name="parameters"></a>パラメーター

*pt*<br/>
ソース ポイント

*fX*<br/>
ソース X

*fY*<br/>
ソース Y

##  <a name="operator_cpoint"></a>  CD2DPointF::operator CPoint

CD2DPointF CPoint オブジェクトに変換します。

```
operator CPoint();
```

### <a name="return-value"></a>戻り値

D2D ポイントの現在の値。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
