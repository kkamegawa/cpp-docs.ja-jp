---
title: CWindowImpl クラス
ms.date: 11/04/2016
f1_keywords:
- CWindowImpl
- ATLWIN/ATL::CWindowImpl
- ATLWIN/ATL::CWindowImpl::Create
- ATLWIN/ATL::CWindowImpl::DefWindowProc
- ATLWIN/ATL::CWindowImpl::GetCurrentMessage
- ATLWIN/ATL::CWindowImpl::GetWindowProc
- ATLWIN/ATL::CWindowImpl::OnFinalMessage
- ATLWIN/ATL::CWindowImpl::SubclassWindow
- ATLWIN/ATL::CWindowImpl::UnsubclassWindow
- ATLWIN/ATL::CWindowImpl::GetWndClassInfo
- ATLWIN/ATL::CWindowImpl::WindowProc
- ATLWIN/ATL::CWindowImpl::m_pfnSuperWindowProc
helpviewer_keywords:
- CWindowImpl class
- subclassing windows, ATL
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
ms.openlocfilehash: b8b633dcf4ea14e899ee00552b553476cf697689
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496187"
---
# <a name="cwindowimpl-class"></a>CWindowImpl クラス

ウィンドウを作成またはサブクラス化するためのメソッドを提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class T, class TBase = CWindow, class TWinTraits = CControlWinTraits>
class ATL_NO_VTABLE CWindowImpl : public CWindowImplBaseT<TBase, TWinTraits>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
`CWindowImpl` から派生した新しいクラス。

*TBase*<br/>
クラスの基底クラス。 既定では、基本クラスは[CWindow](../../atl/reference/cwindow-class.md)です。

