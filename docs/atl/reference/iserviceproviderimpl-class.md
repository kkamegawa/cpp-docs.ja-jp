---
title: IServiceProviderImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
ms.openlocfilehash: e52c28d528e187713d2d0925fed23bd8cd4493d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276005"
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderImpl クラス

このクラスの既定の実装を提供する、`IServiceProvider`インターフェイス。

## <a name="syntax"></a>構文

```
template <class T>
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
派生したクラス、`IServiceProviderImpl`します。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IServiceProviderImpl::QueryService](#queryservice)|作成または指定したサービスにアクセスし、サービスの指定したインターフェイスにインターフェイス ポインターを返します。|

## <a name="remarks"></a>Remarks

`IServiceProvider`インターフェイスの GUID で指定されたサービスを検索し、サービスに要求されたインターフェイスのインターフェイス ポインターを返します。 クラス`IServiceProviderImpl`このインターフェイスの既定の実装を提供します。

`IServiceProviderImpl` 1 つのメソッドを指定します。[QueryService](#queryservice)が作成または指定したサービスにアクセスし、サービスの指定したインターフェイスにインターフェイス ポインターを返します。

`IServiceProviderImpl` 以降では、サービス マップを使用して[BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map)で終わる[END_SERVICE_MAP](service-map-macros.md#end_service_map)します。

サービス マップには、2 つのエントリが含まれています。[SERVICE_ENTRY](service-map-macros.md#service_entry)、オブジェクトでサポートされている指定したサービス id (SID) を示すと[SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain)、呼び出す`QueryService`を別のオブジェクトのチェーンにします。

## <a name="inheritance-hierarchy"></a>継承階層

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom.h

##  <a name="queryservice"></a>  IServiceProviderImpl::QueryService

作成または指定したサービスにアクセスし、サービスの指定したインターフェイスにインターフェイス ポインターを返します。

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>パラメーター

*guidService*<br/>
[in]サービス id (SID) へのポインター。

*riid*<br/>
[in]呼び出し元がアクセスできるインターフェイスの識別子です。

*ppvObj*<br/>
[out]要求されたインターフェイスへの間接ポインター。

### <a name="return-value"></a>戻り値

返された HRESULT の値は、次のいずれか。

|戻り値|説明|
|------------------|-------------|
|S_OK|サービスが正常に作成または取得します。|
|E_INVALIDARG|1 つ以上の引数が無効です。|
|E_OUTOFMEMORY|メモリは、サービスを作成するには不十分です。|
|E_UNEXPECTED|不明なエラーが発生しました。|
|E_NOINTERFACE|要求されたインターフェイスは、このサービスの一部ではないか、サービスが既知です。|

### <a name="remarks"></a>Remarks

`QueryService` 指定されたサービスで要求されたインターフェイスへの間接ポインターを返します。 呼び出し元が必要でなくなったときにこのポインターを解放します。

呼び出すと`QueryService`、両方のサービスの識別子を渡す (*guidService*) とインターフェイス識別子 (*riid*)。 *GuidService* 、アクセス サービスを指定します、 *riid*サービスの一部であるインターフェイスを識別します。 代わりに、インターフェイスへの間接ポインターが表示されます。

インターフェイスを実装するオブジェクトは、他のサービスの一部であるインターフェイスを実装も可能性があります。 次に例を示します。

- これらのインターフェイスの一部は、省略可能な可能性があります。 サービスの説明で定義されているすべてのインターフェイスは、サービスのすべての実装またはすべての返されたオブジェクトに必ずしも存在します。

- 呼び出しとは異なり`QueryInterface`、さまざまなサービス識別子を渡すことが必ずしもその別のコンポーネント オブジェクト モデル (COM) オブジェクトが返されます。

- 返されるオブジェクトは、サービスの定義の一部ではない追加のインターフェイスがあります。

SID_SMyService SID_SYourService などの 2 つの異なるサービス両方を指定できます、同じインターフェイスの使用場合でも、何も 2 つのサービスで共通のインターフェイスの実装があります。 この動作を呼び出す`QueryService`よりも、別のオブジェクトを返すことができます (SID_SMyService、IID_IDispatch) `QueryService` (SID_SYourService、IID_IDispatch)。 オブジェクト id が異なるサービスの識別子を指定する場合とは見なされません。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
