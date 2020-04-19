---
title: サーバー登録のグローバル関数
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
ms.openlocfilehash: f9c3697259e1cee2b1107ded785ca583d730b55e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495462"
---
# <a name="server-registration-global-functions"></a>サーバー登録のグローバル関数

これらの関数は、オブジェクトマップ内のサーバーオブジェクトの登録と登録解除をサポートします。

> [!IMPORTANT]
>  次の表に示す関数は、Windows ランタイムで実行するアプリケーションでは使用できません。

|||
|-|-|
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|オブジェクト マップのオブジェクトをすべて登録します。|
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|オブジェクト マップのオブジェクトの登録をすべて解除します。|
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|この関数は、クラス オブジェクトを登録するために呼び出されます。|
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|この関数は、COM モジュールからクラスオブジェクトを取り消すために呼び出されます。|
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|この関数は、クラスオブジェクトを取得するために呼び出されます。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase. h

##  <a name="atlcommoduleregisterserver"></a>  AtlComModuleRegisterServer

オブジェクト マップのオブジェクトをすべて登録します。

```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>パラメーター

*pComModule*<br/>
COM モジュールへのポインター。

*bRegTypeLib*<br/>
タイプライブラリを登録する場合は TRUE。

*pCLSID*<br/>
登録するオブジェクトの CLSID を指します。 NULL の場合、オブジェクトマップ内のすべてのオブジェクトが登録されます。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

`AtlComModuleRegisterServer`ATL によって自動生成されるオブジェクトマップをウォークし、マップ内の各オブジェクトを登録します。 *Pclsid*が NULL でない場合は、 *pclsid*によって参照されるオブジェクトのみが登録されます。それ以外の場合は、すべてのオブジェクトが登録されます。

この関数は、 [CAtlComModule:: RegisterServer](catlcommodule-class.md#registerserver)によって呼び出されます。

##  <a name="atlcommoduleunregisterserver"></a>  AtlComModuleUnregisterServer

オブジェクト マップのオブジェクトの登録をすべて解除します。

```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```

### <a name="parameters"></a>パラメーター

*pComModule*<br/>
COM モジュールへのポインター。

*bUnRegTypeLib*<br/>
タイプライブラリを登録する場合は TRUE。

*pCLSID*<br/>
登録を解除するオブジェクトの CLSID を指します。 NULL の場合、オブジェクトマップ内のすべてのオブジェクトが登録解除されます。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

`AtlComModuleUnregisterServer`ATL オブジェクトマップをウォークし、マップ内の各オブジェクトの登録を解除します。 *Pclsid*が NULL でない場合は、 *pclsid*によって参照されるオブジェクトのみが登録解除されます。それ以外の場合は、すべてのオブジェクトが登録解除されます。

この関数は、 [CAtlComModule:: UnregisterServer](catlcommodule-class.md#unregisterserver)によって呼び出されます。

##  <a name="atlcommoduleregisterclassobjects"></a>AtlComModuleRegisterClassObjects

この関数は、クラス オブジェクトを登録するために呼び出されます。

```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```

### <a name="parameters"></a>パラメーター

*pComModule*<br/>
COM モジュールへのポインター。

*dwClsContext*<br/>
クラスオブジェクトを実行するコンテキストを指定します。 指定できる値は、CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER、または CLSCTX_LOCAL_SERVER です。 詳細については、「 [Clsctx](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) 」を参照してください。

*dwFlags*<br/>
クラスオブジェクトへの接続の種類を決定します。 指定できる値は、REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE、または REGCLS_MULTI_SEPARATE です。 詳細については、「 [Regcls](/windows/win32/api/combaseapi/ne-combaseapi-regcls) 」を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

このヘルパー関数は、 [CComModule:: RegisterClassObjects](ccommodule-class.md#registerclassobjects) (ATL 7.0 では廃止されました) および[CAtlExeModuleT:: RegisterClassObjects](catlexemodulet-class.md#registerclassobjects)によって使用されます。

##  <a name="atlcommodulerevokeclassobjects"></a>AtlComModuleRevokeClassObjects

クラス ファクトリをランニング オブジェクト テーブルから削除します。

```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```

### <a name="parameters"></a>パラメーター

*pComModule*<br/>
COM モジュールへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

このヘルパー関数は、 [CComModule:: RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (ATL 7.0 では廃止されました) および[CAtlExeModuleT:: RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects)によって使用されます。

##  <a name="atlcommodulegetclassobject"></a>  AtlComModuleGetClassObject

この関数は、クラス ファクトリを返すために呼び出されます。

```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```

### <a name="parameters"></a>パラメーター

*pComModule*<br/>
COM モジュールへのポインター。

*rclsid*<br/>
作成するオブジェクトの CLSID。

*riid*<br/>
要求されたインターフェイスの IID。

*ppv*<br/>
*Riid*によって識別されるインターフェイスポインターへのポインター。 オブジェクトがこのインターフェイスをサポートしていない場合、 *ppv*は NULL に設定されます。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

このヘルパー関数は、 [CComModule:: GetClassObject](ccommodule-class.md#getclassobject) (ATL 7.0 では廃止されました) および[Catldllmodulet:: GetClassObject](catldllmodulet-class.md#getclassobject)によって使用されます。

## <a name="see-also"></a>関連項目

[関数](../../atl/reference/atl-functions.md)
