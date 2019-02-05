---
title: CAxDialogImpl クラス
ms.date: 11/04/2016
f1_keywords:
- CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl::AdviseSinkMap
- ATLWIN/ATL::CAxDialogImpl::Create
- ATLWIN/ATL::CAxDialogImpl::DestroyWindow
- ATLWIN/ATL::CAxDialogImpl::DoModal
- ATLWIN/ATL::CAxDialogImpl::EndDialog
- ATLWIN/ATL::CAxDialogImpl::GetDialogProc
- ATLWIN/ATL::CAxDialogImpl::GetIDD
- ATLWIN/ATL::CAxDialogImpl::IsDialogMessage
- ATLWIN/ATL::CAxDialogImpl::m_bModal
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
ms.openlocfilehash: 852656b33eca1a8c87c6931b58cd49c0c41fe3dc
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893640"
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl クラス

このクラスは、ActiveX コントロールをホストするダイアログ ボックス (モーダルまたはモードレス) を実装します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
派生したクラス、`CAxDialogImpl`します。

*TBase*<br/>
基本ウィンドウ クラス`CDialogImplBaseT`します。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|オブジェクトのシンク イベント マップのすべてのエントリをアドバイズするか、このメソッドを呼び出します。|
|[CAxDialogImpl::Create](#create)|モードレス ダイアログ ボックスを作成するには、このメソッドを呼び出します。|
|[CAxDialogImpl::DestroyWindow](#destroywindow)|モードレス ダイアログ ボックスを破棄するには、このメソッドを呼び出します。|
|[CAxDialogImpl::DoModal](#domodal)|モーダル ダイアログ ボックスを作成するには、このメソッドを呼び出します。|
|[CAxDialogImpl::EndDialog](#enddialog)|モーダル ダイアログ ボックスを破棄するには、このメソッドを呼び出します。|
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|ポインターを取得するには、このメソッドを呼び出し、`DialogProc`コールバック関数。|
|[CAxDialogImpl::GetIDD](#getidd)|ダイアログ テンプレート リソースの ID を取得するには、このメソッドを呼び出す|
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|このダイアログ ボックスのメッセージが対象として かどうかを判断するには、このメソッドを呼び出すし場合は、メッセージを処理します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CAxDialogImpl::m_bModal](#m_bmodal)|デバッグにのみ存在する変数をビルドし、ダイアログ ボックスがモーダルの場合は true に設定されています。|

## <a name="remarks"></a>Remarks

`CAxDialogImpl` モーダルまたはモードレスのダイアログ ボックスを作成することができます。 `CAxDialogImpl` メッセージを適切なハンドラーを送信する既定のメッセージ マップを使用して、ダイアログ ボックス プロシージャを提供します。

`CAxDialogImpl` 派生した`CDialogImplBaseT`、さらにから派生する*TBase* (既定では、 `CWindow`) と`CMessageMap`します。

クラスは、ダイアログ テンプレート リソースの ID を指定する IDD メンバーを定義する必要があります。 ATL ダイアログ オブジェクトを使用して、たとえば、追加、**クラスの追加** ダイアログ ボックスが自動的に次の行をクラスに追加します。

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

場所`MyDialog`は、**短い名前**ATL ダイアログ ウィザードに入力します。

参照してください[ ダイアログ ボックスを実装する](../../atl/implementing-a-dialog-box.md)詳細についてはします。

モーダル ダイアログ ボックスで ActiveX コントロールを使用して作成注`CAxDialogImpl`アクセラレータ キーではサポートされません。 [作成] ダイアログ ボックスのアクセラレータ キーをサポートするために`CAxDialogImpl`モードレス ダイアログ ボックスを作成し、独自のメッセージ ループを使用して、 [CAxDialogImpl::IsDialogMessage](#isdialogmessage)メッセージを処理するためにキューから取得した後、アクセラレータ キー。

詳細については`CAxDialogImpl`を参照してください[ATL コントロール コンテインメント FAQ](../../atl/atl-control-containment-faq.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlwin.h

##  <a name="advisesinkmap"></a>  CAxDialogImpl::AdviseSinkMap

オブジェクトのシンク イベント マップのすべてのエントリをアドバイズするか、このメソッドを呼び出します。

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>パラメーター

*bAdvise*<br/>
シンクのすべてのエントリをアドバイズする場合は true に設定します。false の場合、すべてのシンクのエントリは、アドバイズを中止すること。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="create"></a>  CAxDialogImpl::Create

モードレス ダイアログ ボックスを作成するには、このメソッドを呼び出します。

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>パラメーター

*hWndParent*<br/>
[in]オーナー ウィンドウのハンドル。

*dwInitParam*<br/>
[in]ダイアログ ボックスに渡す値を指定します、 *lParam* WM_INITDIALOG メッセージのパラメーター。

*RECT&*<br/>
このパラメーターは使用されません。 このパラメーターが渡された`CComControl`します。

### <a name="return-value"></a>戻り値

新しく作成されたダイアログ ボックスへのハンドル。

### <a name="remarks"></a>Remarks

このダイアログ ボックスが自動的に接続されている、`CAxDialogImpl`オブジェクト。 モーダル ダイアログ ボックスを作成するには[DoModal](#domodal)します。

2 番目のオーバーライドが提供されるは、ダイアログ ボックスで使用できるためにのみ[CComControl](../../atl/reference/ccomcontrol-class.md)します。

##  <a name="destroywindow"></a>  CAxDialogImpl::DestroyWindow

モードレス ダイアログ ボックスを破棄するには、このメソッドを呼び出します。

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>戻り値

ウィンドウが破棄された場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

呼び出さない`DestroyWindow`モーダル ダイアログ ボックスを破棄します。 呼び出す[EndDialog](#enddialog)代わりにします。

##  <a name="domodal"></a>  CAxDialogImpl::DoModal

モーダル ダイアログ ボックスを作成するには、このメソッドを呼び出します。

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>パラメーター

*hWndParent*<br/>
[in]オーナー ウィンドウのハンドル。 既定値はの戻り値、 [GetActiveWindow](/windows/desktop/api/winuser/nf-winuser-getactivewindow) Win32 関数。

*dwInitParam*<br/>
[in]ダイアログ ボックスに渡す値を指定します、 *lParam* WM_INITDIALOG メッセージのパラメーター。

### <a name="return-value"></a>戻り値

成功した場合の値、*呼び出した*への呼び出しで指定されたパラメーター [EndDialog](#enddialog)。 それ以外の場合、-1。

### <a name="remarks"></a>Remarks

このダイアログ ボックスが自動的に接続されている、`CAxDialogImpl`オブジェクト。

モードレス ダイアログ ボックスを作成するには[作成](#create)です。

##  <a name="enddialog"></a>  CAxDialogImpl::EndDialog

モーダル ダイアログ ボックスを破棄するには、このメソッドを呼び出します。

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>パラメーター

*nRetCode*<br/>
[in]によって返される値[DoModal](#domodal)します。

### <a name="return-value"></a>戻り値

ダイアログ ボックスが破棄された場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

`EndDialog` ダイアログ ボックス プロシージャを呼び出す必要があります。 Windows での値を使用 ダイアログ ボックスを破棄すると、後に*呼び出した*の戻り値として`DoModal`、ダイアログ ボックスを作成します。

> [!NOTE]
>  呼び出さない`EndDialog`モードレス ダイアログ ボックスを破棄します。 呼び出す[DestroyWindow](#destroywindow)代わりにします。

##  <a name="getdialogproc"></a>  CAxDialogImpl::GetDialogProc

ポインターを取得するには、このメソッドを呼び出し、`DialogProc`コールバック関数。

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>戻り値

ポインターを返します、`DialogProc`コールバック関数。

### <a name="remarks"></a>Remarks

`DialogProc`関数は、アプリケーション定義のコールバック関数です。

##  <a name="getidd"></a>  CAxDialogImpl::GetIDD

ダイアログ テンプレート リソースの ID を取得するには、このメソッドを呼び出す

```
int GetIDD();
```

### <a name="return-value"></a>戻り値

ダイアログ テンプレート リソースの ID を返します。

##  <a name="isdialogmessage"></a>  CAxDialogImpl::IsDialogMessage

このダイアログ ボックスのメッセージが対象として かどうかを判断するには、このメソッドを呼び出すし場合は、メッセージを処理します。

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>パラメーター

*pMsg*<br/>
ポインターを[MSG](/windows/desktop/api/winuser/ns-winuser-msg)確認するメッセージを含む構造体。

### <a name="return-value"></a>戻り値

メッセージが処理されたかどうかは TRUE を返します。

### <a name="remarks"></a>Remarks

メッセージ ループ内から呼び出されるメソッドです。

##  <a name="m_bmodal"></a>  CAxDialogImpl::m_bModal

デバッグにのみ存在する変数をビルドし、ダイアログ ボックスがモーダルの場合は true に設定されています。

```
bool m_bModal;
```

## <a name="see-also"></a>関連項目

[CDialogImpl クラス](../../atl/reference/cdialogimpl-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
