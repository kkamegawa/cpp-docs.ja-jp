---
title: CMDIChildWnd クラス
ms.date: 11/04/2016
f1_keywords:
- CMDIChildWnd
- AFXWIN/CMDIChildWnd
- AFXWIN/CMDIChildWnd::CMDIChildWnd
- AFXWIN/CMDIChildWnd::Create
- AFXWIN/CMDIChildWnd::GetMDIFrame
- AFXWIN/CMDIChildWnd::MDIActivate
- AFXWIN/CMDIChildWnd::MDIDestroy
- AFXWIN/CMDIChildWnd::MDIMaximize
- AFXWIN/CMDIChildWnd::MDIRestore
- AFXWIN/CMDIChildWnd::SetHandles
helpviewer_keywords:
- CMDIChildWnd [MFC], CMDIChildWnd
- CMDIChildWnd [MFC], Create
- CMDIChildWnd [MFC], GetMDIFrame
- CMDIChildWnd [MFC], MDIActivate
- CMDIChildWnd [MFC], MDIDestroy
- CMDIChildWnd [MFC], MDIMaximize
- CMDIChildWnd [MFC], MDIRestore
- CMDIChildWnd [MFC], SetHandles
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
ms.openlocfilehash: 09a9846cc3d242ef7d812cb31b4dcdd515d5f6ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506080"
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd クラス

ウィンドウ管理用のメンバーも含めて、Windows のマルチ ドキュメント インターフェイス (MDI: multiple document interface) の子ウィンドウの機能が用意されています。

