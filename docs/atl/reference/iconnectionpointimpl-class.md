---
title: IConnectionPointImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
ms.openlocfilehash: bd88fd5d00df0347c0bd2161129b8cfa3ca35406
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496081"
---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointImpl クラス

このクラスは、コネクションポイントを実装します。

## <a name="syntax"></a>構文

```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`IConnectionPointImpl`派生したクラス。

*piid*<br/>
コネクションポイントオブジェクトによって表されるインターフェイスの IID へのポインター。

*CDV*<br/>
接続を管理するクラス。 既定値は[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)で、無制限の接続を許可します。 固定数の接続を指定する[CComUnkArray](../../atl/reference/ccomunkarray-class.md)を使用することもできます。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IConnectionPointImpl::Advise](#advise)|コネクションポイントとシンクの間の接続を確立します。|
|[IConnectionPointImpl::EnumConnections](#enumconnections)|コネクションポイントの接続を反復処理する列挙子を作成します。|
|[IConnectionPointImpl:: GetConnectionInterface](#getconnectioninterface)|コネクションポイントによって表されるインターフェイスの IID を取得します。|
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|接続可能なオブジェクトへのインターフェイスポインターを取得します。|
|[IConnectionPointImpl:: アドバイズ](#unadvise)|によって`Advise`以前に確立された接続を終了します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[IConnectionPointImpl::m_vec](#m_vec)|コネクションポイントの接続を管理します。|

## <a name="remarks"></a>Remarks

`IConnectionPointImpl`接続ポイントを実装します。これにより、オブジェクトが発信インターフェイスをクライアントに公開できるようになります。 クライアントは、シンクと呼ばれるオブジェクトにこのインターフェイスを実装します。

ATL では、 [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)を使用して、接続可能オブジェクトを実装します。 接続可能オブジェクト内の各コネクションポイントは、 *piid*によって識別される送信インターフェイスを表します。 クラス*Cdv*は、コネクションポイントとシンクの間の接続を管理します。 各接続は、"cookie" によって一意に識別されます。

ATL での接続ポイントの使用方法の詳細については、「[接続ポイント](../../atl/atl-connection-points.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="advise"></a>  IConnectionPointImpl::Advise

コネクションポイントとシンクの間の接続を確立します。

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>Remarks

[アドバイズ](#unadvise)プランを使用して接続呼び出しを終了します。

Windows SDK の「 [IConnectionPoint:: Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) 」を参照してください。

##  <a name="enumconnections"></a>  IConnectionPointImpl::EnumConnections

コネクションポイントの接続を反復処理する列挙子を作成します。

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IConnectionPoint:: EnumConnections](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) 」を参照してください。

##  <a name="getconnectioninterface"></a>  IConnectionPointImpl::GetConnectionInterface

コネクションポイントによって表されるインターフェイスの IID を取得します。

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IConnectionPoint:: GetConnectionInterface](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface) 」を参照してください。

##  <a name="getconnectionpointcontainer"></a>  IConnectionPointImpl::GetConnectionPointContainer

接続可能なオブジェクトへのインターフェイスポインターを取得します。

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IConnectionPoint:: GetConnectionPointContainer](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer) 」を参照してください。

##  <a name="m_vec"></a>  IConnectionPointImpl::m_vec

コネクションポイントオブジェクトとシンクの間の接続を管理します。

```
CDV m_vec;
```

### <a name="remarks"></a>Remarks

既定では`m_vec` 、は[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)型です。

##  <a name="unadvise"></a>  IConnectionPointImpl::Unadvise

事前に[アドバイズ](#advise)によって確立された接続を終了します。

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IConnectionPoint:: アドバイズ](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise)」を参照してください。

## <a name="see-also"></a>関連項目

[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
