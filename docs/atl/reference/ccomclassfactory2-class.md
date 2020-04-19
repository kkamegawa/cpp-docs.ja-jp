---
title: CComClassFactory2 クラス
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
ms.openlocfilehash: e34ebffc937c3e4ef1272fdf13ddcde7513d28e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497461"
---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2 クラス

このクラスは、 [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)インターフェイスを実装します。

## <a name="syntax"></a>構文

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>パラメーター

*使用*<br/>
次の静的関数を実装するクラス。

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComClassFactory2:: CreateInstance](#createinstance)|指定された CLSID のオブジェクトを作成します。|
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|ライセンスキーを指定すると、指定した CLSID のオブジェクトが作成されます。|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|クラスファクトリのライセンス機能について説明する情報を取得します。|
|[CComClassFactory2:: LockServer](#lockserver)|メモリ内のクラスファクトリをロックします。|
|[CComClassFactory2::RequestLicKey](#requestlickey)|ライセンスキーを作成して返します。|

## <a name="remarks"></a>Remarks

`CComClassFactory2`[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)の拡張である[IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)インターフェイスを実装します。 `IClassFactory2`ライセンスによってオブジェクトの作成を制御します。 ライセンスされたコンピューターで実行されるクラスファクトリは、実行時ライセンスキーを提供できます。 このライセンスキーを使用すると、アプリケーションは、完全なコンピューターライセンスが存在しない場合にオブジェクトをインスタンス化できます。

ATL オブジェクトは通常、 [CComCoClass](../../atl/reference/ccomcoclass-class.md)から派生することによってクラスファクトリを取得します。 このクラスには、 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)を既定のクラスファクトリとして宣言する[DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)マクロが含まれています。 を使用`CComClassFactory2`するには、オブジェクトのクラス定義で[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)マクロを指定します。 例えば:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`のテンプレートパラメーター `CComClassFactory2`は、 `GetLicenseKey`静的関数`VerifyLicenseKey`、、および`IsLicenseValid`を実装する必要があります。 単純なライセンスクラスの例を次に示します。

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2`との両方`CComClassFactory2Base`の*ライセンス*から派生します。 `CComClassFactory2Base`さらに、は、および`IClassFactory2` `CComObjectRootEx< CComGlobalsThreadModel >`から派生します。

## <a name="inheritance-hierarchy"></a>継承階層

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="createinstance"></a>CComClassFactory2:: CreateInstance

指定した CLSID のオブジェクトを作成し、このオブジェクトへのインターフェイスポインターを取得します。

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>パラメーター

*pUnkOuter*<br/>
からオブジェクトが集計の一部として作成されている場合、 *pUnkOuter*は外側の unknown である必要があります。 それ以外の場合、 *pUnkOuter*は NULL である必要があります。

*riid*<br/>
から要求されたインターフェイスの IID。 *PUnkOuter*が NULL 以外の場合、 *riid*はで`IID_IUnknown`ある必要があります。

*ppvObj*<br/>
入出力*Riid*によって識別されるインターフェイスポインターへのポインター。 オブジェクトがこのインターフェイスをサポートしていない場合、 *ppvObj*は NULL に設定されます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

コンピューターに完全にライセンスを付与する必要があります。 完全なコンピューターライセンスが存在しない場合は、 [CreateInstanceLic](#createinstancelic)を呼び出します。

##  <a name="createinstancelic"></a>  CComClassFactory2::CreateInstanceLic

には、ライセンスキーが`CreateInstanceLic`必要な点を除いて、[CreateInstance](#createinstance) と似ています。

```
STDMETHOD(CreateInstanceLic)(
    IUnknown* pUnkOuter,
    IUnknown* /* pUnkReserved
*/,
    REFIID riid,
    BSTR bstrKey,
    void** ppvObject);
```

### <a name="parameters"></a>パラメーター

*pUnkOuter*<br/>
からオブジェクトが集計の一部として作成されている場合、 *pUnkOuter*は外側の unknown である必要があります。 それ以外の場合、 *pUnkOuter*は NULL である必要があります。

*pUnkReserved*<br/>
から使用しません。 NULL にする必要があります

*riid*<br/>
から要求されたインターフェイスの IID。 *PUnkOuter*が NULL 以外の場合、 *riid*はで`IID_IUnknown`ある必要があります。

*bstrKey*<br/>
から以前にを呼び出したときに`RequestLicKey`取得したランタイムライセンスキー。 このキーは、オブジェクトを作成するために必要です。

*ppvObject*<br/>
入出力*Riid*によって指定されたインターフェイスポインターへのポインター。 オブジェクトがこのインターフェイスをサポートしていない場合、 *ppvObject*は NULL に設定されます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

[Requestのキー](#requestlickey)を使用してライセンスキーを取得できます。 ライセンスされていないコンピューター上にオブジェクトを作成するに`CreateInstanceLic`は、を呼び出す必要があります。

##  <a name="getlicinfo"></a>  CComClassFactory2::GetLicInfo

は、クラスファクトリのライセンス機能を説明する情報を使用し[て、登録](/windows/win32/api/ocidl/ns-ocidl-licinfo)されている情報を格納します。

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>パラメーター

*pLicInfo*<br/>
入出力構造体へ`LICINFO`のポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

この`fRuntimeKeyAvail`構造体のメンバーは、ライセンスキーが指定されているかどうかを示します。これは、クラスファクトリが、ライセンスされていないコンピューター上でオブジェクトを作成できるかどうかを示します。 *FLicVerified*メンバーは、完全なコンピューターライセンスが存在するかどうかを示します。

##  <a name="lockserver"></a>  CComClassFactory2::LockServer

`_Module::Lock` と`_Module::Unlock`をそれぞれ呼び出して、モジュールのロックカウントをインクリメントおよびデクリメントします。

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>パラメーター

*fLock*<br/>
からTRUE の場合、ロック数がインクリメントされます。それ以外の場合は、ロック数が減少します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

`_Module`[CComModule](../../atl/reference/ccommodule-class.md)のグローバルインスタンス、またはそれから派生したクラスを参照します。

を`LockServer`呼び出すことで、クライアントは、複数のオブジェクトをすばやく作成できるように、クラスファクトリに保持できます。

##  <a name="requestlickey"></a>  CComClassFactory2::RequestLicKey

ライセンスキーを作成して返します。この`fRuntimeKeyAvail`とき、使用している場合は[、そのメンバー](/windows/win32/api/ocidl/ns-ocidl-licinfo)が TRUE であることを示します。

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>パラメーター

*dwReserved*<br/>
から使用しません。 ゼロを指定してください。

*pbstrKey*<br/>
入出力ライセンスキーへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

[CreateInstanceLic](#createinstancelic)を呼び出して、ライセンスされていないコンピューターにオブジェクトを作成するには、ライセンスキーが必要です。 が`fRuntimeKeyAvail` FALSE の場合、オブジェクトは完全にライセンスされたコンピューター上でのみ作成できます。

[Get/info](#getlicinfo)を呼び出して、の`fRuntimeKeyAvail`値を取得します。

## <a name="see-also"></a>関連項目

[CComClassFactoryAutoThread クラス](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComClassFactorySingleton クラス](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx クラス](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