## <a name="syntax"></a>構文

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMDIChildWnd:: CMDIChildWnd](#cmdichildwnd)|`CMDIChildWnd` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMDIChildWnd:: Create](#create)|`CMDIChildWnd`オブジェクトに関連付けられた Windows MDI 子ウィンドウを作成します。|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|MDI クライアントウィンドウの親 MDI フレームを返します。|
|[CMDIChildWnd:: MDIActivate](#mdiactivate)|この MDI 子ウィンドウをアクティブにします。|
|[CMDIChildWnd:: MDIDestroy](#mdidestroy)|この MDI 子ウィンドウを破棄します。|
|[CMDIChildWnd:: MDIMaximize](#mdimaximize)|この MDI 子ウィンドウを最大化します。|
|[CMDIChildWnd:: MDIRestore](#mdirestore)|この MDI 子ウィンドウを最大化または最小化されたサイズから復元します。|
|[CMDIChildWnd:: SetHandles](#sethandles)|メニューとアクセラレータのリソースのハンドルを設定します。|

## <a name="remarks"></a>Remarks

Mdi 子ウィンドウは、一般的なフレームウィンドウのように見えますが、mdi 子ウィンドウは、デスクトップではなく MDI フレームウィンドウ内に表示される点が異なります。 MDI 子ウィンドウには独自のメニューバーはありませんが、代わりに MDI フレームウィンドウのメニューが共有されます。 現在アクティブな MDI 子ウィンドウを表すように、フレームワークによって MDI フレームメニューが自動的に変更されます。

アプリケーションに便利な MDI 子ウィンドウを作成するには、から`CMDIChildWnd`クラスを派生させます。 アプリケーションに固有のデータを格納するために、派生クラスにメンバー変数を追加します。 ウィンドウにメッセージが送られたときに行われる処理を指定するには、派生クラスにメッセージ処理メンバー関数とメッセージ マップを実装します。

MDI 子ウィンドウを構築するには、次の3つの方法があります。

- を使用`Create`して直接作成します。

- を使用`LoadFrame`して直接作成します。

- ドキュメントテンプレートを使用して間接的に構築します。

`Create`または`LoadFrame`を呼び出す前に、 **new**演算子を使用してC++ 、ヒープ上にフレームウィンドウオブジェクトを構築する必要があります。 を呼び出す`Create`前に、ウィンドウクラスを[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)グローバル関数に登録して、フレームのアイコンとクラススタイルを設定することもできます。

`Create`メンバー関数を使用して、フレームの作成パラメーターをイミディエイト引数として渡します。

`LoadFrame`に必要な引数`Create`がより少なく、代わりに、フレームのキャプション、アイコン、アクセラレータテーブル、メニューなど、リソースからほとんどの既定値を取得します。 によって`LoadFrame`アクセスできるようにするには、これらすべてのリソースが同じリソース ID (たとえば、IDR_MAINFRAME) を持っている必要があります。

オブジェクトに`CMDIChildWnd`ビューとドキュメントが含まれている場合は、プログラマが直接作成するのではなく、フレームワークによって間接的に作成されます。 オブジェクト`CDocTemplate`は、フレームの作成、含まれるビューの作成、および適切なドキュメントへのビューの接続を調整します。 `CDocTemplate`コンストラクターのパラメーターは、関連する`CRuntimeClass` 3 つのクラス (ドキュメント、フレーム、およびビュー) のを指定します。 `CRuntimeClass`オブジェクトは、ユーザーが指定したときに新しいフレームを動的に作成するために、フレームワークによって使用されます (たとえば、File new コマンドや MDI Window new コマンドを使用します)。

上の RUNTIME_CLASS 機構を正常に`CMDIChildWnd`動作させるには、から派生したフレームウィンドウクラスを DECLARE_DYNCREATE で宣言する必要があります。

クラス`CMDIChildWnd`は、の既定の`CFrameWnd`実装の多くを継承します。 これらの機能の詳細な一覧については、 [CFrameWnd](../../mfc/reference/cframewnd-class.md)クラスの説明を参照してください。 クラス`CMDIChildWnd`には、次の追加機能があります。

- `CMultiDocTemplate`クラスと共に、同じドキュメント`CMDIChildWnd`テンプレートの複数のオブジェクトが同じメニューを共有し、Windows システムリソースを保存します。

- 現在アクティブな MDI 子ウィンドウメニューは、MDI フレームウィンドウのメニューを完全に置き換えるもので、現在アクティブな MDI 子ウィンドウのキャプションが MDI フレームウィンドウのキャプションに追加されます。 Mdi フレームウィンドウと共に実装される mdi 子ウィンドウ関数のその他の例について`CMDIFrameWnd`は、クラスの説明を参照してください。

フレームウィンドウを破棄C++するために**delete**演算子は使用しないでください。 代わりに、`CWnd::DestroyWindow` を使用してください。 の`CFrameWnd` 実装`PostNcDestroy`は、ウィンドウがC++破棄されたときにオブジェクトを削除します。 ユーザーがフレームウィンドウを閉じると、既定`OnClose`のハンドラーはを呼び出し`DestroyWindow`ます。

の`CMDIChildWnd`詳細については、「[フレームウィンドウ](../../mfc/frame-windows.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="cmdichildwnd"></a>CMDIChildWnd:: CMDIChildWnd

を呼び出して、 `CMDIChildWnd`オブジェクトを構築します。

```
CMDIChildWnd();
```

### <a name="remarks"></a>Remarks

を`Create`呼び出して、表示されるウィンドウを作成します。

### <a name="example"></a>例

  [CMDIChildWnd:: Create](#create)の例を参照してください。

##  <a name="create"></a>CMDIChildWnd:: Create

このメンバー関数を呼び出して、Windows MDI 子ウィンドウを作成し、 `CMDIChildWnd`オブジェクトにアタッチします。

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,
    const RECT& rect = rectDefault,
    CMDIFrameWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszClassName*<br/>
Windows クラス ( [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)構造体) に名前を指定する null で終わる文字列を指します。 クラス名には、 [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)グローバル関数に登録されている任意の名前を指定できます。 標準`CMDIChildWnd`の場合は NULL にする必要があります。

*lpszWindowName*<br/>
ウィンドウ名を表す null で終わる文字列を指します。 タイトルバーのテキストとして使用されます。

*dwStyle*<br/>
ウィンドウ[スタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)属性を指定します。 WS_CHILD スタイルが必要です。

*rect*<br/>
ウィンドウのサイズと位置を格納します。 この`rectDefault`値により、Windows は新しい`CMDIChildWnd`のサイズと位置を指定できます。

*pParentWnd*<br/>
ウィンドウの親を指定します。 NULL の場合、メインアプリケーションウィンドウが使用されます。

*pContext*<br/>
[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)構造体を指定します。 このパラメーターには NULL を指定できます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

現在アクティブな MDI 子フレームウィンドウでは、親フレームウィンドウのキャプションを確認できます。 この機能は、子フレームウィンドウの FWS_ADDTOTITLE スタイルビットをオフにすると無効になります。

フレームワークは、ユーザーコマンドに応答してこのメンバー関数を呼び出し、子ウィンドウを作成します。フレームワークは、 *pContext*パラメーターを使用して、子ウィンドウをアプリケーションに適切に接続します。 を呼び出す`Create`と、 *pContext*を NULL にすることができます。

### <a name="example"></a>例

例 1:

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>例

例 2:

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

##  <a name="getmdiframe"></a>  CMDIChildWnd::GetMDIFrame

MDI 親フレームを返すには、この関数を呼び出します。

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>戻り値

MDI 親フレームウィンドウへのポインター。

### <a name="remarks"></a>Remarks

返されるフレームはから`CMDIChildWnd`削除された2つの親であり、 `CMDIChildWnd`オブジェクトを管理する MDICLIENT 型のウィンドウの親です。 オブジェクトのイミディエイト MDICLIENT parent を一時`CWnd`ポインターとして返す `CMDIChildWnd`には、[GetParent](../../mfc/reference/cwnd-class.md#getparent) メンバー関数を呼び出します。

### <a name="example"></a>例

  [CMDIFrameWnd:: MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu)の例を参照してください。

##  <a name="mdiactivate"></a>CMDIChildWnd:: MDIActivate

Mdi フレームウィンドウとは別に MDI 子ウィンドウをアクティブにするには、このメンバー関数を呼び出します。

```
void MDIActivate();
```

### <a name="remarks"></a>Remarks

フレームがアクティブになると、最後にアクティブ化された子ウィンドウもアクティブになります。

### <a name="example"></a>例

  [CMDIFrameWnd:: GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup)の例を参照してください。

##  <a name="mdidestroy"></a>CMDIChildWnd:: MDIDestroy

このメンバー関数を呼び出して、MDI 子ウィンドウを破棄します。

```
void MDIDestroy();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、フレームウィンドウから子ウィンドウのタイトルを削除し、子ウィンドウを非アクティブにします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

##  <a name="mdimaximize"></a>CMDIChildWnd:: MDIMaximize

MDI 子ウィンドウを最大化するには、このメンバー関数を呼び出します。

```
void MDIMaximize();
```

### <a name="remarks"></a>Remarks

子ウィンドウが最大化されると、クライアント領域がフレームウィンドウのクライアント領域に収まるように、ウィンドウのサイズが変更されます。 Windows では、子ウィンドウのコントロールメニューをフレームのメニューバーに配置して、ユーザーが子ウィンドウを復元または閉じ、子ウィンドウのタイトルをフレームウィンドウのタイトルに追加できるようにします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

##  <a name="mdirestore"></a>CMDIChildWnd:: MDIRestore

このメンバー関数を呼び出して、最大化または最小化されたサイズから MDI 子ウィンドウを復元します。

```
void MDIRestore();
```

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

##  <a name="sethandles"></a>CMDIChildWnd:: SetHandles

メニューとアクセラレータのリソースのハンドルを設定します。

```
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>パラメーター

*hMenu*<br/>
メニューリソースのハンドル。

*hAccel*<br/>
アクセラレータリソースのハンドル。

### <a name="remarks"></a>Remarks

MDI 子ウィンドウオブジェクトによって使用されるメニューおよびアクセラレータリソースを設定するには、この関数を呼び出します。

## <a name="see-also"></a>関連項目

[MFC のサンプル MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC のサンプル MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[MFC のサンプル SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd クラス](../../mfc/reference/cframewnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd クラス](../../mfc/reference/cmdiframewnd-class.md)
