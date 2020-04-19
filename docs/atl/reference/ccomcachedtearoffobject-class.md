---
title: CComCachedTearOffObject クラス
ms.date: 11/04/2016
f1_keywords:
- CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::AddRef
- ATLCOM/ATL::CComCachedTearOffObject::FinalConstruct
- ATLCOM/ATL::CComCachedTearOffObject::FinalRelease
- ATLCOM/ATL::CComCachedTearOffObject::QueryInterface
- ATLCOM/ATL::CComCachedTearOffObject::Release
- ATLCOM/ATL::CComCachedTearOffObject::m_contained
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
ms.openlocfilehash: d993a349d38342bda30a83dfdbe25577953799b3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497536"
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOffObject クラス

このクラスは、ティアオフインターフェイスの[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)を実装します。

## <a name="syntax"></a>構文

```
template
<class contained>
class CComCachedTearOffObject : public
    IUnknown,
public CComObjectRootEx<contained
::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>パラメーター

*格納*<br/>
から`CComTearOffObjectBase`派生したティアオフクラス、およびティアオフオブジェクトがサポートするインターフェイスです。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|コンストラクターです。|
|[CComCachedTearOffObject:: ~ CComCachedTearOffObject](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComCachedTearOffObject::AddRef](#addref)|`CComCachedTearOffObject`オブジェクトの参照カウントをインクリメントします。|
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|(ティアオフ`m_contained::FinalConstruct`クラス ' method) を呼び出します。|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|(ティアオフ`m_contained::FinalRelease`クラス ' method) を呼び出します。|
|[CComCachedTearOffObject:: QueryInterface](#queryinterface)|オブジェクトのへ`IUnknown`のポインター、またはティアオフクラス (クラス`contained`) 上の要求されたインターフェイスへのポインターを返します。 `CComCachedTearOffObject`|
|[CComCachedTearOffObject:: Release](#release)|`CComCachedTearOffObject`オブジェクトの参照カウントをデクリメントし、参照カウントが0の場合はオブジェクトを破棄します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CComCachedTearOffObject::m_contained](#m_contained)|ティアオフ`CComContainedObject`クラス (クラス`contained`) から派生したオブジェクト。|

## <a name="remarks"></a>Remarks

`CComCachedTearOffObject`ティアオフインターフェイスに[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)を実装します。 このクラス`CComCachedTearOffObject`は、 `CComTearOffObject`所有者オブジェクトの`IUnknown`と`IUnknown`は別の独自のを持つとは異なります (所有者は、ティアオフを作成する対象のオブジェクトです)。 `CComCachedTearOffObject`に対して独自の`IUnknown`参照カウントを保持し、参照カウントが0になるとそれ自体を削除します。 ただし、そのいずれかのティアオフインターフェイスに対してクエリを実行すると、所有者オブジェクト`IUnknown`の参照カウントがインクリメントされます。

ティアオフを実装している`CComCachedTearOffObject` オブジェクトが既にインスタンス化されている場合に、ティアオフインターフェイスに対してもう一度クエリを実行すると、同じオブジェクトが再利用されます。`CComCachedTearOffObject` これに対して、によって`CComTearOffObject`実装されたティアオフインターフェイスが owner オブジェクトを介して再びクエリされる場合、別`CComTearOffObject`のがインスタンス化されます。

Owner クラスはを実装`FinalRelease`し、 `Release`に対し`CComCachedTearOffObject`て`IUnknown`キャッシュされたでを呼び出す必要があります。これにより、参照カウントが減少します。 これ`FinalRelease`により`CComCachedTearOffObject`、が呼び出され、ティアオフが削除されます。

## <a name="inheritance-hierarchy"></a>継承階層

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="addref"></a>CComCachedTearOffObject:: AddRef

`CComCachedTearOffObject`オブジェクトの参照カウントを1だけインクリメントします。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>戻り値

診断とテストに役立つ可能性のある値。

##  <a name="ccomcachedtearoffobject"></a>CComCachedTearOffObject::CComCachedTearOffObject

コンストラクターです。

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>パラメーター

*pv*<br/>
から`IUnknown`のへのポインター。 `CComCachedTearOffObject`

### <a name="remarks"></a>Remarks

メンバー [m_contained](#m_contained) を初期化します。`CComContainedObject`

##  <a name="dtor"></a>CComCachedTearOffObject:: ~ CComCachedTearOffObject

デストラクターです。

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>Remarks

割り当てられたすべてのリソースを解放し、 [FinalRelease](#finalrelease)を呼び出します。

##  <a name="finalconstruct"></a>CComCachedTearOffObject::FinalConstruct

を`m_contained::FinalConstruct`呼び出して`m_contained`、 `CComContainedObject`ティアオフクラスによって実装されたインターフェイスにアクセスするために使用する>オブジェクトを作成します。<  `contained`

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="finalrelease"></a>CComCachedTearOffObject::FinalRelease

を`m_contained::FinalRelease`呼び出して`m_contained` 、>`CComContainedObject`オブジェクトを解放します。 <  `contained`

```
void FinalRelease();
```

##  <a name="m_contained"></a>CComCachedTearOffObject::m_contained

ティアオフクラスから派生した[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)オブジェクト。

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>パラメーター

*格納*<br/>
からから`CComTearOffObjectBase`派生したティアオフクラス、およびティアオフオブジェクトがサポートするインターフェイスです。

### <a name="remarks"></a>Remarks

継承さ`m_contained`れたメソッドは、キャッシュされたティアオフオブジェクトの`QueryInterface`、 `FinalConstruct`、および`FinalRelease`を使用して、ティアオフクラスのティアオフインターフェイスにアクセスするために使用されます。

##  <a name="queryinterface"></a>  CComCachedTearOffObject::QueryInterface

要求されたインターフェイスへのポインターを取得します。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>パラメーター

*iid*<br/>
から要求されているインターフェイスの GUID。

*ppvObject*<br/>
入出力*Iid*によって識別されるインターフェイスポインターへのポインター。インターフェイスが見つからない場合は NULL。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

要求されたインターフェイス`IUnknown`がの場合、自体`CComCachedTearOffObject` `IUnknown`へのポインターを返し、参照カウントをインクリメントします。 それ以外の場合は、から`CComObjectRootEx`継承された[internalqueryinterface](ccomobjectrootex-class.md#internalqueryinterface)メソッドを使用して、ティアオフクラスのインターフェイスに対してクエリを行います。

##  <a name="release"></a>CComCachedTearOffObject:: Release

参照カウントを1だけデクリメントし、参照カウントが0の場合は`CComCachedTearOffObject`オブジェクトを削除します。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>戻り値

非デバッグビルドでは、は常に0を返します。 デバッグビルドでは、診断またはテストに役立つ値が返されます。

## <a name="see-also"></a>関連項目

[CComTearOffObject クラス](../../atl/reference/ccomtearoffobject-class.md)<br/>
[CComObjectRootEx クラス](../../atl/reference/ccomobjectrootex-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
