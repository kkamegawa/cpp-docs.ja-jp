---
title: CAtlComModule クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
ms.openlocfilehash: 09adcb33ca9e6f8524063130d6aedca044d6ecb5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247192"
---
# <a name="catlcommodule-class"></a>CAtlComModule クラス

このクラスは、COM サーバー モジュールを実装します。

## <a name="syntax"></a>構文

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlComModule::CAtlComModule](#catlcommodule)|コンストラクターです。|
|[CAtlComModule::~CAtlComModule](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|オブジェクト マップ内の各オブジェクトのシステム レジストリを更新するには、このメソッドを呼び出します。|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|タイプ ライブラリを登録するには、このメソッドを呼び出します。|
|[CAtlComModule::UnregisterServer](#unregisterserver)|オブジェクト マップ内の各オブジェクトの登録を解除するには、このメソッドを呼び出します。|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|タイプ ライブラリの登録を解除するには、このメソッドを呼び出します。|

## <a name="remarks"></a>Remarks

`CAtlComModule` クライアントが、モジュールのコンポーネントにアクセスできるよう、COM サーバー モジュールを実装します。

このクラスは廃止された置換[CComModule](../../atl/reference/ccommodule-class.md) ATL の以前のバージョンで使用されるクラス 参照してください[ATL モジュール クラス](../../atl/atl-module-classes.md)の詳細。

## <a name="inheritance-hierarchy"></a>継承階層

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="catlcommodule"></a>  CAtlComModule::CAtlComModule

コンストラクターです。

```
CAtlComModule() throw();
```

### <a name="remarks"></a>Remarks

モジュールを初期化します。

##  <a name="dtor"></a>  CAtlComModule::~CAtlComModule

デストラクターです。

```
~CAtlComModule();
```

### <a name="remarks"></a>Remarks

すべてのクラス ファクトリを解放します。

##  <a name="registerserver"></a>  CAtlComModule::RegisterServer

オブジェクト マップ内の各オブジェクトのシステム レジストリを更新するには、このメソッドを呼び出します。

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>パラメーター

*bRegTypeLib*<br/>
TRUE の場合、タイプ ライブラリを登録します。 既定値は FALSE です。

*pclsid の値*<br/>
登録するオブジェクトの CLSID を指します。 NULL (既定値) の場合は、オブジェクト マップ内のすべてのオブジェクトを登録するかどうか。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

グローバル関数を呼び出す[AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver)します。

##  <a name="registertypelib"></a>  CAtlComModule::RegisterTypeLib

タイプ ライブラリを登録するには、このメソッドを呼び出します。

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>パラメーター

*lpszIndex*<br/>
形式の文字列"\\\N"、N はタイプ ライブラリのリソースの整数インデックス。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

タイプ ライブラリに関する情報をシステム レジストリに追加します。 モジュールのインスタンスに複数のタイプ ライブラリが含まれている場合は、このメソッドの最初のバージョンを使用して、どのタイプ ライブラリを使用する必要がありますを指定します。

##  <a name="unregisterserver"></a>  CAtlComModule::UnregisterServer

オブジェクト マップ内の各オブジェクトの登録を解除するには、このメソッドを呼び出します。

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>パラメーター

*bRegTypeLib*<br/>
タイプ ライブラリは、登録解除する場合は TRUE。 既定値は FALSE です。

*pclsid の値*<br/>
登録解除するオブジェクトの CLSID を指します。 場合は NULL (既定値) の場合は、オブジェクト マップ内のすべてのオブジェクトが登録されます。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

グローバル関数を呼び出す[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)します。

##  <a name="unregistertypelib"></a>  CAtlComModule::UnRegisterTypeLib

タイプ ライブラリの登録を解除するには、このメソッドを呼び出します。

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>パラメーター

*lpszIndex*<br/>
形式の文字列"\\\N"、N はタイプ ライブラリのリソースの整数インデックス。

### <a name="remarks"></a>Remarks

システム レジストリからタイプ ライブラリに関する情報を削除します。 モジュールのインスタンスに複数のタイプ ライブラリが含まれている場合は、このメソッドの最初のバージョンを使用して、どのタイプ ライブラリを使用する必要がありますを指定します。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

## <a name="see-also"></a>関連項目

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
