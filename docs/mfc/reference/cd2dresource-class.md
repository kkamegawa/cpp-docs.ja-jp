---
title: CD2DResource クラス
ms.date: 03/27/2019
f1_keywords:
- CD2DResource
- AFXRENDERTARGET/CD2DResource
- AFXRENDERTARGET/CD2DResource::CD2DResource
- AFXRENDERTARGET/CD2DResource::Create
- AFXRENDERTARGET/CD2DResource::Destroy
- AFXRENDERTARGET/CD2DResource::IsValid
- AFXRENDERTARGET/CD2DResource::IsAutoDestroy
- AFXRENDERTARGET/CD2DResource::ReCreate
- AFXRENDERTARGET/CD2DResource::m_bIsAutoDestroy
- AFXRENDERTARGET/CD2DResource::m_pParentTarget
helpviewer_keywords:
- CD2DResource [MFC], CD2DResource
- CD2DResource [MFC], Create
- CD2DResource [MFC], Destroy
- CD2DResource [MFC], IsValid
- CD2DResource [MFC], IsAutoDestroy
- CD2DResource [MFC], ReCreate
- CD2DResource [MFC], m_bIsAutoDestroy
- CD2DResource [MFC], m_pParentTarget
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
ms.openlocfilehash: e2cc6be7119a2df193aa2af415a9c8d4054f537c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396302"
---
# <a name="cd2dresource-class"></a>CD2DResource クラス

D2D リソースなど、ブラシ、レイヤー、およびテキスト作成および管理するインターフェイスを提供する抽象クラス。

## <a name="syntax"></a>構文

```
class CD2DResource : public CObject;
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DResource::CD2DResource](#cd2dresource)|CD2DResource オブジェクトを構築します。|
|[CD2DResource:: ~ CD2DResource](#_dtorcd2dresource)|デストラクターです。 D2D リソース オブジェクトが破棄されるときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CD2DResource::Create](#create)|CD2DResource を作成します。|
|[CD2DResource::Destroy](#destroy)|CD2DResource オブジェクトを破棄します。|
|[CD2DResource::IsValid](#isvalid)|リソースの有効性のチェック|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CD2DResource::IsAutoDestroy](#isautodestroy)|自動のチェックは、フラグを破棄します。|
|[CD2DResource::ReCreate](#recreate)|CD2DResource を再作成します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CD2DResource::m_bIsAutoDestroy](#m_bisautodestroy)|所有者 (CRenderTarget) によってリソースが破棄されます。|
|[CD2DResource::m_pParentTarget](#m_pparenttarget)|CRenderTarget 親へのポインター)|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CD2DResource`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="_dtorcd2dresource"></a>  CD2DResource:: ~ CD2DResource

デストラクターです。 D2D リソース オブジェクトが破棄されるときに呼び出されます。

```
virtual ~CD2DResource();
```

##  <a name="cd2dresource"></a>  CD2DResource::CD2DResource

CD2DResource オブジェクトを構築します。

```
CD2DResource(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy);
```

### <a name="parameters"></a>パラメーター

*pParentTarget*<br/>
レンダー ターゲットへのポインター。

*bAutoDestroy*<br/>
所有者 (pParentTarget) によって、オブジェクトが破棄されることを示します。

##  <a name="create"></a>  CD2DResource::Create

CD2DResource を作成します。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;
```

### <a name="parameters"></a>パラメーター

*pRenderTarget*<br/>
レンダー ターゲットへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功すると、S_OK を返します。 それ以外の場合、HRESULT エラー コードを返します。

##  <a name="destroy"></a>  CD2DResource::Destroy

CD2DResource オブジェクトを破棄します。

```
virtual void Destroy() = 0;
```

##  <a name="isautodestroy"></a>  CD2DResource::IsAutoDestroy

自動のチェックは、フラグを破棄します。

```
BOOL IsAutoDestroy() const;
```

### <a name="return-value"></a>戻り値

の所有者によって、オブジェクトが破棄される場合は TRUE。それ以外の場合は FALSE です。

##  <a name="isvalid"></a>  CD2DResource::IsValid

リソースの有効性のチェック

```
virtual BOOL IsValid() const = 0;
```

### <a name="return-value"></a>戻り値

リソースが有効な場合は TRUE。それ以外の場合は FALSE です。

##  <a name="m_bisautodestroy"></a>  CD2DResource::m_bIsAutoDestroy

所有者 (CRenderTarget) によってリソースが破棄されます。

```
BOOL m_bIsAutoDestroy;
```

##  <a name="m_pparenttarget"></a>  CD2DResource::m_pParentTarget

CRenderTarget 親へのポインター)

```
CRenderTarget* m_pParentTarget;
```

##  <a name="recreate"></a>  CD2DResource::ReCreate

CD2DResource を再作成します。

```
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>パラメーター

*pRenderTarget*<br/>
レンダー ターゲットへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功すると、S_OK を返します。 それ以外の場合、HRESULT エラー コードを返します。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
