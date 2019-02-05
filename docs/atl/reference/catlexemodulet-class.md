---
title: CAtlExeModuleT クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::CAtlExeModuleT
- ATLBASE/ATL::CAtlExeModuleT::InitializeCom
- ATLBASE/ATL::CAtlExeModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlExeModuleT::PostMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::RegisterClassObjects
- ATLBASE/ATL::CAtlExeModuleT::RevokeClassObjects
- ATLBASE/ATL::CAtlExeModuleT::Run
- ATLBASE/ATL::CAtlExeModuleT::RunMessageLoop
- ATLBASE/ATL::CAtlExeModuleT::UninitializeCom
- ATLBASE/ATL::CAtlExeModuleT::Unlock
- ATLBASE/ATL::CAtlExeModuleT::WinMain
- ATLBASE/ATL::CAtlExeModuleT::m_bDelayShutdown
- ATLBASE/ATL::CAtlExeModuleT::m_dwPause
- ATLBASE/ATL::CAtlExeModuleT::m_dwTimeOut
helpviewer_keywords:
- CAtlExeModuleT class
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
ms.openlocfilehash: d31dd9ed1d30633b8f7078794dad06d51ec119f2
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893439"
---
# <a name="catlexemodulet-class"></a>CAtlExeModuleT クラス

このクラスは、アプリケーションのモジュールを表します。

## <a name="syntax"></a>構文

