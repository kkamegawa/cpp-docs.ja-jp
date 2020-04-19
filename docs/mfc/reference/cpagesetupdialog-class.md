---
title: CPageSetupDialog クラス
ms.date: 11/04/2016
f1_keywords:
- CPageSetupDialog
- AFXDLGS/CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CreatePrinterDC
- AFXDLGS/CPageSetupDialog::DoModal
- AFXDLGS/CPageSetupDialog::GetDeviceName
- AFXDLGS/CPageSetupDialog::GetDevMode
- AFXDLGS/CPageSetupDialog::GetDriverName
- AFXDLGS/CPageSetupDialog::GetMargins
- AFXDLGS/CPageSetupDialog::GetPaperSize
- AFXDLGS/CPageSetupDialog::GetPortName
- AFXDLGS/CPageSetupDialog::OnDrawPage
- AFXDLGS/CPageSetupDialog::PreDrawPage
- AFXDLGS/CPageSetupDialog::m_psd
helpviewer_keywords:
- CPageSetupDialog [MFC], CPageSetupDialog
- CPageSetupDialog [MFC], CreatePrinterDC
- CPageSetupDialog [MFC], DoModal
- CPageSetupDialog [MFC], GetDeviceName
- CPageSetupDialog [MFC], GetDevMode
- CPageSetupDialog [MFC], GetDriverName
- CPageSetupDialog [MFC], GetMargins
- CPageSetupDialog [MFC], GetPaperSize
- CPageSetupDialog [MFC], GetPortName
- CPageSetupDialog [MFC], OnDrawPage
- CPageSetupDialog [MFC], PreDrawPage
- CPageSetupDialog [MFC], m_psd
ms.assetid: 049c0ac8-f254-4854-9414-7a8271d1447a
ms.openlocfilehash: b81e2a65d09bf5dadbc0860d692caee7a4bd386f
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739758"
---
# <a name="cpagesetupdialog-class"></a>CPageSetupDialog クラス

印刷マージンの設定や変更の追加サポートと共に [OLE ページの設定] ダイアログ ボックスにより提供されるサービスをカプセル化します。

## <a name="syntax"></a>構文

