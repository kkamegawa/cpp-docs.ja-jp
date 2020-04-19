---
title: CComObject クラス
ms.date: 11/04/2016
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
ms.openlocfilehash: a2051932413d8658eb7cedb67ed0eab2077b599d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497134"
---
# <a name="ccomobject-class"></a>CComObject クラス

このクラスは`IUnknown` 、非集計オブジェクトに対してを実装します。

## <a name="syntax"></a>構文

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>パラメーター

*常用*<br/>
[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)または[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)から派生したクラス、およびオブジェクトでサポートする他のインターフェイスから派生したクラス。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComObject::CComObject](#ccomobject)|コンストラクターです。|
|[CComObject::~CComObject](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComObject::AddRef](#addref)|オブジェクトの参照カウントをインクリメントします。|
|[CComObject::CreateInstance](#createinstance)|雑音新しい`CComObject`オブジェクトを作成します。|
|[CComObject::QueryInterface](#queryinterface)|要求されたインターフェイスへのポインターを取得します。|
|[CComObject::Release](#release)|オブジェクトの参照カウントをデクリメントします。|

## <a name="remarks"></a>Remarks

`CComObject`非集計オブジェクトの[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)を実装します。 ただし、、 `AddRef`、 `QueryInterface`および`Release`への呼び出しはに`CComObjectRootEx`委任されます。

の使用`CComObject`方法の詳細については、「 [ATL COM オブジェクトの基礎](../../atl/fundamentals-of-atl-com-objects.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`Base`

`CComObject`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="addref"></a>  CComObject::AddRef

オブジェクトの参照カウントをインクリメントします。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>戻り値

この関数は、オブジェクトに対してインクリメントされた新しい参照カウントを返します。 この値は、診断またはテストに便利な場合があります。

##  <a name="ccomobject"></a>  CComObject::CComObject

コンストラクターは、モジュールのロックカウントをインクリメントします。

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>パラメーター

<em>void\*</em><br/>
からこの無名パラメーターは使用されません。 これは、他の`CComXXXObjectXXX`コンストラクターとの対称のために存在します。

### <a name="remarks"></a>Remarks

デストラクターはこれをデクリメントします。

派生オブジェクトが new 演算子を使用して正常に構築された場合、最初の参照カウントは0になります。 `CComObject` 参照カウントを適切な値 (1) に設定するには、 [AddRef](#addref)関数を呼び出します。

##  <a name="dtor"></a>CComObject:: ~ CComObject

デストラクターです。

```
CComObject();
```

### <a name="remarks"></a>Remarks

割り当てられたすべてのリソースを解放し、 [FinalRelease](ccomobjectrootex-class.md#finalrelease)を呼び出して、モジュールのロックカウントをデクリメントします。

##  <a name="createinstance"></a>  CComObject::CreateInstance

この静的関数を使用すると、 [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)のオーバーヘッドを発生させることなく、新しい**CComObject <** `Base` **>** オブジェクトを作成できます。

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>パラメーター

*ページ*<br/>
入出力**CComObject <** `Base` **ポインターへのポインター。>** が`CreateInstance`失敗した場合、 *pp*は NULL に設定されます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

返されるオブジェクトは、参照カウントが0であるため`AddRef` 、をすぐに`Release`呼び出し、を使用してオブジェクトポインターの参照を解放します。

オブジェクトへの直接アクセスが不要でも、の`CoCreateInstance`オーバーヘッドなしで新しいオブジェクトを作成する場合は、代わりに[CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)を使用します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

##  <a name="queryinterface"></a>  CComObject::QueryInterface

要求されたインターフェイスへのポインターを取得します。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>パラメーター

*iid*<br/>
から要求されているインターフェイスの識別子。

*ppvObject*<br/>
入出力*Iid*によって識別されるインターフェイスポインターへのポインター。 オブジェクトがこのインターフェイスをサポートしていない場合、 *ppvObject*は NULL に設定されます。

*ページ*<br/>
入出力型`Q`によって識別されるインターフェイスポインターへのポインター。 オブジェクトがこのインターフェイスをサポートしていない場合、 *pp*は NULL に設定されます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="release"></a>  CComObject::Release

オブジェクトの参照カウントをデクリメントします。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>戻り値

この関数は、オブジェクトの新しいデクリメントされた参照カウントを返します。 デバッグビルドでは、診断またはテストに戻り値が役立つ場合があります。 非デバッグビルドでは、 `Release`は常に0を返します。

## <a name="see-also"></a>関連項目

[CComAggObject クラス](../../atl/reference/ccomaggobject-class.md)<br/>
[CComPolyObject クラス](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
