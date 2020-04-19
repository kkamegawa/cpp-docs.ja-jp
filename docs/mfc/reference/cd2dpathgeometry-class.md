---
title: CD2DPathGeometry クラス
ms.date: 11/04/2016
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
helpviewer_keywords:
- CD2DPathGeometry [MFC], CD2DPathGeometry
- CD2DPathGeometry [MFC], Attach
- CD2DPathGeometry [MFC], Create
- CD2DPathGeometry [MFC], Destroy
- CD2DPathGeometry [MFC], Detach
- CD2DPathGeometry [MFC], GetFigureCount
- CD2DPathGeometry [MFC], GetSegmentCount
- CD2DPathGeometry [MFC], Open
- CD2DPathGeometry [MFC], Stream
- CD2DPathGeometry [MFC], m_pPathGeometry
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
ms.openlocfilehash: 8657421e67239cdeb782cffbbd42e0c50f6c0e96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396354"
---
# <a name="cd2dpathgeometry-class"></a>CD2DPathGeometry クラス

ID2D1PathGeometry のラッパーです。

## <a name="syntax"></a>構文

```
class CD2DPathGeometry : public CD2DGeometry;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DPathGeometry::CD2DPathGeometry](#cd2dpathgeometry)|CD2DPathGeometry オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CD2DPathGeometry::Attach](#attach)|既存のリソース インターフェイス オブジェクトにアタッチします|
|[CD2DPathGeometry::Create](#create)|CD2DPathGeometry を作成します。 (上書き[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create))。|
|[CD2DPathGeometry::Destroy](#destroy)|CD2DPathGeometry オブジェクトを破棄します。 (上書き[CD2DGeometry::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy))。|
|[CD2DPathGeometry::Detach](#detach)|オブジェクトからリソースのインターフェイスをデタッチします。|
|[CD2DPathGeometry::GetFigureCount](#getfigurecount)|パス ジオメトリの数値の数を取得します。|
|[CD2DPathGeometry::GetSegmentCount](#getsegmentcount)|パス ジオメトリのセグメントの数を取得します。|
|[CD2DPathGeometry::Open](#open)|図形とセグメント パス ジオメトリを作成するために使用するジオメトリ シンクを取得します。|
|[CD2DPathGeometry::Stream](#stream)|指定した ID2D1GeometrySink には、パス ジオメトリの内容をコピーします。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CD2DPathGeometry::m_pPathGeometry](#m_ppathgeometry)|ID2D1PathGeometry へのポインター。|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)

`CD2DPathGeometry`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="attach"></a>  CD2DPathGeometry::Attach

既存のリソース インターフェイス オブジェクトにアタッチします

```
void Attach(ID2D1PathGeometry* pResource);
```

### <a name="parameters"></a>パラメーター

*pResource*<br/>
既存のリソース インターフェイスです。 NULL にすることはできません。

##  <a name="cd2dpathgeometry"></a>  CD2DPathGeometry::CD2DPathGeometry

CD2DPathGeometry オブジェクトを構築します。

```
CD2DPathGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>パラメーター

*pParentTarget*<br/>
レンダー ターゲットへのポインター。

*bAutoDestroy*<br/>
所有者 (pParentTarget) によって、オブジェクトが破棄されることを示します。

##  <a name="create"></a>  CD2DPathGeometry::Create

CD2DPathGeometry を作成します。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>パラメーター

*pRenderTarget*<br/>
レンダー ターゲットへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功すると、S_OK を返します。 それ以外の場合、HRESULT エラー コードを返します。

##  <a name="destroy"></a>  CD2DPathGeometry::Destroy

CD2DPathGeometry オブジェクトを破棄します。

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DPathGeometry::Detach

オブジェクトからリソースのインターフェイスをデタッチします。

```
ID2D1PathGeometry* Detach();
```

### <a name="return-value"></a>戻り値

インターフェイスのデタッチされたリソースへのポインター。

##  <a name="getfigurecount"></a>  CD2DPathGeometry::GetFigureCount

パス ジオメトリの数値の数を取得します。

```
int GetFigureCount() const;
```

### <a name="return-value"></a>戻り値

パス ジオメトリに数値の数を返します。

##  <a name="getsegmentcount"></a>  CD2DPathGeometry::GetSegmentCount

パス ジオメトリのセグメントの数を取得します。

```
int GetSegmentCount() const;
```

### <a name="return-value"></a>戻り値

パス ジオメトリには、セグメントの数を返します。

##  <a name="m_ppathgeometry"></a>  CD2DPathGeometry::m_pPathGeometry

ID2D1PathGeometry へのポインター。

```
ID2D1PathGeometry* m_pPathGeometry;
```

##  <a name="open"></a>  CD2DPathGeometry::Open

図形とセグメント パス ジオメトリを作成するために使用するジオメトリ シンクを取得します。

```
ID2D1GeometrySink* Open();
```

### <a name="return-value"></a>戻り値

図形とセグメント パス ジオメトリを作成するために使用される ID2D1GeometrySink へのポインター。

##  <a name="stream"></a>  CD2DPathGeometry::Stream

指定した ID2D1GeometrySink には、パス ジオメトリの内容をコピーします。

```
BOOL Stream(ID2D1GeometrySink* geometrySink);
```

### <a name="parameters"></a>パラメーター

*geometrySink*<br/>
パス ジオメトリの内容のコピー先となるシンク。 このシンクを変更しても、このパス ジオメトリの内容は変わりません。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
