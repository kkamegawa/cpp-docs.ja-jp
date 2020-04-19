---
title: レジストリとタイプ ライブラリに関するグローバル関数
ms.date: 03/27/2019
f1_keywords:
- atlbase/ATL::AtlGetPerUserRegistration
- afxpriv/ATL::AfxRegCreateKey
- afxpriv/ATL::AfxRegDeleteKey
- atlbase/ATL::AtlRegisterTypeLib
- afxpriv/ATL::AfxRegOpenKey
- afxpriv/ATL::AfxRegOpenKeyEx
- afxdisp/ATL::AfxUnregisterPreviewHandler
- atlbase/ATL::AtlSetPerUserRegistration
- atlbase/ATL::AtlUnRegisterTypeLib
- atlbase/ATL::AtlLoadTypeLib
- atlbase/ATL::AtlUpdateRegistryFromResourceD
- atlbase/ATL::RegistryDataExchange
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
ms.openlocfilehash: c5fdaceb47b6cd09dd9d66f26af1337a8dc6bbae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275080"
---
# <a name="registry-and-typelib-global-functions"></a>レジストリとタイプ ライブラリに関するグローバル関数

これらの関数は、読み込みと登録のタイプ ライブラリのサポートを提供します。

> [!IMPORTANT]
>  次の表に示す関数は、Windows ランタイムで実行するアプリケーションでは使用できません。

