---
title: CToolTipCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CToolTipCtrl
- AFXCMN/CToolTipCtrl
- AFXCMN/CToolTipCtrl::CToolTipCtrl
- AFXCMN/CToolTipCtrl::Activate
- AFXCMN/CToolTipCtrl::AddTool
- AFXCMN/CToolTipCtrl::AdjustRect
- AFXCMN/CToolTipCtrl::Create
- AFXCMN/CToolTipCtrl::CreateEx
- AFXCMN/CToolTipCtrl::DelTool
- AFXCMN/CToolTipCtrl::GetBubbleSize
- AFXCMN/CToolTipCtrl::GetCurrentTool
- AFXCMN/CToolTipCtrl::GetDelayTime
- AFXCMN/CToolTipCtrl::GetMargin
- AFXCMN/CToolTipCtrl::GetMaxTipWidth
- AFXCMN/CToolTipCtrl::GetText
- AFXCMN/CToolTipCtrl::GetTipBkColor
- AFXCMN/CToolTipCtrl::GetTipTextColor
- AFXCMN/CToolTipCtrl::GetTitle
- AFXCMN/CToolTipCtrl::GetToolCount
- AFXCMN/CToolTipCtrl::GetToolInfo
- AFXCMN/CToolTipCtrl::HitTest
- AFXCMN/CToolTipCtrl::Pop
- AFXCMN/CToolTipCtrl::Popup
- AFXCMN/CToolTipCtrl::RelayEvent
- AFXCMN/CToolTipCtrl::SetDelayTime
- AFXCMN/CToolTipCtrl::SetMargin
- AFXCMN/CToolTipCtrl::SetMaxTipWidth
- AFXCMN/CToolTipCtrl::SetTipBkColor
- AFXCMN/CToolTipCtrl::SetTipTextColor
- AFXCMN/CToolTipCtrl::SetTitle
- AFXCMN/CToolTipCtrl::SetToolInfo
- AFXCMN/CToolTipCtrl::SetToolRect
- AFXCMN/CToolTipCtrl::SetWindowTheme
- AFXCMN/CToolTipCtrl::Update
- AFXCMN/CToolTipCtrl::UpdateTipText
helpviewer_keywords:
- CToolTipCtrl [MFC], CToolTipCtrl
- CToolTipCtrl [MFC], Activate
- CToolTipCtrl [MFC], AddTool
- CToolTipCtrl [MFC], AdjustRect
- CToolTipCtrl [MFC], Create
- CToolTipCtrl [MFC], CreateEx
- CToolTipCtrl [MFC], DelTool
- CToolTipCtrl [MFC], GetBubbleSize
- CToolTipCtrl [MFC], GetCurrentTool
- CToolTipCtrl [MFC], GetDelayTime
- CToolTipCtrl [MFC], GetMargin
- CToolTipCtrl [MFC], GetMaxTipWidth
- CToolTipCtrl [MFC], GetText
- CToolTipCtrl [MFC], GetTipBkColor
- CToolTipCtrl [MFC], GetTipTextColor
- CToolTipCtrl [MFC], GetTitle
- CToolTipCtrl [MFC], GetToolCount
- CToolTipCtrl [MFC], GetToolInfo
- CToolTipCtrl [MFC], HitTest
- CToolTipCtrl [MFC], Pop
- CToolTipCtrl [MFC], Popup
- CToolTipCtrl [MFC], RelayEvent
- CToolTipCtrl [MFC], SetDelayTime
- CToolTipCtrl [MFC], SetMargin
- CToolTipCtrl [MFC], SetMaxTipWidth
- CToolTipCtrl [MFC], SetTipBkColor
- CToolTipCtrl [MFC], SetTipTextColor
- CToolTipCtrl [MFC], SetTitle
- CToolTipCtrl [MFC], SetToolInfo
- CToolTipCtrl [MFC], SetToolRect
- CToolTipCtrl [MFC], SetWindowTheme
- CToolTipCtrl [MFC], Update
- CToolTipCtrl [MFC], UpdateTipText
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
ms.openlocfilehash: 177f6eeada942440c33f7dd0a0cbc6d9e59d867c
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894147"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl Class