```
class CPageSetupDialog : public CCommonDialog
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|`CPageSetupDialog` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|印刷用のデバイスコンテキストを作成します。|
|[CPageSetupDialog::DoModal](#domodal)|ダイアログボックスを表示し、ユーザーが選択できるようにします。|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|プリンターのデバイス名を返します。|
|[CPageSetupDialog::GetDevMode](#getdevmode)|プリンターの現在の DEVMODE を返します。|
|[CPageSetupDialog::GetDriverName](#getdrivername)|プリンターで使用されているドライバーを返します。|
|[CPageSetupDialog::GetMargins](#getmargins)|プリンターの現在の余白設定を返します。|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|プリンターの用紙サイズを返します。|
|[CPageSetupDialog::GetPortName](#getportname)|出力ポート名を返します。|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|印刷されたページの画面イメージをレンダリングするために、フレームワークによって呼び出されます。|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|印刷されたページの画面イメージを描画する前に、フレームワークによって呼び出されます。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|オブジェクトを`CPageSetupDialog`カスタマイズするために使用される構造体。|

## <a name="remarks"></a>Remarks

このクラスは、[印刷設定] ダイアログボックスの代わりに使用するように設計されています。

`CPageSetupDialog`オブジェクトを使用するには、最初に`CPageSetupDialog`コンストラクターを使用してオブジェクトを作成します。 ダイアログボックスを構築したら、 `m_psd`データメンバーの任意の値を設定または変更して、ダイアログボックスのコントロールの値を初期化できます。 [M_psd](#m_psd)構造体の型は PAGESETUPDLG です。

ダイアログボックスコントロールを初期化した後、 `DoModal`メンバー関数を呼び出してダイアログボックスを表示し、ユーザーが印刷オプションを選択できるようにします。 `DoModal` ユーザーが [ok] \(IDOK) またはキャンセル (IDCANCEL) ボタンを選択するかどうかを返します。

が`DoModal` IDOK を返す場合は、のいくつ`CPageSetupDialog`かのメンバー `m_psd`関数を使用するか、データメンバーにアクセスして、ユーザーが入力した情報を取得することができます。

> [!NOTE]
>  [OLE ページの共通設定] ダイアログボックスを閉じた後は、ユーザーによって行われた変更はフレームワークによって保存されません。 このダイアログボックスの任意の値を、アプリケーションのドキュメントまたはアプリケーションクラスのメンバーなどの永続的な場所に保存するのは、アプリケーション自体で行う必要があります。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdlgs

##  <a name="cpagesetupdialog"></a>CPageSetupDialog::CPageSetupDialog

オブジェクトを構築するには`CPageSetupDialog` 、この関数を呼び出します。

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*dwFlags*<br/>
ダイアログボックスの設定をカスタマイズするために使用できる1つ以上のフラグ。 値は、ビットごとの OR 演算子を使用して組み合わせることができます。 これらの値の意味は次のとおりです。

- PSD_DEFAULTMINMARGINS は、ページ余白に許容される最小の幅を、プリンターの最小値と同じに設定します。 PSD_MARGINS フラグと PSD_MINMARGINS フラグも指定されている場合、このフラグは無視されます。

- PSD_INWININIINTLMEASURE が実装されていません。

- PSD_MINMARGINS を使用すると、 `rtMinMargin`メンバーに指定された値が、左、上、右、および下の余白に対して許容される最小の幅として、システムによって使用されます。 システムにより、ユーザーは指定された最小値よりも小さい幅を入力できなくなります。 PSD_MINMARGINS が指定されていない場合は、プリンターで許可されている幅の最小値が設定されます。

- PSD_MARGINS は、余白コントロール領域をアクティブにします。

- PSD_INTHOUSANDTHSOFINCHES を指定すると、ダイアログボックスの単位は1/1000 インチ単位で測定されます。

- PSD_INHUNDREDTHSOFMILLIMETERS を指定すると、ダイアログボックスの単位は1/100 ミリ秒単位で測定されます。

- PSD_DISABLEMARGINS は、余白のダイアログボックスコントロールを無効にします。

- PSD_DISABLEPRINTER は、[プリンター] ボタンを無効にします。

- PSD_NOWARNING は、既定のプリンターが存在しないときに警告メッセージが表示されないようにします。

- PSD_DISABLEORIENTATION ページの向きのダイアログコントロールを無効にします。

- PSD_RETURNDEFAULT は、`CPageSetupDialog` がダイアログボックスを表示せず に、システムの既定のプリンター用に初期化された [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) および [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) 構造体を返すようにします。 との両方`hDevNames`が NULL で`hDevMode`あることを前提としています。それ以外の場合、関数はエラーを返します。 システムの既定のプリンターが古いプリンタードライバー (Windows バージョン3.0 より前) でサポートされて`hDevNames`いる場合は、のみが返されます。`hDevMode`が NULL です。

- PSD_DISABLEPAPER は、用紙選択コントロールを無効にします。

- PSD_SHOWHELP を使用すると、ダイアログボックスに [ヘルプ] ボタンが表示されます。 この`hwndOwner`フラグが指定されている場合、メンバーを NULL にすることはできません。

- PSD_ENABLEPAGESETUPHOOK では、で`lpfnSetupHook`指定されたフック関数を有効にします。

- PSD_ENABLEPAGESETUPTEMPLATE を使用すると、および`hInstance` `lpSetupTemplateName`で識別されるダイアログテンプレートボックスを使用して、オペレーティングシステムによってダイアログボックスが作成されます。

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE は、 `hInstance`がプリロードされたダイアログボックステンプレートを含むデータブロックを識別することを示します。 このフラグが`lpSetupTemplateName`指定されている場合、システムは無視します。

- PSD_ENABLEPAGEPAINTHOOK では、で`lpfnPagePaintHook`指定されたフック関数を有効にします。

- PSD_DISABLEPAGEPAINTING を選択すると、ダイアログボックスの描画領域が無効になります。

*pParentWnd*<br/>
ダイアログボックスの親または所有者へのポインター。

### <a name="remarks"></a>Remarks

ダイアログボックスを表示するには、 [DoModal](../../mfc/reference/cdialog-class.md#domodal)関数を使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPageSetupDialog::CreatePrinterDC

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)および[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)構造体からプリンターデバイスコンテキストを作成します。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>戻り値

新しく作成されたプリンターデバイスコンテキスト (DC) を処理します。

##  <a name="domodal"></a>  CPageSetupDialog::DoModal

この関数を呼び出すと、[Windows コモン OLE ページ設定] ダイアログボックスが表示され、印刷の余白、用紙のサイズと向き、宛先のプリンターなどのさまざまな印刷設定オプションをユーザーが選択できます。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>戻り値

IDOK または IDCANCEL。 IDCANCEL が返された場合は、Windows の[Commdlgextendederror](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)関数を呼び出して、エラーが発生したかどうかを確認します。

IDOK と IDCANCEL は、ユーザーが [OK] または [キャンセル] ボタンを選択したかどうかを示す定数です。

### <a name="remarks"></a>Remarks

さらに、ユーザーは、選択したプリンターに固有のネットワークの場所やプロパティなど、プリンターのセットアップオプションにアクセスできます。

`m_psd`構造体のメンバーを設定することによって、さまざまなページ設定ダイアログオプションを初期化する場合は、 `DoModal`を呼び出す前、およびダイアログオブジェクトが構築された後に実行する必要があります。 を呼び出し`DoModal`た後、他のメンバー関数を呼び出して、ユーザーがダイアログボックスに入力した設定または情報を取得します。

ユーザーが入力した現在の設定を伝達する場合は、 [CWinApp:: SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter)を呼び出します。 この関数は、 `CPageSetupDialog`オブジェクトからの情報を受け取り、適切な属性を使用して新しいプリンター DC を初期化して選択します。

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>例

  [CPageSetupDialog:: CPageSetupDialog](#cpagesetupdialog)の例を参照してください。

##  <a name="getdevicename"></a>  CPageSetupDialog::GetDeviceName

現在選択され`DoModal`ているプリンターの名前を取得するには、の後にこの関数を呼び出します。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>戻り値

`CPageSetupDialog`オブジェクトによって使用されるデバイス名。

##  <a name="getdevmode"></a>  CPageSetupDialog::GetDevMode

を呼び出し`DoModal`た後に、 `CPageSetupDialog`この関数を呼び出して、オブジェクトのプリンターデバイスコンテキストに関する情報を取得します。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>戻り値

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)データ構造体。これには、印刷ドライバーのデバイスの初期化と環境に関する情報が含まれます。 この構造体によって取得されるメモリは、Windows [globalunlock](/windows/win32/api/winbase/nf-winbase-globalunlock)関数を使用してロック解除する必要があります。これについては、Windows SDK を参照してください。

##  <a name="getdrivername"></a>  CPageSetupDialog::GetDriverName

システム定義のプリンターデバイスドライバーの名前を取得するには、 [DoModal](../../mfc/reference/cprintdialog-class.md#domodal)を呼び出した後にこの関数を呼び出します。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>戻り値

システム定義のドライバー名を指定する。`CString`

### <a name="remarks"></a>Remarks

[CDC:: createdc](../../mfc/reference/cdc-class.md#createdc)への呼び出し`GetDriverName`で、によっ`lpszDriverName`て返される`CString`オブジェクトへのポインターを、の値として使用します。

##  <a name="getmargins"></a>  CPageSetupDialog::GetMargins

を呼び出した後に、プリンター `DoModal`デバイスドライバーの余白を取得するために、この関数を呼び出します。

```
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>パラメーター