|||
|-|-|
|[AfxRegCreateKey](#afxregcreatekey)|指定されたレジストリ キーを作成します。|
|[AfxRegDeleteKey](#afxregdeletekey)|指定されたレジストリ キーを削除します。|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|プレビュー ハンドラーを登録するためのヘルパー。|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| プレビュー ハンドラーの登録を解除するヘルパー。 |
|[AtlRegisterTypeLib](#atlregistertypelib)|この関数は、タイプ ライブラリを登録するために呼び出されます。|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|この関数は、タイプ ライブラリの登録を解除するには|
|[AfxRegOpenKey](#afxregopenkey)|指定されたレジストリ キーを開きます。|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|指定されたレジストリ キーを開きます。|
|[AtlLoadTypeLib](#atlloadtypelib)|この関数は、タイプ ライブラリを読み込むために呼び出されます。|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|この関数は、提供されたリソースのレジストリを更新するために呼び出されます。|
|[RegistryDataExchange](#registrydataexchange)|システム レジストリのデータの読み取り/書き込みを行います。 メソッドを呼び出して、[レジストリ データ交換マクロ](../../atl/reference/registry-data-exchange-macros.md)します。|

これらの関数は、情報を格納するプログラムを使用して、レジストリ内のどのノードを制御します。

|||
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|アプリケーションにレジストリのアクセスをリダイレクトするかどうかを取得、 **HKEY_CURRENT_USER** ( **HKCU**) ノードです。|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|アプリケーションにレジストリのアクセスをリダイレクトするかどうかを設定、 **HKEY_CURRENT_USER** ( **HKCU**) ノードです。|

### <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

## <a name="atlgetperuserregistration"></a> AtlGetPerUserRegistration

この関数を使用して、アプリケーションがレジストリ アクセスにリダイレクトするかどうかを判断する、 **HKEY_CURRENT_USER** (**HKCU**) ノードです。

### <a name="syntax"></a>構文

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>パラメーター

*pEnabled*<br/>
[out]TRUE は、レジストリ情報に送られることを示します、 **HKCU**ノードです。FALSE は、アプリケーションが既定のノードにレジストリ情報を書き出すことを示します。 既定のノードが**HKEY_CLASSES_ROOT** (**HKCR**)。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は S_OK、それ以外の場合、HRESULT エラー コード、エラーが発生した場合。

### <a name="remarks"></a>Remarks

既定では、レジストリのリダイレクトが有効になっていません。 このオプションを有効にすると、レジストリへのアクセスにリダイレクトされます**する**します。

リダイレクトはグローバルではありません。 MFC と ATL のフレームワークは、このレジストリのリダイレクトの影響を受けます。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

## <a name="afxregcreatekey"></a> AfxRegCreateKey

指定されたレジストリ キーを作成します。

### <a name="syntax"></a>構文

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>パラメーター

*hKey*<br/>
開いているレジストリ キーへのハンドル。

*いったん*<br/>
この関数を開くか作成するキーの名前。

*phkResult*<br/>
開くか、作成したキーを識別するハンドルを受け取る変数へのポインター。

*pTM*<br/>
ポインターを`CAtlTransactionManager`オブジェクト。

### <a name="return-value"></a>戻り値

関数が成功した場合は、ERROR_SUCCESS を返します。 関数が失敗した場合は、Winerror.h で定義されている 0 以外のエラー コードは、戻り値。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxpriv.h

## <a name="afxregdeletekey"></a> AfxRegDeleteKey

指定されたレジストリ キーを削除します。

### <a name="syntax"></a>構文

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>パラメーター

*hKey*<br/>
開いているレジストリ キーへのハンドル。

*いったん*<br/>
削除するキーの名前。

*pTM*<br/>
ポインターを`CAtlTransactionManager`オブジェクト。

### <a name="return-value"></a>戻り値

関数が成功した場合は、ERROR_SUCCESS を返します。 関数が失敗した場合は、Winerror.h で定義されている 0 以外のエラー コードは、戻り値。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxpriv.h

## <a name="afxregisterpreviewhandler"></a>

プレビュー ハンドラーを登録するためのヘルパー。

### <a name="syntax"></a>構文

```
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);
```

### <a name="parameters"></a>パラメーター

*lpszCLSID*<br/>
ハンドラーの CLSID を指定します。

*lpszShortTypeName*<br/>
ハンドラーの ProgID を指定します。

*lpszFilterExt*<br/>
このハンドラーに登録されているファイル拡張子を指定します。

### <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

##  <a name="atlregistertypelib"></a>  AtlRegisterTypeLib

この関数は、タイプ ライブラリを登録するために呼び出されます。

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>パラメーター

*hInstTypeLib*<br/>
モジュールのインスタンスへのハンドル。

*lpszIndex*<br/>
形式の文字列"\\\N"、N はタイプ ライブラリのリソースの整数インデックス。 インデックスが必要ない場合、NULL を指定できます。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

このヘルパー関数が利用[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)と[CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

## <a name="afxregopenkey"></a> AfxRegOpenKey

指定されたレジストリ キーを開きます。

### <a name="syntax"></a>構文

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>パラメーター

*hKey*<br/>
開いているレジストリ キーへのハンドル。

*いったん*<br/>
この関数を開くか作成するキーの名前。

*phkResult*<br/>
作成されたキーを識別するハンドルを受け取る変数へのポインター。

*pTM*<br/>
ポインターを`CAtlTransactionManager`オブジェクト。

### <a name="return-value"></a>戻り値

関数が成功した場合は、ERROR_SUCCESS を返します。 関数が失敗した場合は、Winerror.h で定義されている 0 以外のエラー コードは、戻り値。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxpriv.h

## <a name="afxregopenkeyex"></a>  AfxRegOpenKeyEx

指定されたレジストリ キーを開きます。

### <a name="syntax"></a>構文

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>パラメーター

*hKey*<br/>
開いているレジストリ キーへのハンドル。

*いったん*<br/>
この関数を開くか作成するキーの名前。

*ulOptions*<br/>
このパラメーターは予約されており、0 にする必要があります。

*samDesired*<br/>
キーに必要なアクセス権を指定するマスク。

*phkResult*<br/>
開いているキーへのハンドルを受け取る変数へのポインター。

*pTM*<br/>
ポインターを`CAtlTransactionManager`オブジェクト。

### <a name="return-value"></a>戻り値

関数が成功した場合は、ERROR_SUCCESS を返します。 関数が失敗した場合は、Winerror.h で定義されている 0 以外のエラー コードは、戻り値。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxpriv.h

## <a name="afxunregisterpreviewhandler"></a> AfxUnregisterPreviewHandler

プレビュー ハンドラーの登録を解除するヘルパー。

### <a name="syntax"></a>構文

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>パラメーター

*lpszCLSID*<br/>
登録解除するハンドラーの CLSID を指定します。

### <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

## <a name="atlsetperuserregistration"></a> AtlSetPerUserRegistration

アプリケーションにレジストリのアクセスをリダイレクトするかどうかを設定、 **HKEY_CURRENT_USER** (**HKCU**) ノードです。

### <a name="syntax"></a>構文

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
[in]TRUE は、レジストリ情報に送られることを示します、 **HKCU**ノードです。FALSE は、アプリケーションが既定のノードにレジストリ情報を書き出すことを示します。 既定のノードが**HKEY_CLASSES_ROOT** (**HKCR**)。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は S_OK、それ以外の場合、HRESULT エラー コード、エラーが発生した場合。

### <a name="remarks"></a>Remarks

既定では、レジストリのリダイレクトが有効になっていません。 このオプションを有効にすると、レジストリへのアクセスにリダイレクトされます**する**します。

リダイレクトはグローバルではありません。 MFC と ATL のフレームワークは、このレジストリのリダイレクトの影響を受けます。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="atlunregistertypelib"></a>  AtlUnRegisterTypeLib

この関数は、タイプ ライブラリの登録を解除するために呼び出されます。

### <a name="syntax"></a>構文

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>パラメーター

*hInstTypeLib*<br/>
モジュールのインスタンスへのハンドル。

*lpszIndex*<br/>
形式の文字列"\\\N"、N はタイプ ライブラリのリソースの整数インデックス。 インデックスが必要ない場合、NULL を指定できます。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

このヘルパー関数が利用[CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib)と[AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="atlloadtypelib"></a>  AtlLoadTypeLib

この関数は、タイプ ライブラリを読み込むために呼び出されます。

### <a name="syntax"></a>構文

```
ATLINLINE ATLAPI AtlLoadTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex,
    BSTR* pbstrPath,
    ITypeLib** ppTypeLib);
```

### <a name="parameters"></a>パラメーター

*hInstTypeLib*<br/>
タイプ ライブラリに関連付けられているモジュールへのハンドルします。

*lpszIndex*<br/>
形式の文字列"\\\N"、N はタイプ ライブラリのリソースの整数インデックス。 インデックスが必要ない場合、NULL を指定できます。

*pbstrPath*<br/>
正常に返された場合は、タイプ ライブラリに関連付けられているモジュールの完全なパスが含まれています。

*ppTypeLib*<br/>
正常に返された場合は、読み込まれたタイプ ライブラリへのポインターへのポインターを格納します。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

このヘルパー関数が利用[AtlRegisterTypeLib](#atlregistertypelib)と[この代替](#atlunregistertypelib)します。

##  <a name="atlupdateregistryfromresourced"></a>  AtlUpdateRegistryFromResourceD

この関数は Visual Studio 2013 で非推奨とされ、Visual Studio 2015 で削除されます。

```
<removed>
```

##  <a name="registrydataexchange"></a>  RegistryDataExchange

システム レジストリのデータの読み取り/書き込みを行います。

### <a name="syntax"></a>構文

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>パラメーター

*pT*<br/>
現在のオブジェクトへのポインター。

*rdxOp*<br/>
どの操作を示す列挙値、関数を実行する必要があります。 使用できる値は、「解説」表を参照してください。

*pItem*<br/>
読み取り、またはレジストリに書き込まれるデータへのポインター。 データでは、レジストリから削除するキーを表すこともできます。 既定値は、NULL です。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

マクロ[BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map)と[END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map)を呼び出す関数に展開`RegistryDataExchange`します。

関数は、操作を実行する必要がありますかを示す列挙値は、次の表に示します。

|列挙値|操作|
|----------------|---------------|
|eReadFromReg|レジストリからデータを読み取ります。|
|eWriteToReg|レジストリにデータを書き込みます。|
|eDeleteFromReg|キーがレジストリから削除します。|

### <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

## <a name="see-also"></a>関連項目

[関数](atl-functions.md)<br/>
[レジストリ データ エクスチェンジに関するマクロ](registry-data-exchange-macros.md)
