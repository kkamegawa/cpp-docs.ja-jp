---
title: CComTearOffObject クラス
ms.date: 11/04/2016
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
ms.openlocfilehash: 0d27a6fa3c0070cd32c78971a7544327c51d4393
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496913"
---
# <a name="ccomtearoffobject-class"></a>CComTearOffObject クラス

このクラスは、ティアオフインターフェイスを実装します。

## <a name="syntax"></a>構文

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>パラメーター

*常用*<br/>
から`CComTearOffObjectBase`派生したティアオフクラス、およびティアオフオブジェクトがサポートするインターフェイスです。

ATL は、2つのフェーズでそのティアオフインターフェイスを`CComTearOffObjectBase`実装します。メソッドは`QueryInterface`、参照`CComTearOffObject`カウントを処理し、で[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)を実装します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|コンストラクターです。|
|[CComTearOffObject:: ~ CComTearOffObject](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComTearOffObject:: AddRef](#addref)|`CComTearOffObject`オブジェクトの参照カウントをインクリメントします。|
|[CComTearOffObject:: QueryInterface](#queryinterface)|は、ティアオフクラスまたは owner クラスで、要求されたインターフェイスへのポインターを返します。|
|[CComTearOffObject:: Release](#release)|`CComTearOffObject`オブジェクトの参照カウントをデクリメントして破棄します。|

### <a name="ccomtearoffobjectbase-methods"></a>CComTearOffObjectBase メソッド

|||
|-|-|
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|コンストラクターです。|

### <a name="ccomtearoffobjectbase-data-members"></a>CComTearOffObjectBase データメンバー

|||
|-|-|
|[m_pOwner](#m_powner)|Owner クラスから`CComObject`派生したへのポインター。|

## <a name="remarks"></a>Remarks

`CComTearOffObject`は、そのインターフェイスに対してクエリを行うときにのみインスタンス化される個別のオブジェクトとして、ティアオフインターフェイスを実装します。 破棄は、その参照カウントが0になると削除されます。 通常、破棄を使用すると、メインオブジェクトのすべてのインスタンスに vtable ポインターが保存されるため、ほとんど使用されないインターフェイスのために、ティアオフインターフェイスを構築します。

ティアオフオブジェクトがサポートするインターフェイスとの間`CComTearOffObjectBase`で、ティアオフを実装するクラスを派生させる必要があります。 `CComTearOffObjectBase`は、owner クラスとスレッドモデルのテンプレート化にあります。 Owner クラスは、ティアオフが実装されているオブジェクトのクラスです。 スレッドモデルを指定しない場合は、既定のスレッドモデルが使用されます。

ティアオフクラスの COM マップを作成する必要があります。 ATL によってティアオフがインスタンス化されると`CComTearOffObject<CYourTearOffClass>` 、 `CComCachedTearOffObject<CYourTearOffClass>`またはが作成されます。

たとえば、BEEPER サンプル`CBeeper2`では、クラスはティアオフクラス`CBeeper`であり、クラスは owner クラスです。

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>継承階層

`Base`

`CComTearOffObject`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="addref"></a>CComTearOffObject:: AddRef

`CComTearOffObject`オブジェクトの参照カウントを1だけインクリメントします。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>戻り値

診断とテストに役立つ可能性のある値。

##  <a name="ccomtearoffobject"></a>CComTearOffObject::CComTearOffObject

コンストラクターです。

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>パラメーター

*pv*<br/>
から`CComObject<Owner>`オブジェクトへのポインターに変換されるポインター。

### <a name="remarks"></a>Remarks

所有者の参照カウントを1だけインクリメントします。

##  <a name="dtor"></a>CComTearOffObject:: ~ CComTearOffObject

デストラクターです。

```
~CComTearOffObject();
```

### <a name="remarks"></a>Remarks

割り当てられたすべてのリソースを解放し、FinalRelease を呼び出して、モジュールのロックカウントをデクリメントします。

##  <a name="ccomtearoffobjectbase"></a>CComTearOffObject::CComTearOffObjectBase

コンストラクターです。

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>Remarks

[M_pOwner](#m_powner)メンバーを NULL に初期化します。

##  <a name="m_powner"></a>CComTearOffObject::m_pOwner

*所有者*から派生した[CComObject](../../atl/reference/ccomobject-class.md)オブジェクトへのポインター。

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>パラメーター

*[所有者]*<br/>
からティアオフが実装されているクラス。

### <a name="remarks"></a>Remarks

構築中にポインターが NULL に初期化されます。

##  <a name="queryinterface"></a>  CComTearOffObject::QueryInterface

要求されたインターフェイスへのポインターを取得します。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>パラメーター

*iid*<br/>
から要求されているインターフェイスの IID。

*ppvObject*<br/>
入出力*Iid*によって識別されるインターフェイスポインターへのポインター。インターフェイスが見つからない場合は NULL。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

まず、ティアオフクラスのインターフェイスに対してクエリを行います。 インターフェイスが存在しない場合、は所有者オブジェクトのインターフェイスを照会します。 要求されたインターフェイス`IUnknown`がの場合`IUnknown`は、所有者のを返します。

##  <a name="release"></a>CComTearOffObject:: Release

参照カウントを1だけデクリメントし、参照カウントが0の場合はを削除`CComTearOffObject`します。

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>戻り値

非デバッグビルドでは、は常に0を返します。 デバッグビルドでは、診断またはテストに役立つ値が返されます。

## <a name="see-also"></a>関連項目

[CComCachedTearOffObject クラス](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
