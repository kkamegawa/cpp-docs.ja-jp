---
title: マクロと Dll を管理するための関数
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: b27f8763b60dc7ce3ee074cad1365e7e1de3a7e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322203"
---
# <a name="macros-and-functions-for-managing-dlls"></a>マクロと Dll を管理するための関数

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|クラスをエクスポートします。|
|[AFX_MANAGE_STATE](#afx_manage_state)|DLL でエクスポートされた関数を保護します。|
|[AfxOleInitModule](#afxoleinitmodule)|MFC と動的にリンクされるレギュラー MFC DLL から OLE サポートを提供します。|
|[AfxNetInitModule](#afxnetinitmodule)|MFC と動的にリンクされるレギュラー MFC DLL からの MFC ソケットをサポートを提供します。|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|各モジュールの状態フラグの現在の状態を取得します。|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|モジュールの状態をクリーンアップした後は、前のモジュール状態を復元するや初期化の前に設定します。|
|[AfxInitExtensionModule](#afxinitextensionmodule)|DLL を初期化します。|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|MFC の WinSxS 動作に影響するモジュールの状態フラグを設定します。|
|[AfxTermExtensionModule](#afxtermextensionmodule)|各プロセスは、DLL からデタッチされるときに、MFC 拡張 DLL をクリーンアップする MFC を使用できます。|

## <a name="afx_ext_class"></a>  AFX_EXT_CLASS

[MFC 拡張 Dll](../../build/extension-dlls.md)クラスをエクスポートする AFX_EXT_CLASS マクロを使用します。 MFC 拡張 DLL にリンクする実行可能ファイルは、クラスをインポートするマクロを使用します。

### <a name="remarks"></a>Remarks

AFX_EXT_CLASS マクロでは、同じヘッダー ファイルが MFC 拡張 DLL をビルドするために使用を DLL にリンクする実行可能ファイルで使用できます。

DLL のヘッダー ファイルのようにクラスの宣言に AFX_EXT_CLASS キーワードを追加します。

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

詳細については、次を参照してください。[エクスポートとインポートを使用して AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxv_dll.h

## <a name="afx_manage_state"></a>  AFX_MANAGE_STATE

DLL でエクスポートされた関数を保護するには、このマクロを呼び出します。

### <a name="syntax"></a>構文

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>パラメーター

*pModuleState*<br/>
ポインター、`AFX_MODULE_STATE`構造体。

### <a name="remarks"></a>Remarks

このマクロが呼び出されたときに*pModuleState*イミディ エイトの残りの部分の有効なモジュールの状態は、スコープを含むです。 スコープから離れると、前のモジュールの状態が自動的に復元されます。
`AFX_MODULE_STATE`構造体には、モジュールでは、プッシュまたはポップされているモジュールの状態の部分は、グローバルなデータが含まれています。

既定では、MFC では、メイン アプリケーションのリソース ハンドルを使用して、リソースのテンプレートを読み込みます。 など、DLL 内のダイアログ ボックスを起動する 1 つの DLL にエクスポートされた関数がある場合、このテンプレートは、DLL のモジュールに実際に格納されます。 適切なハンドルを使用するモジュールの状態を切り替える必要があります。 関数の先頭に次のコードを追加することで、これを行うことができます。

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

モジュールの現在の状態から返された状態と交換この[AfxGetStaticModuleState](#afxgetstaticmodulestate)現在のスコープが終わるまでです。

モジュールの状態と MFC の詳細についてを参照してください「の管理モジュールの状態データの MFC モジュール」[新しいドキュメントの作成、Windows、およびビュー](../creating-new-documents-windows-and-views.md)と[テクニカル ノート 58](../tn058-mfc-module-state-implementation.md)します。

> [!NOTE]
>  MFC では、アセンブリのアクティベーション コンテキストを作成するときに使用して[AfxWinInit](application-information-and-management.md#afxwininit)コンテキストを作成して`AFX_MANAGE_STATE`をアクティブ化して、非アクティブ化します。 また、 `AFX_MANAGE_STATE` MFC コードがユーザーの DLL によって選択されている適切なライセンス認証のコンテキストで実行するには静的の MFC ライブラリと MFC の Dll に対してを有効にします。 詳細については、次を参照してください。[の MFC モジュール状態でアクティブ化コンテキストのサポート](../support-for-activation-contexts-in-the-mfc-module-state.md)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxstat_.h

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> AfxOleInitModule

MFC と動的にリンクされるレギュラー MFC DLL から OLE サポートについては、この関数を呼び出して、レギュラー MFC DLL の`CWinApp::InitInstance`MFC OLE DLL を初期化します。

### <a name="syntax"></a>構文

```
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Remarks

MFC OLE DLL が MFC 拡張 DLL です。MFC 拡張 DLL にワイヤード (有線) を取得するため、`CDynLinkLibrary`チェーンを作成する必要がありますが、`CDynLinkLibrary`使用するすべてのモジュールのコンテキスト内のオブジェクト。 `AfxOleInitModule` 作成、`CDynLinkLibrary`にワイヤード (有線) を取得するために、レギュラー MFC DLL のコンテキストでオブジェクト、`CDynLinkLibrary`レギュラー MFC DLL のチェーンのオブジェクトします。

OLE コントロールを構築してを使用している場合`COleControlModule`、呼び出す必要はありません`AfxOleInitModule`ため、`InitInstance`メンバー関数の`COleControlModule`呼び出し`AfxOleInitModule`します。

### <a name="requirements"></a>必要条件

**ヘッダー**: \<afxdll_.h >

## <a name="afxnetinitmodule"></a>  AfxNetInitModule

MFC ソケットは、MFC と動的にリンクされるレギュラー MFC DLL からサポートは、この関数の呼び出しを追加でレギュラー MFC DLL の`CWinApp::InitInstance`MFC ソケットの DLL を初期化します。

### <a name="syntax"></a>構文

```
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Remarks

MFC ソケットの DLL が MFC 拡張 DLL です。MFC 拡張 DLL にワイヤード (有線) を取得するため、`CDynLinkLibrary`チェーンを作成する必要がありますが、`CDynLinkLibrary`使用するすべてのモジュールのコンテキスト内のオブジェクト。 `AfxNetInitModule` 作成、`CDynLinkLibrary`にワイヤード (有線) を取得するために、レギュラー MFC DLL のコンテキストでオブジェクト、`CDynLinkLibrary`レギュラー MFC DLL のチェーンのオブジェクトします。

### <a name="requirements"></a>必要条件

**ヘッダー:** \<afxdll_.h >

## <a name="afxgetambientactctx"></a> AfxGetAmbientActCtx

MFC の WinSxS 動作に影響を与える、モジュールの状態フラグの現在の状態を取得するのにには、この関数を使用します。

### <a name="syntax"></a>構文

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>戻り値

モジュールの状態フラグの現在値。

### <a name="remarks"></a>Remarks

(これが既定です)、フラグが設定し、スレッドが、MFC のモジュールに入る (を参照してください[AFX_MANAGE_STATE](#afx_manage_state))、モジュールのコンテキストをアクティブ化します。

フラグが設定されていない場合、エントリには、モジュールのコンテキストがアクティブ化されません。

モジュールのコンテキストは、通常モジュール リソースに埋め込まれて、そのマニフェストから決定されます。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxcomctl32.h

## <a name="afxgetstaticmodulestate"></a> AfxGetStaticModuleState

初期化の前にモジュールの状態を設定またはクリーンアップした後は、前のモジュール状態を復元する、この関数を呼び出します。

### <a name="syntax"></a>構文

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>戻り値

ポインター、`AFX_MODULE_STATE`構造体。

### <a name="remarks"></a>Remarks

`AFX_MODULE_STATE`構造体には、モジュールでは、プッシュまたはポップされているモジュールの状態の部分は、グローバルなデータが含まれています。

既定では、MFC では、メイン アプリケーションのリソース ハンドルを使用して、リソースのテンプレートを読み込みます。 など、DLL 内のダイアログ ボックスを起動する 1 つの DLL にエクスポートされた関数がある場合、このテンプレートは、DLL のモジュールに実際に格納されます。 適切なハンドルを使用するモジュールの状態を切り替える必要があります。 関数の先頭に次のコードを追加することで、これを行うことができます。

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

モジュールの現在の状態から返された状態と交換この`AfxGetStaticModuleState`現在のスコープが終わるまでです。

モジュールの状態と MFC の詳細についてを参照してください「の管理モジュールの状態データの MFC モジュール」[新しいドキュメントの作成、Windows、およびビュー](../creating-new-documents-windows-and-views.md)と[テクニカル ノート 58](../tn058-mfc-module-state-implementation.md)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxstat_.h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

MFC 拡張 DLL のこの関数を呼び出す`DllMain`DLL を初期化します。

### <a name="syntax"></a>構文

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>パラメーター

*state*<br/>
参照、 [AFX_EXTENSION_MODULE 構造体](afx-extension-module-structure.md)初期化後に、MFC 拡張 DLL のモジュールの状態を格納する構造体。 状態には、前に実行される通常の静的オブジェクトの構築の一部としてに MFC 拡張 DLL が初期化されたランタイム クラスのオブジェクトのコピーが含まれています。`DllMain`を入力します。

*hModule*<br/>
MFC 拡張 DLL のモジュールのハンドル。

### <a name="return-value"></a>戻り値

MFC 拡張 DLL が正常に初期化される場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

例:

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;
...
```

`AfxInitExtensionModule` DLL の HMODULE のコピーを作成し、DLL のランタイム クラスをキャプチャ (`CRuntimeClass`構造) とそのオブジェクトのファクトリ (`COleObjectFactory`オブジェクト) 使用するときに後で、`CDynLinkLibrary`オブジェクトが作成されます。
MFC 拡張 Dll の 2 つの作業を実行しなければ、`DllMain`関数。

- 呼び出す[AfxInitExtensionModule](#afxinitextensionmodule)戻り値を確認します。

- 作成、`CDynLinkLibrary`オブジェクトの DLL をエクスポートするかどうかは[CRuntimeClass 構造](cruntimeclass-structure.md)オブジェクトか、独自のカスタム リソース。

呼び出すことができます`AfxTermExtensionModule`各プロセスは、MFC 拡張 DLL からデタッチされるときに、MFC 拡張 DLL をクリーンアップする (動作は、プロセスの終了時に、またはの結果として、DLL がアンロードされるときに、`AfxFreeLibrary`呼び出します)。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxdll_.h

## <a name="afxsetambientactctx"></a>  AfxSetAmbientActCtx

MFC の WinSxS 動作に影響は、モジュールの状態フラグを設定するのにには、この関数を使用します。

### <a name="syntax"></a>構文

```
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>パラメーター

*bSet*<br/>
モジュールの状態フラグの新しい値。

### <a name="remarks"></a>Remarks

(これが既定です)、フラグが設定し、スレッドが、MFC のモジュールに入る (を参照してください[AFX_MANAGE_STATE](#afx_manage_state))、モジュールのコンテキストをアクティブ化します。
フラグが設定されていない場合、エントリには、モジュールのコンテキストがアクティブ化されません。
モジュールのコンテキストは、通常モジュール リソースに埋め込まれて、そのマニフェストから決定されます。

### <a name="example"></a>例

```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
}
```

### <a name="requirements"></a>必要条件

**ヘッダー:** afxcomctl32.h

## <a name="afxtermextensionmodule"></a>  AfxTermExtensionModule

各プロセスは、DLL からデタッチされるときに、MFC 拡張 DLL をクリーンアップする MFC を許可するには、この関数を呼び出す (動作は、プロセスの終了時に、またはの結果として、DLL がアンロードされるときに、`AfxFreeLibrary`呼び出します)。

### <a name="syntax"></a>構文

```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>パラメーター

*state*<br/>
参照、 [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) MFC 拡張 DLL のモジュールの状態を格納する構造体。

*ボール*<br/>
TRUE の場合は、すべての MFC 拡張 DLL のモジュールをクリーンアップします。 それ以外の場合、現在の DLL のモジュールのみをクリーンアップします。

### <a name="remarks"></a>Remarks

`AfxTermExtensionModule` モジュールに接続されている任意のローカル ストレージを削除し、メッセージ マップのキャッシュからエントリを削除します。 例:

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;

        new CMyDynLinkLibrary(NVC_MFC_DLLDLL);

    }
    else if (dwReason == DLL_PROCESS_DETACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Terminating!\n");

        // Terminate the library before destructors are called
        AfxTermExtensionModule(NVC_MFC_DLLDLL);
    }
    return 1;   // ok
}
```

読み込みとするアプリケーションと MFC 拡張 Dll を動的に解放する場合に呼び出してください`AfxTermExtensionModule`します。 ほとんどの MFC 拡張 Dll が動的に読み込まれていないため (通常は、リンク、インポート ライブラリを使用して)、呼び出し`AfxTermExtensionModule`は通常必要ありません。

MFC 拡張 Dll を呼び出す必要があります[AfxInitExtensionModule](#afxinitextensionmodule)でその`DllMain`します。 DLL をエクスポートする場合[CRuntimeClass](cruntimeclass-structure.md)オブジェクトか、独自のカスタム リソースも作成する必要があります、`CDynLinkLibrary`オブジェクト`DllMain`します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxdll_.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[MFC モジュールの状態データの管理](../managing-the-state-data-of-mfc-modules.md)<br/>
