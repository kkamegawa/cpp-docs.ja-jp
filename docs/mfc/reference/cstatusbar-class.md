---
title: CStatusBar クラス
ms.date: 11/04/2016
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
helpviewer_keywords:
- CStatusBar [MFC], CStatusBar
- CStatusBar [MFC], CommandToIndex
- CStatusBar [MFC], Create
- CStatusBar [MFC], CreateEx
- CStatusBar [MFC], DrawItem
- CStatusBar [MFC], GetItemID
- CStatusBar [MFC], GetItemRect
- CStatusBar [MFC], GetPaneInfo
- CStatusBar [MFC], GetPaneStyle
- CStatusBar [MFC], GetPaneText
- CStatusBar [MFC], GetStatusBarCtrl
- CStatusBar [MFC], SetIndicators
- CStatusBar [MFC], SetPaneInfo
- CStatusBar [MFC], SetPaneStyle
- CStatusBar [MFC], SetPaneText
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
ms.openlocfilehash: 48de31d95814ce5fc1fb015e69cf38d73337cb79
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502335"
---
# <a name="cstatusbar-class"></a>CStatusBar クラス

テキスト出力用のペインまたは "インジケーター" の行を持つコントロール バーです。

## <a name="syntax"></a>構文

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CStatusBar:: CStatusBar](#cstatusbar)|`CStatusBar` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CStatusBar:: CommandToIndex](#commandtoindex)|指定されたインジケーター ID のインデックスを取得します。|
|[CStatusBar:: Create](#create)|ステータスバーを作成し、 `CStatusBar`オブジェクトに添付し、初期のフォントとバーの高さを設定します。|
|[CStatusBar:: CreateEx](#createex)|埋め込み`CStatusBar` `CStatusBarCtrl`オブジェクトに対して追加のスタイルを使用してオブジェクトを作成します。|
|[CStatusBar::D rawItem](#drawitem)|オーナー描画ステータスバーコントロールの外観が変化したときに呼び出されます。|
|[CStatusBar:: GetItemID](#getitemid)|指定されたインデックスのインジケーター ID を取得します。|
|[CStatusBar:: GetItemRect](#getitemrect)|指定されたインデックスの表示四角形を取得します。|
|[CStatusBar:: Get Info](#getpaneinfo)|指定されたインデックスのインジケーター ID、スタイル、および幅を取得します。|
|[CStatusBar:: Get Style](#getpanestyle)|指定されたインデックスのインジケータースタイルを取得します。|
|[CStatusBar:: Getて Text](#getpanetext)|指定されたインデックスのインジケーターテキストを取得します。|
|[CStatusBar:: GetStatusBarCtrl](#getstatusbarctrl)|基になるコモンコントロールに直接アクセスできるようにします。|
|[CStatusBar:: SetIndicators](#setindicators)|インジケーター Id を設定します。|
|[CStatusBar:: Setて Info](#setpaneinfo)|指定されたインデックスのインジケーター ID、スタイル、および幅を設定します。|
|[CStatusBar:: Setて Style](#setpanestyle)|指定されたインデックスのインジケーターのスタイルを設定します。|
|[CStatusBar:: Setて Text](#setpanetext)|指定されたインデックスのインジケーターテキストを設定します。|

## <a name="remarks"></a>Remarks

通常、出力ウィンドウは、メッセージ行として、また状態インジケーターとして使用されます。 たとえば、選択したメニューコマンドを簡単に説明するメニューのヘルプメッセージ行や、スクロールロック、NUMLOCK、およびその他のキーの状態を示すインジケーターがあります。

MFC 4.0 の新機能である[CStatusBar:: GetStatusBarCtrl](#getstatusbarctrl)では、Windows コモンコントロールのステータスバーのカスタマイズと追加機能のサポートを利用できます。 `CStatusBar`メンバー関数は、Windows コモンコントロールのほとんどの機能を提供します。ただし、を呼び出し`GetStatusBarCtrl`たときに、ステータスバーに Windows 95/98 ステータスバーの特性をさらに指定できます。 を呼び出す`GetStatusBarCtrl`と、 `CStatusBarCtrl`オブジェクトへの参照が返されます。 Windows コモンコントロールを使用したツールバーのデザインの詳細については、「 [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) 」を参照してください。 一般的なコントロールの全般的な情報については、「Windows SDK の[コモンコントロール](/windows/win32/Controls/common-controls-intro)」を参照してください。

フレームワークは、左端のインジケーターが0の位置にある配列にインジケーター情報を格納します。 ステータスバーを作成する場合は、フレームワークが対応するインジケーターに関連付けている文字列 Id の配列を使用します。 その後、文字列 ID またはインデックスを使用してインジケーターにアクセスできます。

既定では、最初のインジケーターは "エラスティック" で、他のインジケーターペインでは使用されていないステータスバーの長さを占有するので、他のペインは右に並べられます。

ステータスバーを作成するには、次の手順を実行します。

1. オブジェクトを`CStatusBar`構築します。

1. [Create](#create) (または[CreateEx](#createex)) 関数を呼び出して、ステータスバーウィンドウを作成し、 `CStatusBar`オブジェクトにアタッチします。

1. [Setindicators](#setindicators)を呼び出して、文字列 ID を各インジケーターに関連付けます。

ステータスバーペインのテキストを更新するには、次の3つの方法があります。

1. ペイン0のテキストのみを更新するには、 [CWnd:: SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)を呼び出します。

1. ステータスバーの ON_UPDATE_COMMAND_UI ハンドラーで[CCmdUI:: SetText](../../mfc/reference/ccmdui-class.md#settext)を呼び出します。

1. 任意のペインのテキストを更新するには、 [setpane text](#setpanetext)を呼び出します。

[Setpane スタイル](#setpanestyle)を呼び出して、ステータスバーペインのスタイルを更新します。

の使用方法`CStatusBar`の詳細については、「 [MFC でのステータスバーの実装](../../mfc/status-bar-implementation-in-mfc.md)」および[「テクニカルノート 31:コントロールバー](../../mfc/tn031-control-bars.md)。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxext.h

##  <a name="commandtoindex"></a>CStatusBar:: CommandToIndex

指定された ID のインジケーターインデックスを取得します。

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>パラメーター

*nIDFind*<br/>
インデックスを取得するインジケーターの文字列 ID。

### <a name="return-value"></a>戻り値

成功した場合は、インジケーターのインデックス。成功しない場合は-1。

### <a name="remarks"></a>Remarks

最初のインジケーターのインデックスは0です。

##  <a name="create"></a>  CStatusBar::Create

ステータスバー (子ウィンドウ) を作成し、 `CStatusBar`オブジェクトに関連付けます。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
Windows ウィンドウがステータスバーの親である[CWnd](../../mfc/reference/cwnd-class.md)オブジェクトへのポインター。

*dwStyle*<br/>
ステータスバーのスタイル。 標準の Windows[スタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)に加えて、これらのスタイルがサポートされています。

- CBRS_TOP コントロールバーは、フレームウィンドウの上部にあります。

- CBRS_BOTTOM コントロールバーは、フレームウィンドウの下部にあります。

- 親のサイズを変更しても、CBRS_NOALIGN コントロールバーは再配置されません。

*nID*<br/>
ツールバーの子ウィンドウ ID。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

また、初期フォントを設定し、ステータスバーの高さを既定値に設定します。

##  <a name="createex"></a>  CStatusBar::CreateEx

この関数を呼び出して、ステータスバー (子ウィンドウ) を作成し、 `CStatusBar`オブジェクトに関連付けます。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
Windows ウィンドウがステータスバーの親である[CWnd](../../mfc/reference/cwnd-class.md)オブジェクトへのポインター。

*dwCtrlStyle*<br/>
埋め込み[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)オブジェクトを作成するための追加のスタイル。 既定では、サイズ変更グリップまたはツールヒントがサポートされていないステータスバーを指定します。 サポートされているステータスバーのスタイルは次のとおりです。

- SBARS_SIZEGRIP ステータスバーコントロールには、ステータスバーの右端にサイズ変更グリップが含まれています。 サイズ変更グリップは、サイズ変更の境界線に似ています。これは、ユーザーがクリックしてドラッグして親ウィンドウのサイズを変更できる四角形の領域です。

- SBT_TOOLTIPS ステータスバーはツールヒントをサポートします。

これらのスタイルの詳細については、 [CStatusBarCtrl の設定](../../mfc/settings-for-the-cstatusbarctrl.md)を参照してください。

*dwStyle*<br/>
ステータスバーのスタイル。 既定では、表示されているステータスバーがフレームウィンドウの下部に作成されることを指定します。 [「ウィンドウのスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)」および「 [CDialogBar:: Create](../../mfc/reference/cdialogbar-class.md#create)」に記載されているステータスバーコントロールスタイルの任意の組み合わせを適用します。 ただし、このパラメーターには常に WS_CHILD スタイルと WS_VISIBLE スタイルが含まれている必要があります。

*nID*<br/>
ステータスバーの子ウィンドウ ID。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

また、初期フォントを設定し、ステータスバーの高さを既定値に設定します。

埋め`CreateEx`込みステータスバーコントロールの作成中に特定のスタイルが存在する必要がある場合は、 [Create](#create)ではなくを使用します。 たとえば、ステータスバーオブジェクトにツールヒントを表示するには、 *dwCtrlStyle*を SBT_TOOLTIPS に設定します。

##  <a name="cstatusbar"></a>CStatusBar:: CStatusBar

`CStatusBar`オブジェクトを構築し、必要に応じて既定のステータスバーフォントを作成し、フォント特性を既定値に設定します。

```
CStatusBar();
```

##  <a name="drawitem"></a>CStatusBar::D rawItem

このメンバー関数は、オーナー描画ステータスバーの外観が変化したときにフレームワークによって呼び出されます。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>パラメーター

*lpDrawItemStruct*<br/>
必要な描画の種類に関する情報を格納している[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)構造体へのポインター。

### <a name="remarks"></a>Remarks

構造`DRAWITEMSTRUCT`体のメンバーは`itemAction` 、実行する描画アクションを定義します。 オーナー描画`CStatusBar`オブジェクトの描画を実装するには、このメンバー関数をオーバーライドします。 アプリケーションは、このメンバー関数が終了する前に、 *lpDrawItemStruct*で指定された表示コンテキスト用に選択されたすべてのグラフィックスデバイスインターフェイス (GDI) オブジェクトを復元する必要があります。

##  <a name="getitemid"></a>CStatusBar:: GetItemID

*NIndex*によって指定されたインジケーターの ID を返します。

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
ID を取得するインジケーターのインデックス。

### <a name="return-value"></a>戻り値

*NIndex*によって指定されたインジケーターの ID。

##  <a name="getitemrect"></a>  CStatusBar::GetItemRect

*NIndex*によって指定されたインジケーターの座標を、 *lpRect*が指す構造体にコピーします。

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
四角形の座標を取得するインジケーターのインデックス。

*lpRect*<br/>
*NIndex*によって指定されたインジケーターの座標を受け取る[RECT](/previous-versions/dd162897\(v=vs.85\))構造体または[CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトをポイントします。

### <a name="remarks"></a>Remarks

座標は、ステータスバーの左上隅を基準とした相対的なピクセル数です。

##  <a name="getpaneinfo"></a>  CStatusBar::GetPaneInfo

*NID*、 *Nstyle*、および*cxwidth*を、 *nIndex*によって指定された場所のインジケーターペインの ID、スタイル、および幅に設定します。

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
情報を取得するペインのインデックス。

*nID*<br/>
ペインの ID に設定されている UINT への参照。

*nStyle*<br/>
ペインのスタイルに設定されている UINT への参照。

*cxWidth*<br/>
ペインの幅に設定された整数への参照。

##  <a name="getpanestyle"></a>CStatusBar:: Get Style

ステータスバーのペインのスタイルを取得するには、このメンバー関数を呼び出します。

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
スタイルを取得するペインのインデックス。

### <a name="return-value"></a>戻り値

*NIndex*によって指定されたステータスバーペインのスタイル。

### <a name="remarks"></a>Remarks

ペインのスタイルによって、ペインの表示方法が決まります。

ステータスバーで使用できるスタイルの一覧については、「[作成](#create)」を参照してください。

##  <a name="getpanetext"></a>  CStatusBar::GetPaneText

ステータスバーペインに表示されるテキストを取得するには、このメンバー関数を呼び出します。

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
テキストを取得するペインのインデックス。

*rString*<br/>
取得するテキストが格納されている[CString](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクトへの参照。

### <a name="return-value"></a>戻り値

ペインのテキストを格納しているオブジェクト。`CString`

### <a name="remarks"></a>Remarks

このメンバー関数の2番目の形式`CString`は、文字列テキストをオブジェクトに入力します。

##  <a name="getstatusbarctrl"></a>  CStatusBar::GetStatusBarCtrl

このメンバー関数は、基になるコモンコントロールに直接アクセスできるようにします。

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>戻り値

[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)オブジェクトへの参照が含まれています。

### <a name="remarks"></a>Remarks

を`GetStatusBarCtrl`使用して、Windows ステータスバーコモンコントロールの機能を活用し、ステータスバーのカスタマイズに[CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)が提供するサポートを利用します。 たとえば、コモンコントロールを使用して、ステータスバーにサイズ変更グリップを含むスタイルを指定したり、ステータスバーを親ウィンドウのクライアント領域の最上部に表示するスタイルを指定したりできます。

一般的なコントロールの全般的な情報については、「Windows SDK の[コモンコントロール](/windows/win32/Controls/common-controls-intro)」を参照してください。

##  <a name="setindicators"></a>CStatusBar:: SetIndicators

各インジケーターの ID を配列*Lpidarray*の対応する要素によって指定された値に設定し、各 id によって指定された文字列リソースを読み込み、インジケーターのテキストを文字列に設定します。

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>パラメーター

*lpIDArray*<br/>
Id の配列へのポインター。

*nIDCount*<br/>
*Lpidarray*が指す配列内の要素の数。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

##  <a name="setpaneinfo"></a>  CStatusBar::SetPaneInfo

指定したインジケーターペインに新しい ID、スタイル、および幅を設定します。

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
スタイルを設定するインジケーターペインのインデックス。

*nID*<br/>
インジケーターペインの新しい ID。

*nStyle*<br/>
インジケーターペインの新しいスタイル。

*cxWidth*<br/>
インジケーターペインの新しい幅。

### <a name="remarks"></a>Remarks

次のインジケータースタイルがサポートされています。

- SBPS_NOBORDERS ペインの周囲に3-d 境界線を表示しません。

- SBPS_POPOUT テキストが "ポップアウト" されるように反転罫線を解除します。

- SBPS_DISABLED は、テキストを描画しません。

- SBPS_STRETCH Stretch pane を使用して未使用領域を埋める。 このスタイルを設定できるのは、ステータスバーごとに1つのウィンドウのみです。

- SBPS_NORMAL は伸縮、枠線、ポップアウトを行いません。

##  <a name="setpanestyle"></a>CStatusBar:: Setて Style

ステータスバーのペインのスタイルを設定するには、このメンバー関数を呼び出します。

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
スタイルを設定するペインのインデックス。

*nStyle*<br/>
スタイルを設定するペインのスタイル。

### <a name="remarks"></a>Remarks

ペインのスタイルによって、ペインの表示方法が決まります。

ステータスバーで使用できるスタイルの一覧については、「 [setて info](#setpaneinfo)」を参照してください。

##  <a name="setpanetext"></a>  CStatusBar::SetPaneText

このメンバー関数を呼び出して、ペインのテキストを*lpszNewText*が指す文字列に設定します。

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
テキストを設定するペインのインデックス。

*lpszNewText*<br/>
新しいペインのテキストへのポインター。

*bUpdate*<br/>
TRUE の場合、テキストが設定された後、ペインは無効になります。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

を呼び出し`SetPaneText`た後、ステータスバーに新しいテキストを表示するには、UI 更新ハンドラーを追加する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>関連項目

[MFC のサンプル CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC のサンプル DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[CControlBar クラス](../../mfc/reference/ccontrolbar-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl クラス](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar クラス](../../mfc/reference/ccontrolbar-class.md)
