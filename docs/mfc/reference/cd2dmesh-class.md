---
title: CD2DMesh クラス
ms.date: 11/04/2016
f1_keywords:
- CD2DMesh
- AFXRENDERTARGET/CD2DMesh
- AFXRENDERTARGET/CD2DMesh::CD2DMesh
- AFXRENDERTARGET/CD2DMesh::Attach
- AFXRENDERTARGET/CD2DMesh::Create
- AFXRENDERTARGET/CD2DMesh::Destroy
- AFXRENDERTARGET/CD2DMesh::Detach
- AFXRENDERTARGET/CD2DMesh::Get
- AFXRENDERTARGET/CD2DMesh::IsValid
- AFXRENDERTARGET/CD2DMesh::Open
- AFXRENDERTARGET/CD2DMesh::m_pMesh
helpviewer_keywords:
- CD2DMesh [MFC], CD2DMesh
- CD2DMesh [MFC], Attach
- CD2DMesh [MFC], Create
- CD2DMesh [MFC], Destroy
- CD2DMesh [MFC], Detach
- CD2DMesh [MFC], Get
- CD2DMesh [MFC], IsValid
- CD2DMesh [MFC], Open
- CD2DMesh [MFC], m_pMesh
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
ms.openlocfilehash: f4ad6fd054eeb8576c2fdb2dc924f70034b3abad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396367"
---
# <a name="cd2dmesh-class"></a>CD2DMesh クラス

ID2D1Mesh のラッパーです。

## <a name="syntax"></a>構文

```
class CD2DMesh : public CD2DResource;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DMesh::CD2DMesh](#cd2dmesh)|CD2DMesh オブジェクトを構築します。|
|[CD2DMesh:: ~ CD2DMesh](#_dtorcd2dmesh)|デストラクターです。 D2D メッシュ オブジェクトが破棄されるときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CD2DMesh::Attach](#attach)|既存のリソース インターフェイス オブジェクトにアタッチします|
|[CD2DMesh::Create](#create)|CD2DMesh を作成します。 (上書き[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create))。|
|[CD2DMesh::Destroy](#destroy)|CD2DMesh オブジェクトを破棄します。 (上書き[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy))。|
|[CD2DMesh::Detach](#detach)|オブジェクトからリソースのインターフェイスをデタッチします。|
|[CD2DMesh::Get](#get)|返します ID2D1Mesh インターフェイス|
|[CD2DMesh::IsValid](#isvalid)|リソースの有効性を確認します (上書き[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid))。|
|[CD2DMesh::Open](#open)|母集団のメッシュを開きます。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CD2DMesh::operator ID2D1Mesh *](#operator_id2d1mesh_star)|返します ID2D1Mesh インターフェイス|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CD2DMesh::m_pMesh](#m_pmesh)|ID2D1Mesh へのポインター。|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DMesh`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="_dtorcd2dmesh"></a>  CD2DMesh:: ~ CD2DMesh

デストラクターです。 D2D メッシュ オブジェクトが破棄されるときに呼び出されます。

```
virtual ~CD2DMesh();
```

##  <a name="attach"></a>  CD2DMesh::Attach

既存のリソース インターフェイス オブジェクトにアタッチします

```
void Attach(ID2D1Mesh* pResource);
```

### <a name="parameters"></a>パラメーター

*pResource*<br/>
既存のリソース インターフェイスです。 NULL にすることはできません。

##  <a name="cd2dmesh"></a>  CD2DMesh::CD2DMesh

CD2DMesh オブジェクトを構築します。

```
CD2DMesh(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>パラメーター

*pParentTarget*<br/>
レンダー ターゲットへのポインター。

*bAutoDestroy*<br/>
所有者 (pParentTarget) によって、オブジェクトが破棄されることを示します。

##  <a name="create"></a>  CD2DMesh::Create

CD2DMesh を作成します。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>パラメーター

*pRenderTarget*<br/>
レンダー ターゲットへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功すると、S_OK を返します。 それ以外の場合、HRESULT エラー コードを返します。

##  <a name="destroy"></a>  CD2DMesh::Destroy

CD2DMesh オブジェクトを破棄します。

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DMesh::Detach

オブジェクトからリソースのインターフェイスをデタッチします。

```
ID2D1Mesh* Detach();
```

### <a name="return-value"></a>戻り値

インターフェイスのデタッチされたリソースへのポインター。

##  <a name="get"></a>  CD2DMesh::Get

返します ID2D1Mesh インターフェイス

```
ID2D1Mesh* Get();
```

### <a name="return-value"></a>戻り値

ID2D1Mesh インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="isvalid"></a>  CD2DMesh::IsValid

リソースの有効性のチェック

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>戻り値

リソースが有効な場合は TRUE。それ以外の場合は FALSE です。

##  <a name="m_pmesh"></a>  CD2DMesh::m_pMesh

ID2D1Mesh へのポインター。

```
ID2D1Mesh* m_pMesh;
```

##  <a name="open"></a>  CD2DMesh::Open

母集団のメッシュを開きます。

```
ID2D1TessellationSink* Open();
```

### <a name="return-value"></a>戻り値

メッシュの作成に使用される、ID2D1TessellationSink へのポインター。

##  <a name="operator_id2d1mesh_star"></a>  CD2DMesh::operator ID2D1Mesh *

返します ID2D1Mesh インターフェイス

```
operator ID2D1Mesh*();
```

### <a name="return-value"></a>戻り値

ID2D1Mesh インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
