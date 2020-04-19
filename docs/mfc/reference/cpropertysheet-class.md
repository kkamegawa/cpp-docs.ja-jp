---
title: CPropertySheet クラス
ms.date: 11/04/2016
f1_keywords:
- CPropertySheet
- AFXDLGS/CPropertySheet
- AFXDLGS/CPropertySheet::CPropertySheet
- AFXDLGS/CPropertySheet::AddPage
- AFXDLGS/CPropertySheet::Construct
- AFXDLGS/CPropertySheet::Create
- AFXDLGS/CPropertySheet::DoModal
- AFXDLGS/CPropertySheet::EnableStackedTabs
- AFXDLGS/CPropertySheet::EndDialog
- AFXDLGS/CPropertySheet::GetActiveIndex
- AFXDLGS/CPropertySheet::GetActivePage
- AFXDLGS/CPropertySheet::GetPage
- AFXDLGS/CPropertySheet::GetPageCount
- AFXDLGS/CPropertySheet::GetPageIndex
- AFXDLGS/CPropertySheet::GetTabControl
- AFXDLGS/CPropertySheet::MapDialogRect
- AFXDLGS/CPropertySheet::OnInitDialog
- AFXDLGS/CPropertySheet::PressButton
- AFXDLGS/CPropertySheet::RemovePage
- AFXDLGS/CPropertySheet::SetActivePage
- AFXDLGS/CPropertySheet::SetFinishText
- AFXDLGS/CPropertySheet::SetTitle
- AFXDLGS/CPropertySheet::SetWizardButtons
- AFXDLGS/CPropertySheet::SetWizardMode
- AFXDLGS/CPropertySheet::m_psh
helpviewer_keywords:
- CPropertySheet [MFC], CPropertySheet
- CPropertySheet [MFC], AddPage
- CPropertySheet [MFC], Construct
- CPropertySheet [MFC], Create
- CPropertySheet [MFC], DoModal
- CPropertySheet [MFC], EnableStackedTabs
- CPropertySheet [MFC], EndDialog
- CPropertySheet [MFC], GetActiveIndex
- CPropertySheet [MFC], GetActivePage
- CPropertySheet [MFC], GetPage
- CPropertySheet [MFC], GetPageCount
- CPropertySheet [MFC], GetPageIndex
- CPropertySheet [MFC], GetTabControl
- CPropertySheet [MFC], MapDialogRect
- CPropertySheet [MFC], OnInitDialog
- CPropertySheet [MFC], PressButton
- CPropertySheet [MFC], RemovePage
- CPropertySheet [MFC], SetActivePage
- CPropertySheet [MFC], SetFinishText
- CPropertySheet [MFC], SetTitle
- CPropertySheet [MFC], SetWizardButtons
- CPropertySheet [MFC], SetWizardMode
- CPropertySheet [MFC], m_psh
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
ms.openlocfilehash: 23d17aee2aacbc1484c0f3e181bc824546ab49a2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502826"
---
# <a name="cpropertysheet-class"></a>CPropertySheet クラス

タブ ダイアログ ボックスとしても知られるプロパティ シートを表します。

