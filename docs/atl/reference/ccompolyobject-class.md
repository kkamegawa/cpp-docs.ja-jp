---
title: CComPolyObject クラス
ms.date: 11/04/2016
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
ms.openlocfilehash: deed29b5fb80ea8bbd06b3d50f45e38740b1619f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497151"
---
# <a name="ccompolyobject-class"></a>CComPolyObject クラス

このクラスは`IUnknown` 、集計または非集計オブジェクトに対してを実装します。

## <a name="syntax"></a>構文

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>パラメーター

*格納*<br/>
[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)または[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)から派生したクラス、およびオブジェクトでサポートする他のインターフェイスから派生したクラス。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|コンストラクターです。|
|[CComPolyObject::~CComPolyObject](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|オブジェクトの参照カウントをインクリメントします。|
|[CComPolyObject::CreateInstance](#createinstance)|雑音[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)のオーバーヘッドを発生させずに、新しい**CComPolyObject <** `contained` **>** オブジェクトを作成できます。|
|[CComPolyObject::FinalConstruct](#finalconstruct)|の最終初期化を`m_contained`実行します。|
|[CComPolyObject::FinalRelease](#finalrelease)|の最終的な破棄`m_contained`を実行します。|
|[CComPolyObject::QueryInterface](#queryinterface)|要求されたインターフェイスへのポインターを取得します。|
|[CComPolyObject::Release](#release)|オブジェクトの参照カウントをデクリメントします。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|オブジェクト`IUnknown`が集計されている場合、またはオブジェクトが集計`IUnknown`されていない場合にオブジェクトのに対して、外側の unknown への呼び出しをデリゲートします。|

## <a name="remarks"></a>Remarks

`CComPolyObject`集計または非集計オブジェクトの[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)を実装します。

の`CComPolyObject`インスタンスが作成されると、[外側の不明] の値がチェックされます。 NULL の場合は、 `IUnknown`非集計オブジェクトに対してが実装されます。 外側の unknown が NULL でない場合`IUnknown` 、は集計オブジェクトに対して実装されます。

を使用`CComPolyObject`する利点は、集計されたケースと非集計ケースを処理するために、 [CComAggObject](../../atl/reference/ccomaggobject-class.md)と[CComObject](../../atl/reference/ccomobject-class.md)の両方がモジュールに存在しないことです。 1つ`CComPolyObject`のオブジェクトが両方のケースを処理します。 つまり、モジュールには vtable のコピーと関数のコピーが1つだけ存在します。 Vtable が大きい場合は、モジュールのサイズを大幅に減らすことができます。 ただし、vtable が小さい場合、を使用`CComPolyObject`する`CComAggObject`と、と`CComObject`のように集計または非集計オブジェクトに対して最適化されていないため、モジュールサイズが少し大きくなります。

DECLARE_POLY_AGGREGATABLE マクロがオブジェクトのクラス定義で指定されている`CComPolyObject`場合は、がオブジェクトの作成に使用されます。 ATL プロジェクトウィザードを使用してフルコントロールまたは Internet Explorer コントロールを作成すると、DECLARE_POLY_AGGREGATABLE が自動的に宣言されます。

集計された`CComPolyObject`場合、オブジェクトは`IUnknown`、外側のオブジェクトの`IUnknown`とは別に独自のを持ち、独自の参照カウントを保持します。 `CComPolyObject`[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)を使用して、外側の不明なに委任します。

集計の詳細については、「 [ATL COM オブジェクトの基礎](../../atl/fundamentals-of-atl-com-objects.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="addref"></a>  CComPolyObject::AddRef

オブジェクトの参照カウントをインクリメントします。

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>戻り値

診断またはテストに役立つ可能性のある値。

##  <a name="ccompolyobject"></a>  CComPolyObject::CComPolyObject

コンストラクターです。

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>パラメーター

*pv*<br/>
からオブジェクトが集計される場合は、外側の unknown へのポインター。オブジェクトが集計されない場合は NULL。オブジェクトの場合は NULL。

### <a name="remarks"></a>Remarks

データメンバー [m_contained](#m_contained) を初期化し、モジュールのロックカウントをインクリメントします。`CComContainedObject`

デストラクターは、モジュールのロックカウントをデクリメントします。

##  <a name="dtor"></a>CComPolyObject:: ~ CComPolyObject

デストラクターです。

```
~CComPolyObject();
```

### <a name="remarks"></a>Remarks

割り当てられたすべてのリソースを解放し、 [FinalRelease](#finalrelease)を呼び出して、モジュールのロックカウントをデクリメントします。

##  <a name="createinstance"></a>  CComPolyObject::CreateInstance

[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)のオーバーヘッドを発生させずに、新しい**CComPolyObject <** `contained` **>** オブジェクトを作成できます。

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>パラメーター

*ページ*<br/>
入出力**CComPolyObject <** `contained` **ポインターへのポインター。>** が`CreateInstance`失敗した場合、 *pp*は NULL に設定されます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

返されるオブジェクトは、参照カウントが0であるため`AddRef` 、をすぐに`Release`呼び出し、を使用してオブジェクトポインターの参照を解放します。

オブジェクトへの直接アクセスが不要でも、の`CoCreateInstance`オーバーヘッドなしで新しいオブジェクトを作成する場合は、代わりに[CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance)を使用します。

##  <a name="finalconstruct"></a>  CComPolyObject::FinalConstruct

オブジェクト構築の最終段階で呼び出されます。このメソッドは、 [m_contained](#m_contained)データメンバーに対して最終的な初期化を実行します。

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="finalrelease"></a>  CComPolyObject::FinalRelease

オブジェクトの破棄中に呼び出されます。このメソッドは、 [m_contained](#m_contained)データメンバーを解放します。

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComPolyObject::m_contained

クラスから派生した[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)オブジェクト。

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>パラメーター

*格納*<br/>
から[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)または[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)から派生したクラス、およびオブジェクトでサポートする他のインターフェイスから派生したクラス。

### <a name="remarks"></a>Remarks

`IUnknown`オブジェクトが`m_contained`集計されている場合、またはオブジェクトが集計されて`IUnknown`いない場合は、このオブジェクトのに対して、による呼び出しがデリゲートされます。

##  <a name="queryinterface"></a>  CComPolyObject::QueryInterface

要求されたインターフェイスへのポインターを取得します。

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>パラメーター

*Q*<br/>
COM インターフェイス。

*iid*<br/>
から要求されているインターフェイスの識別子。

*ppvObject*<br/>
入出力*Iid*によって識別されるインターフェイスポインターへのポインター。 オブジェクトがこのインターフェイスをサポートしていない場合、 *ppvObject*は NULL に設定されます。

*ページ*<br/>
入出力によって`__uuidof(Q)`識別されるインターフェイスへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

集計オブジェクトの場合、要求されたインターフェイス`IUnknown`が`QueryInterface`の場合は、集計されたオブジェクト`IUnknown`自体へのポインターを返し、参照カウントをインクリメントします。 それ以外の場合、このメソッドは`CComContainedObject`データメンバー [m_contained](#m_contained)を通じてインターフェイスを照会します。

##  <a name="release"></a>  CComPolyObject::Release

オブジェクトの参照カウントをデクリメントします。

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>戻り値

デバッグビルドでは`Release` 、診断またはテストに役立つ値が返されます。 Nondebug のビルドで`Release`は、は常に0を返します。

## <a name="see-also"></a>関連項目

[CComObjectRootEx クラス](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
