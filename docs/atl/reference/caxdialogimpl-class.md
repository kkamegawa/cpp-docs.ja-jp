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
ms.openlocfilehash: 548d2aed0644187b4b8dee1e472b581f1f92d6a1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865057"
---
# <a name="caxdialogimpl-class"></a>CAxDialogImpl クラス

このクラスは、ActiveX コントロールをホストするダイアログボックス (モーダルまたはモードレス) を実装します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
`CAxDialogImpl`から派生したクラス。

*TBase*<br/>
`CDialogImplBaseT`の基本ウィンドウクラス。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|Description|
|----------|-----------------|
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|このメソッドを呼び出して、オブジェクトのシンクマップのイベントマップ内のすべてのエントリをアドバイズまたはアドバイズ中止します。|
|[CAxDialogImpl:: Create](#create)|モードレスダイアログボックスを作成するには、このメソッドを呼び出します。|
|[CAxDialogImpl::D estroyWindow](#destroywindow)|このメソッドを呼び出して、モードレスダイアログボックスを破棄します。|
|[CAxDialogImpl::D oModal](#domodal)|モーダルダイアログボックスを作成するには、このメソッドを呼び出します。|
|[CAxDialogImpl:: EndDialog](#enddialog)|モーダルダイアログボックスを破棄するには、このメソッドを呼び出します。|
|[CAxDialogImpl:: Get Proc](#getdialogproc)|`DialogProc` コールバック関数へのポインターを取得するには、このメソッドを呼び出します。|
|[CAxDialogImpl:: GetIDD](#getidd)|ダイアログテンプレートリソース ID を取得するには、このメソッドを呼び出します。|
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|メッセージがこのダイアログボックスを対象としているかどうかを判断するには、このメソッドを呼び出します。メッセージが表示されている場合は、メッセージを処理します。|

### <a name="protected-data-members"></a>保護されるデータ メンバー

|Name|Description|
|----------|-----------------|
|[CAxDialogImpl:: m_bModal](#m_bmodal)|デバッグビルドにのみ存在し、ダイアログボックスがモーダルである場合は true に設定されている変数。|

## <a name="remarks"></a>解説

`CAxDialogImpl` では、モーダルまたはモードレスのダイアログボックスを作成できます。 `CAxDialogImpl` には、既定のメッセージマップを使用してメッセージを適切なハンドラーに送信するダイアログボックスの手順が用意されています。

`CAxDialogImpl` は `CDialogImplBaseT`から派生します。これは、 *Tbase* (既定では `CWindow`) と `CMessageMap`から派生します。

クラスでは、ダイアログテンプレートリソース ID を指定する IDD メンバーを定義する必要があります。 たとえば、 **[クラスの追加]** ダイアログボックスを使用して ATL ダイアログオブジェクトを追加すると、クラスに次の行が自動的に追加されます。

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

ここで、`MyDialog` は ATL ダイアログウィザードで入力した**短い名前**です。

詳細について[は、「ダイアログボックスの実装](../../atl/implementing-a-dialog-box.md)」を参照してください。

`CAxDialogImpl` で作成されたモーダルダイアログボックス上の ActiveX コントロールは、アクセラレータキーをサポートしていないことに注意してください。 `CAxDialogImpl`で作成されたダイアログボックスでアクセラレータキーをサポートするには、モードレスダイアログボックスを作成し、独自のメッセージループを使用して、キーを処理するメッセージをキューから取得した後で[CAxDialogImpl:: IsDialogMessage](#isdialogmessage)を使用します。

`CAxDialogImpl`の詳細については、「 [ATL コントロールコンテインメント](../../atl/atl-control-containment-faq.md)に関する FAQ」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="advisesinkmap"></a>CAxDialogImpl::AdviseSinkMap

このメソッドを呼び出して、オブジェクトのシンクマップのイベントマップ内のすべてのエントリをアドバイズまたはアドバイズ中止します。

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>パラメーター

*bAdvise*<br/>
すべてのシンクエントリを推奨する場合は true に設定します。すべてのシンクエントリをスキップする場合は false。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

##  <a name="create"></a>CAxDialogImpl:: Create

モードレスダイアログボックスを作成するには、このメソッドを呼び出します。

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>パラメーター

*hWndParent*<br/>
からオーナーウィンドウへのハンドル。

*dwInitParam*<br/>
からWM_INITDIALOG メッセージの*lParam*パラメーターのダイアログボックスに渡す値を指定します。

*RECT &*<br/>
このパラメーターは使用されません。 このパラメーターは `CComControl`によって渡されます。

### <a name="return-value"></a>戻り値

新しく作成されたダイアログボックスへのハンドル。

### <a name="remarks"></a>解説

このダイアログボックスは、`CAxDialogImpl` オブジェクトに自動的にアタッチされます。 モーダルダイアログボックスを作成するには、 [DoModal](#domodal)を呼び出します。

2番目のオーバーライドは、 [CComControl](../../atl/reference/ccomcontrol-class.md)でダイアログボックスを使用できるようにするためだけに用意されています。

##  <a name="destroywindow"></a>CAxDialogImpl::D estroyWindow

このメソッドを呼び出して、モードレスダイアログボックスを破棄します。

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>戻り値

ウィンドウが正常に破棄された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

モーダルダイアログボックスを破棄するために `DestroyWindow` を呼び出さないでください。 代わりに[EndDialog](#enddialog)を呼び出してください。

##  <a name="domodal"></a>CAxDialogImpl::D oModal

モーダルダイアログボックスを作成するには、このメソッドを呼び出します。

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>パラメーター

*hWndParent*<br/>
からオーナーウィンドウへのハンドル。 既定値は、 [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32 関数の戻り値です。

*dwInitParam*<br/>
からWM_INITDIALOG メッセージの*lParam*パラメーターのダイアログボックスに渡す値を指定します。

### <a name="return-value"></a>戻り値

成功した場合は、 [EndDialog](#enddialog)への呼び出しで指定された*nRetCode*パラメーターの値。それ以外の場合は-1。

### <a name="remarks"></a>解説

このダイアログボックスは、`CAxDialogImpl` オブジェクトに自動的にアタッチされます。

モードレスダイアログボックスを作成するには、 [create](#create)を呼び出します。

##  <a name="enddialog"></a>CAxDialogImpl:: EndDialog

モーダルダイアログボックスを破棄するには、このメソッドを呼び出します。

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>パラメーター

*nRetCode*<br/>
から[DoModal](#domodal)によって返される値。

### <a name="return-value"></a>戻り値

ダイアログボックスが破棄される場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

`EndDialog` は、ダイアログボックスのプロシージャを使用して呼び出す必要があります。 ダイアログボックスが破棄された後、Windows では、ダイアログボックスを作成した `DoModal`の戻り値として*nRetCode*の値が使用されます。

> [!NOTE]
>  `EndDialog` を呼び出して、モードレスダイアログボックスを破棄しないでください。 代わりに[DestroyWindow](#destroywindow)を呼び出してください。

##  <a name="getdialogproc"></a>CAxDialogImpl:: Get Proc

`DialogProc` コールバック関数へのポインターを取得するには、このメソッドを呼び出します。

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>戻り値

`DialogProc` コールバック関数へのポインターを返します。

### <a name="remarks"></a>解説

`DialogProc` 関数は、アプリケーション定義のコールバック関数です。

##  <a name="getidd"></a>CAxDialogImpl:: GetIDD

ダイアログテンプレートリソース ID を取得するには、このメソッドを呼び出します。

```
int GetIDD();
```

### <a name="return-value"></a>戻り値

ダイアログテンプレートリソース ID を返します。

##  <a name="isdialogmessage"></a>CAxDialogImpl::IsDialogMessage

メッセージがこのダイアログボックスを対象としているかどうかを判断するには、このメソッドを呼び出します。メッセージが表示されている場合は、メッセージを処理します。

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>パラメーター

*pMsg*<br/>
確認するメッセージを含む[MSG](/windows/win32/api/winuser/ns-winuser-msg)構造体へのポインター。

### <a name="return-value"></a>戻り値

メッセージが処理されている場合は TRUE、それ以外の場合は FALSE を返します。

### <a name="remarks"></a>解説

このメソッドは、メッセージループ内から呼び出すことを目的としています。

##  <a name="m_bmodal"></a>CAxDialogImpl:: m_bModal

デバッグビルドにのみ存在し、ダイアログボックスがモーダルである場合は true に設定されている変数。

```
bool m_bModal;
```

## <a name="see-also"></a>参照

[CDialogImpl クラス](../../atl/reference/cdialogimpl-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
