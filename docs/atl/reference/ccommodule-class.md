---
title: CComModule クラス
ms.date: 08/19/2019
f1_keywords:
- CComModule
- ATLBASE/ATL::CComModule
- ATLBASE/ATL::CComModule::GetClassObject
- ATLBASE/ATL::CComModule::GetModuleInstance
- ATLBASE/ATL::CComModule::GetResourceInstance
- ATLBASE/ATL::CComModule::GetTypeLibInstance
- ATLBASE/ATL::CComModule::Init
- ATLBASE/ATL::CComModule::RegisterClassHelper
- ATLBASE/ATL::CComModule::RegisterClassObjects
- ATLBASE/ATL::CComModule::RegisterServer
- ATLBASE/ATL::CComModule::RegisterTypeLib
- ATLBASE/ATL::CComModule::RevokeClassObjects
- ATLBASE/ATL::CComModule::Term
- ATLBASE/ATL::CComModule::UnregisterClassHelper
- ATLBASE/ATL::CComModule::UnregisterServer
- ATLBASE/ATL::CComModule::UpdateRegistryClass
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CComModule::m_csObjMap
- ATLBASE/ATL::CComModule::m_csTypeInfoHolder
- ATLBASE/ATL::CComModule::m_csWindowCreate
- ATLBASE/ATL::CComModule::m_hInst
- ATLBASE/ATL::CComModule::m_hInstResource
- ATLBASE/ATL::CComModule::m_hInstTypeLib
- ATLBASE/ATL::CComModule::m_pObjMap
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
ms.openlocfilehash: 482f29bae28841ab40ca8a8f80ab7f0df42ddc8b
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630658"
---
# <a name="ccommodule-class"></a>CComModule クラス

