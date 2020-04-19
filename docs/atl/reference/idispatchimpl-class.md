---
title: IDispatchImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
ms.openlocfilehash: 7e9cb903742cdc31c1d9bba2c4aabbb0472407c1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495956"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl クラス

デュアルインターフェイスの`IDispatch`一部の既定の実装を提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<class T,
        const IID* piid= &__uuidof(T),
        const GUID* plibid = &CAtlModule::m_libid,
        WORD wMajor = 1,
        WORD wMinor = 0,
        class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IDispatchImpl : public T
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
からデュアルインターフェイス。

*piid*<br/>
から*T*の IID へのポインター。

*plibid*<br/>
からインターフェイスに関する情報を格納しているタイプライブラリの LIBID へのポインター。 既定では、サーバーレベルのタイプライブラリが渡されます。

*wMajor*<br/>
からタイプライブラリのメジャーバージョンです。 既定値は1です。

*wMinor*<br/>
からタイプライブラリのマイナーバージョン。 既定値は0です。

*tihclass*<br/>
から*T*の型情報の管理に使用されるクラス。既定では、値は `CComTypeInfoHolder` です。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[IDispatchImpl:: IDispatchImpl](#idispatchimpl)|コンストラクターです。 デュアル`AddRef`インターフェイスの型情報を管理するプロテクトメンバー変数に対してを呼び出します。 このデストラクターは `Release` を呼び出します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IDispatchImpl:: Idispatch.getidsofnames](#getidsofnames)|一連の名前を対応する一連のディスパッチ識別子に割り当てます。|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|デュアルインターフェイスの型情報を取得します。|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|デュアルインターフェイスに使用できる型情報があるかどうかを判断します。|
|[IDispatchImpl::Invoke](#invoke)|デュアルインターフェイスによって公開されるメソッドとプロパティへのアクセスを提供します。|

## <a name="remarks"></a>Remarks

`IDispatchImpl`オブジェクトの任意のデュアルインターフェイス`IDispatch`の一部の既定の実装を提供します。 デュアルインターフェイスはから`IDispatch`派生し、オートメーションと互換性のある型のみを使用します。 デュアルインターフェイスは、ディスパッチインターフェイスと同様に、事前バインディングと遅延バインディングをサポートします。ただし、デュアルインターフェイスでは、vtable バインドもサポートされています。

次の例は、の`IDispatchImpl`一般的な実装を示しています。

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

既定では、 `IDispatchImpl`クラスは、レジストリ内の*T*の型情報を検索します。 登録されていないインターフェイスを実装する`IDispatchImpl`には、定義済みのバージョン番号を使用してレジストリにアクセスすることなく、クラスを使用できます。 Wmajor と 0xffff `IDispatchImpl`の値が*wmajor*の値として0xffff のオブジェクトを作成した場合、クラス`IDispatchImpl`はレジストリではなく .dll ファイルからタイプライブラリを取得します。

`IDispatchImpl`デュアルインターフェイスの型情報を`CComTypeInfoHolder`管理する型の静的メンバーを格納します。 同じデュアルインターフェイスを実装する複数のオブジェクトがある場合は、の`CComTypeInfoHolder`インスタンスを1つだけ使用します。

## <a name="inheritance-hierarchy"></a>継承階層

`T`

`IDispatchImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="getidsofnames"></a>IDispatchImpl:: Idispatch.getidsofnames

一連の名前を対応する一連のディスパッチ識別子に割り当てます。

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IDispatch:: idispatch.getidsofnames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) 」を参照してください。

##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo

デュアルインターフェイスの型情報を取得します。

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IDispatch:: GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) 」を参照してください。

##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount

デュアルインターフェイスに使用できる型情報があるかどうかを判断します。

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Remarks

Windows SDK `IDispatch::GetTypeInfoCount`の「」を参照してください。

##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl

コンストラクターです。 デュアル`AddRef`インターフェイスの型情報を管理するプロテクトメンバー変数に対してを呼び出します。 このデストラクターは `Release` を呼び出します。

```
IDispatchImpl();
```

##  <a name="invoke"></a>  IDispatchImpl::Invoke

デュアルインターフェイスによって公開されるメソッドとプロパティへのアクセスを提供します。

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* pexcepinfo,
    UINT* puArgErr);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) 」を参照してください。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
