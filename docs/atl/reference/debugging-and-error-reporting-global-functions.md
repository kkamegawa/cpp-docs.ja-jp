---
title: デバッグとエラー報告に関するグローバル関数
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: f7483b7473383958089b0c88d0b3c2645ddc2a4f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276667"
---
# <a name="debugging-and-error-reporting-global-functions"></a>デバッグとエラー報告に関するグローバル関数

これらの関数は、便利なデバッグとトレース機能を提供します。

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|返します、 `GetLastError` HRESULT の形式でのエラー コード。|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Win32 エラー コードを HRESULT に変換します。|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|設定`IErrorInfo`をクライアントにエラーの詳細を提供します。|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|`CAtlException` をスローします。|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Windows の `GetLastError` 関数の結果に基づいてエラーを通知します。|

##  <a name="atlhresultfromlasterror"></a>  AtlHresultFromLastError

呼び出し側スレッドの直前のエラー コード値を HRESULT の形式で返します。

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>Remarks

`AtlHresultFromLastError` 呼び出し`GetLastError`最後のエラーを取得して、HRESULT_FROM_WIN32 マクロを使用して、HRESULT に変換してから、エラーが返されます。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlcomcli.h

##  <a name="atlhresultfromwin32"></a>  AtlHresultFromWin32

Win32 エラー コードを HRESULT に変換します。

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>パラメーター

*error*<br/>
変換するエラー値。

### <a name="remarks"></a>Remarks

Win32 エラー コードを HRESULT_FROM_WIN32 マクロを使用して、HRESULT に変換します。

> [!NOTE]
>  使用する代わりに`HRESULT_FROM_WIN32(GetLastError())`、関数を使用して[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlcomcli.h

##  <a name="atlreporterror"></a>  AtlReportError

設定、`IErrorInfo`オブジェクトのクライアントにエラー情報を提供するインターフェイス。

```
HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>パラメーター

*clsid*<br/>
[in]エラーを報告するオブジェクトの CLSID。

*lpszDesc*<br/>
[in]エラーを説明する文字列。 Unicode バージョンを指定する*lpszDesc*の入力 LPCOLESTR; ANSI バージョンは、LPCSTR の種類を指定します。

*iid*<br/>
[in]エラーがオペレーティング システムによって定義されている場合は、エラーまたは GUID_ を定義するインターフェイスの IID。

*hRes*<br/>
[in]呼び出し元に必要な HRESULT が返されます。

*nID*<br/>
[in]エラー説明文字列が格納されているリソースの識別子です。 この値は 0x0200 と 0 xffff の範囲である必要があります。 デバッグ ビルドで、 **ASSERT**なります*nID*有効な文字列のインデックスを作成しません。 リリース ビルドでエラーを説明する文字列を「不明なエラー」に設定されます。

*dwHelpID*<br/>
[in]エラーのヘルプ コンテキスト識別子。

*lpszHelpFile*<br/>
[in]パスとエラーを説明するヘルプ ファイルの名前。

*hInst*<br/>
[in]リソースへのハンドル。 このパラメーターは、既定では、`__AtlBaseModuleModule::GetResourceInstance`ここで、`__AtlBaseModuleModule`のグローバル インスタンス[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)またはその派生クラス。

### <a name="return-value"></a>戻り値

場合、 *hRes*パラメーターが 0 以外の場合は、値を返します*hRes*します。 場合*hRes*が 0 の最初の 4 つのバージョン`AtlReportError`DISP_E_EXCEPTION を返します。 最後の 2 つのバージョンが、マクロの結果を返す**MAKE_HRESULT (1, FACILITY_ITF、** `nID` **)** します。

### <a name="remarks"></a>Remarks

文字列*lpszDesc*エラーの説明テキストとして使用されます。 クライアントが受信すると、 *hRes*から返す`AtlReportError`、クライアントがアクセスできる、`IErrorInfo`エラーの詳細の構造。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
>  使用しない`AtlReportError`C++ の catch ハンドラー。 これらの関数の一部のオーバーライドを使用して、ATL 文字列変換マクロは、内部的には、使用される、`_alloca`関数を内部的にします。 使用して`AtlReportError`C++ catch ハンドラーの C++ の catch ハンドラーで例外が発生します。

### <a name="requirements"></a>必要条件

**ヘッダー:** atlcom.h

##  <a name="atlthrow"></a>  AtlThrow

この関数では、HRESULT のステータス コードに基づいてエラーを通知します。

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>パラメーター

*hr*<br/>
標準の HRESULT 値。

### <a name="remarks"></a>Remarks

この関数は、エラーが発生した場合の ATL および MFC コードによって使用されます。 独自のコードから呼び出すこともできます。 この関数の既定の実装は、MFC または ATL プロジェクトの種類とシンボルのシンボルの定義に依存します。

すべてのケースでは、この関数は、デバッガーに HRESULT をトレースします。

Visual Studio 2015 Update 3 以降では、この関数は、誤った SAL 警告を回避するために、属性付き __declspec(noreturn) です。

MFC プロジェクトでシンボルが定義されていない場合に、この関数がスロー、 [CMemoryException](../../mfc/reference/cmemoryexception-class.md)または[COleException](../../mfc/reference/coleexception-class.md) HRESULT の値に基づきます。

ATL プロジェクトでシンボルが定義されていない場合、関数、 [CAtlException](../../atl/reference/catlexception-class.md)します。

シンボルが定義されている場合、関数は例外をスローする代わりにアサーション失敗を発生させます。

ATL プロジェクトでは、ATL によって、障害発生時に使用するには、この関数の実装を提供することができます。 これを行うには、定義、独自の関数と同じシグネチャを持つ`AtlThrow`と #define`AtlThrow`関数の名前になります。 これは、atlexcept.h (つまり atlbase.h atlexcept.h が含まれるために、ATL ヘッダーをインクルードする前に行う必要があります) を含める前に実行する必要があります。 関数の属性`__declspec(noreturn)`誤った SAL 警告を回避するためにします。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

## <a name="requirements"></a>必要条件

**ヘッダー:** atldef.h

##  <a name="atlthrowlastwin32"></a>  AtlThrowLastWin32

Windows の `GetLastError` 関数の結果に基づいてエラーを通知します。

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>Remarks

この関数の結果のトレース`GetLastError`デバッガーにします。

MFC プロジェクトでシンボルが定義されていない場合に、この関数がスロー、 [CMemoryException](../../mfc/reference/cmemoryexception-class.md)または[COleException](../../mfc/reference/coleexception-class.md)によって返される値に基づいて`GetLastError`します。

ATL プロジェクトでシンボルが定義されていない場合、関数、 [CAtlException](../../atl/reference/catlexception-class.md)します。

シンボルが定義されている場合、関数は例外をスローする代わりにアサーション失敗を発生させます。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldef.h

## <a name="see-also"></a>関連項目

[関数](../../atl/reference/atl-functions.md)<br/>
[デバッグとエラー報告に関するマクロ](../../atl/reference/debugging-and-error-reporting-macros.md)
