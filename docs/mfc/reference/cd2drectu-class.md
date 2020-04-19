---
title: CD2DRectU クラス
ms.date: 11/04/2016
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
ms.openlocfilehash: 4bbf7014fc1b612804289dcb647f85b5e7905aeb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244400"
---
# <a name="cd2drectu-class"></a>CD2DRectU クラス

`D2D1_RECT_U`のラッパー。

## <a name="syntax"></a>構文

```
class CD2DRectU : public D2D1_RECT_U;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DRectU::CD2DRectU](#cd2drectu)|オーバーロードされます。 構築、`CD2DRectU`オブジェクトから`D2D1_RECT_U`オブジェクト。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CD2DRectU::IsNull](#isnull)|返します、**ブール**式に有効なデータ (NULL) がないかどうかを示す値です。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CD2DRectU::operator CRect](#operator_crect)|変換`CD2DRectU`に`CRect`オブジェクト。|

## <a name="inheritance-hierarchy"></a>継承階層

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="cd2drectu"></a>  CD2DRectU::CD2DRectU

CRect オブジェクトから CD2DRectU オブジェクトを構築します。

```
CD2DRectU(const CRect& rect);
CD2DRectU(const D2D1_RECT_U& rect);
CD2DRectU(const D2D1_RECT_U* rect);

CD2DRectU(
    UINT32 uLeft = 0,
    UINT32 uTop = 0,
    UINT32 uRight = 0,
    UINT32 uBottom = 0);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
元の四角形

*uLeft*<br/>
ソースの左座標

*uTop*<br/>
ソースの上座標

*uRight*<br/>
右側の座標のソース

*uBottom*<br/>
ソースの下端の座標

##  <a name="isnull"></a>  CD2DRectU::IsNull

式に有効なデータ (Null) がないかどうかを示すブール値を返します。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>戻り値

四角形の上、左、下、および適切な値が 0 に等しい場合は TRUE。それ以外の場合は FALSE です。

##  <a name="operator_crect"></a>  CD2DRectU::operator CRect

CD2DRectU CRect オブジェクトに変換します。

```
operator CRect();
```

### <a name="return-value"></a>戻り値

D2D の四角形の現在の値。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
