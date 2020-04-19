---
title: IObjectWithSiteImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl::GetSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetChildSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetSite
- ATLCOM/ATL::IObjectWithSiteImpl::m_spUnkSite
helpviewer_keywords:
- IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
ms.openlocfilehash: e857f739e3ff7235c473e99abbef6aab0d3f4205
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495837"
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl クラス

このクラスは、オブジェクトがそのサイトと通信できるようにするメソッドを提供します。

## <a name="syntax"></a>構文

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`IObjectWithSiteImpl`派生したクラス。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IObjectWithSiteImpl:: GetSite](#getsite)|サイトにインターフェイスポインターを照会します。|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|サイトの`IUnknown`ポインターをオブジェクトに提供します。|
|[IObjectWithSiteImpl:: SetSite](#setsite)|サイトの`IUnknown`ポインターをオブジェクトに提供します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|サイトの`IUnknown`ポインターを管理します。|

## <a name="remarks"></a>Remarks

[IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite)インターフェイスを使用すると、オブジェクトはそのサイトと通信できます。 クラス`IObjectWithSiteImpl`は、このインターフェイスの既定の実装を`IUnknown`提供し、デバッグビルドでダンプデバイスに情報を送信することによってを実装します。

`IObjectWithSiteImpl`2つのメソッドを指定します。 クライアントは、まず`SetSite`を呼び出し、サイトの`IUnknown`ポインターを渡します。 このポインターはオブジェクト内に格納され、後での呼び出しに`GetSite`よって取得できます。

通常は、コントロールではない`IObjectWithSiteImpl`オブジェクトを作成するときに、からクラスを派生させます。 コントロールの場合は、サイトポインターも提供する[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)からクラスを派生させます。 `IObjectWithSiteImpl` と`IOleObjectImpl`の両方からクラスを派生させないでください。

## <a name="inheritance-hierarchy"></a>継承階層

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="getsite"></a>  IObjectWithSiteImpl::GetSite

によって`riid`識別されるインターフェイスへのポインターをサイトに照会します。

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>Remarks

サイトでこのインターフェイスがサポートされている場合は`ppvSite`、によってポインターが返されます。 それ以外`ppvSite`の場合、は NULL に設定されます。

Windows SDK の「 [IObjectWithSite:: GetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-getsite) 」を参照してください。

##  <a name="m_spunksite"></a>IObjectWithSiteImpl::m_spUnkSite

サイトの`IUnknown`ポインターを管理します。

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>Remarks

`m_spUnkSite`は、 [SetSite](#setsite)を呼び出すことによって、最初にこのポインターを受け取ります。

##  <a name="setchildsite"></a>  IObjectWithSiteImpl::SetChildSite

サイトの`IUnknown`ポインターをオブジェクトに提供します。

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>パラメーター

*pUnkSite*<br/>
からこのオブジェクトを`IUnknown`管理しているサイトのインターフェイスポインターへのポインター。 NULL の場合は、オブジェクトが`IUnknown::Release`そのサイトを認識しなくなった時点の既存のサイトでを呼び出す必要があります。

### <a name="return-value"></a>戻り値

S_OK を返します。

##  <a name="setsite"></a>  IObjectWithSiteImpl::SetSite

サイトの`IUnknown`ポインターをオブジェクトに提供します。

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) 」を参照してください。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