## <a name="syntax"></a>構文

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CPropertySheet:: CPropertySheet](#cpropertysheet)|`CPropertySheet` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CPropertySheet:: AddPage](#addpage)|プロパティ シートにページを追加します。|
|[CPropertySheet:: Construct](#construct)|`CPropertySheet` オブジェクトを構築します。|
|[CPropertySheet:: Create](#create)|モードレスプロパティシートを表示します。|
|[CPropertySheet::D oModal](#domodal)|モーダルプロパティシートを表示します。|
|[CPropertySheet:: EnableStackedTabs](#enablestackedtabs)|プロパティシートで積み上げタブまたはスクロールタブを使用するかどうかを示します。|
|[CPropertySheet:: EndDialog](#enddialog)|プロパティシートを終了します。|
|[CPropertySheet:: GetActiveIndex](#getactiveindex)|プロパティシートのアクティブページのインデックスを取得します。|
|[CPropertySheet:: GetActivePage](#getactivepage)|アクティブなページオブジェクトを返します。|
|[CPropertySheet:: GetPage](#getpage)|指定されたページへのポインターを取得します。|
|[CPropertySheet:: GetPageCount](#getpagecount)|プロパティシート内のページ数を取得します。|
|[CPropertySheet:: GetPageIndex](#getpageindex)|プロパティシートの指定されたページのインデックスを取得します。|
|[CPropertySheet:: GetTabControl](#gettabcontrol)|タブコントロールへのポインターを取得します。|
|[CPropertySheet:: Map Rect](#mapdialogrect)|四角形のダイアログボックス単位を画面単位に変換します。|
|[CPropertySheet:: OnInitDialog](#oninitdialog)|プロパティシートの初期化を強化するためにオーバーライドします。|
|[CPropertySheet::P ressButton](#pressbutton)|プロパティシート内の指定したボタンの選択をシミュレートします。|
|[CPropertySheet::RemovePage](#removepage)|プロパティシートからページを削除します。|
|[CPropertySheet:: SetActivePage](#setactivepage)|アクティブなページオブジェクトをプログラムによって設定します。|
|[CPropertySheet:: Setfinish テキスト](#setfinishtext)|[完了] ボタンのテキストを設定します。|
|[CPropertySheet:: SetTitle](#settitle)|プロパティシートのキャプションを設定します。|
|[CPropertySheet:: SetWizardButtons](#setwizardbuttons)|ウィザードボタンを有効にします。|
|[CPropertySheet:: SetWizardMode](#setwizardmode)|ウィザードモードを有効にします。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CPropertySheet:: m_psh](#m_psh)|Windows の[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)構造体。 基本的なプロパティシートパラメーターへのアクセスを提供します。|

## <a name="remarks"></a>Remarks

プロパティシートは、1つ`CPropertySheet`のオブジェクトと1つ以上の[CPropertyPage](../../mfc/reference/cpropertypage-class.md)オブジェクトで構成されます。 フレームワークは、タブインデックスのセットと、現在選択されているページを含む領域をウィンドウとして表示します。 ユーザーは、適切なタブを使用して特定のページに移動します。

`CPropertySheet`Windows 98 および Windows NT 2000 で導入された拡張[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)構造体をサポートします。 構造体には、"ウォーターマーク" 背景ビットマップの使用をサポートする追加のフラグとメンバーが含まれています。

これらの新しいイメージをプロパティシートオブジェクトに自動的に表示するには、 [CPropertySheet:: Construct](#construct)または[CPropertySheet:: CPropertySheet](#cpropertysheet)の呼び出しで、ビットマップおよびパレットのイメージに有効な値を渡します。

は、 [CDialog](../../mfc/reference/cdialog-class.md)から派生した`CPropertySheet`ものではありませんが、オブジェクトの管理は、オブジェクトの`CDialog`管理と似ています。 `CPropertySheet` たとえば、プロパティシートを作成するには、コンストラクターを呼び出し、モーダルプロパティシートに対して[DoModal](#domodal)を呼び出すか、モードレスプロパティシートに対してを[作成](#create)するという2部構成の構築が必要になります。 `CPropertySheet`には、次の2種類のコンストラクターがあります。[CPropertySheet:: Construct](#construct)と[CPropertySheet:: CPropertySheet](#cpropertysheet)。

オブジェクトを`CPropertySheet`構築すると、[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)によっては初回例外が発生する可能性があります。 この結果、システムは、シートが作成される前にプロパティシートのスタイルを変更しようとします。 この例外を回避するには、を作成`CPropertySheet`するときに次のスタイルを設定してください。

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

次のスタイルは省略可能であり、初回例外が発生することはありません。

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

それ以外`Window Styles`は禁止されているため、有効にしないでください。

`CPropertySheet`オブジェクトと外部オブジェクトとの間でのデータ交換は、 `CDialog`オブジェクトとのデータ交換に似ています。 重要な違いは、プロパティシートの設定は通常、 `CPropertyPage` `CPropertySheet`オブジェクト自体ではなく、オブジェクトのメンバー変数であることです。

ウィザードと呼ばれるタブダイアログボックスの種類を作成することができます。これは、デバイスの設定やニュースレターの作成など、操作の手順をユーザーに案内する一連のプロパティページを含むプロパティシートで構成されています。 ウィザードの [型タブ] ダイアログボックスでは、プロパティページにタブはなく、一度に表示できるプロパティページは1つだけです。 また、 **[OK]** ボタンと **[今すぐ適用]** ボタンの代わりに、ウィザードの種類 タブのダイアログボックスには、 **[戻る]** ボタン、 **[次へ]** または **[完了**] ボタン、 **[キャンセル**] ボタン、および **[ヘルプ]** ボタンがあります。

ウィザードの種類のダイアログボックスを作成するには、標準のプロパティシートを作成する場合と同じ手順に従いますが、 [DoModal](#domodal)を呼び出す前に[setwizardmode](#setwizardmode)を呼び出します。 ウィザードのボタンを有効にするには、 [Setwizardbuttons](#setwizardbuttons)を呼び出し、フラグを使用して関数と外観をカスタマイズします。 **[完了**] ボタンを有効にするには、ウィザードの最後のページでユーザーが操作を実行した後で、 [setfinish text](#setfinishtext)を呼び出します。

オブジェクトの使用`CPropertySheet`方法の詳細については、「[プロパティシートとプロパティページ](../../mfc/property-sheets-and-property-pages-in-mfc.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdlgs

##  <a name="addpage"></a>CPropertySheet:: AddPage

指定されたページを、プロパティシートの右端のタブに追加します。

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>パラメーター

*pPage*<br/>
プロパティシートに追加するページをポイントします。 Nll は指定できません。

### <a name="remarks"></a>Remarks

プロパティシートに表示するページを左から右に追加します。

`AddPage``CPropertySheet`オブジェクトのページリストに[CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)オブジェクトを追加しますが、実際にはページのウィンドウを作成しません。 フレームワークは、ユーザーがページを選択するまで、ページのウィンドウの作成を延期します。

を使用して`AddPage` `CPropertySheet`プロパティページを追加すると、はの親`CPropertyPage`になります。 プロパティページからプロパティシートにアクセスするには、 [CWnd:: GetParent](../../mfc/reference/cwnd-class.md#getparent)を呼び出します。

プロパティシートウィンドウの作成が呼び出さ`AddPage`れるまで待機する必要はありません。 通常は、 [DoModal](#domodal)を`AddPage`呼び出す前、またはを[作成](#create)する前に、を呼び出します。

プロパティページの`AddPage`表示後にを呼び出すと、タブ行に新しく追加されたページが反映されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

##  <a name="construct"></a>CPropertySheet:: Construct

`CPropertySheet` オブジェクトを構築します。

```
void Construct(
    UINT nIDCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

void Construct(
    LPCTSTR pszCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

void Construct(
    UINT nIDCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);

void Construct(
    LPCTSTR pszCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);
```

### <a name="parameters"></a>パラメーター

*nIDCaption*<br/>
プロパティシートに使用するキャプションの ID。

*pParentWnd*<br/>
プロパティシートの親ウィンドウへのポインター。 NULL の場合、親ウィンドウはアプリケーションのメインウィンドウになります。

*iSelectPage*<br/>
最初に配置されるページのインデックス。 既定値は、シートに追加された最初のページです。

*pszCaption*<br/>
プロパティシートに使用するキャプションを格納している文字列へのポインター。 Nll は指定できません。

*hbmWatermark*<br/>
プロパティページのウォーターマークビットマップを処理します。

*Hて透かし*<br/>
ウォーターマークのビットマップやヘッダービットマップのパレットを処理します。

*hbmHeader*<br/>
プロパティページのヘッダービットマップを処理します。

### <a name="remarks"></a>Remarks

クラスコンストラクターのいずれかがまだ呼び出されていない場合は、このメンバー関数を呼び出します。 たとえば、オブジェクトの`Construct` `CPropertySheet`配列を宣言または割り当てたときに、を呼び出します。 配列の場合は、配列内の各`Construct`メンバーに対してを呼び出す必要があります。

プロパティシートを表示するには、 [DoModal](#domodal)または[Create](#create)を呼び出します。 最初のパラメーターに含まれる文字列は、プロパティシートのキャプションバーに配置されます。

上に示したの3番目または4番`Construct`目のプロトタイプを使用している場合は、透かしやヘッダーの画像を自動的に表示することができます。また、 *hbmwatermark*、hて*透かし*、および/または*hbmwatermark*パラメーターに有効な値を渡します。

### <a name="example"></a>例

次の例は、どのような状況で`Construct`呼び出すかを示しています。

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

##  <a name="cpropertysheet"></a>CPropertySheet:: CPropertySheet

`CPropertySheet` オブジェクトを構築します。

```
CPropertySheet();

explicit CPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

explicit CPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

CPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);

CPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);
```

### <a name="parameters"></a>パラメーター

*nIDCaption*<br/>
プロパティシートに使用するキャプションの ID。

*pParentWnd*<br/>
プロパティシートの親ウィンドウを指します。 NULL の場合、親ウィンドウはアプリケーションのメインウィンドウになります。

*iSelectPage*<br/>
最初に配置されるページのインデックス。 既定値は、シートに追加された最初のページです。

*pszCaption*<br/>
プロパティシートに使用するキャプションを格納している文字列を指します。 Nll は指定できません。

*hbmWatermark*<br/>
プロパティシートの背景ビットマップを処理するハンドル。

*Hて透かし*<br/>
ウォーターマークビットマップまたはヘッダービットマップのパレットを処理するハンドル。

*hbmHeader*<br/>
プロパティページのヘッダービットマップを処理するハンドル。

### <a name="remarks"></a>Remarks

プロパティシートを表示するには、 [DoModal](#domodal)または[Create](#create)を呼び出します。 最初のパラメーターに含まれる文字列は、プロパティシートのキャプションバーに配置されます。

複数のパラメーターがある場合 (たとえば、配列を使用している場合) は、`CPropertySheet` の代わりに [Construct](#construct) を使用します。

上記の3番目または4番目`CPropertySheet`のプロトタイプを使用し、 *hbmwatermark*パラメーター、hて*透かし*値、または*hbmwatermark*パラメーターに有効な値を渡すと、ウォーターマークやヘッダー画像を自動的に表示できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

##  <a name="create"></a>CPropertySheet:: Create

モードレスプロパティシートを表示します。

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
親ウィンドウをポイントします。 NULL の場合、親はデスクトップです。

*dwStyle*<br/>
プロパティシートのウィンドウスタイル。 使用できるスタイルの完全な一覧については、「[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)」を参照してください。

*dwExStyle*<br/>
プロパティシートの拡張ウィンドウスタイル。 使用できるスタイルの完全な一覧については、「[拡張ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)」を参照してください。

### <a name="return-value"></a>戻り値

プロパティシートが正常に作成された場合は0以外の値。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

の呼び出しは`Create` 、コンストラクターの内部に配置することも、コンストラクターが呼び出された後に呼び出すこともできます。

*DwStyle*として-1 を渡すことによって表される既定&#124;の&#124;スタイル&#124;は&#124;、&#124;実際には WS_SYSMENU WS_POPUP WS_CAPTION DS_MODALFRAME DS_CONTEXTHELP WS_VISIBLE です。 既定の拡張ウィンドウスタイルは、 *Dwexstyle*として0を渡すことによって表され、実際には WS_EX_DLGMODALFRAME です。

この`Create`メンバー関数は、プロパティシートを作成した直後にを返します。 プロパティシートを破棄するには、 [CWnd::D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow)を呼び出します。

の呼び出しで表示されるモードレスプロパティ`Create`シートには、[OK]、[キャンセル]、[今すぐ適用]、および [ヘルプ] ボタンはモーダルプロパティシートとして表示されません。 必要なボタンは、ユーザーが作成する必要があります。

モーダルプロパティシートを表示するには、代わりに[DoModal](#domodal)を呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

##  <a name="domodal"></a>  CPropertySheet::DoModal

モーダルプロパティシートを表示します。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>戻り値

IDOK または IDCANCEL (関数が成功した場合)。それ以外の場合は0または-1。 プロパティシートがウィザードとして設定されている場合 (「 [setwizardmode](#setwizardmode)」を参照)、 `DoModal` ID_WIZFINISH または IDCANCEL のいずれかが返されます。

### <a name="remarks"></a>Remarks

戻り値は、プロパティシートを閉じたコントロールの ID に対応します。 この関数が戻ると、プロパティシートとすべてのページに対応するウィンドウが破棄されます。 オブジェクト自体も存在します。 通常は、`DoModal` が IDOK を返した後、[CPropertyPage](../../mfc/reference/cpropertypage-class.md) オブジェクトからデータを取得します。

モードレスプロパティシートを表示するには、代わりに[Create](#create)を呼び出します。

対応するダイアログリソースからプロパティページを作成すると、初回例外が発生する可能性があります。 これにより、ページが作成される前に、プロパティページによってダイアログリソースのスタイルが必要なスタイルに変わります。 一般に、リソースは読み取り専用であるため、例外が発生します。 システムは例外を処理し、変更されたリソースのコピーを作成します。 そのため、初回例外を無視することができます。

> [!NOTE]
>  この例外は、非同期例外処理モデルを使用してコンパイルする場合に、オペレーティングシステムによって処理される必要があります。 例外処理モデルの詳細については、「 [/EH (例外処理モデル)](../../build/reference/eh-exception-handling-model.md)」を参照してください。 この場合は、catch がすべての例外`CPropertySheet::DoModal`を処理C++する try-catch ブロックを使用して、の呼び出しをラップしません`catch (...)`。たとえば、のようになります。 このブロックは、オペレーティングシステムに対して想定されている例外を処理し、予期しない動作を発生させます。 ただし、特定の例外のC++種類や、アクセス違反例外がオペレーティングシステムに渡される構造化例外処理では、例外処理を安全に使用できます。

この初回例外が生成されないようにするには、プロパティシートの[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)が正しいことを手動で保証します。 プロパティシートには、次のスタイルを設定する必要があります。

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

初回例外を発生させずに、次のオプションのスタイルを使用できます。

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

他のすべての Windows スタイルは、プロパティシートと互換性がないため、無効にします。 このアドバイスは、拡張スタイルには適用されません。 これらの標準スタイルを適切に設定すると、プロパティシートを変更する必要がなくなり、初回例外の生成を回避できます。

### <a name="example"></a>例

[CPropertySheet:: AddPage](#addpage)の例を参照してください。

##  <a name="enablestackedtabs"></a>  CPropertySheet::EnableStackedTabs

プロパティシート内のタブの行を積み重ねるかどうかを示します。

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>パラメーター

*bStacked*<br/>
プロパティシートで積み上げタブを有効にするかどうかを示します。 *Bstacked*を FALSE に設定して、タグの積み上げ行を無効にします。

### <a name="remarks"></a>Remarks

既定では、プロパティシートに表示されるタブの数が、プロパティシートの幅の1行に収まりきらない場合、タブは複数の行にスタックされます。 スタックタブではなくスクロールタブを使用するには、[DoModal](#domodal) または [Create](#create) を呼び出す前に、*bstacked* を FALSE に設定して `EnableStackedTabs` を呼び出します。

モーダルプロパティシート`EnableStackedTabs`またはモードレスプロパティシートを作成するときに、を呼び出す必要があります。 このスタイルをから派生し`CPropertySheet`たクラスに組み込むには、WM_CREATE のメッセージハンドラーを記述します。 [CWnd:: OnCreate](../../mfc/reference/cwnd-class.md#oncreate)のオーバーライドされたバージョンで`EnableStackedTabs( FALSE )` 、基本クラスの実装を呼び出す前にを呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

##  <a name="enddialog"></a>CPropertySheet:: EndDialog

プロパティシートを終了します。

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>パラメーター

*nEndID*<br/>
プロパティシートの戻り値として使用される識別子。

### <a name="remarks"></a>Remarks

このメンバー関数は、[OK]、[キャンセル]、または [閉じる] ボタンが押されたときにフレームワークによって呼び出されます。 プロパティシートを閉じる必要があるイベントが発生した場合は、このメンバー関数を呼び出します。

このメンバー関数は、モーダルダイアログボックスでのみ使用されます。

### <a name="example"></a>例

[CPropertySheet::P ressButton](#pressbutton)の例を参照してください。

##  <a name="getactiveindex"></a>  CPropertySheet::GetActiveIndex

プロパティシートウィンドウのアクティブページのインデックス番号を取得し、返されたインデックス番号をの`GetPage`パラメーターとして使用します。

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>戻り値

アクティブページのインデックス番号。

### <a name="example"></a>例

[CPropertySheet:: GetActivePage](#getactivepage)の例を参照してください。

##  <a name="getactivepage"></a>CPropertySheet:: GetActivePage

プロパティシートウィンドウのアクティブページを取得します。

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>戻り値

アクティブページへのポインター。

### <a name="remarks"></a>Remarks

アクティブページで何らかのアクションを実行するには、このメンバー関数を使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

##  <a name="getpage"></a>CPropertySheet:: GetPage

このプロパティシート内の指定されたページへのポインターを返します。

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>パラメーター

*nPage*<br/>
目的のページのインデックス (0 から開始)。 0から、プロパティシート内のページ数より1小さい値にする必要があります。

### <a name="return-value"></a>戻り値

*Npage*パラメーターに対応するページへのポインター。

### <a name="example"></a>例

[CPropertyPage:: OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)の例を参照してください。

##  <a name="getpagecount"></a>  CPropertySheet::GetPageCount

プロパティシート内の現在のページ数を決定します。

```
int GetPageCount() const;
```

### <a name="return-value"></a>戻り値

プロパティシート内のページ数。

### <a name="example"></a>例

[CPropertyPage:: OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish)の例を参照してください。

##  <a name="getpageindex"></a>  CPropertySheet::GetPageIndex

プロパティシート内の指定されたページのインデックス番号を取得します。

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>パラメーター

*pPage*<br/>
検索するインデックスを持つページをポイントします。 Nll は指定できません。

### <a name="return-value"></a>戻り値

ページのインデックス番号。

### <a name="remarks"></a>Remarks

たとえば、を使用`GetPageIndex`して、 [setactivepage](#setactivepage)または[getpage](#getpage)を使用するためにページインデックスを取得します。

### <a name="example"></a>例

[CPropertySheet:: GetActivePage](#getactivepage)の例を参照してください。

##  <a name="gettabcontrol"></a>CPropertySheet:: GetTabControl

タブコントロールに固有の操作 (つまり、 [CTabCtrl](../../mfc/reference/ctabctrl-class.md)内のいずれかの api を使用する場合) を行うための、タブコントロールへのポインターを取得します。

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>戻り値

タブコントロールへのポインター。

### <a name="remarks"></a>Remarks

たとえば、初期化中に各タブにビットマップを追加する場合は、このメンバー関数を呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

##  <a name="m_psh"></a>  CPropertySheet::m_psh

[PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2)の特性を格納するメンバーを持つ構造体。

### <a name="remarks"></a>Remarks

この構造体を使用して、プロパティシートを構築した後で、 [DoModal](#domodal)メンバー関数と共に表示する前に、外観を初期化します。 たとえば、の`m_psh` *dwSize*メンバーを、プロパティシートに設定するサイズに設定します。

メンバーの一覧など、この構造の詳細については、Windows SDK の「PROPSHEETHEADER」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

##  <a name="mapdialogrect"></a>  CPropertySheet::MapDialogRect

四角形のダイアログボックス単位を画面単位に変換します。

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
変換するダイアログボックス座標を格納している[RECT](/previous-versions/dd162897\(v=vs.85\))構造体または[CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトをポイントします。

### <a name="remarks"></a>Remarks

ダイアログボックスの単位は、ダイアログボックスのテキストに使用されるフォントの平均の幅と高さから派生した、現在のダイアログボックスの基本単位に関して示されています。 1つの水平方向の単位はダイアログボックスの基本幅の単位の1番目で、1つの垂直方向の単位はダイアログボックスの基本高さの単位の8分の1です。

[GetDS_SETFONT Baseunits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) Windows 関数はシステムフォントのサイズ情報を返しますが、リソース定義ファイルでスタイルを使用する場合は、各プロパティシートに別のフォントを指定できます。 Windows SDK で説明されている[Mapの rect](/windows/win32/api/winuser/nf-winuser-mapdialogrect)ウィンドウ関数は、このダイアログボックスに適したフォントを使用します。

この`MapDialogRect`メンバー関数は、 *lpRect*内のダイアログボックス単位を画面単位 (ピクセル) で置き換えます。これにより、四角形を使用してダイアログボックスを作成したり、ボックス内にコントロールを配置したりすることができます。

##  <a name="oninitdialog"></a>  CPropertySheet::OnInitDialog

をオーバーライドして、プロパティシートの初期化を強化します。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>戻り値

アプリケーションで、プロパティシート内のコントロールのいずれかに入力フォーカスを設定するかどうかを指定します。 が`OnInitDialog` 0 以外の値を返した場合、Windows は、プロパティシートの最初のコントロールに入力フォーカスを設定します。 アプリケーションが0を返すのは、プロパティシート内のコントロールのいずれかに入力フォーカスが明示的に設定されている場合のみです。

### <a name="remarks"></a>Remarks

このメンバー関数は、WM_INITDIALOG メッセージへの応答として呼び出されます。 このメッセージは、プロパティシートが表示される直前に発生する、 [Create](#create)または[DoModal](#domodal)呼び出し中にプロパティシートに送信されます。

プロパティシートの初期化時に特別な処理を実行する必要がある場合は、このメンバー関数をオーバーライドします。 オーバーライドされたバージョンでは、最初に`OnInitDialog`基本クラスを呼び出しますが、戻り値は無視します。 通常は、オーバーライドされたメンバー関数から TRUE を返します。

このメンバー関数には、メッセージマップエントリは必要ありません。

##  <a name="pressbutton"></a>CPropertySheet::P ressButton

プロパティシート内の指定したボタンの選択をシミュレートします。

```
void PressButton(int nButton);
```

### <a name="parameters"></a>パラメーター

*nButton*<br/>
nButton:押されたボタンを識別します。 このパラメーターには、次のいずれかの値を指定できます。

- PSBTN_BACK は、[戻る] ボタンを選択します。

- PSBTN_NEXT は [次へ] ボタンを選択します。

- PSBTN_FINISH は [完了] ボタンを選択します。

- PSBTN_OK は、[OK] ボタンを選択します。

- PSBTN_APPLYNOW によって [今すぐ適用] ボタンが選択されます。

- PSBTN_CANCEL は [キャンセル] ボタンを選択します。

- PSBTN_HELP は、[ヘルプ] ボタンを選択します。

### <a name="remarks"></a>Remarks

Windows SDK Pressbutton メッセージの詳細については、「 [PSM_PRESSBUTTON](/windows/win32/Controls/psm-pressbutton) 」を参照してください。

を`PressButton`呼び出すと、プロパティページからフレームワークに[PSN_APPLY](/windows/win32/Controls/psn-apply)通知が送信されません。 この通知を送信するには、 [CPropertyPage:: OnOK](../../mfc/reference/cpropertypage-class.md#onok)を呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

##  <a name="removepage"></a>  CPropertySheet::RemovePage

プロパティシートからページを削除し、関連付けられているウィンドウを破棄します。

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>パラメーター

*pPage*<br/>
プロパティシートから削除するページをポイントします。 Nll は指定できません。

*nPage*<br/>
削除するページのインデックス。 0から、プロパティシート内のページ数より1小さい値にする必要があります。

### <a name="remarks"></a>Remarks

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)オブジェクト自体は、 `CPropertySheet`ウィンドウの所有者が閉じられるまで破棄されません。

##  <a name="setactivepage"></a>CPropertySheet:: SetActivePage

アクティブページを変更します。

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>パラメーター

*nPage*<br/>
設定するページのインデックス。 0から、プロパティシート内のページ数より1小さい値にする必要があります。

*pPage*<br/>
プロパティシートで設定するページをポイントします。 NULL にすることはできません。

### <a name="return-value"></a>戻り値

プロパティシートが正常にアクティブ化された場合は0以外の値。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

たとえば、あるページ`SetActivePage`に対するユーザーの操作によって、別のページがアクティブページになるようにする場合は、を使用します。

### <a name="example"></a>例

[CPropertySheet:: GetActivePage](#getactivepage)の例を参照してください。

##  <a name="setfinishtext"></a>CPropertySheet:: Setfinish テキスト

[完了] コマンドボタンのテキストを設定します。

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>パラメーター

*lpszText*<br/>
[完了] コマンドボタンに表示されるテキストを指します。

### <a name="remarks"></a>Remarks

を`SetFinishText`呼び出して、[完了] コマンドボタンにテキストを表示し、ウィザードの最後のページでユーザーが操作を完了した後、[次へ] ボタンと [戻る] ボタンを非表示にします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="settitle"></a>CPropertySheet:: SetTitle

プロパティシートのキャプション (フレームウィンドウのタイトルバーに表示されるテキスト) を指定します。

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>パラメーター

*nStyle*<br/>
プロパティシートのタイトルのスタイルを指定します。 スタイルは、0または PSH_PROPTITLE として指定する必要があります。 スタイルが PSH_PROPTITLE に設定されている場合は、キャプションとして指定されたテキストの後に "Properties" という単語が表示されます。 たとえば、(" `SetTitle`simple", PSH_PROPTITLE) を呼び出すと、プロパティシートのキャプションが "simple Properties" になります。

*lpszText*<br/>
プロパティシートのタイトルバーでキャプションとして使用されるテキストを指します。

### <a name="remarks"></a>Remarks

既定では、プロパティシートはプロパティシートコンストラクターの caption パラメーターを使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

##  <a name="setwizardbuttons"></a>CPropertySheet:: SetWizardButtons

ウィザードプロパティシートの [戻る]、[次へ]、[完了] ボタンを有効または無効にします。

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>パラメーター

*dwFlags*<br/>
ウィザードのボタンの機能と外観をカスタマイズするフラグのセット。 このパラメーターは、次の値の組み合わせにすることができます。

- PSWIZB_BACK 戻るボタン

- PSWIZB_NEXT [次へ] ボタン

- PSWIZB_FINISH 完了ボタン

- PSWIZB_DISABLEDFINISH Disabled [完了] ボタン

### <a name="remarks"></a>Remarks

ダイアログ`SetWizardButtons`が開いた後にのみを呼び出します。 `SetWizardButtons` [DoModal](#domodal)を呼び出す前にを呼び出すことはできません。 通常は、 `SetWizardButtons` [CPropertyPage:: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive)からを呼び出す必要があります。

ユーザーがウィザードを完了した後で [完了] ボタンのテキストを変更したり、[次へ] ボタンと [戻る] ボタンを非表示にしたりする場合は、 [Setfinish テキスト](#setfinishtext)を呼び出します。 [完了] と [次へ] と同じボタンが共有されていることに注意してください。 [完了] ボタンまたは [次へ] ボタンを一度に表示できますが、両方を表示することはできません。

### <a name="example"></a>例

には`CStylePage`、、 `CColorPage`、および`CShapePage`の3つのウィザードプロパティページがあります。`CPropertySheet`  次のコード片では、ウィザードのプロパティページで **[戻る]** ボタンと **[次へ**] ボタンを有効または無効にする方法を示しています。

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="setwizardmode"></a>CPropertySheet:: SetWizardMode

ウィザードとしてプロパティページを確立します。

```
void SetWizardMode();
```

### <a name="remarks"></a>Remarks

ウィザードのプロパティページの重要な特性は、ユーザーがタブではなく [次へ] または [完了]、[戻る]、および [キャンセル] の各ボタンを使用して移動することです。

[DoModal](#domodal) を呼び出す前に `SetWizardMode` を呼び出します。 を呼び出し`SetWizardMode`た後`DoModal` 、は ID_WIZFINISH (ユーザーが [完了] ボタンで閉じた場合) または IDCANCEL を返します。

`SetWizardMode`PSH_WIZARD フラグを設定します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>関連項目

[MFC のサンプル CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC のサンプル CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC のサンプル PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[MFC のサンプル SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