*TWinTraits*<br/>
ウィンドウのスタイルを定義する[特徴クラス](../../atl/understanding-window-traits.md)。 既定値は `CControlWinTraits` です。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CWindowImpl::Create](#create)|ウィンドウを作成します。|

### <a name="cwindowimplbaset-methods"></a>CWindowImplBaseT メソッド

|||
|-|-|
|[DefWindowProc](#defwindowproc)|既定のメッセージ処理を提供します。|
|[GetCurrentMessage](#getcurrentmessage)|現在のメッセージを返します。|
|[GetWindowProc](#getwindowproc)|現在のウィンドウ プロシージャを返します。|
|[OnFinalMessage](#onfinalmessage)|最後のメッセージを受信した後 (通常は WM_NCDESTROY) に呼び出されます。|
|[SubclassWindow](#subclasswindow)|ウィンドウをサブクラス化します。|
|[UnsubclassWindow](#unsubclasswindow)|前にサブクラス化されたウィンドウを復元します。|

### <a name="static-methods"></a>静的メソッド

|||
|-|-|
|[GetWndClassInfo](#getwndclassinfo)|ウィンドウクラスの情報を管理する[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)の静的なインスタンスを返します。|
|[WindowProc](#windowproc)|ウィンドウに送信されるメッセージを処理します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)|ウィンドウ クラスの元のウィンドウ プロシージャをポイントします。|

## <a name="remarks"></a>Remarks

を使用`CWindowImpl`すると、ウィンドウを作成したり、既存のウィンドウをサブクラス化したりできます。 ウィンドウ`CWindowImpl`プロシージャはメッセージマップを使用して、メッセージを適切なハンドラーに送信します。

`CWindowImpl::Create`[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)によって管理されるウィンドウクラスの情報に基づいて、ウィンドウを作成します。 `CWindowImpl`[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)マクロが含まれてい`CWndClassInfo`ます。これは、新しいウィンドウクラスを登録することを意味します。 既存のウィンドウクラスをスーパークラス化する場合は、から`CWindowImpl`クラスを派生させ、 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)マクロをインクルードします。 この場合、`CWndClassInfo` は、既存のクラスに基づくウィンドウ クラスを登録しますが、`CWindowImpl::WindowProc` を使用します。 例えば:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwindowimpl-class_1.h)]

> [!NOTE]
>  `CWndClassInfo` は、1 つのウィンドウ クラスの情報のみを管理するため、`CWindowImpl` のインスタンスによって作成された各ウィンドウは、同じウィンドウ クラスに基づきます。

`CWindowImpl` は、ウィンドウのサブクラス化もサポートします。 `SubclassWindow` メソッドは、既存のウィンドウを `CWindowImpl` オブジェクトにアタッチし、ウィンドウ プロシージャを `CWindowImpl::WindowProc` に変更します。 `CWindowImpl` の各インスタンスは、別のウィンドウをサブクラス化できます。

> [!NOTE]
>  特定`CWindowImpl`のオブジェクトに対して、 `Create`また`SubclassWindow`はを呼び出します。 同じオブジェクトで両方のメソッドを呼び出さないでください。

に`CWindowImpl`加えて、ATL には、別のオブジェクトに格納されているウィンドウを作成するための[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)が用意されています。

基本クラスのデストラクター (~ `CWindowImplRoot`) では、オブジェクトが破棄される前にウィンドウが失われることが保証されます。

`CWindowImpl`から派生します。これは、から派生`TBase`し、[CMessageMap](../../atl/reference/cmessagemap-class.md) から派生します。`CWindowImplBaseT` `CWindowImplRoot`

|詳細情報:|解決方法|
|--------------------------------|---------|
|コントロールの作成|[ATL チュートリアル](../../atl/active-template-library-atl-tutorial.md)|
|ATL でのウィンドウの使用|[ATL ウィンドウ クラス](../../atl/atl-window-classes.md)|
|ATL プロジェクト ウィザード|[ATL プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)|

## <a name="inheritance-hierarchy"></a>継承階層

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CWindowImplBaseT`

`CWindowImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="create"></a>  CWindowImpl::Create

新しいウィンドウクラスに基づいてウィンドウを作成します。

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="parameters"></a>パラメーター

*hWndParent*<br/>
から親ウィンドウまたはオーナーウィンドウへのハンドル。

*rect*<br/>
からウィンドウの位置を指定する[RECT](/previous-versions/dd162897\(v=vs.85\))構造体。 は`RECT` 、ポインターによって、または参照渡しで渡すことができます。

*szWindowName*<br/>
からウィンドウの名前を指定します。 既定値は NULL です。

*dwStyle*<br/>
からウィンドウのスタイル。 この値は、ウィンドウの特徴クラスによって提供されるスタイルと組み合わされます。 既定値は、特徴クラスにスタイルに対する完全な制御を与えます。 使用可能な値の一覧については、Windows SDK の「 [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) 」を参照してください。

*dwExStyle*<br/>
から拡張ウィンドウスタイル。 この値は、ウィンドウの特徴クラスによって提供されるスタイルと組み合わされます。 既定値は、特徴クラスにスタイルに対する完全な制御を与えます。 使用可能な値の一覧については、Windows SDK の「 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) 」を参照してください。

*MenuOrID*<br/>
から子ウィンドウの場合は、ウィンドウ識別子。 トップレベルウィンドウの場合は、ウィンドウのメニューハンドル。 既定値は**0u**です。

*lpCreateParam*<br/>
からウィンドウ作成データへのポインター。 詳細については、 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)の最後のパラメーターの説明を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は、新しく作成されたウィンドウへのハンドル。 それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

`Create`は、最初にウィンドウクラスが登録されていない場合は、それを登録します。 新しく作成されたウィンドウは、自動的`CWindowImpl`にオブジェクトにアタッチされます。

> [!NOTE]
>  既に`Create` [SubclassWindow](#subclasswindow)を呼び出している場合は、を呼び出さないでください。

既存のウィンドウクラスに基づくウィンドウクラスを使用するには、から`CWindowImpl`クラスを派生させ、 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)マクロをインクルードします。 既存のウィンドウクラスのウィンドウプロシージャは、 [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)に保存されます。 詳細については、「 [CWindowImpl](../../atl/reference/cwindowimpl-class.md)の概要」を参照してください。

> [!NOTE]
>  0を*Menuorid*パラメーターの値として使用する場合は、コンパイラエラーを回避するために、0u (既定値) として指定する必要があります。

##  <a name="defwindowproc"></a>  CWindowImpl::DefWindowProc

[WindowProc](#windowproc)によって呼び出され、メッセージマップによって処理されないメッセージを処理します。

```
LRESULT DefWindowProc(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);

LRESULT DefWindowProc();
```

### <a name="parameters"></a>パラメーター

*uMsg*<br/>
からウィンドウに送信されたメッセージ。

*wParam*<br/>
からメッセージ固有の追加情報。

*lParam*<br/>
からメッセージ固有の追加情報。

### <a name="return-value"></a>戻り値

メッセージ処理の結果。

### <a name="remarks"></a>Remarks

既定では`DefWindowProc` 、は[CallWindowProc](/windows/win32/api/winuser/nf-winuser-callwindowprocw) Win32 関数を呼び出して、 [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)で指定されたウィンドウプロシージャにメッセージ情報を送信します。

パラメーターのない関数は、現在のメッセージから必要なパラメーターを自動的に取得します。

##  <a name="getcurrentmessage"></a>  CWindowImpl::GetCurrentMessage

`MSG`構造体にパッケージ化された現在のメッセージを返します。

```
const MSG* GetCurrentMessage();
```

### <a name="return-value"></a>戻り値

現在のメッセージ。

##  <a name="getwindowproc"></a>  CWindowImpl::GetWindowProc

現在`WindowProc`のウィンドウプロシージャを返します。

```
virtual WNDPROC GetWindowProc();
```

### <a name="return-value"></a>戻り値

現在のウィンドウプロシージャ。

### <a name="remarks"></a>Remarks

ウィンドウプロシージャを独自のに置き換えるには、このメソッドをオーバーライドします。

##  <a name="getwndclassinfo"></a>  CWindowImpl::GetWndClassInfo

ウィンドウクラス情報にアクセスするために、 [Create](#create)によって呼び出されます。

```
static CWndClassInfo& GetWndClassInfo();
```

### <a name="return-value"></a>戻り値

[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)の静的インスタンス。

### <a name="remarks"></a>Remarks

既定では`CWindowImpl` 、は、新しいウィンドウクラスを指定する[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)マクロを使用してこのメソッドを取得します。

既存のウィンドウクラスをスーパークラスにするには`CWindowImpl` 、からクラスを派生させ`GetWndClassInfo`、 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)マクロを含めてオーバーライドします。 詳細については、「 [CWindowImpl](../../atl/reference/cwindowimpl-class.md)の概要」を参照してください。

DECLARE_WND_CLASS マクロと DECLARE_WND_SUPERCLASS マクロを使用するだけでなく`GetWndClassInfo` 、独自の実装でをオーバーライドすることもできます。

##  <a name="m_pfnsuperwindowproc"></a>  CWindowImpl::m_pfnSuperWindowProc

ウィンドウに応じて、は次のいずれかのウィンドウプロシージャを指します。

```
WNDPROC m_pfnSuperWindowProc;
```

### <a name="remarks"></a>Remarks

|ウィンドウの種類|ウィンドウプロシージャ|
|--------------------|----------------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)マクロを使用して指定された新しいウィンドウクラスに基づくウィンドウ。|[DefWindowProc](/windows/win32/api/winuser/nf-winuser-defwindowprocw) Win32 関数。|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)マクロを使用して指定された既存のクラスを変更するウィンドウクラスに基づくウィンドウ。|既存のウィンドウクラスのウィンドウプロシージャ。|
|サブクラスウィンドウです。|サブクラスウィンドウの元のウィンドウプロシージャ。|

[CWindowImpl::D efwindowproc](#defwindowproc)は、に保存されている`m_pfnSuperWindowProc`ウィンドウプロシージャにメッセージ情報を送信します。

##  <a name="onfinalmessage"></a>CWindowImpl:: OnFinalMessage

最後のメッセージを受信した後に呼び出されます (通常は WM_NCDESTROY)。

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>パラメーター

*hWnd*<br/>
から破棄されるウィンドウへのハンドル。

### <a name="remarks"></a>Remarks

の既定の`OnFinalMessage`実装では何も実行されませんが、ウィンドウを破棄する前に、この関数をオーバーライドしてクリーンアップを処理することができます。 ウィンドウの破棄時にオブジェクトを自動的に削除する場合は、この関数で**delete this;** を呼び出すことができます。

##  <a name="subclasswindow"></a>  CWindowImpl::SubclassWindow

*HWnd*によって識別されるウィンドウをサブクラス`CWindowImpl`化し、オブジェクトにアタッチします。

```
BOOL SubclassWindow(HWND hWnd);
```

### <a name="parameters"></a>パラメーター

*hWnd*<br/>
からサブクラス化されているウィンドウへのハンドル。

### <a name="return-value"></a>戻り値

ウィンドウが正常にサブクラス化された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

サブクラス化されたウィンドウで、 [CWindowImpl:: WindowProc](#windowproc)が使用されるようになりました。 元のウィンドウプロシージャは[m_pfnSuperWindowProc](#m_pfnsuperwindowproc)に保存されます。

> [!NOTE]
>  既に`SubclassWindow` [Create](#create)を呼び出している場合は、を呼び出さないでください。

##  <a name="unsubclasswindow"></a>CWindowImpl:: UnsubclassWindow

サブクラスウィンドウを`CWindowImpl`オブジェクトからデタッチし、 [m_pfnSuperWindowProc](#m_pfnsuperwindowproc)に保存されている元のウィンドウプロシージャを復元します。

```
HWND UnsubclassWindow();
```

### <a name="return-value"></a>戻り値

以前にサブクラス化されたウィンドウへのハンドル。

##  <a name="windowproc"></a>  CWindowImpl::WindowProc

この静的関数は、ウィンドウプロシージャを実装します。

```
static LRESULT CALLBACK WindowProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>パラメーター

*hWnd*<br/>
からウィンドウへのハンドル。

*uMsg*<br/>
からウィンドウに送信されたメッセージ。

*wParam*<br/>
からメッセージ固有の追加情報。

*lParam*<br/>
からメッセージ固有の追加情報。

### <a name="return-value"></a>戻り値

メッセージ処理の結果。

### <a name="remarks"></a>Remarks

`WindowProc`は、 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)で宣言された既定のメッセージマップを使用して、メッセージを適切なハンドラーに送信します。 必要に応じ`WindowProc`て、 [DefWindowProc](#defwindowproc)を呼び出して、追加のメッセージ処理を行います。 最終的なメッセージが処理されない`WindowProc`場合、は次の処理を実行します。

- ウィンドウがサブクラス化されていない場合は、サブクラス解除を実行します。

- `m_hWnd` を消去します。

- ウィンドウが破棄される前に[Onfinalmessage](#onfinalmessage)を呼び出します。

をオーバーライド`WindowProc`して、メッセージを処理するためのさまざまなメカニズムを提供できます。

## <a name="see-also"></a>関連項目

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[CComControl クラス](../../atl/reference/ccomcontrol-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
