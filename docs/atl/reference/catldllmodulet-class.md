---
title: CAtlDllModuleT クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
ms.openlocfilehash: be42915c6c2e941bc5fc1de78c5c7ac26ccca6e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247101"
---
# <a name="catldllmodulet-class"></a>CAtlDllModuleT クラス

このクラスは、DLL のモジュールを表します。

## <a name="syntax"></a>構文

```
template <class T>
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
クラスから派生した`CAtlDllModuleT`します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|コンストラクターです。|
|[CAtlDllModuleT:: ~ CAtlDllModuleT](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|DLL をアンロードできるかどうかをテストします。|
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|クラス ファクトリを返します。|
|[CAtlDllModuleT::DllMain](#dllmain)|ダイナミック リンク ライブラリ (DLL) への省略可能なエントリ ポイント。|
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|DLL 内のオブジェクトのシステム レジストリにエントリを追加します。|
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|DLL 内のオブジェクトのシステム レジストリにエントリを削除します。|
|[CAtlDllModuleT::GetClassObject](#getclassobject)|クラス ファクトリを返します。 によって呼び出された[DllGetClassObject](#dllgetclassobject)します。|

## <a name="remarks"></a>Remarks

`CAtlDllModuleT` ダイナミック リンク ライブラリ (DLL) 用のモジュールを表し、すべての DLL プロジェクトで使用される関数を提供します。 この特殊化[CAtlModuleT](../../atl/reference/catlmodulet-class.md)クラスには、登録のサポートが含まれています。

ATL でモジュールの詳細については、次を参照してください。 [ATL モジュール クラス](../../atl/atl-module-classes.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlDllModuleT`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="catldllmodulet"></a>  CAtlDllModuleT::CAtlDllModuleT

コンストラクターです。

```
CAtlDllModuleT() throw();
```

##  <a name="dtor"></a>  CAtlDllModuleT:: ~ CAtlDllModuleT

デストラクターです。

```
~CAtlDllModuleT() throw();
```

##  <a name="dllcanunloadnow"></a>  CAtlDllModuleT::DllCanUnloadNow

DLL をアンロードできるかどうかをテストします。

```
HRESULT DllCanUnloadNow() throw();
```

### <a name="return-value"></a>戻り値

できない場合は、DLL をアンロードできる場合は S_OK または S_FALSE を返します。

##  <a name="dllgetclassobject"></a>  CAtlDllModuleT::DllGetClassObject

クラス ファクトリを返します。

```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>パラメーター

*rclsid*<br/>
作成するオブジェクトの CLSID。

*riid*<br/>
要求されたインターフェイスの IID。

*ppv*<br/>
によって識別されるインターフェイス ポインターへのポインター *riid*します。 オブジェクトは、このインターフェイスをサポートしていない場合*ppv* NULL に設定されます。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="dllmain"></a>  CAtlDllModuleT::DllMain

ダイナミック リンク ライブラリ (DLL) への省略可能なエントリ ポイント。

```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```

### <a name="parameters"></a>パラメーター

*dwReason*<br/>
場合は、DLL_PROCESS_ATTACH、DLL_THREAD_ATTACH および DLL_THREAD_DETACH 通知の呼び出しに設定が無効です。

*lpReserved*<br/>
予約済み。

### <a name="return-value"></a>戻り値

常に TRUE を返します。

### <a name="remarks"></a>Remarks

DLL_THREAD_ATTACH を無効にして、呼び出しは、多くの Dll を持つアプリケーションはマルチ スレッドの有効な最適化を指定できます、DLL_THREAD_DETACH 通知を頻繁に作成し、スレッドを削除、Dll を持つ必要はありませんのこれらのスレッド レベル通知添付ファイル/デタッチできません。

##  <a name="dllregisterserver"></a>  CAtlDllModuleT::DllRegisterServer

DLL 内のオブジェクトのシステム レジストリにエントリを追加します。

```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>パラメーター

*bRegTypeLib*<br/>
TRUE の場合、タイプ ライブラリを登録します。 既定値は TRUE です。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="dllunregisterserver"></a>  CAtlDllModuleT::DllUnregisterServer

DLL 内のオブジェクトのシステム レジストリにエントリを削除します。

```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```

### <a name="parameters"></a>パラメーター

*bUnRegTypeLib*<br/>
タイプ ライブラリは、レジストリから削除する場合は TRUE。 既定値は TRUE です。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="getclassobject"></a>  CAtlDllModuleT::GetClassObject

指定した CLSID のオブジェクトを作成します。

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>パラメーター

*rclsid*<br/>
作成するオブジェクトの CLSID。

*riid*<br/>
要求されたインターフェイスの IID。

*ppv*<br/>
によって識別されるインターフェイス ポインターへのポインター *riid*します。 オブジェクトは、このインターフェイスをサポートしていない場合*ppv* NULL に設定されます。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

このメソッドを呼び出して[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)と下位互換性のために用意されています。

## <a name="see-also"></a>関連項目

[CAtlModuleT クラス](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlExeModuleT クラス](../../atl/reference/catlexemodulet-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[モジュール クラス](../../atl/atl-module-classes.md)
