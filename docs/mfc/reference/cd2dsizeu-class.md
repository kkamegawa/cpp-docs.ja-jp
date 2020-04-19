---
title: CD2DSizeU クラス
ms.date: 08/29/2019
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
helpviewer_keywords:
- CD2DSizeU [MFC], CD2DSizeU
- CD2DSizeU [MFC], IsNull
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
ms.openlocfilehash: 45625331d0c1be8ca7c663d12c53516dc7bd77c7
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177189"
---
# <a name="cd2dsizeu-class"></a>CD2DSizeU クラス

D2D1_SIZE_U のラッパー。

## <a name="syntax"></a>構文

```
class CD2DSizeU : public D2D1_SIZE_U;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DSizeU:: CD2DSizeU](#cd2dsizeu)|オーバーロードされます。 オブジェクトから`CD2DSizeU` `D2D1_SIZE_U`オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CD2DSizeU:: IsNull](#isnull)|式に有効なデータが含まれていない (NULL) かどうかを示す**ブール**値を返します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CD2DSizeU:: operator CSize](#operator_csize)|を`CD2DSizeU`オブジェクト`CSize`に変換します。|

## <a name="inheritance-hierarchy"></a>継承階層

`D2D1_SIZE_U`

[CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget

##  <a name="cd2dsizeu"></a>CD2DSizeU:: CD2DSizeU

CD2DSizeU オブジェクトを CSize オブジェクトから構築します。

```
CD2DSizeU(const CSize& size);
CD2DSizeU(const D2D1_SIZE_U& size);
CD2DSizeU(const D2D1_SIZE_U* size);

CD2DSizeU(
    UINT32 cx = 0,
    UINT32 cy = 0);
```

### <a name="parameters"></a>パラメーター

*size*<br/>
ソースサイズ

*cx*<br/>
ソースの幅

*暦年*<br/>
ソースの高さ

##  <a name="isnull"></a>  CD2DSizeU::IsNull

式に有効なデータが含まれていない (Null) かどうかを示すブール値を返します。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>戻り値

幅と高さが空の場合は TRUE。それ以外の場合は FALSE。

##  <a name="operator_csize"></a>CD2DSizeU:: operator CSize

CD2DSizeU を CSize オブジェクトに変換します。

```
operator CSize();
```

### <a name="return-value"></a>戻り値

D2D サイズの現在の値。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
