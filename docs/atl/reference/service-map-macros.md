---
title: サービス マップに関するマクロ
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: ab130b2401dc9885f82fd5668a2d722a96dd289b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274565"
---
# <a name="service-map-macros"></a>サービス マップに関するマクロ

これらのマクロは、サービス マップとエントリを定義します。

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|ATL サービス マップの先頭をマークします。|
|[END_SERVICE_MAP](#end_service_map)|ATL サービス マップの末尾をマークします。|
|[SERVICE_ENTRY](#service_entry)|オブジェクトが特定のサービス ID をサポートしていることを示します。|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|指示[IServiceProviderImpl::QueryService](#queryservice)チェーンして、指定されたオブジェクト。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom.h

##  <a name="begin_service_map"></a>  BEGIN_SERVICE_MAP

サービス マップの先頭をマークします。

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
[in]サービス マップを含むクラスを指定します。

### <a name="remarks"></a>Remarks

サービス マップを使用すると、COM オブジェクトをサービス プロバイダーの機能を実装します。 クラスを派生する必要があります最初に、 [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)します。 2 つの種類のエントリがあります。

- [SERVICE_ENTRY](#service_entry)指定したサービス ID (SID) のサポートを示します。

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)ように指示[IServiceProviderImpl::QueryService](#queryservice) 、別の指定したオブジェクトにチェーンします。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

##  <a name="end_service_map"></a>  END_SERVICE_MAP

サービス マップの最後をマークします。

```
END_SERVICE_MAP()
```

### <a name="example"></a>例

例をご覧ください[BEGIN_SERVICE_MAP](#begin_service_map)します。

##  <a name="service_entry"></a>  SERVICE_ENTRY

オブジェクトで指定したサービス id をサポートしていることを示します*SID*します。

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>パラメーター

*SID*<br/>
サービス id です。

### <a name="example"></a>例

例をご覧ください[BEGIN_SERVICE_MAP](#begin_service_map)します。

##  <a name="service_entry_chain"></a>  SERVICE_ENTRY_CHAIN

指示[IServiceProviderImpl::QueryService](#queryservice)で指定されたオブジェクトをチェーンする*punk*します。

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>パラメーター

*punk*<br/>
ポインター、 **IUnknown**チェーンにするインターフェイス。

### <a name="example"></a>例

例をご覧ください[BEGIN_SERVICE_MAP](#begin_service_map)します。

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

[[マクロ]](../../atl/reference/atl-macros.md)
