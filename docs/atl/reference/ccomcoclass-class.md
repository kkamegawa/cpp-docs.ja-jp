---
title: CComCoClass クラス
ms.date: 11/04/2016
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
ms.openlocfilehash: 5b4e39fa4d93893d288bb8de03d8a71b671be087
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497393"
---
# <a name="ccomcoclass-class"></a>CComCoClass クラス

このクラスには、クラスのインスタンスを作成し、そのプロパティを取得するためのメソッドが用意されています。

## <a name="syntax"></a>構文

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`CComCoClass`派生したクラス。

*pclsid*<br/>
オブジェクトの CLSID へのポインター。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComCoClass:: CreateInstance](#createinstance)|雑音クラスのインスタンスを作成し、インターフェイスを照会します。|
|[CComCoClass:: Error](#error)|雑音クライアントに豊富なエラー情報を返します。|
|[CComCoClass:: GetObjectCLSID](#getobjectclsid)|雑音オブジェクトのクラス識別子を返します。|
|[CComCoClass:: GetObjectDescription](#getobjectdescription)|雑音をオーバーライドして、オブジェクトの説明を返します。|

## <a name="remarks"></a>Remarks

`CComCoClass`オブジェクトの CLSID を取得し、エラー情報を設定し、クラスのインスタンスを作成するためのメソッドを提供します。 オブジェクトマップに登録されているクラスは、 `CComCoClass`から派生する必要があります。

`CComCoClass`では、オブジェクトの既定のクラスファクトリと集計モデルも定義されています。 `CComCoClass`では、次の2つのマクロを使用します。

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)するクラスファクトリを宣言します。

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)オブジェクトを集計できることを宣言します。

クラス定義で別のマクロを指定することで、これらの既定値のいずれかをオーバーライドできます。 たとえば、の`CComClassFactory`代わりに[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)を使用するには、 [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)マクロを指定します。

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="createinstance"></a>CComCoClass:: CreateInstance

Com API `CreateInstance`を使用せずに com オブジェクトのインスタンスを作成し、インターフェイスポインターを取得するには、これらの関数を使用します。

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>パラメーター

*Q*<br/>
*Pp*を介して返される COM インターフェイス。

*punkOuter*<br/>
から外側の不明または集計の不明なコントロールです。

*ページ*<br/>
入出力要求されたインターフェイスポインターを受け取るポインター変数のアドレス (作成が成功した場合)。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。 返される可能性のある戻り値の説明については、Windows SDK の「 [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) 」を参照してください。

### <a name="remarks"></a>Remarks

一般的なオブジェクトの作成には、この関数の最初のオーバーロードを使用します。作成されるオブジェクトを集計する必要がある場合は、2番目のオーバーロードを使用します。

必要な COM オブジェクトを実装する ATL クラス (つまり、 [CComCoClass](../../atl/reference/ccomcoclass-class.md)の最初のテンプレートパラメーターとして使用されるクラス) は、呼び出し元のコードと同じプロジェクトに存在する必要があります。 COM オブジェクトの作成は、この ATL クラスに登録されているクラスファクトリによって実行されます。

これらの関数は、 [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)マクロを使用して外部から作成できないようにしたオブジェクトを作成する場合に便利です。 また、効率を向上させるために COM API を回避する必要がある場合にも役立ちます。

インターフェイス*Q*には、 [__uuidof](../../cpp/uuidof-operator.md)演算子を使用して取得できる IID が関連付けられている必要があることに注意してください。

### <a name="example"></a>例

次の例では`CDocument` 、は、 `IDocument`インターフェイスを実装するから`CComCoClass`派生したウィザードで生成された ATL クラスです。 クラスは、OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO マクロを使用してオブジェクトマップに登録されるため、クライアントが[CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)を使用してドキュメントのインスタンスを作成することはできません。 `CApplication`は、ドキュメントクラスのインスタンスを作成するために、独自の COM インターフェイスの1つにメソッドを提供するコクラスです。 次のコードは、 `CreateInstance` `CComCoClass`基本クラスから継承されたメンバーを使用して、ドキュメントクラスのインスタンスを簡単に作成する方法を示しています。

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

##  <a name="error"></a>CComCoClass:: Error

この静的関数は`IErrorInfo` 、クライアントにエラー情報を提供するインターフェイスを設定します。

```
static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance ());

static HRESULT Error(
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>パラメーター

*lpszDesc*<br/>
からエラーを説明する文字列。 Unicode バージョンの`Error`では、 *lpszdesc*の種類が LPCOLESTR であることが指定されています。 ANSI バージョンでは、LPCSTR の種類が指定されています。

*iid*<br/>
からエラーがオペレーティングシステムによって定義されている場合は、エラーまたは GUID_NULL (既定値) を定義するインターフェイスの IID。

*hRes*<br/>
から呼び出し元に返される HRESULT。 既定値は 0 です。 *Hres*の詳細については、「解説」を参照してください。

*nID*<br/>
からエラー説明文字列が格納されているリソース識別子。 この値は、0x0200 ~ 0xFFFF の範囲で指定する必要があります。 デバッグビルドでは、 *nID*が有効な文字列にインデックスを作成しない場合、**アサート**が発生します。 リリースビルドでは、エラーの説明文字列が "不明なエラー" に設定されます。

*dwHelpID*<br/>
からエラーのヘルプコンテキスト識別子。

*lpszHelpFile*<br/>
からエラーを説明するヘルプファイルのパスと名前。

*hInst*<br/>
からリソースへのハンドル。 既定では、このパラメーター `_AtlModule::GetResourceInstance`はです`_AtlModule` 。ここで、は[CAtlModule](../../atl/reference/catlmodule-class.md)のグローバルインスタンスです。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。 詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

を呼び出す`Error`には、オブジェクトが`ISupportErrorInfo Interface`インターフェイスを実装する必要があります。

*Hres*パラメーターが0以外の場合、 `Error`は*hres*の値を返します。 *Hres*が0の場合、の最初の`Error` 4 つのバージョンは DISP_E_EXCEPTION を返します。 最後の2つのバージョンは、マクロ**MAKE_HRESULT (1, FACILITY_ITF,** *nID* **)** の結果を返します。

##  <a name="getobjectclsid"></a>CComCoClass:: GetObjectCLSID

オブジェクトの CLSID を一貫して取得する方法を提供します。

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>戻り値

オブジェクトのクラス識別子。

##  <a name="getobjectdescription"></a>CComCoClass:: GetObjectDescription

この静的関数は、クラスオブジェクトの説明テキストを取得します。

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>戻り値

クラスオブジェクトの説明。

### <a name="remarks"></a>Remarks

既定の実装では、NULL が返されます。 このメソッドは、 [DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description)マクロを使用してオーバーライドできます。 例えば:

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription`はによっ`IComponentRegistrar::GetComponents`て呼び出されます。 `IComponentRegistrar`は、DLL 内の個々のコンポーネントの登録と登録解除を可能にするオートメーションインターフェイスです。 ATL プロジェクトウィザードを使用してコンポーネントレジストラーオブジェクトを作成すると、ウィザードによって`IComponentRegistrar`インターフェイスが自動的に実装されます。 `IComponentRegistrar`は、通常、Microsoft トランザクションサーバーによって使用されます。

ATL プロジェクトウィザードの詳細については、「 [Atl プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)」を参照してください。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
