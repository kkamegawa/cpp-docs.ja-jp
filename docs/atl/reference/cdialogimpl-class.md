---
title: CDialogImpl クラス
ms.date: 11/04/2016
f1_keywords:
- CDialogImpl
- ATLWIN/ATL::CDialogImpl
- ATLWIN/ATL::Create
- ATLWIN/ATL::DestroyWindow
- ATLWIN/ATL::DoModal
- ATLWIN/ATL::EndDialog
- ATLWIN/ATL::GetDialogProc
- ATLWIN/ATL::MapDialogRect
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::DialogProc
- ATLWIN/ATL::StartDialogProc
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
ms.openlocfilehash: bc39a5deeb270b0426a4b199fc9ba01917c292bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496813"
---
# <a name="cdialogimpl-class"></a>CDialogImpl クラス

このクラスには、モーダルまたはモードレスのダイアログボックスを作成するためのメソッドが用意されています。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`CDialogImpl`派生したクラス。

*TBase*<br/>
新しいクラスの基本クラス。 既定の基底クラスは[CWindow](../../atl/reference/cwindow-class.md)です。

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[作成](#create)|モードレスダイアログボックスを作成します。|
|[DestroyWindow](#destroywindow)|モードレスダイアログボックスを破棄します。|
|[DoModal](#domodal)|モーダルダイアログボックスを作成します。|
|[EndDialog](#enddialog)|モーダルダイアログボックスを破棄します。|

### <a name="cdialogimplbaset-methods"></a>CDialogImplBaseT メソッド

|||
|-|-|
|[Getの Proc](#getdialogproc)|現在のダイアログボックスプロシージャを返します。|
|[Mapの Rect](#mapdialogrect)|指定した四角形のダイアログボックスの単位を画面単位 (ピクセル) にマップします。|
|[OnFinalMessage](#onfinalmessage)|最後のメッセージを受信した後に呼び出されます。通常は WM_NCDESTROY です。|

### <a name="static-functions"></a>静的関数

|||
|-|-|
|[DialogProc](#dialogproc)|ダイアログボックスに送信されたメッセージを処理します。|
|[Startview Proc](#startdialogproc)|ダイアログボックスに送信されたメッセージを処理するために最初のメッセージを受信したときに呼び出されます。|

## <a name="remarks"></a>Remarks

で`CDialogImpl`は、モーダルまたはモードレスのダイアログボックスを作成できます。 `CDialogImpl`既定のメッセージマップを使用してメッセージを適切なハンドラーに送信するダイアログボックスの手順を示します。

基底クラスのデストラクター `~CWindowImplRoot`は、オブジェクトを破棄する前に、ウィンドウが失われることを保証します。

`CDialogImpl` は `CDialogImplBaseT` から派生します。また、後者は `CWindowImplRoot` から派生します。

> [!NOTE]
>  クラスでは、ダイアログ`IDD`テンプレートリソース ID を指定するメンバーを定義する必要があります。 たとえば、ATL プロジェクトウィザードでは、クラスに次の行が自動的に追加されます。

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

ここ`MyDlg`で、はウィザードの **[名前]** ページに入力された**短い名前**です。

|詳細情報:|解決方法|
|--------------------------------|---------|
|コントロールの作成|[ATL チュートリアル](../../atl/active-template-library-atl-tutorial.md)|
|ATL でのダイアログボックスの使用|[ATL ウィンドウ クラス](../../atl/atl-window-classes.md)|
|ATL プロジェクト ウィザード|[ATL プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)|
|ダイアログ ボックス|Windows SDK の[ダイアログボックス](/windows/win32/dlgbox/dialog-boxes)と後続トピック|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="create"></a>  CDialogImpl::Create

モードレスダイアログボックスを作成します。

```
HWND Create(
    HWND hWndParent,
    LPARAM dwInitParam = NULL );

HWND Create(
    HWND hWndParent,
    RECT&,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>パラメーター

*hWndParent*<br/>
からオーナーウィンドウへのハンドル。

**RECT &** *rect*からダイアログのサイズと位置を指定する[RECT](/previous-versions/dd162897\(v=vs.85\))構造体。

*dwInitParam*<br/>
からWM_INITDIALOG メッセージの*lParam*パラメーターのダイアログボックスに渡す値を指定します。

### <a name="return-value"></a>戻り値

新しく作成されたダイアログボックスへのハンドル。

### <a name="remarks"></a>Remarks

このダイアログボックスは、 `CDialogImpl`自動的にオブジェクトにアタッチされます。 モーダルダイアログボックスを作成するには、 [DoModal](#domodal)を呼び出します。 上記の2番目のオーバーライドは、 [CComControl](../../atl/reference/ccomcontrol-class.md)でのみ使用されます。

##  <a name="destroywindow"></a>CDialogImpl::D estroyWindow

モードレスダイアログボックスを破棄します。

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>戻り値

ダイアログボックスが正常に破棄された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ダイアログボックスが正常に破棄された場合は TRUE を返します。それ以外の場合は FALSE。

##  <a name="dialogproc"></a>  CDialogImpl::DialogProc

この静的関数は、ダイアログボックスプロシージャを実装します。

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>パラメーター

*hWnd*<br/>
からダイアログボックスへのハンドル。

*uMsg*<br/>
からダイアログボックスに送信されたメッセージ。

*wParam*<br/>
からメッセージ固有の追加情報。

*lParam*<br/>
からメッセージ固有の追加情報。

### <a name="return-value"></a>戻り値

メッセージが処理される場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

`DialogProc`は、既定のメッセージマップを使用して、メッセージを適切なハンドラーに送信します。

をオーバーライド`DialogProc`して、メッセージを処理するためのさまざまなメカニズムを提供できます。

##  <a name="domodal"></a>CDialogImpl::D oModal

モーダルダイアログボックスを作成します。

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

成功した場合は、 [EndDialog](#enddialog)への呼び出しで指定された*nRetCode*パラメーターの値。 それ以外の場合は-1。

### <a name="remarks"></a>Remarks

このダイアログボックスは、 `CDialogImpl`自動的にオブジェクトにアタッチされます。

モードレスダイアログボックスを作成するには、 [create](#create)を呼び出します。

##  <a name="enddialog"></a>  CDialogImpl::EndDialog

モーダルダイアログボックスを破棄します。

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>パラメーター

*nRetCode*<br/>
からCDialogImpl によって返される値[::D oModal](#domodal)。

### <a name="return-value"></a>戻り値

ダイアログボックスが破棄される場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

`EndDialog`は、ダイアログプロシージャを使用して呼び出す必要があります。 ダイアログボックスが破棄された後、Windows では 、ダイアログボックスを作成し`DoModal`たの戻り値として nRetCode の値が使用されます。

> [!NOTE]
>  モードレスダイアログボックス`EndDialog`を破棄するためにを呼び出さないでください。 代わりに[CWindow::D estroywindow](../../atl/reference/cwindow-class.md#destroywindow)を呼び出します。

##  <a name="getdialogproc"></a>  CDialogImpl::GetDialogProc

現在`DialogProc`のダイアログボックスプロシージャであるを返します。

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>戻り値

現在のダイアログボックスプロシージャ。

### <a name="remarks"></a>Remarks

このメソッドをオーバーライドして、ダイアログプロシージャを独自のに置き換えます。

##  <a name="mapdialogrect"></a>  CDialogImpl::MapDialogRect

指定した四角形のダイアログボックスの単位を画面単位 (ピクセル) に変換 (マップ) します。

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
更新領域を`CRect`囲む更新プログラムのクライアント座標を受け取るオブジェクトまたは[RECT](/windows/win32/api/windef/ns-windef-rect)構造体を指します。

### <a name="return-value"></a>戻り値

更新が成功した場合は0以外の。更新が失敗した場合は0。 拡張されたエラー情報を取得するには、`GetLastError` を呼び出します。

### <a name="remarks"></a>Remarks

関数は、指定された`RECT`構造体の座標を変換された座標で置き換えます。これにより、構造体を使用してダイアログボックスを作成したり、ダイアログボックス内にコントロールを配置したりできます。

##  <a name="onfinalmessage"></a>CDialogImpl:: OnFinalMessage

最後のメッセージを受信した後`WM_NCDESTROY`に呼び出されます (通常は)。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>パラメーター

*hWnd*<br/>
から破棄されるウィンドウへのハンドル。

### <a name="remarks"></a>Remarks

ウィンドウの破棄時にオブジェクトを自動的に削除する場合は、 **[delete this]** を呼び出すことができます。

##  <a name="startdialogproc"></a>  CDialogImpl::StartDialogProc

ダイアログボックスに送信されたメッセージを処理するために、最初のメッセージを受信したときに1回だけ呼び出されます。

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>パラメーター

*hWnd*<br/>
からダイアログボックスへのハンドル。

*uMsg*<br/>
からダイアログボックスに送信されたメッセージ。

*wParam*<br/>
からメッセージ固有の追加情報。

*lParam*<br/>
からメッセージ固有の追加情報。

### <a name="return-value"></a>戻り値

ウィンドウプロシージャ。

### <a name="remarks"></a>Remarks

へ`StartDialogProc`の最初の呼び出しの`DialogProc`後、はダイアログプロシージャとして設定され、それ以降の呼び出しはそこに送られます。

## <a name="see-also"></a>関連項目

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
