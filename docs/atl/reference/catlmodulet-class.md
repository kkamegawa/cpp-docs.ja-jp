---
title: CAtlModuleT クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlModuleT
- ATLBASE/ATL::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::InitLibId
- ATLBASE/ATL::CAtlModuleT::RegisterAppId
- ATLBASE/ATL::CAtlModuleT::RegisterServer
- ATLBASE/ATL::CAtlModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlModuleT::UnregisterServer
- ATLBASE/ATL::CAtlModuleT::UpdateRegistryAppId
helpviewer_keywords:
- CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
ms.openlocfilehash: 2cd207038a92b944bf95575f0e0c820b8f09d615
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260150"
---
# <a name="catlmodulet-class"></a>CAtlModuleT クラス

このクラスは、ATL モジュールを実装します。

## <a name="syntax"></a>構文

```
template <class T>
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
クラスから派生した`CAtlModuleT`します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlModuleT::InitLibId](#initlibid)|現在のモジュールの GUID を格納しているデータ メンバーを初期化します。|
|[CAtlModuleT::RegisterAppId](#registerappid)|レジストリに、exe ファイルを追加します。|
|[CAtlModuleT::RegisterServer](#registerserver)|レジストリにサービスを追加します。|
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|レジストリからの exe ファイルを削除します。|
|[CAtlModuleT::UnregisterServer](#unregisterserver)|レジストリからサービスを削除します。|
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|レジストリ内の EXE の情報を更新します。|

## <a name="remarks"></a>Remarks

`CAtlModuleT`、から派生した[CAtlModule](../../atl/reference/catlmodule-class.md)、実行可能ファイル (EXE) またはサービス (EXE) ATL モジュールを実装します。 実行可能モジュールは、サービス モジュールは Windows の起動時に、バック グラウンドで実行されている Windows アプリケーションのローカルのアウト プロセス サーバー、です。

`CAtlModuleT` 初期化、登録、およびモジュールの登録を解除するには、サポートを提供します。

## <a name="inheritance-hierarchy"></a>継承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`CAtlModuleT`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="catlmodulet"></a>  CAtlModuleT::CAtlModuleT

コンストラクターです。

```
CAtlModuleT() throw();
```

### <a name="remarks"></a>Remarks

呼び出し[CAtlModuleT::InitLibId](#initlibid)します。

##  <a name="initlibid"></a>  CAtlModuleT::InitLibId

現在のモジュールの GUID を格納しているデータ メンバーを初期化します。

```
static void InitLibId() throw();
```

### <a name="remarks"></a>Remarks

コンス トラクターによって呼び出される[CAtlModuleT::CAtlModuleT](#catlmodulet)します。

##  <a name="registerappid"></a>  CAtlModuleT::RegisterAppId

レジストリに、exe ファイルを追加します。

```
HRESULT RegisterAppId() throw();
```

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="registerserver"></a>  CAtlModuleT::RegisterServer

レジストリにサービスを追加します。

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*bRegTypeLib*<br/>
TRUE の場合、タイプ ライブラリを登録します。 既定値は FALSE です。

*pclsid の値*<br/>
登録するオブジェクトの CLSID を指します。 NULL (既定値) の場合は、オブジェクト マップ内のすべてのオブジェクトを登録するかどうか。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="unregisterappid"></a>  CAtlModuleT::UnregisterAppId

レジストリからの exe ファイルを削除します。

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="unregisterserver"></a>  CAtlModuleT::UnregisterServer

レジストリからサービスを削除します。

```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*bUnRegTypeLib*<br/>
タイプ ライブラリが登録解除するにもある場合は TRUE。

*pclsid の値*<br/>
登録解除するオブジェクトの CLSID を指します。 場合は NULL (既定値) の場合は、オブジェクト マップ内のすべてのオブジェクトが登録されます。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="updateregistryappid"></a>  CAtlModuleT::UpdateRegistryAppId

レジストリ内の EXE の情報を更新します。

```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```

### <a name="parameters"></a>パラメーター

*bRegister*<br/>
予約済み。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

## <a name="see-also"></a>関連項目

[CAtlModule クラス](../../atl/reference/catlmodule-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[モジュール クラス](../../atl/atl-module-classes.md)