*lpRectMargins*<br/>
現在選択されているプリンターの印刷余白を (1/1000 インチまたは 1/100 mm で) 記述する[RECT](/windows/win32/api/windef/ns-windef-rect)構造体または[CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトへのポインター。 この四角形に関心がない場合は、このパラメーターに NULL を渡します。

*lpRectMinMargins*<br/>
現在選択さ`RECT`れて`CRect`いるプリンターの最小印刷余白を (1/1000 インチまたは 1/100 mm で) 記述する構造体またはオブジェクトへのポインター。 この四角形に関心がない場合は、このパラメーターに NULL を渡します。

##  <a name="getpapersize"></a>  CPageSetupDialog::GetPaperSize

印刷用に選択した用紙のサイズを取得します。

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>戻り値

印刷用に選択された用紙のサイズ (1/1000 インチまたは 1/100 mm) を含む[CSize](../../atl-mfc-shared/reference/csize-class.md)オブジェクト。

##  <a name="getportname"></a>  CPageSetupDialog::GetPortName

を呼び出し`DoModal`た後に、現在選択されているプリンターポートの名前を取得するために、この関数を呼び出します。

```
CString GetPortName() const;
```

### <a name="return-value"></a>戻り値

現在選択されているプリンターポートの名前。

##  <a name="m_psd"></a>  CPageSetupDialog::m_psd

PAGESETUPDLG 型の構造体。このメンバーには、ダイアログオブジェクトの特性が格納されています。

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>Remarks

構築した後、`CPageSetupDialog`オブジェクトを使用する`m_psd`を呼び出す前に ダイアログ ボックスのさまざまな側面を設定する、`DoModal`メンバー関数。

`m_psd`データメンバーを直接変更すると、すべての既定の動作がオーバーライドされます。

[Pagesetupdlg](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw)構造体の詳細については、Windows SDK を参照してください。

[CPageSetupDialog:: CPageSetupDialog](#cpagesetupdialog)の例を参照してください。

##  <a name="ondrawpage"></a>  CPageSetupDialog::OnDrawPage

印刷されたページの画面イメージを描画するために、フレームワークによって呼び出されます。

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
プリンターデバイスコンテキストへのポインター。

*N メッセージ*<br/>
現在描画されているページの領域を示すメッセージを指定します。 次のいずれかの値を指定します。

- ページ領域全体を WM_PSD_FULLPAGERECT します。

- WM_PSD_MINMARGINRECT の現在の最小余白。

- 現在の余白を WM_PSD_MARGINRECT します。

- ページの内容を WM_PSD_GREEKTEXTRECT します。

- WM_PSD_ENVSTAMPRECT は、切手のスタンプ表現用に予約されています。

- リターンアドレス表現の WM_PSD_YAFULLPAGERECT 領域。 この領域は、サンプルページ領域の端まで拡張されます。

*lpRect*<br/>
描画領域の座標を格納している、 [CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトまたは[RECT](/windows/win32/api/windef/ns-windef-rect)オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

処理された場合は0以外の値。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このイメージは、[共通の OLE ページ設定] ダイアログボックスの一部として表示されます。 既定の実装は、テキストページのイメージを描画します。

イメージの特定の領域またはイメージ全体の描画をカスタマイズするには、この関数をオーバーライドします。 これを行うには、 **switch**ステートメントと**case**ステートメントを使用して*n メッセージ*の値をチェックします。 たとえば、ページイメージの内容の表示をカスタマイズするには、次のコード例を使用します。

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

*N メッセージ*のすべてのケースを処理する必要がないことに注意してください。 イメージの1つのコンポーネント、イメージの複数の要素、または領域全体を処理するように選択できます。

##  <a name="predrawpage"></a>  CPageSetupDialog::PreDrawPage

印刷されたページの画面イメージを描画する前に、フレームワークによって呼び出されます。

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>パラメーター

*wPaper*<br/>
用紙サイズを示す値を指定します。 この値には、 [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)構造体の説明に示されている**DMPAPER_** 値のいずれかを指定できます。

*wFlags*<br/>
用紙または封筒の向き、およびプリンターがドットマトリックスまたは HPPCL (ヒューレットパッカード Printer Control Language) デバイスであるかどうかを示します。 このパラメーターには、次のいずれかの値を指定できます。

- 0x001 用紙 (横モード) (ドットマトリックス)

- 0x003 用紙横モード (HPPCL)

- 0x005 用紙縦モード (ドットマトリックス)

- 縦モードの0x007 用紙 (HPPCL)

- 横モードの0x00b 封筒 (HPPCL)

- 縦モードの0x00d 封筒 (ドットマトリックス)

- 横モードの0x019 封筒 (ドットマトリックス)

- 横モードの0x01f 封筒 (ドットマトリックス)

*pPSD*<br/>
`PAGESETUPDLG` 構造体へのポインター。 [Pagesetupdlg](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw)の詳細については、Windows SDK を参照してください。

### <a name="return-value"></a>戻り値

処理された場合は0以外の値。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

イメージの描画をカスタマイズするには、この関数をオーバーライドします。 この関数をオーバーライドして TRUE を返す場合は、イメージ全体を描画する必要があります。 この関数をオーバーライドして FALSE を返すと、既定のイメージ全体がフレームワークによって描画されます。

## <a name="see-also"></a>関連項目

[MFC のサンプルワードパッド](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog クラス](../../mfc/reference/ccommondialog-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