```
template <class T>
class ATL_NO_VTABLE CAtlExeModuleT : public CAtlModuleT<T>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
クラスから派生した`CAtlExeModuleT`します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|コンストラクターです。|
|[CAtlExeModuleT::~CAtlExeModuleT](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlExeModuleT::InitializeCom](#initializecom)|COM を初期化します。|
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|コマンドラインを解析し、必要な場合は、登録を実行します。|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|このメソッドは、メッセージ ループが終了した直後後に呼び出されます。|
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|このメソッドは、メッセージ ループを開始する直前に呼び出されます。|
|[CAtlExeModuleT::RegisterClassObjects](#registerclassobjects)|クラスのオブジェクトを登録します。|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|クラスのオブジェクトを取り消します。|
|[CAtlExeModuleT::Run](#run)|このメソッドは、初期化は、メッセージ ループを実行するには、EXE モジュールのコードが実行してクリーンアップします。|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|このメソッドは、メッセージ ループを実行します。|
|[CAtlExeModuleT::UninitializeCom](#uninitializecom)|COM. の初期化を解除します。|
|[CAtlExeModuleT::Unlock](#unlock)|モジュールのロック カウントをデクリメントします。|
|[CAtlExeModuleT::WinMain](#winmain)|このメソッドは、EXE の実行に必要なコードを実装します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|モジュールをシャット ダウン遅延が発生する必要がありますを示すフラグです。|
|[CAtlExeModuleT::m_dwPause](#m_dwpause)|すべてのオブジェクトがシャット ダウンする前にリリースされたことを確認するために使用する一時停止の値。|
|[CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)|モジュールのアンロードを遅延するために使用するタイムアウト値。|

## <a name="remarks"></a>Remarks

`CAtlExeModuleT` アプリケーション (EXE) のモジュールを表し、終了時に、EXE を作成する、コマンドラインの処理、クラスのオブジェクトの登録、メッセージ ループを実行しているおよびクリーンアップをサポートするコードが含まれています。

このクラスは、EXE サーバーで COM オブジェクトは継続的に作成および破棄されるときに、パフォーマンスを向上させるために設計されています。 最後の COM オブジェクトがリリースされると、EXE 待機で指定した期間、 [CAtlExeModuleT::m_dwTimeOut](#m_dwtimeout)データ メンバー。 この期間中にアクティビティがない場合 (つまり、COM オブジェクトは作成されません)、シャット ダウン プロセスが開始されます。

[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)データ メンバーは、フラグのかどうか、exe ファイルは、上記で定義したメカニズムを使用する必要がありますを決定するために使用します。 False に設定されている場合、モジュールは、直ちに終了します。

ATL でモジュールの詳細については、次を参照してください。 [ATL モジュール クラス](../../atl/atl-module-classes.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="catlexemodulet"></a>  CAtlExeModuleT::CAtlExeModuleT

コンストラクターです。

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Remarks

場合は、EXE モジュールを初期化できませんでした、WinMain はさらに処理することがなくすぐに返します。

##  <a name="dtor"></a>  CAtlExeModuleT:: ~ CAtlExeModuleT

デストラクターです。

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Remarks

割り当てられているすべてのリソースを解放します。

##  <a name="initializecom"></a>  CAtlExeModuleT::InitializeCom

COM を初期化します。

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

このメソッドは、コンス トラクターから呼び出され、既定の実装から別の方法で COM を初期化するためにオーバーライドすることができます。 既定の実装を呼び出すか、`CoInitializeEx(NULL, COINIT_MULTITHREADED)`または`CoInitialize(NULL)`プロジェクト構成によって異なります。

通常このメソッドをオーバーライドする場合は、オーバーライドする必要があります[CAtlExeModuleT::UninitializeCom](#uninitializecom)します。

##  <a name="m_bdelayshutdown"></a>  CAtlExeModuleT::m_bDelayShutdown

モジュールをシャット ダウン遅延が発生する必要がありますを示すフラグです。

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>Remarks

参照してください、 [CAtlExeModuleT 概要](../../atl/reference/catlexemodulet-class.md)詳細についてはします。

##  <a name="m_dwpause"></a>  CAtlExeModuleT::m_dwPause

シャット ダウンする前にすべてのオブジェクトを削除することを確認するために使用する一時停止の値。

```
DWORD m_dwPause;
```

### <a name="remarks"></a>Remarks

この値を呼び出した後に変更[する](#initializecom)サーバーをシャット ダウン、一時停止の値として使用するミリ秒単位の数を設定します。 既定値は、1000 ミリ秒です。

##  <a name="m_dwtimeout"></a>  CAtlExeModuleT::m_dwTimeOut

モジュールのアンロードを遅延するために使用するタイムアウト値。

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>Remarks

この値を呼び出した後に変更[する](#initializecom)サーバーをシャット ダウン タイムアウト値として使用するミリ秒単位の数を定義します。 既定値は 5000 ミリ秒です。 参照してください、 [CAtlExeModuleT 概要](../../atl/reference/catlexemodulet-class.md)の詳細。

##  <a name="parsecommandline"></a>  CAtlExeModuleT::ParseCommandLine

コマンドラインを解析し、必要な場合は、登録を実行します。

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>パラメーター

*lpCmdLine*<br/>
コマンドラインは、アプリケーションに渡されます。

*pnRetCode*<br/>
(これが、行われた) 場合は、登録に対応する HRESULT。

### <a name="return-value"></a>戻り値

True の場合は、アプリケーション実行を継続する、それ以外の場合は false を返します。

### <a name="remarks"></a>Remarks

このメソッドの呼び出し元[CAtlExeModuleT::WinMain](#winmain)コマンド ライン スイッチを処理するためにオーバーライドできます。 既定の実装 **/RegServer**と **/UnRegServer**コマンドライン引数し登録または登録解除を実行します。

##  <a name="postmessageloop"></a>  CAtlExeModuleT::PostMessageLoop

このメソッドは、メッセージ ループが終了した直後後に呼び出されます。

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

カスタム アプリケーションのクリーンアップを実行するには、このメソッドをオーバーライドします。 既定の実装[で](#revokeclassobjects)します。

##  <a name="premessageloop"></a>  CAtlExeModuleT::PreMessageLoop

このメソッドは、メッセージ ループを開始する直前に呼び出されます。

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>パラメーター

*nShowCmd*<br/>
渡された値、 *nShowCmd* WinMain のパラメーター。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

アプリケーションのカスタム初期化コードを追加するには、このメソッドをオーバーライドします。 既定の実装では、クラス オブジェクトを登録します。

##  <a name="registerclassobjects"></a>  CAtlExeModuleT::RegisterClassObjects

他のアプリケーションが接続できるように、クラス オブジェクトを OLE に登録します。

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>パラメーター

*dwClsContext*<br/>
クラスのオブジェクトが実行コンテキストを指定します。 指定できる値は、CLSCTX_INPROC_SERVER や CLSCTX_INPROC_HANDLER、CLSCTX_LOCAL_SERVER は。

*dwFlags*<br/>
クラス オブジェクトへの接続の種類を決定します。 指定できる値は、REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE、または REGCLS_MULTI_SEPARATE は。

### <a name="return-value"></a>戻り値

成功、S_FALSE を登録するクラスが存在しなかった場合、またはエラー発生時のエラー HRESULT が S_OK を返します。

##  <a name="revokeclassobjects"></a>  CAtlExeModuleT::RevokeClassObjects

クラスのオブジェクトを削除します。

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>戻り値

成功、S_FALSE を登録するクラスが存在しなかった場合、またはエラー発生時のエラー HRESULT が S_OK を返します。

##  <a name="run"></a>  CAtlExeModuleT::Run

このメソッドは、初期化は、メッセージ ループを実行するには、EXE モジュールのコードが実行してクリーンアップします。

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>パラメーター

*nShowCmd*<br/>
ウィンドウの表示方法を指定します。 このパラメーターで説明されている値のいずれかを指定できます、 [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain)セクション。 既定値は SW_HIDE です。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

このメソッドをオーバーライドできます。 ただし、実際にする方がオーバーライド[CAtlExeModuleT::PreMessageLoop](#premessageloop)、 [CAtlExeModuleT::RunMessageLoop](#runmessageloop)、または[CAtlExeModuleT::PostMessageLoop](#postmessageloop)その代わりに。

##  <a name="runmessageloop"></a>  CAtlExeModuleT::RunMessageLoop

このメソッドは、メッセージ ループを実行します。

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>Remarks

メッセージ ループの動作を変更するのには、このメソッドをオーバーライドできます。

##  <a name="uninitializecom"></a>  CAtlExeModuleT::UninitializeCom

COM. の初期化を解除します。

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>Remarks

既定でこのメソッドを呼び出すだけです[CoUninitialize](/windows/desktop/api/combaseapi/nf-combaseapi-couninitialize)デストラクターから呼び出されるとします。 オーバーライドする場合は、このメソッドをオーバーライド[する](#initializecom)します。

##  <a name="unlock"></a>  CAtlExeModuleT::Unlock

モジュールのロック カウントをデクリメントします。

```
LONG Unlock() throw();
```

### <a name="return-value"></a>戻り値

テストや診断に使用できる値を返します。

##  <a name="winmain"></a>  CAtlExeModuleT::WinMain

このメソッドは、EXE の実行に必要なコードを実装します。

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>パラメーター

*nShowCmd*<br/>
ウィンドウの表示方法を指定します。 このパラメーターで説明されている値のいずれかを指定できます、 [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain)セクション。

### <a name="return-value"></a>戻り値

実行可能ファイルの戻り値を返します。

### <a name="remarks"></a>Remarks

このメソッドをオーバーライドできます。 オーバーライドする場合[CAtlExeModuleT::PreMessageLoop](#premessageloop)、 [CAtlExeModuleT::PostMessageLoop](#postmessageloop)、または[CAtlExeModuleT::RunMessageLoop](#runmessageloop)十分な柔軟性を提供しませんをオーバーライドすることができます、`WinMain`このメソッドを使用して機能します。

## <a name="see-also"></a>関連項目

[ATLDuck サンプル](../../visual-cpp-samples.md)<br/>
[CAtlModuleT クラス](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT クラス](../../atl/reference/catldllmodulet-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