Atl 7.0 では、 `CComModule`が非推奨とされます。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComModule:: GetClassObject](#getclassobject)|指定された CLSID のオブジェクトを作成します。 Dll の場合のみ。|
|[CComModule:: GetModuleInstance](#getmoduleinstance)|`m_hInst` を返します。|
|[CComModule:: GetResourceInstance](#getresourceinstance)|`m_hInstResource` を返します。|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|`m_hInstTypeLib` を返します。|
|[CComModule::Init](#init)|データメンバーを初期化します。|
|[CComModule:: RegisterClassHelper](#registerclasshelper)|オブジェクトの標準クラスの登録をシステムレジストリに入力します。|
|[CComModule:: RegisterClassObjects](#registerclassobjects)|クラスオブジェクトを登録します。 Exe の場合のみ。|
|[CComModule:: RegisterServer](#registerserver)|オブジェクトマップ内の各オブジェクトのシステムレジストリを更新します。|
|[CComModule::RegisterTypeLib](#registertypelib)|タイプ ライブラリを登録します。|
|[CComModule:: RevokeClassObjects](#revokeclassobjects)|クラスオブジェクトを取り消します。 Exe の場合のみ。|
|[CComModule:: Term](#term)|データメンバーを解放します。|
|[CComModule:: UnregisterClassHelper](#unregisterclasshelper)|オブジェクトの標準クラスの登録をシステムレジストリから削除します。|
|[CComModule:: UnregisterServer](#unregisterserver)|オブジェクトマップ内の各オブジェクトの登録を解除します。|
|[CComModule:: UpdateRegistryClass](#updateregistryclass)|オブジェクトの標準クラスの登録を登録または登録解除します。|
|[CComModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced)|指定したリソースに含まれているスクリプトを実行して、オブジェクトの登録または登録解除を行います。|
|[CComModule:: UpdateRegistryFromResourceS](#updateregistryfromresources)|ATL レジストリコンポーネントに静的にリンクします。 指定したリソースに含まれているスクリプトを実行して、オブジェクトの登録または登録解除を行います。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CComModule:: m_csObjMap](#m_csobjmap)|オブジェクトマップ情報への同期アクセスを保証します。|
|[CComModule:: m_csTypeInfoHolder](#m_cstypeinfoholder)|タイプライブラリ情報への同期アクセスを保証します。|
|[CComModule:: m_csWindowCreate](#m_cswindowcreate)|ウィンドウの作成時に使用されるウィンドウクラス情報と静的データへの同期アクセスを保証します。|
|[CComModule:: m_hInst](#m_hinst)|モジュールインスタンスへのハンドルを格納します。|
|[CComModule:: m_hInstResource](#m_hinstresource)|既定では、にはモジュールインスタンスへのハンドルが格納されます。|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|既定では、にはモジュールインスタンスへのハンドルが格納されます。|
|[CComModule:: m_pObjMap](#m_pobjmap)|モジュールインスタンスによって管理されるオブジェクトマップを指します。|

## <a name="remarks"></a>Remarks

> [!NOTE]
>  このクラスは非推奨とされており、ATL コード生成ウィザードでは、 [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)および[CAtlModule](../../atl/reference/catlmodule-class.md)派生クラスが使用されるようになりました。 詳細については、「 [ATL モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。 次の情報は、ATL の旧リリースで作成されたアプリケーションで使用されます。 `CComModule`は、後方の機能のために ATL の一部になっています。

`CComModule`COM サーバーモジュールを実装して、クライアントがモジュールのコンポーネントにアクセスできるようにします。 `CComModule`では、DLL (インプロセス) モジュールと EXE (ローカル) モジュールの両方がサポートされています。

インスタンス`CComModule`は、オブジェクトマップを使用して、クラスオブジェクト定義のセットを保持します。 このオブジェクトマップは、構造体の`_ATL_OBJMAP_ENTRY`配列として実装され、次の情報が含まれています。

- システムレジストリにオブジェクトの説明を入力および削除します。

- クラスファクトリを使用したオブジェクトのインスタンス化。

- クライアントと、コンポーネント内のルートオブジェクトとの間の通信を確立します。

- クラスオブジェクトの有効期間の管理を実行しています。

ATL COM AppWizard を実行すると、ウィザードによって`_Module`、の`CComModule`グローバルインスタンス、またはそれから派生したクラスが自動的に生成されます。 ATL プロジェクトウィザードの詳細については、「 [Atl プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)」を参照してください。

に`CComModule`加えて、ATL には、exe および Windows サービス用のアパートメントモデルモジュールを実装する[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)が用意されています。 複数のアパートメントで`CComAutoThreadModule`オブジェクトを作成する場合は、からモジュールを派生させます。

## <a name="inheritance-hierarchy"></a>継承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase. h

##  <a name="getclassobject"></a>CComModule:: GetClassObject

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>パラメーター

*rclsid*<br/>
から作成するオブジェクトの CLSID。

*riid*<br/>
から要求されたインターフェイスの IID。

*ppv*<br/>
入出力*Riid*によって識別されるインターフェイスポインターへのポインター。 オブジェクトがこのインターフェイスをサポートしていない場合、 *ppv*は NULL に設定されます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

指定した CLSID のオブジェクトを作成し、このオブジェクトへのインターフェイスポインターを取得します。

`GetClassObject`は、Dll でのみ使用できます。

##  <a name="getmoduleinstance"></a>CComModule:: GetModuleInstance

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>戻り値

このモジュールを識別する HINSTANCE。

### <a name="remarks"></a>Remarks

[M_hInst](#m_hinst)データメンバーを返します。

##  <a name="getresourceinstance"></a>  CComModule::GetResourceInstance

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>戻り値

HINSTANCE。

### <a name="remarks"></a>Remarks

[M_hInstResource](#m_hinstresource)データメンバーを返します。

##  <a name="gettypelibinstance"></a>  CComModule::GetTypeLibInstance

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>戻り値

HINSTANCE。

### <a name="remarks"></a>Remarks

[M_hInstTypeLib](#m_hinsttypelib)データメンバーを返します。

##  <a name="init"></a>  CComModule::Init

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
からオブジェクトマップエントリの配列へのポインター。

*h*<br/>
からまたは`DLLMain` `WinMain`に渡される HINSTANCE。

*plibid*<br/>
からプロジェクトに関連付けられているタイプライブラリの LIBID へのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

すべてのデータメンバーを初期化します。

##  <a name="m_csobjmap"></a>  CComModule::m_csObjMap

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Remarks

オブジェクトマップへの同期アクセスを保証します。

##  <a name="m_cstypeinfoholder"></a>  CComModule::m_csTypeInfoHolder

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Remarks

タイプライブラリへの同期アクセスを保証します。

##  <a name="m_cswindowcreate"></a>CComModule:: m_csWindowCreate

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Remarks

ウィンドウクラスの情報と、ウィンドウの作成時に使用される静的データへの同期アクセスを保証します。

##  <a name="m_hinst"></a>  CComModule::m_hInst

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Remarks

モジュールインスタンスへのハンドルを格納します。

[Init](#init)メソッドは、 `m_hInst`または`WinMain`に`DLLMain`渡されるハンドルにを設定します。

##  <a name="m_hinstresource"></a>  CComModule::m_hInstResource

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Remarks

既定では、にはモジュールインスタンスへのハンドルが格納されます。

[Init](#init)メソッドは、 `m_hInstResource`または`WinMain`に`DLLMain`渡されるハンドルにを設定します。 明示的にリソース`m_hInstResource`をハンドルするように設定できます。

[Getresourceinstance](#getresourceinstance)メソッドは、に`m_hInstResource`格納されているハンドルを返します。

##  <a name="m_hinsttypelib"></a>  CComModule::m_hInstTypeLib

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Remarks

既定では、にはモジュールインスタンスへのハンドルが格納されます。

[Init](#init)メソッドは、 `m_hInstTypeLib`または`WinMain`に`DLLMain`渡されるハンドルにを設定します。 を明示的に`m_hInstTypeLib`タイプライブラリへのハンドルに設定できます。

[GetTypeLibInstance](#gettypelibinstance)メソッドは、に`m_hInstTypeLib`格納されているハンドルを返します。

##  <a name="m_pobjmap"></a>  CComModule::m_pObjMap

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Remarks

モジュールインスタンスによって管理されるオブジェクトマップを指します。

##  <a name="registerclasshelper"></a>CComModule:: RegisterClassHelper

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
ATL_DEPRECATED HRESULT RegisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>パラメーター

*clsid*<br/>
から登録するオブジェクトの CLSID。

*lpszProgID*<br/>
からオブジェクトに関連付けられている ProgID。

*lpszVerIndProgID*<br/>
からオブジェクトに関連付けられているバージョンに依存しない ProgID。

*nDescID*<br/>
からオブジェクトの説明の文字列リソースの識別子。

*dwFlags*<br/>
からレジストリに入力するスレッド処理モデルを指定します。 指定できる値は、THREADFLAGS_APARTMENT、THREADFLAGS_BOTH、または AUTPRXFLAG です。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

オブジェクトの標準クラスの登録をシステムレジストリに入力します。

[UpdateRegistryClass](#updateregistryclass)メソッドはを`RegisterClassHelper`呼び出します。

##  <a name="registerclassobjects"></a>CComModule:: RegisterClassObjects

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>パラメーター

*dwClsContext*<br/>
からクラスオブジェクトを実行するコンテキストを指定します。 指定できる値は、CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER、または CLSCTX_LOCAL_SERVER です。 これらの値の詳細については、Windows SDK の「 [Clsctx](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) 」を参照してください。

*dwFlags*<br/>
からクラスオブジェクトへの接続の種類を決定します。 指定できる値は、REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE、または REGCLS_MULTI_SEPARATE です。 これらの値の詳細については、Windows SDK の「 [Regcls](/windows/win32/api/combaseapi/ne-combaseapi-regcls) 」を参照してください。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

他のアプリケーションが接続できるように、EXE クラスのオブジェクトを OLE に登録します。 このメソッドは、Exe でのみ使用できます。

##  <a name="registerserver"></a>  CComModule::RegisterServer

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*bRegTypeLib*<br/>
からタイプライブラリを登録するかどうかを示します。 既定値は FALSE です。

*pCLSID*<br/>
から登録するオブジェクトの CLSID を指します。 NULL (既定値) の場合、オブジェクトマップ内のすべてのオブジェクトが登録されます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

*Pclsid*パラメーターに応じて、によって、単一のクラスオブジェクトまたはオブジェクトマップ内のすべてのオブジェクトのシステムレジストリが更新されます。

*Bregtypelib*が TRUE の場合は、タイプライブラリ情報も更新されます。

オブジェクトマップにエントリを追加する方法については、「 [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) 」を参照してください。

`RegisterServer`は、DLL に対し`DLLRegisterServer`て、 `WinMain`または`/RegServer`コマンドラインオプションを指定して実行される EXE によって、によって自動的に呼び出されます。

##  <a name="registertypelib"></a>  CComModule::RegisterTypeLib

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>パラメーター

*lpszIndex*<br/>
から形式`"\\N"`の文字列。ここ`N`で、は TYPELIB リソースの整数インデックスです。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

タイプライブラリに関する情報をシステムレジストリに追加します。

モジュールインスタンスに複数のタイプライブラリが含まれている場合は、このメソッドの2番目のバージョンを使用して、使用するタイプライブラリを指定します。

##  <a name="revokeclassobjects"></a>  CComModule::RevokeClassObjects

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

クラスオブジェクトを削除します。 このメソッドは、Exe でのみ使用できます。

##  <a name="term"></a>CComModule:: Term

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
void Term() throw();
```

### <a name="remarks"></a>Remarks

すべてのデータメンバーを解放します。

##  <a name="unregisterclasshelper"></a>CComModule:: UnregisterClassHelper

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>パラメーター

*clsid*<br/>
から登録を解除するオブジェクトの CLSID。

*lpszProgID*<br/>
からオブジェクトに関連付けられている ProgID。

*lpszVerIndProgID*<br/>
からオブジェクトに関連付けられているバージョンに依存しない ProgID。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

オブジェクトの標準クラスの登録をシステムレジストリから削除します。

[UpdateRegistryClass](#updateregistryclass)メソッドはを`UnregisterClassHelper`呼び出します。

##  <a name="unregisterserver"></a>  CComModule::UnregisterServer

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>パラメーター

*bUnRegTypeLib*<br/>
TRUE の場合、タイプライブラリも登録解除されます。

*pCLSID*<br/>
登録を解除するオブジェクトの CLSID を指します。 NULL (既定値) の場合、オブジェクトマップ内のすべてのオブジェクトの登録が解除されます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

*Pclsid*パラメーターに応じて、は、単一のクラスオブジェクトまたはオブジェクトマップ内のすべてのオブジェクトの登録を解除します。

`UnregisterServer`は、DLL に対し`DLLUnregisterServer`て、 `WinMain`または`/UnregServer`コマンドラインオプションを指定して実行される EXE によって、によって自動的に呼び出されます。

オブジェクトマップにエントリを追加する方法については、「 [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) 」を参照してください。

##  <a name="updateregistryclass"></a>CComModule:: UpdateRegistryClass

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
ATL_DEPRECATED HRESULT UpdateRegistryClass(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags,
    BOOL bRegister);

ATL_DEPRECATED HRESULT UpdateRegistryClass(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    LPCTSTR szDesc,
    DWORD dwFlags,
    BOOL bRegister);
```

### <a name="parameters"></a>パラメーター

*clsid*<br/>
登録または登録解除するオブジェクトの CLSID。

*lpszProgID*<br/>
オブジェクトに関連付けられている ProgID。

*lpszVerIndProgID*<br/>
オブジェクトに関連付けられているバージョンに依存しない ProgID。

*nDescID*<br/>
オブジェクトの説明の文字列リソースの識別子。

*szDesc*<br/>
オブジェクトの説明を表す文字列です。

*dwFlags*<br/>
レジストリに入力するスレッド処理モデルを指定します。 指定できる値は、THREADFLAGS_APARTMENT、THREADFLAGS_BOTH、または AUTPRXFLAG です。

*bRegister*<br/>
オブジェクトを登録する必要があるかどうかを示します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

*Bregister*が TRUE の場合、このメソッドはオブジェクトの標準クラスの登録をシステムレジストリに入力します。

*Bregister*が FALSE の場合は、オブジェクトの登録が削除されます。

*Bregister*の値に応じて、 `UpdateRegistryClass`は[RegisterClassHelper](#registerclasshelper)または[UnregisterClassHelper](#unregisterclasshelper)のいずれかを呼び出します。

[DECLARE_REGISTRY](registry-macros.md#declare_registry)マクロを指定すること`UpdateRegistryClass`により、オブジェクトマップが処理されるときにが自動的に呼び出されます。

##  <a name="updateregistryfromresourced"></a>CComModule:: UpdateRegistryFromResourceD

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
virtual HRESULT UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw ();
```

### <a name="parameters"></a>パラメーター

*lpszRes*<br/>
からリソース名。

*nResID*<br/>
からリソース ID。

*bRegister*<br/>
からオブジェクトを登録する必要があるかどうかを示します。

*pMapEntries*<br/>
からスクリプトの置き換え可能パラメーターに関連付けられた値を格納する置換マップへのポインター。 ATL はを`%MODULE%`自動的に使用します。 追加の置き換え可能パラメーターを使用するには、詳細について「解説」を参照してください。 それ以外の場合は、NULL の既定値を使用します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

*Lpszres*または*nResID*によって指定されたリソースに含まれるスクリプトを実行します。

*Bregister*が TRUE の場合、このメソッドはオブジェクトをシステムレジストリに登録します。それ以外の場合は、オブジェクトの登録を解除します。

[DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource)または[DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid)マクロを指定する`UpdateRegistryFromResourceD`ことにより、オブジェクトマップが処理されるときにが自動的に呼び出されます。

> [!NOTE]
>  実行時に置換値を置き換えるには、DECLARE_REGISTRY_RESOURCE マクロまたは DECLARE_REGISTRY_RESOURCEID マクロを指定しないでください。 代わりに、構造体の`_ATL_REGMAP_ENTRIES`配列を作成します。各エントリには、実行時にプレースホルダーを置き換える値と組み合わせた変数プレースホルダーが含まれています。 次に`UpdateRegistryFromResourceD`、を呼び出し、 *pmapentries*パラメーターの配列を渡します。 これにより、 `_ATL_REGMAP_ENTRIES`構造体のすべての置換値がレジストラーの置換マップに追加されます。

> [!NOTE]
>  ATL レジストリコンポーネント (レジストラー) に静的にリンクするには、「 [UpdateRegistryFromResourceS](#updateregistryfromresources)」を参照してください。

置換可能なパラメーターとスクリプトの詳細については、「 [ATL レジストリコンポーネント (レジストラー)](../../atl/atl-registry-component-registrar.md)」を参照してください。

##  <a name="updateregistryfromresources"></a>CComModule:: UpdateRegistryFromResourceS

Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
virtual HRESULT UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*lpszRes*<br/>
からリソース名。

*nResID*<br/>
からリソース ID。

*bRegister*<br/>
からリソーススクリプトを登録する必要があるかどうかを示します。

*pMapEntries*<br/>
からスクリプトの置き換え可能パラメーターに関連付けられた値を格納する置換マップへのポインター。 ATL はを`%MODULE%`自動的に使用します。 追加の置き換え可能パラメーターを使用するには、詳細について「解説」を参照してください。 それ以外の場合は、NULL の既定値を使用します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

[UpdateRegistryFromResourceD](#updateregistryfromresourced) `UpdateRegistryFromResourceS`と同様に、ATL レジストリコンポーネント (レジストラー) への静的リンクを作成します。

`UpdateRegistryFromResourceS`は、オブジェクトマップが処理されると自動的に呼び出されます`#define _ATL_STATIC_REGISTRY` *。* これは、Visual Studio 2017 以前のバージョンである*stdafx.h*に追加した場合に実行されます。

> [!NOTE]
>  実行時に置換値を置き換えるには、 [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource)マクロまたは[DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid)マクロを指定しないでください。 代わりに、構造体の`_ATL_REGMAP_ENTRIES`配列を作成します。各エントリには、実行時にプレースホルダーを置き換える値と組み合わせた変数プレースホルダーが含まれています。 次に`UpdateRegistryFromResourceS`、を呼び出し、 *pmapentries*パラメーターの配列を渡します。 これにより、 `_ATL_REGMAP_ENTRIES`構造体のすべての置換値がレジストラーの置換マップに追加されます。

置換可能なパラメーターとスクリプトの詳細については、「 [ATL レジストリコンポーネント (レジストラー)](../../atl/atl-registry-component-registrar.md)」を参照してください。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
