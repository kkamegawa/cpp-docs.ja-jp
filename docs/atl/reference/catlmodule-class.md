---
title: CAtlModule クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlModule
- ATLBASE/ATL::CAtlModule
- ATLBASE/ATL::CAtlModule::CAtlModule
- ATLBASE/ATL::CAtlModule::AddCommonRGSReplacements
- ATLBASE/ATL::CAtlModule::AddTermFunc
- ATLBASE/ATL::CAtlModule::GetGITPtr
- ATLBASE/ATL::CAtlModule::GetLockCount
- ATLBASE/ATL::CAtlModule::Lock
- ATLBASE/ATL::CAtlModule::Term
- ATLBASE/ATL::CAtlModule::Unlock
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceDHelper
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CAtlModule::m_libid
- ATLBASE/ATL::CAtlModule::m_pGIT
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
ms.openlocfilehash: 798e94aed3bbd98108866ce0a1810485bd68699b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497748"
---
# <a name="catlmodule-class"></a>CAtlModule クラス

このクラスは、いくつかの ATL モジュールクラスによって使用されるメソッドを提供します。

## <a name="syntax"></a>構文

```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlModule::CAtlModule](#catlmodule)|コンストラクターです。|
|[CAtlModule:: ~ CAtlModule](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|このメソッドをオーバーライドして、ATL レジストリコンポーネント (レジストラー) の置換マップにパラメーターを追加します。|
|[CAtlModule::AddTermFunc](#addtermfunc)|モジュールが終了したときに呼び出される新しい関数を追加します。|
|[CAtlModule::GetGITPtr](#getgitptr)|グローバルインターフェイスポインターを返します。|
|[CAtlModule::GetLockCount](#getlockcount)|ロック数を返します。|
|[CAtlModule:: Lock](#lock)|ロック数をインクリメントします。|
|[CAtlModule:: Term](#term)|すべてのデータメンバーを解放します。|
|[CAtlModule::Unlock](#unlock)|ロック カウントをデクリメントします。|
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|指定したリソースに含まれているスクリプトを実行して、オブジェクトの登録または登録解除を行います。|
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|このメソッドは、レジストリ`UpdateRegistryFromResourceD`の更新を実行するためにによって呼び出されます。|
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|指定したリソースに含まれているスクリプトを実行して、オブジェクトの登録または登録解除を行います。 このメソッドは、ATL レジストリコンポーネントに静的にリンクします。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CAtlModule::m_libid](#m_libid)|現在のモジュールの GUID を格納します。|
|[CAtlModule::m_pGIT](#m_pgit)|グローバルインターフェイステーブルへのポインター。|

## <a name="remarks"></a>Remarks

このクラスは、 [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)クラスおよび[CAtlServiceModuleT クラス](../../atl/reference/catlservicemodulet-class.md)[によって](../../atl/reference/catldllmodulet-class.md)使用され、それぞれ DLL アプリケーション、EXE アプリケーション、および Windows サービスのサポートを提供します。

ATL のモジュールの詳細については、「 [Atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

このクラスは、以前のバージョンの ATL で使用されていた古い[CComModule クラス](../../atl/reference/ccommodule-class.md)に代わるものです。

## <a name="inheritance-hierarchy"></a>継承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

`CAtlModule`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase. h

##  <a name="addcommonrgsreplacements"></a>  CAtlModule::AddCommonRGSReplacements

このメソッドをオーバーライドして、ATL レジストリコンポーネント (レジストラー) の置換マップにパラメーターを追加します。

```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```

### <a name="parameters"></a>パラメーター

*pRegistrar*<br/>
予約済み。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

置き換え可能パラメーターを使用すると、レジストラーのクライアントは実行時のデータを指定できます。 これを行うために、レジストラーは、スクリプト内の置き換え可能パラメーターに関連付けられた値を入力する置換マップを保持します。 レジストラーは、これらのエントリを実行時に作成します。

詳細については、「[置換可能なパラメーター (レジストラーのプリプロセッサ) の使用](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)」を参照してください。

##  <a name="addtermfunc"></a>  CAtlModule::AddTermFunc

モジュールが終了したときに呼び出される新しい関数を追加します。

```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```

### <a name="parameters"></a>パラメーター

*pFunc*<br/>
追加する関数へのポインター。

*dw*<br/>
関数に渡されるユーザー定義データ。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="catlmodule"></a>CAtlModule::CAtlModule

コンストラクターです。

```
CAtlModule() throw();
```

### <a name="remarks"></a>Remarks

データメンバーを初期化し、モジュールのスレッドの周囲のクリティカルセクションを開始します。

##  <a name="dtor"></a>CAtlModule:: ~ CAtlModule

デストラクターです。

```
~CAtlModule() throw();
```

### <a name="remarks"></a>Remarks

すべてのデータメンバーを解放します。

##  <a name="getgitptr"></a>  CAtlModule::GetGITPtr

グローバルインターフェイステーブルへのポインターを取得します。

```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```

### <a name="parameters"></a>パラメーター

*ppGIT*<br/>
グローバルインターフェイステーブルへのポインターを受け取る変数へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラーコードを返します。 E_POINTER は、 *Ppgit*が NULL と等しい場合に返されます。

### <a name="remarks"></a>Remarks

グローバルインターフェイステーブルオブジェクトが存在しない場合は、そのオブジェクトが作成され、そのアドレスがメンバー変数[CAtlModule:: m_pGIT](#m_pgit)に格納されます。

デバッグビルドでは、 *Ppgit*が NULL と等しい場合、またはグローバルインターフェイステーブルポインターを取得できない場合にアサーションエラーが発生します。

グローバルインターフェイステーブルの詳細については、「 [Igloの interfacetable](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable) 」を参照してください。

##  <a name="getlockcount"></a>  CAtlModule::GetLockCount

ロック数を返します。

```
virtual LONG GetLockCount() throw();
```

### <a name="return-value"></a>戻り値

ロック数を返します。 この値は、診断やデバッグに役立ちます。

##  <a name="lock"></a>  CAtlModule::Lock

ロック数をインクリメントします。

```
virtual LONG Lock() throw();
```

### <a name="return-value"></a>戻り値

ロックカウントをインクリメントし、更新された値を返します。 この値は、診断やデバッグに役立ちます。

##  <a name="m_libid"></a>  CAtlModule::m_libid

現在のモジュールの GUID を格納します。

```
static GUID m_libid;
```

##  <a name="m_pgit"></a>  CAtlModule::m_pGIT

グローバルインターフェイステーブルへのポインター。

```
IGlobalInterfaceTable* m_pGIT;
```

##  <a name="term"></a>  CAtlModule::Term

すべてのデータメンバーを解放します。

```
void Term() throw();
```

### <a name="remarks"></a>Remarks

すべてのデータメンバーを解放します。 このメソッドは、デストラクターによって呼び出されます。

##  <a name="unlock"></a>CAtlModule:: Unlock

ロック カウントをデクリメントします。

```
virtual LONG Unlock() throw();
```

### <a name="return-value"></a>戻り値

ロックカウントをデクリメントし、更新された値を返します。 この値は、診断やデバッグに役立ちます。

##  <a name="updateregistryfromresourced"></a>CAtlModule::UpdateRegistryFromResourceD

指定したリソースに含まれているスクリプトを実行して、オブジェクトの登録または登録解除を行います。

```
HRESULT WINAPI UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*lpszRes*<br/>
リソース名。

