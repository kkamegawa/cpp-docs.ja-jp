---
title: CMiniFrameWnd クラス
ms.date: 11/04/2016
f1_keywords:
- CMiniFrameWnd
- AFXWIN/CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::Create
- AFXWIN/CMiniFrameWnd::CreateEx
helpviewer_keywords:
- CMiniFrameWnd [MFC], CMiniFrameWnd
- CMiniFrameWnd [MFC], Create
- CMiniFrameWnd [MFC], CreateEx
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
ms.openlocfilehash: 45b4698cc70487a6c3fe1470fe27f7b5c4f95402
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504601"
---
# <a name="cminiframewnd-class"></a>CMiniFrameWnd クラス

フローティング ツール バーの周りなどで使用される、半分の高さのフレーム ウィンドウを表します。

## <a name="syntax"></a>構文

```
class CMiniFrameWnd : public CFrameWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|`CMiniFrameWnd` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMiniFrameWnd:: Create](#create)|構築後`CMiniFrameWnd`にオブジェクトを作成します。|
|[CMiniFrameWnd:: CreateEx](#createex)|構築後`CMiniFrameWnd`に、追加のオプションを使用してオブジェクトを作成します。|

## <a name="remarks"></a>Remarks

これらのミニフレームウィンドウは通常のフレームウィンドウと同様に動作しますが、最小化/最大化のボタンやメニューがない点が異なります。また、[システム] メニューをクリックするだけで、それらを閉じることができます。

`CMiniFrameWnd`オブジェクトを使用するには、まずオブジェクトを定義します。 次に、 [Create](#create) member 関数を呼び出してミニフレームウィンドウを表示します。

オブジェクトの使用`CMiniFrameWnd`方法の詳細については、「[ドッキングツールバーとフローティングツールバー](../../mfc/docking-and-floating-toolbars.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="cminiframewnd"></a>CMiniFrameWnd::CMiniFrameWnd

オブジェクトを`CMiniFrameWnd`構築しますが、ウィンドウを作成しません。

```
CMiniFrameWnd();
```

### <a name="remarks"></a>Remarks

ウィンドウを作成するには、 [CMiniFrameWnd:: create](#create)を呼び出します。

##  <a name="create"></a>  CMiniFrameWnd::Create

Windows ミニフレームウィンドウを作成し、 `CMiniFrameWnd`オブジェクトにアタッチします。

```
virtual BOOL Create(
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>パラメーター

*lpClassName*<br/>
Windows クラスに名前を指定する null で終わる文字列を指します。 クラス名には、グローバル[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)関数に登録されている任意の名前を指定できます。 NULL の場合、ウィンドウクラスはフレームワークによって登録されます。 MFC では、既定のクラスに次のスタイルと属性が付与されます。

- スタイルビット CS_DBLCLKS を設定します。これは、ユーザーがマウスをダブルクリックすると、ダブルクリックメッセージをウィンドウプロシージャに送信します。

- スタイルのビット CS_HREDRAW と CS_VREDRAW を設定します。これは、ウィンドウのサイズが変更されたときに再描画されるクライアント領域の内容を指定します。

- クラスカーソルを Windows 標準 IDC_ARROW に設定します。

- クラスの背景ブラシを NULL に設定します。これにより、ウィンドウの背景が消去されません。

- クラスアイコンを標準の [フラグが設定された Windows ロゴ] アイコンに設定します。

- Windows によって示される既定のサイズと位置にウィンドウを設定します。

*lpWindowName*<br/>
ウィンドウ名を含む null で終わる文字列を指します。

*dwStyle*<br/>
ウィンドウスタイル属性を指定します。 これには、標準のウィンドウスタイルと、次の特殊なスタイルの1つ以上を含めることができます。

- MFS_MOVEFRAME を使用すると、キャプションだけでなく、ウィンドウの任意の端をクリックして、ミニフレームウィンドウを移動できます。

- MFS_4THICKFRAME は、ミニフレームウィンドウのサイズ変更を無効にします。

- MFS_SYNCACTIVE は、ミニフレームウィンドウのアクティブ化を、親ウィンドウのアクティブ化に同期します。

- MFS_THICKFRAME を使用すると、クライアント領域のコンテンツで許可されているサイズでミニフレームウィンドウのサイズを小さくすることができます。

- MFS_BLOCKSYSMENU は、[システム] メニューと [コントロール] メニューへのアクセスを無効にし、キャプション (タイトルバー) の一部に変換します。

使用可能なウィンドウスタイル値の説明については、「 [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) 」を参照してください。 ミニフレームウィンドウで使用される一般的な組み合わせは&#124;、&#124;WS_POPUP WS_CAPTION WS_SYSMENU です。

*rect*<br/>
ウィンドウの目的の大きさを指定する構造体。`RECT`

*pParentWnd*<br/>
親ウィンドウをポイントします。 トップレベルウィンドウには NULL を使用します。

*nID*<br/>
ミニフレームウィンドウが子ウィンドウとして作成された場合、これは子コントロールの識別子になります。それ以外の場合は0です。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

`Create`ウィンドウのクラス名とウィンドウ名を初期化し、そのスタイルと親の既定値を登録します。

##  <a name="createex"></a>CMiniFrameWnd:: CreateEx

`CMiniFrameWnd` オブジェクトを作成します。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>パラメーター

*dwExStyle*<br/>
作成する`CMiniFrameWnd`の拡張スタイルを指定します。 ウィンドウに任意の[拡張ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)を適用します。

*lpClassName*<br/>
Windows クラス ( [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)構造体) に名前を指定する null で終わる文字列を指します。 クラス名には、グローバル[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)関数に登録されている任意の名前を指定することも、定義済みのコントロールクラス名を使用することもできます。 NULL にすることはできません。

*lpWindowName*<br/>
ウィンドウ名を含む null で終わる文字列を指します。

*dwStyle*<br/>
ウィンドウスタイル属性を指定します。 使用可能な値の説明については、「[ウィンドウのスタイル」](../../mfc/reference/styles-used-by-mfc.md#window-styles)および「 [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) 」を参照してください。

*rect*<br/>
ウィンドウのサイズと位置 ( *pParentWnd*のクライアント座標)。

*pParentWnd*<br/>
親ウィンドウオブジェクトを指します。

*nID*<br/>
子ウィンドウの識別子。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

パラメーター `CreateEx`では、ウィンドウの WNDCLASS、ウィンドウスタイル、および (必要に応じて) 初期位置とサイズを指定します。 `CreateEx`ウィンドウの親 (存在する場合) と ID も指定します。

を`CreateEx`実行すると、Windows は[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)、 [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)、 [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)、および[WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)の各メッセージをウィンドウに送信します。

既定のメッセージ処理を拡張するには、から`CMiniFrameWnd`クラスを派生させ、新しいクラスにメッセージマップを追加して、上記のメッセージのメンバー関数を指定します。 たとえば`OnCreate`、新しいクラスに必要な初期化を実行する場合は、をオーバーライドします。

さら`On`に*メッセージ*メッセージハンドラーをオーバーライドして、派生クラスにさらに機能を追加します。

WS_VISIBLE スタイルが指定されている場合、アクティブ化してウィンドウを表示するために必要なすべてのメッセージがウィンドウに送信されます。 ウィンドウスタイルでタイトルバーが指定されている場合は、 *lpszWindowName*パラメーターによって示されるウィンドウタイトルがタイトルバーに表示されます。

*DwStyle*パラメーターには、[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)の任意の組み合わせを指定できます。

旧形式の [パレット] ツールボックスウィンドウはサポートされなくなりました。 以前のバージョンの Windows で MFC アプリケーションを実行しているときに、"X" 閉じるボタンのない古いスタイルはサポートされていましたが、 C++Visual .net ではサポートされなくなりました。 新しい WS_EX_TOOLWINDOW スタイルのみがサポートされるようになりました。このスタイルの詳細については、「[拡張ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)」を参照してください。

## <a name="see-also"></a>関連項目

[CFrameWnd クラス](../../mfc/reference/cframewnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd クラス](../../mfc/reference/cframewnd-class.md)
