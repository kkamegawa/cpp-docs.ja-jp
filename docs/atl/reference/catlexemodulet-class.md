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
ms.openlocfilehash: d37cc8e97d29cbedfeb4ba79502d44529485399f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497839"
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
から`CAtlExeModuleT`派生したクラス。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlExeModuleT::CAtlExeModuleT](#catlexemodulet)|コンストラクターです。|
|[CAtlExeModuleT:: ~ CAtlExeModuleT](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlExeModuleT:: 初期化 Ecom](#initializecom)|COM を初期化します。|
|[CAtlExeModuleT::ParseCommandLine](#parsecommandline)|コマンドラインを解析し、必要に応じて登録を実行します。|
|[CAtlExeModuleT::PostMessageLoop](#postmessageloop)|このメソッドは、メッセージループが終了した直後に呼び出されます。|
|[CAtlExeModuleT::PreMessageLoop](#premessageloop)|このメソッドは、メッセージループを開始する直前に呼び出されます。|
|[CAtlExeModuleT:: RegisterClassObjects](#registerclassobjects)|クラスオブジェクトを登録します。|
|[CAtlExeModuleT::RevokeClassObjects](#revokeclassobjects)|クラスオブジェクトを取り消します。|
|[CAtlExeModuleT::Run](#run)|このメソッドは、EXE モジュール内のコードを実行して初期化し、メッセージループを実行して、クリーンアップします。|
|[CAtlExeModuleT::RunMessageLoop](#runmessageloop)|このメソッドは、メッセージループを実行します。|
|[CAtlExeModuleT:: Uninitializer Ecom](#uninitializecom)|初期化前 COM。|
|[CAtlExeModuleT:: Unlock](#unlock)|モジュールのロックカウントをデクリメントします。|
|[CAtlExeModuleT:: WinMain](#winmain)|このメソッドは、EXE を実行するために必要なコードを実装します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CAtlExeModuleT::m_bDelayShutdown](#m_bdelayshutdown)|モジュールをシャットダウンする遅延があることを示すフラグ。|
|[CAtlExeModuleT:: m_dwPause](#m_dwpause)|シャットダウン前にすべてのオブジェクトが解放されるようにするために使用される一時停止値。|
|[CAtlExeModuleT:: m_dwTimeOut](#m_dwtimeout)|モジュールのアンロードを遅延させるために使用するタイムアウト値。|

## <a name="remarks"></a>Remarks

`CAtlExeModuleT`アプリケーション (EXE) のモジュールを表します。 EXE の作成、コマンドラインの処理、クラスオブジェクトの登録、メッセージループの実行、終了時のクリーンアップをサポートするコードが含まれています。

このクラスは、EXE サーバーの COM オブジェクトが継続的に作成および破棄されるときのパフォーマンスを向上するように設計されています。 最後の COM オブジェクトが解放されると、EXE は[CAtlExeModuleT:: m_dwTimeOut](#m_dwtimeout)データメンバーによって指定された期間待機します。 この期間中にアクティビティがない場合 (つまり、COM オブジェクトが作成されていない場合)、シャットダウンプロセスが開始されます。

[CAtlExeModuleT:: m_bDelayShutdown](#m_bdelayshutdown)データメンバーは、実行時に定義されたメカニズムを使用するかどうかを判断するために使用されるフラグです。 False に設定されている場合、モジュールは直ちに終了します。

ATL のモジュールの詳細については、「 [Atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CAtlExeModuleT`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase. h

##  <a name="catlexemodulet"></a>  CAtlExeModuleT::CAtlExeModuleT

コンストラクターです。

```
CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Remarks

EXE モジュールを初期化できなかった場合、WinMain は、後続の処理を行わずにすぐに制御を戻します。

##  <a name="dtor"></a>CAtlExeModuleT:: ~ CAtlExeModuleT

デストラクターです。

```
~CAtlExeModuleT() throw();
```

### <a name="remarks"></a>Remarks

割り当てられたすべてのリソースを解放します。

##  <a name="initializecom"></a>CAtlExeModuleT:: 初期化 Ecom

COM を初期化します。

```
static HRESULT InitializeCom() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

このメソッドはコンストラクターから呼び出され、既定の実装とは異なる方法で COM を初期化するようにオーバーライドできます。 既定の実装では`CoInitializeEx(NULL, COINIT_MULTITHREADED)` 、 `CoInitialize(NULL)`プロジェクトの構成に応じて、またはが呼び出されます。

通常、このメソッドをオーバーライドするに[は、CAtlExeModuleT:: Un初期化 Ecom](#uninitializecom)をオーバーライドする必要があります。

##  <a name="m_bdelayshutdown"></a>  CAtlExeModuleT::m_bDelayShutdown

モジュールをシャットダウンする遅延があることを示すフラグ。

```
bool m_bDelayShutdown;
```

### <a name="remarks"></a>Remarks

詳細については、「 [CAtlExeModuleT の概要](../../atl/reference/catlexemodulet-class.md)」を参照してください。

##  <a name="m_dwpause"></a>  CAtlExeModuleT::m_dwPause

すべてのオブジェクトがシャットダウン前に失われることを保証するために使用される一時停止値。

```
DWORD m_dwPause;
```

### <a name="remarks"></a>Remarks

[CAtlExeModuleT:: Initializer Ecom](#initializecom)を呼び出した後にこの値を変更して、サーバーをシャットダウンするための一時停止値として使用されるミリ秒数を設定します。 既定値は1000ミリ秒です。

##  <a name="m_dwtimeout"></a>  CAtlExeModuleT::m_dwTimeOut

モジュールのアンロードを遅延させるために使用するタイムアウト値。

```
DWORD m_dwTimeOut;
```

### <a name="remarks"></a>Remarks

[CAtlExeModuleT:: Initializer Ecom](#initializecom)を呼び出した後にこの値を変更して、サーバーをシャットダウンするためのタイムアウト値として使用されるミリ秒数を定義します。 既定値は 5000 ミリ秒です。 詳細については、 [CAtlExeModuleT の概要](../../atl/reference/catlexemodulet-class.md)に関するトピックを参照してください。

##  <a name="parsecommandline"></a>  CAtlExeModuleT::ParseCommandLine

コマンドラインを解析し、必要に応じて登録を実行します。

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>パラメーター

*lpCmdLine*<br/>
アプリケーションに渡されるコマンドライン。

*pnRetCode*<br/>
登録に対応する HRESULT (行われた場合)。

### <a name="return-value"></a>戻り値

アプリケーションの実行を継続する必要がある場合は true を返します。それ以外の場合は false を返します。

### <a name="remarks"></a>Remarks

このメソッドは[CAtlExeModuleT:: WinMain](#winmain)から呼び出され、コマンドラインスイッチを処理するようにオーバーライドできます。 既定の実装では 、 **/UnRegServer**コマンドライン引数を確認し、登録または登録解除を実行します。

##  <a name="postmessageloop"></a>  CAtlExeModuleT::PostMessageLoop

このメソッドは、メッセージループが終了した直後に呼び出されます。

```
HRESULT PostMessageLoop() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

カスタムアプリケーションのクリーンアップを実行するには、このメソッドをオーバーライドします。 既定の実装では、 [CAtlExeModuleT:: RevokeClassObjects](#revokeclassobjects)が呼び出されます。

##  <a name="premessageloop"></a>  CAtlExeModuleT::PreMessageLoop

このメソッドは、メッセージループを開始する直前に呼び出されます。

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>パラメーター

*nShowCmd*<br/>
WinMain の*Nshowcmd*パラメーターとして渡された値。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

アプリケーションのカスタム初期化コードを追加するには、このメソッドをオーバーライドします。 既定の実装では、クラスオブジェクトが登録されます。

##  <a name="registerclassobjects"></a>  CAtlExeModuleT::RegisterClassObjects

他のアプリケーションが接続できるように、クラスオブジェクトを OLE に登録します。

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>パラメーター

*dwClsContext*<br/>
クラスオブジェクトを実行するコンテキストを指定します。 指定できる値は、CLSCTX_INPROC_SERVER、CLSCTX_INPROC_HANDLER、または CLSCTX_LOCAL_SERVER です。

*dwFlags*<br/>
クラスオブジェクトへの接続の種類を決定します。 指定できる値は、REGCLS_SINGLEUSE、REGCLS_MULTIPLEUSE、または REGCLS_MULTI_SEPARATE です。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、登録するクラスがない場合は S_FALSE、失敗した場合はエラー HRESULT を返します。

##  <a name="revokeclassobjects"></a>  CAtlExeModuleT::RevokeClassObjects

クラスオブジェクトを削除します。

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、登録するクラスがない場合は S_FALSE、失敗した場合はエラー HRESULT を返します。

##  <a name="run"></a>  CAtlExeModuleT::Run

このメソッドは、EXE モジュール内のコードを実行して初期化し、メッセージループを実行して、クリーンアップします。

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>パラメーター

*nShowCmd*<br/>
ウィンドウの表示方法を指定します。 このパラメーターには、 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain)セクションで説明されている値のいずれかを指定できます。 既定値は SW_HIDE です。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

このメソッドはオーバーライドできます。 ただし、実際には、 [CAtlExeModuleT::P Remessagの op](#premessageloop)、 [CAtlExeModuleT:: runmessag](#runmessageloop)Op、または[CAtlExeModuleT::P ostmessag賢明](#postmessageloop)な操作をオーバーライドすることをお勧めします。

##  <a name="runmessageloop"></a>  CAtlExeModuleT::RunMessageLoop

このメソッドは、メッセージループを実行します。

```
void RunMessageLoop() throw();
```

### <a name="remarks"></a>Remarks

このメソッドをオーバーライドすると、メッセージループの動作を変更できます。

##  <a name="uninitializecom"></a>CAtlExeModuleT:: Uninitializer Ecom

初期化前 COM。

```
static void UninitializeCom() throw();
```

### <a name="remarks"></a>Remarks

既定では、このメソッドは単に[CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize)を呼び出し、デストラクターから呼び出されます。 [CAtlExeModuleT:: 初期化 Ecom](#initializecom)をオーバーライドする場合は、このメソッドをオーバーライドします。

##  <a name="unlock"></a>CAtlExeModuleT:: Unlock

モジュールのロックカウントをデクリメントします。

```
LONG Unlock() throw();
```

### <a name="return-value"></a>戻り値

診断またはテストに役立つ値を返します。

##  <a name="winmain"></a>  CAtlExeModuleT::WinMain

このメソッドは、EXE を実行するために必要なコードを実装します。

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>パラメーター

*nShowCmd*<br/>
ウィンドウの表示方法を指定します。 このパラメーターには、 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain)セクションで説明されている値のいずれかを指定できます。

### <a name="return-value"></a>戻り値

実行可能ファイルの戻り値を返します。

### <a name="remarks"></a>Remarks

このメソッドはオーバーライドできます。 [CAtlExeModuleT::P remessagCAtlExeModuleT](#premessageloop) [::P ostmessagop](#postmessageloop)op、または[CAtlExeModuleT:: runmessag](#runmessageloop)をオーバーライドしても十分な柔軟性が得られ`WinMain`ない場合は、次を使用して関数をオーバーライドすることができます。b.

## <a name="see-also"></a>関連項目

[ATLDuck のサンプル](../../overview/visual-cpp-samples.md)<br/>
[CAtlModuleT クラス](../../atl/reference/catlmodulet-class.md)<br/>
[CAtlDllModuleT クラス](../../atl/reference/catldllmodulet-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