"ツールヒント コントロール" の機能をカプセル化しています。このコンロトールは、アプリケーションでツールの目的を説明する 1 行のテキストを表示する小さなポップアップ ウィンドウです。

## <a name="syntax"></a>構文

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CToolTipCtrl::CToolTipCtrl](#ctooltipctrl)|`CToolTipCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CToolTipCtrl::Activate](#activate)|アクティブにし、ツール ヒント コントロールを非アクティブ化されます。|
|[CToolTipCtrl::AddTool](#addtool)|ツール ヒント コントロールでツールを登録します。|
|[CToolTipCtrl::AdjustRect](#adjustrect)|ツール ヒント コントロールのテキストの間の変換は、四角形とそのウィンドウの四角形を表示します。|
|[CToolTipCtrl::Create](#create)|ツール ヒント コントロールを作成しにアタッチします、`CToolTipCtrl`オブジェクト。|
|[CToolTipCtrl::CreateEx](#createex)|指定した Windows の拡張スタイルを使用して、ツール ヒント コントロールを作成しにアタッチします、`CToolTipCtrl`オブジェクト。|
|[CToolTipCtrl::DelTool](#deltool)|ツール ヒント コントロールからツールを削除します。|
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|ツール ヒントのサイズを取得します。|
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|サイズ、位置、および現在のツール ヒント コントロールを表示するツールヒント ウィンドウのテキストなどの情報を取得します。|
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|初期、ポップアップで、再表示必要時間を取得する期間のツールは、現在設定されているコントロールのヒントします。|
|[CToolTipCtrl::GetMargin](#getmargin)|上、左、下、およびツール ヒントのウィンドウに設定されている右の余白を取得します。|
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|ツール ヒント ウィンドウの最大幅を取得します。|
|[CToolTipCtrl::GetText](#gettext)|ツールは、ツール ヒント コントロールを保持するテキストを取得します。|
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|ツール ヒント ウィンドウの背景色を取得します。|
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|ツール ヒント ウィンドウのテキストの色を取得します。|
|[CToolTipCtrl::GetTitle](#gettitle)|現在のツール ヒント コントロールのタイトルを取得します。|
|[CToolTipCtrl::GetToolCount](#gettoolcount)|ツール ヒント コントロールで保持しているツールの数を取得します。|
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|ツールのツール ヒント コントロールを保持する情報を取得します。|
|[CToolTipCtrl::HitTest](#hittest)|指定したツールの外接する四角形内にあるかどうかを判断する点をテストします。 そうである場合は、ツールに関する情報を取得します。|
|[CToolTipCtrl::Pop](#pop)|ビューから表示されるツール ヒント ウィンドウを削除します。|
|[CToolTipCtrl::Popup](#popup)|現在のツールヒント コントロールの最後のマウス メッセージの座標にある表示させます。|
|[CToolTipCtrl::RelayEvent](#relayevent)|マウス メッセージを処理するためのツール ヒント コントロールに渡します。|
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|初期のポップアップ ウィンドウを設定し、ツール ヒント コントロールの期間を表示します。|
|[CToolTipCtrl::SetMargin](#setmargin)|上、左、下、およびツール ヒント ウィンドウの右余白を設定します。|
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|ツール ヒント ウィンドウの最大幅を設定します。|
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|ツール ヒント ウィンドウの背景色を設定します。|
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|ツール ヒント ウィンドウのテキストの色を設定します。|
|[CToolTipCtrl::SetTitle](#settitle)|ツール ヒントには、標準的なアイコンとタイトルの文字列を追加します。|
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|ツール ヒントが保持するツールの情報を設定します。|
|[CToolTipCtrl::SetToolRect](#settoolrect)|ツールの新しい外接する四角形を設定します。|
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|ツール ヒントのウィンドウの表示スタイルを設定します。|
|[CToolTipCtrl::Update](#update)|現在のツールを再描画を強制します。|
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|ツールは、ツール ヒントのテキストを設定します。|

## <a name="remarks"></a>Remarks

「ツール」とは、子ウィンドウやコントロール、ウィンドウのクライアント領域内でアプリケーションで定義された四角形領域など、いずれか、ウィンドウです。 ツール ヒントには、ほとんどの場合、表示され場合にのみ、ユーザー ツールの上にカーソルを置きます約半分のままに 2 つ目は表示されません。 ツール ヒントは、カーソルの近くに表示し、ユーザーがマウス ボタンをクリックしてまたはツールから、カーソルを移動するときは表示されなくなります。

`CToolTipCtrl` ツール ヒントのテキスト、自体には、ツール ヒント ウィンドウの幅、およびツールヒントの背景とテキストの色を囲む余白の幅の初期時間や、ツール ヒントの期間を制御する機能を提供します。 1 つのツール ヒント コントロールは、1 つ以上のツールの情報を提供できます。

`CToolTipCtrl`クラスには、Windows の一般的なツール ヒント コントロールの機能が用意されています。 このコントロール (つまり、`CToolTipCtrl`クラス) は以降 Windows 95/98 および Windows NT 3.51 の下で実行中のプログラムにのみ使用できます。

ツール ヒントを有効にする方法の詳細については、次を参照してください。[いない CFrameWnd から派生した Windows でのツール ヒント](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)します。

使用しての詳細については`CToolTipCtrl`を参照してください[コントロール](../../mfc/controls-mfc.md)と[を使用して CToolTipCtrl](../../mfc/using-ctooltipctrl.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcmn.h

##  <a name="activate"></a>  CToolTipCtrl::Activate

この関数では、ツール ヒント コントロールをアクティブまたは非アクティブにします。

```
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>パラメーター

*bActivate*<br/>
ツール ヒント コントロールがアクティブ化または非アクティブ化するかどうかを指定します。

### <a name="remarks"></a>Remarks

場合*bActivate*が true の場合、コントロールがアクティブになる; が非アクティブ化、FALSE の場合。

コントロールに登録されているツールのカーソルがある場合、ツール ヒント コントロールがアクティブである場合、ツール ヒント情報が表示されます。アクティブな場合は、ツール ヒントの情報が表示されないもツールにカーソルがある場合。

### <a name="example"></a>例

  例をご覧ください[CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)します。

##  <a name="addtool"></a>  CToolTipCtrl::AddTool

ツール ヒント コントロールでツールを登録します。

```
BOOL AddTool(
    CWnd* pWnd,
    UINT nIDText,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);

BOOL AddTool(
    CWnd* pWnd,
    LPCTSTR lpszText = LPSTR_TEXTCALLBACK,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>パラメーター

*我が物*<br/>
含む、ツール ウィンドウへのポインター。

*nIDText*<br/>
ツールのテキストを含む文字列リソースの ID。

*lpRectTool*<br/>
ポインターを[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)ツールの座標を含む構造体の外接する四角形。 識別されるウィンドウのクライアント領域の左上隅に対する相対座標は、*我が物*します。

*nIDTool*<br/>
ツールの ID。

*lpszText*<br/>
ツールのテキストへのポインター。 TTN_NEEDTEXT 通知のメッセージがウィンドウの親に移動してこのパラメーターに保持するようにする値が含まれている場合を*我が物*を指します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

*LpRectTool*と*nIDTool*パラメーター両方必要があります、有効な場合、または*lpRectTool*が null の場合、 *nIDTool* 0 にする必要があります。

ツール ヒント コントロールは、1 つ以上のツールを関連付けることができます。 ツールのカーソルがあるときにツール ヒントに格納されている情報が表示されるように、ツール ヒント コントロールでツールを登録するには、この関数を呼び出します。

> [!NOTE]
>  使用してスタティック コントロールにツール ヒントを設定することはできません`AddTool`します。

### <a name="example"></a>例

  例をご覧ください[CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)します。

##  <a name="adjustrect"></a>  CToolTipCtrl::AdjustRect

ツールヒント コントロールのテキストの間の変換は、四角形とそのウィンドウの四角形を表示します。

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>パラメーター

*lprc*<br/>
ポインターを[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)ツール ヒント ウィンドウの四角形またはテキストの表示の四角形を保持する構造体。

*き*<br/>
TRUE の場合、 *lprc* 、テキスト表示の四角形を指定するために使用され、対応するウィンドウの四角形を受け取ります。 FALSE の場合、 *lprc*ウィンドウの四角形を指定するために使用され、対応するテキストの表示の四角形を受け取ります。

### <a name="return-value"></a>戻り値

以外の場合は、四角形は正常に調整されました。それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、そのウィンドウの四角形、または指定したテキストの表示の四角形を表示するために必要なツール ヒント ウィンドウ四角形から、ツール ヒント コントロールのテキスト表示の四角形を計算します。

このメンバー関数は、Win32 メッセージの動作を実装[TTM_ADJUSTRECT](/windows/desktop/Controls/ttm-adjustrect)」の説明に従って、Windows SDK。

##  <a name="create"></a>  CToolTipCtrl::Create

ツール ヒント コントロールを作成しにアタッチします、`CToolTipCtrl`オブジェクト。

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
ツール ヒント コントロールの親ウィンドウを通常を指定します、`CDialog`します。 NULL は指定できません。

*dwStyle*<br/>
ツール ヒント コントロールのスタイルを指定します。 参照してください、**解説**詳細についてはします。

### <a name="return-value"></a>戻り値

0 以外の値、`CToolTipCtrl`オブジェクトが正常に作成した。 それ以外の場合には 0。

### <a name="remarks"></a>Remarks

構築する、`CToolTipCtrl`で 2 つの手順。 最初に、構築するコンス トラクターを呼び出し、`CToolTipCtrl`オブジェクトを呼び出して`Create`をツール ヒント コントロールを作成し、アタッチ先、`CToolTipCtrl`オブジェクト。

*DwStyle*パラメーターの任意の組み合わせを指定できます[ウィンドウ スタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)します。 さらに、ツール ヒント コントロールでは、2 つのクラスに固有のスタイルがあります。TTS_ALWAYSTIP TTS_NOPREFIX.

|スタイル|説明|
|-----------|-------------|
|TTS_ALWAYSTIP|ツール ヒント コントロールのオーナー ウィンドウがアクティブまたは非アクティブなのかどうかに関係なく、ツールの上にカーソルがある場合、ツール ヒントが表示されることを指定します。 このスタイルでは、しない場合は、ツール ヒント コントロールは、ツールのオーナー ウィンドウがアクティブの場合は、それがアクティブでない場合は表示されます。|
|TTS_NOPREFIX|このスタイルでは、システムがアンパサンド (&)、文字列から文字を削除できなくなります。 ツール ヒント コントロールが TTS_NOPREFIX スタイルを持たない場合、アプリケーション メニュー項目とは、ツール ヒント コントロールでテキストとして、同じ文字列を使用することにより、アンパサンド文字が自動的に削除します。|

ツール ヒント コントロールが、WS_EX_TOOLWINDOW と WS_POPUP ウィンドウ スタイルの 以下の指定にコントロールを作成するときに関係なく、します。

拡張ウィンドウ スタイルを使用して、ツール ヒント コントロールを作成するには、呼び出す[CToolTipCtrl::CreateEx](#createex)の代わりに`Create`します。

### <a name="example"></a>例

  例をご覧ください[CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)します。

##  <a name="createex"></a>  CToolTipCtrl::CreateEx

コントロール (子ウィンドウ) を作成し、関連付けること、`CToolTipCtrl`オブジェクト。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
コントロールの親であるウィンドウへのポインター。

*dwStyle*<br/>
ツール ヒント コントロールのスタイルを指定します。 参照してください、**解説**の[作成](#create)詳細についてはします。

*dwStyleEx*<br/>
作成されるコントロールの拡張スタイルを指定します。 拡張 Windows スタイルの一覧は、次を参照してください。、 *dwExStyle*パラメーターを[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK に含まれています。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外。 それ以外の場合は 0。

### <a name="remarks"></a>Remarks

使用`CreateEx`の代わりに`Create`、Windows の拡張スタイルの先頭で指定された、Windows の拡張スタイルを適用する**WS_EX**します。

##  <a name="ctooltipctrl"></a>  CToolTipCtrl::CToolTipCtrl

`CToolTipCtrl` オブジェクトを構築します。

```
CToolTipCtrl();
```

### <a name="remarks"></a>Remarks

呼び出す必要があります`Create`後、オブジェクトを構築します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

##  <a name="deltool"></a>  CToolTipCtrl::DelTool

指定されたツールを削除します*我が物*と*nIDTool* 、ツール ヒント コントロールでサポートされているツールのコレクションから。

```
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>パラメーター

*我が物*<br/>
含む、ツール ウィンドウへのポインター。

*nIDTool*<br/>
ツールの ID。

##  <a name="getbubblesize"></a>  CToolTipCtrl::GetBubbleSize

ツール ヒントのサイズを取得します。

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>パラメーター

*lpToolInfo*<br/>
ツール ヒントへのポインター [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)構造体。

### <a name="return-value"></a>戻り値

ツール ヒントのサイズ。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[TTM_GETBUBBLESIZE](/windows/desktop/Controls/ttm-getbubblesize)」の説明に従って、Windows SDK。

##  <a name="getcurrenttool"></a>  CToolTipCtrl::GetCurrentTool

サイズ、位置、および現在のツールヒント コントロールによって表示されるツールヒント ウィンドウのテキストなどの情報を取得します。

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*lpToolInfo*|[out]ポインターを[TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)現在ツールヒント ウィンドウに関する情報を受け取る構造体。|

### <a name="return-value"></a>戻り値

情報が正常に取得される場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [TTM_GETCURRENTTOOL](/windows/desktop/Controls/ttm-getcurrenttool)メッセージは、Windows SDK で説明します。

### <a name="example"></a>例

次のコード例では、現在のツールヒント ウィンドウに関する情報を取得します。

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

##  <a name="getdelaytime"></a>  CToolTipCtrl::GetDelayTime

初期のポップアップ ウィンドウを取得し、表示、ツール ヒント コントロールに現在設定されています。

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>パラメーター

*dwDuration*<br/>
期間値を指定するフラグが取得されます。 このパラメーターには、次の値のいずれかを指定できます。

- ツール ヒント ウィンドウの時間の長さは TTDT_AUTOPOP 取得が表示されるは、ポインターが静止しているツールの外接する四角形内の場合。

- TTDT_INITIAL 取得ツール ヒントのウィンドウの前に、ツールの外接する四角形内で、ポインターを静止時間の長さが表示されます。

- TTDT_RESHOW 取得ポインターとして表示する次のツール ヒントのウィンドウにかかる時間の長さ 1 つのツールから別に移動します。

### <a name="return-value"></a>戻り値

指定遅延時間 (ミリ秒)

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[TTM_GETDELAYTIME](/windows/desktop/Controls/ttm-getdelaytime)」の説明に従って、Windows SDK。

##  <a name="getmargin"></a>  CToolTipCtrl::GetMargin

上、左、下、および右余白のツール ヒント ウィンドウの設定を取得します。

```
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>パラメーター

*lprc*<br/>
アドレスを`RECT`余白の情報を受け取る構造体。 メンバー、 [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)構造体は、外接する四角形を定義しないでください。 このメッセージのためには構造体のメンバーはように解釈されます。

|メンバー|表現|
|------------|--------------------|
|`top`|上罫線と (ピクセル単位)、ツール ヒントのテキストの上端との間の距離。|
|`left`|左罫線と (ピクセル単位) のツールヒントのテキストの左端間の距離。|
|`bottom`|下罫線と (ピクセル単位) のツールヒントのテキストの下部にある間の距離。|
|`right`|右罫線と (ピクセル単位) のツールヒントのテキストの右端までの間の距離。|

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[TTM_GETMARGIN](/windows/desktop/Controls/ttm-getmargin)」の説明に従って、Windows SDK。

##  <a name="getmaxtipwidth"></a>  CToolTipCtrl::GetMaxTipWidth

ツール ヒント ウィンドウの最大幅を取得します。

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>戻り値

ツール ヒント ウィンドウの最大幅。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[TTM_GETMAXTIPWIDTH](/windows/desktop/Controls/ttm-getmaxtipwidth)」の説明に従って、Windows SDK。

##  <a name="gettext"></a>  CToolTipCtrl::GetText

ツールは、ツール ヒント コントロールを保持するテキストを取得します。

```
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>パラメーター

*str*<br/>
参照を`CString`ツールのテキストを受け取るオブジェクト。

*我が物*<br/>
含む、ツール ウィンドウへのポインター。

*nIDTool*<br/>
ツールの ID。

### <a name="remarks"></a>Remarks

*我が物*と*nIDTool*パラメーターは、ツールを指定します。 以前の呼び出し、ツール ヒント コントロールにツールが既に登録されている場合`CToolTipCtrl::AddTool`、によって参照されるオブジェクト、 *str*パラメーターには、ツールのテキストが割り当てられます。

##  <a name="gettipbkcolor"></a>  CToolTipCtrl::GetTipBkColor

ツール ヒント ウィンドウの背景色を取得します。

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>戻り値

A [COLORREF](/windows/desktop/gdi/colorref)背景色を表す値です。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[TTM_GETTIPBKCOLOR](/windows/desktop/Controls/ttm-gettipbkcolor)」の説明に従って、Windows SDK。

##  <a name="gettiptextcolor"></a>  CToolTipCtrl::GetTipTextColor

ツール ヒント ウィンドウのテキストの色を取得します。

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>戻り値

A [COLORREF](/windows/desktop/gdi/colorref)テキストの色を表す値です。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[TTM_GETTIPTEXTCOLOR](/windows/desktop/Controls/ttm-gettiptextcolor)」の説明に従って、Windows SDK。

##  <a name="gettitle"></a>  CToolTipCtrl::GetTitle

現在のツール ヒント コントロールのタイトルを取得します。

```
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pttgt*|[out]ポインターを[TTGETTITLE](/windows/desktop/api/commctrl/ns-commctrl-_ttgettitle)ツール ヒント コントロールに関する情報を含む構造体。 このメソッドが戻るとき、 *pszTitle*のメンバー、 [TTGETTITLE](/windows/desktop/api/commctrl/ns-commctrl-_ttgettitle)タイトルのテキストへのポインターを構造体します。|

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [TTM_GETTITLE](/windows/desktop/Controls/ttm-gettitle)メッセージは、Windows SDK で説明します。

##  <a name="gettoolcount"></a>  CToolTipCtrl::GetToolCount

ツール ヒント コントロールに登録されているツールの数を取得します。

```
int GetToolCount() const;
```

### <a name="return-value"></a>戻り値

ツールの数は、ツール ヒント コントロールに登録します。

##  <a name="gettoolinfo"></a>  CToolTipCtrl::GetToolInfo

ツールのツール ヒント コントロールを保持する情報を取得します。

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>パラメーター

*ToolInfo*<br/>
参照を`TOOLINFO`ツールのテキストを受け取るオブジェクト。

*我が物*<br/>
含む、ツール ウィンドウへのポインター。

*nIDTool*<br/>
ツールの ID。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

`hwnd`と`uId`のメンバー、 [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)構造によって参照される*CToolInfo*ツールを識別します。 そのツールが以前の呼び出し、ツール ヒント コントロールに登録されている場合`AddTool`、`TOOLINFO`ツールに関する情報の構造が入力されます。

##  <a name="hittest"></a>  CToolTipCtrl::HitTest

指定したツールの外接する四角形内にあるかどうかを判断し、そうである場合は、ツールに関する情報を取得する点をテストします。

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>パラメーター

*我が物*<br/>
含む、ツール ウィンドウへのポインター。

*pt*<br/>
ポインターを`CPoint`をテストする点の座標を格納しているオブジェクト。

*lpToolInfo*<br/>
ポインター [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)ツールに関する情報を含む構造体。

### <a name="return-value"></a>戻り値

ヒット テスト情報で指定されたポイントが、ツールの外接する四角形内にある場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

この関数は 0 以外の値を返す場合、構造体が指す*返すとき*点は四角形が内のツールの情報が入力されます。

`TTHITTESTINFO`構造は次のように定義されます。

```cpp
typedef struct _TT_HITTESTINFO { // tthti
    HWND hwnd;   // handle of tool or window with tool
    POINT pt;    // client coordinates of point to test
    TOOLINFO ti; // receives information about the tool
} TTHITTESTINFO, FAR * LPHITTESTINFO;
```

- `hwnd`

   ツールのハンドルを指定します。

- `pt`

   ポイントは、ツールの外接する四角形の場合は、点の座標を指定します。

- `ti`

   このツールに関する情報。 詳細については、`TOOLINFO`構造体は、「 [CToolTipCtrl::GetToolInfo](#gettoolinfo)します。

##  <a name="pop"></a>  CToolTipCtrl::Pop

ビューから表示されるツール ヒント ウィンドウを削除します。

```
void Pop();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[TTM_POP](/windows/desktop/Controls/ttm-pop)」の説明に従って、Windows SDK。

##  <a name="popup"></a>  CToolTipCtrl::Popup

現在のツールヒント コントロールの最後のマウス メッセージの座標にある表示させます。

```
void Popup();
```

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [TTM_POPUP](/windows/desktop/Controls/ttm-popup)メッセージは、Windows SDK で説明します。

### <a name="example"></a>例

次のコード例では、ツールヒント ウィンドウが表示されます。

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

##  <a name="relayevent"></a>  CToolTipCtrl::RelayEvent

マウス メッセージを処理するためのツール ヒント コントロールに渡します。

```
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>パラメーター

*lpMsg*<br/>
ポインターを[MSG](/windows/desktop/api/winuser/ns-winuser-msg)リレーにメッセージを含む構造体。

### <a name="remarks"></a>Remarks

ツール ヒント コントロールの処理のみ次のメッセージを送信する`RelayEvent`:

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>例

  例をご覧ください[CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)します。

##  <a name="setdelaytime"></a>  CToolTipCtrl::SetDelayTime

ツール ヒント コントロールの遅延時間を設定します。

```
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>パラメーター

*nDelay*<br/>
新しい時刻の遅延 (ミリ秒) を指定します。

*dwDuration*<br/>
期間値を指定するフラグが取得されます。 参照してください[については](#getdelaytime)の有効な値の説明。

*iTime*<br/>
指定遅延時間 (ミリ秒)。

### <a name="remarks"></a>Remarks

時刻の遅延はツール ヒントのウィンドウが表示されるまで、ツールのカーソルを維持する必要があります。 既定の遅延時間は、500 ミリ秒です。

##  <a name="setmargin"></a>  CToolTipCtrl::SetMargin

上、左、下、およびツール ヒント ウィンドウの右余白を設定します。

```
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>パラメーター

*lprc*<br/>
アドレスを`RECT`を設定する余白の情報を含む構造体。 メンバー、`RECT`構造体は、外接する四角形を定義しないでください。 参照してください[CToolTipCtrl::GetMargin](#getmargin)余白情報の説明についてはします。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[TTM_SETMARGIN](/windows/desktop/Controls/ttm-setmargin)」の説明に従って、Windows SDK。

##  <a name="setmaxtipwidth"></a>  CToolTipCtrl::SetMaxTipWidth

ツール ヒント ウィンドウの最大幅を設定します。

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>パラメーター

*iWidth*<br/>
設定する最大のツール ヒント ウィンドウの幅。

### <a name="return-value"></a>戻り値

前のヒントの最大の幅。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[TTM_SETMAXTIPWIDTH](/windows/desktop/Controls/ttm-setmaxtipwidth)」の説明に従って、Windows SDK。

##  <a name="settipbkcolor"></a>  CToolTipCtrl::SetTipBkColor

ツール ヒント ウィンドウの背景色を設定します。

```
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>パラメーター

*clr*<br/>
新しい背景色です。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[TTM_SETTIPBKCOLOR](/windows/desktop/Controls/ttm-settipbkcolor)」の説明に従って、Windows SDK。

##  <a name="settiptextcolor"></a>  CToolTipCtrl::SetTipTextColor

ツール ヒント ウィンドウのテキストの色を設定します。

```
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>パラメーター

*clr*<br/>
新しいテキストの色。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[TTM_SETTIPTEXTCOLOR](/windows/desktop/Controls/ttm-settiptextcolor)」の説明に従って、Windows SDK。

##  <a name="settitle"></a>  CToolTipCtrl::SetTitle

ツール ヒントには、標準的なアイコンとタイトルの文字列を追加します。

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>パラメーター

*uIcon*<br/>
参照してください*アイコン*で[TTM_SETTITLE](/windows/desktop/Controls/ttm-settitle) Windows SDK に含まれています。

*lpstrTitle*<br/>
タイトル文字列へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[TTM_SETTITLE](/windows/desktop/Controls/ttm-settitle)」の説明に従って、Windows SDK。

##  <a name="settoolinfo"></a>  CToolTipCtrl::SetToolInfo

ツール ヒントが保持するツールの情報を設定します。

```
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>パラメーター

*lpToolInfo*<br/>
ポインターを[TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)設定情報を指定する構造体。

##  <a name="settoolrect"></a>  CToolTipCtrl::SetToolRect

ツールの新しい外接する四角形を設定します。

```
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*我が物*<br/>
含む、ツール ウィンドウへのポインター。

*nIDTool*<br/>
ツールの ID。

*lpRect*<br/>
ポインターを[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)構造体の新しい外接する四角形を指定します。

##  <a name="setwindowtheme"></a>  CToolTipCtrl::SetWindowTheme

ツール ヒントのウィンドウの表示スタイルを設定します。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>パラメーター

*pszSubAppName*<br/>
設定する visual スタイルを含む Unicode 文字列へのポインター。

### <a name="return-value"></a>戻り値

戻り値は使用されません。

### <a name="remarks"></a>Remarks

このメンバー関数の機能をエミュレートする、 [TTM_SETWINDOWTHEME](/windows/desktop/Controls/ttm-setwindowtheme)メッセージ、Windows SDK で説明されているとします。

##  <a name="update"></a>  CToolTipCtrl::Update

現在のツールを再描画を強制します。

```
void Update();
```

##  <a name="updatetiptext"></a>  CToolTipCtrl::UpdateTipText

このコントロールのツールのツールヒントのテキストを更新します。

```
void UpdateTipText(
    LPCTSTR lpszText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);

void UpdateTipText(
    UINT nIDText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>パラメーター

*lpszText*<br/>
ツールのテキストへのポインター。

*我が物*<br/>
含む、ツール ウィンドウへのポインター。

*nIDTool*<br/>
ツールの ID。

*nIDText*<br/>
ツールのテキストを含む文字列リソースの ID。

## <a name="see-also"></a>関連項目

[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CToolBar クラス](../../mfc/reference/ctoolbar-class.md)