*nResID*<br/>
リソース ID。

*bRegister*<br/>
オブジェクトを登録する必要がある場合は TRUE。それ以外の場合は FALSE。

*pMapEntries*<br/>
スクリプトの置き換え可能パラメーターに関連付けられた値を格納する置換マップへのポインター。 ATL は% MODULE% を自動的に使用します。 追加の置き換え可能なパラメーターを使用するには、「 [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements)」を参照してください。 それ以外の場合は、NULL の既定値を使用します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

*Lpszres または nResID*によって指定されたリソースに含まれるスクリプトを実行します。 *Bregister*が TRUE の場合、このメソッドはオブジェクトをシステムレジストリに登録します。それ以外の場合は、レジストリからオブジェクトを削除します。

ATL レジストリコンポーネント (レジストラー) に静的にリンクするには、「 [CAtlModule:: UpdateRegistryFromResourceS](#updateregistryfromresources)」を参照してください。

このメソッド[は、CAtlModule:: UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)と[Iregistrar:: resourceunregister 解除](iregistrar-class.md#resourceunregister)を呼び出します。

##  <a name="updateregistryfromresourcedhelper"></a>CAtlModule::UpdateRegistryFromResourceDHelper

このメソッドは、レジストリ`UpdateRegistryFromResourceD`の更新を実行するためにによって呼び出されます。

```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*lpszRes*<br/>
リソース名。

*bRegister*<br/>
オブジェクトを登録する必要があるかどうかを示します。

*pMapEntries*<br/>
スクリプトの置き換え可能パラメーターに関連付けられた値を格納する置換マップへのポインター。 ATL は% MODULE% を自動的に使用します。 追加の置き換え可能なパラメーターを使用するには、「 [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements)」を参照してください。 それ以外の場合は、NULL の既定値を使用します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

このメソッドは、 [CAtlModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced)の実装を提供します。

##  <a name="updateregistryfromresources"></a>CAtlModule::UpdateRegistryFromResourceS

指定したリソースに含まれているスクリプトを実行して、オブジェクトの登録または登録解除を行います。 このメソッドは、ATL レジストリコンポーネントに静的にリンクします。

```
HRESULT WINAPI UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*nResID*<br/>
リソース ID。

*lpszRes*<br/>
リソース名。

*bRegister*<br/>
リソーススクリプトを登録する必要があるかどうかを示します。

*pMapEntries*<br/>
スクリプトの置き換え可能パラメーターに関連付けられた値を格納する置換マップへのポインター。 ATL は% MODULE% を自動的に使用します。 追加の置き換え可能なパラメーターを使用するには、「 [CAtlModule:: AddCommonRGSReplacements](#addcommonrgsreplacements)」を参照してください。 それ以外の場合は、NULL の既定値を使用します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

[CAtlModule:: UpdateRegistryFromResourceD](#updateregistryfromresourced) `CAtlModule::UpdateRegistryFromResourceS`に似ていますが、ATL レジストリコンポーネント (レジストラー) への静的リンクを作成します。

## <a name="see-also"></a>関連項目

[_ATL_MODULE](atl-typedefs.md#_atl_module)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[モジュールクラス](../../atl/atl-module-classes.md)<br/>
[レジストリ コンポーネント (レジストラー)](../../atl/atl-registry-component-registrar.md)
