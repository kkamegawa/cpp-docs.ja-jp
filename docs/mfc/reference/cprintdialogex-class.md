---
title: CPrintDialogEx クラス
ms.date: 11/04/2016
f1_keywords:
- CPrintDialogEx
- AFXDLGS/CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CreatePrinterDC
- AFXDLGS/CPrintDialogEx::DoModal
- AFXDLGS/CPrintDialogEx::GetCopies
- AFXDLGS/CPrintDialogEx::GetDefaults
- AFXDLGS/CPrintDialogEx::GetDeviceName
- AFXDLGS/CPrintDialogEx::GetDevMode
- AFXDLGS/CPrintDialogEx::GetDriverName
- AFXDLGS/CPrintDialogEx::GetPortName
- AFXDLGS/CPrintDialogEx::GetPrinterDC
- AFXDLGS/CPrintDialogEx::PrintAll
- AFXDLGS/CPrintDialogEx::PrintCollate
- AFXDLGS/CPrintDialogEx::PrintCurrentPage
- AFXDLGS/CPrintDialogEx::PrintRange
- AFXDLGS/CPrintDialogEx::PrintSelection
- AFXDLGS/CPrintDialogEx::m_pdex
helpviewer_keywords:
- CPrintDialogEx [MFC], CPrintDialogEx
- CPrintDialogEx [MFC], CreatePrinterDC
- CPrintDialogEx [MFC], DoModal
- CPrintDialogEx [MFC], GetCopies
- CPrintDialogEx [MFC], GetDefaults
- CPrintDialogEx [MFC], GetDeviceName
- CPrintDialogEx [MFC], GetDevMode
- CPrintDialogEx [MFC], GetDriverName
- CPrintDialogEx [MFC], GetPortName
- CPrintDialogEx [MFC], GetPrinterDC
- CPrintDialogEx [MFC], PrintAll
- CPrintDialogEx [MFC], PrintCollate
- CPrintDialogEx [MFC], PrintCurrentPage
- CPrintDialogEx [MFC], PrintRange
- CPrintDialogEx [MFC], PrintSelection
- CPrintDialogEx [MFC], m_pdex
ms.assetid: 1d506703-ee1c-44cc-b4ce-4e778fec26b8
ms.openlocfilehash: 76c3968b20a66e9653fd769339e23ede2a756bbd
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741329"
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx クラス

Windows の [印刷] プロパティシートによって提供されるサービスをカプセル化します。

## <a name="syntax"></a>構文

```
class CPrintDialogEx : public CCommonDialog
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CPrintDialogEx::CPrintDialogEx](#cprintdialogex)|`CPrintDialogEx` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|[印刷] ダイアログボックスを表示せずに、プリンターデバイスコンテキストを作成します。|
|[CPrintDialogEx::DoModal](#domodal)|ダイアログボックスを表示し、ユーザーが選択できるようにします。|
|[CPrintDialogEx::GetCopies](#getcopies)|要求されたコピーの数を取得します。|
|[CPrintDialogEx::GetDefaults](#getdefaults)|ダイアログボックスを表示せずに、デバイスの既定値を取得します。|
|[CPrintDialogEx::GetDeviceName](#getdevicename)|現在選択されているプリンターデバイスの名前を取得します。|
|[CPrintDialogEx::GetDevMode](#getdevmode)|`DEVMODE`構造体を取得します。|
|[CPrintDialogEx::GetDriverName](#getdrivername)|システム定義のプリンターデバイスドライバーの名前を取得します。|
|[CPrintDialogEx::GetPortName](#getportname)|現在選択されているプリンターポートの名前を取得します。|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|プリンターデバイスコンテキストへのハンドルを取得します。|
|[CPrintDialogEx::PrintAll](#printall)|ドキュメントのすべてのページを印刷するかどうかを決定します。|
|[CPrintDialogEx::PrintCollate](#printcollate)|照合されたコピーが要求されるかどうかを決定します。|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|ドキュメントの現在のページを印刷するかどうかを決定します。|
|[CPrintDialogEx::PrintRange](#printrange)|指定した範囲のページだけを印刷するかどうかを決定します。|
|[CPrintDialogEx::PrintSelection](#printselection)|現在選択されている項目だけを印刷するかどうかを決定します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CPrintDialogEx::m_pdex](#m_pdex)|オブジェクトを`CPrintDialogEx`カスタマイズするために使用される構造体。|

## <a name="remarks"></a>Remarks

フレームワークに依存して、アプリケーションの印刷プロセスの多くの要素を処理できます。 フレームワークを使用して印刷タスクを処理する方法の詳細については、「[印刷](../../mfc/printing.md)」を参照してください。

アプリケーションで、フレームワークの関与なしに印刷を処理する場合は、提供され`CPrintDialogEx`たコンストラクターを使用して "そのまま" クラスを使用するか、から`CPrintDialogEx`独自のダイアログクラスを派生させ、必要に応じてコンストラクターを記述することができます。 どちらの場合も、これらのダイアログボックスはクラス`CCommonDialog`から派生しているので、標準の MFC ダイアログボックスのように動作します。

`CPrintDialogEx`オブジェクトを使用するには、最初に`CPrintDialogEx`コンストラクターを使用してオブジェクトを作成します。 ダイアログボックスが構築されたら、 [m_pdex](#m_pdex)構造体の任意の値を設定または変更して、ダイアログボックスのコントロールの値を初期化できます。 構造体の型は[printdlgex です。](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) `m_pdex` この構造の詳細については、Windows SDK を参照してください。

メンバー `m_pdex` `hDevMode`と`GlobalFree`メンバーに対して独自のハンドルを指定しない場合は、ダイアログボックスが終了したときに、これらのハンドルに対して Windows の関数を呼び出す必要があります。 `hDevNames`

ダイアログボックスコントロールを初期化した後、 `DoModal`メンバー関数を呼び出してダイアログボックスを表示し、ユーザーが印刷オプションを選択できるようにします。 から`DoModal`制御が戻ったときに、ユーザーが [OK]、[適用]、または [キャンセル] ボタンを選択したかどうかを確認できます。

ユーザーが [OK] を押した場合`CPrintDialogEx`は、のメンバー関数を使用して、ユーザーが入力した情報を取得できます。

この`CPrintDialogEx::GetDefaults`メンバー関数は、ダイアログボックスを表示せずに現在のプリンターの既定値を取得する場合に便利です。 このメソッドでは、ユーザーの操作は必要ありません。

Windows `CommDlgExtendedError`の関数を使用すると、ダイアログボックスの初期化中にエラーが発生したかどうかを判断し、エラーの詳細を確認できます。 この関数の詳細については、Windows SDK を参照してください。

の使用方法`CPrintDialogEx`の詳細については、「[コモンダイアログクラス](../../mfc/common-dialog-classes.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`IObjectWithSite`

`IPrintDialogCallback`

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialogEx`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdlgs

##  <a name="cprintdialogex"></a>CPrintDialogEx::CPrintDialogEx

Windows 印刷プロパティシートを構築します。

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*dwFlags*<br/>
ダイアログボックスの設定をカスタマイズするために使用できる1つ以上のフラグ。ビットごとの OR 演算子を使用して結合します。 たとえば、PD_ALLPAGES フラグは、既定の印刷範囲をドキュメントのすべてのページに設定します。 これらのフラグの詳細については、Windows SDK の[Printdlgex](/windows/win32/api/commdlg/ns-commdlg-printdlgexw)構造体を参照してください。

*pParentWnd*<br/>
ダイアログボックスの親またはオーナーウィンドウへのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、オブジェクトを構築するだけです。 このダイアログ`DoModal`ボックスを表示するには、メンバー関数を使用します。

##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)および[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)構造体からプリンターデバイスコンテキスト (DC) を作成します。

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>戻り値

新しく作成されたプリンターデバイスコンテキストを処理します。

### <a name="remarks"></a>Remarks

返された DC は、 [m_pdex](#m_pdex)の`hDC`メンバーにも格納されます。

この DC は現在のプリンタ DC であると想定されており、以前に取得した他のすべてのプリンタ dc を削除する必要があります。 この関数は、[印刷] ダイアログボックスを表示せずに、結果として使用される DC を呼び出すことができます。

##  <a name="domodal"></a>CPrintDialogEx::D oModal

この関数を呼び出すと、Windows の印刷プロパティシートが表示され、ユーザーはさまざまな印刷オプション (コピー数、ページ範囲、およびコピーを照合するかどうかなど) を選択できます。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>戻り値

INT_PTR 戻り値は実際には HRESULT です。 Windows SDK の「 [Printdlgex](/previous-versions/windows/desktop/legacy/ms646942\(v=vs.85\)) 」の「戻り値」セクションを参照してください。

### <a name="remarks"></a>Remarks

`m_pdex`構造体のメンバーを設定することによって、さまざまな印刷ダイアログオプションを初期化する場合は、 `DoModal`を呼び出す前に、ダイアログオブジェクトが構築された後にこの操作を行う必要があります。

を呼び出し`DoModal`た後、他のメンバー関数を呼び出して、ユーザーがダイアログボックスに入力した設定または情報を取得できます。

を呼び出す`DoModal`ときに PD_RETURNDC フラグが使用されている場合は、 [m_pdex](#m_pdex)の`hDC`メンバーにプリンター DC が返されます。 この DC は、の呼び出し元によって[DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)への`CPrintDialogEx`呼び出しを使用して解放する必要があります。

##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies

を呼び出し`DoModal`た後に、要求されたコピーの数を取得するために、この関数を呼び出します。

```
int GetCopies() const;
```

### <a name="return-value"></a>戻り値

要求されたコピーの数。

##  <a name="getdefaults"></a>CPrintDialogEx::GetDefaults

ダイアログボックスを表示せずに、既定のプリンターのデバイスの既定値を取得するには、この関数を呼び出します。

```
BOOL GetDefaults();
```

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)および[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)構造体からプリンターデバイスコンテキスト (DC) を作成します。

`GetDefaults`[印刷] プロパティシートは表示されません。 代わりに、[m_pdex](#m_pdex) のメンバーの `hDevNames` と `hDevMode` メンバーを、システムの既定のプリンター用に初期化された [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) および [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) 構造体にハンドルするように設定します。 `GetDefaults`と`hDevNames` はどちらもNULLであるか、`hDevMode`失敗します。

PD_RETURNDC フラグが設定されている場合、この関数は`hDevNames` `hDevMode` (および`m_pdex.hDevMode`に`m_pdex.hDevNames`あります) を呼び出し元に返すだけではなく、で`m_pdex.hDC`もプリンター DC を返します。 `CPrintDialogEx`オブジェクトの操作が完了したら、プリンター DC を削除して、ハンドルに対して Windows [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)関数を呼び出す必要があります。

##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName

この関数は、 [DoModal](#domodal)を呼び出して現在選択されているプリンターの名前を取得した後、または[GetDefaults](#getdefaults)を呼び出して既定のプリンターの名前を取得した後に呼び出されます。

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>戻り値

現在選択されているプリンターの名前。

### <a name="remarks"></a>Remarks

[CDC:: createdc](../../mfc/reference/cdc-class.md#createdc)への呼び出し`GetDeviceName`で、によっ`lpszDeviceName`て返される`CString`オブジェクトへのポインターを、の値として使用します。

##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode

[DoModal](#domodal)または[GetDefaults](#getdefaults)を呼び出した後に、この関数を呼び出して、印刷デバイスに関する情報を取得します。

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>戻り値

[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)データ構造体。これには、印刷ドライバーのデバイスの初期化と環境に関する情報が含まれます。 この構造体によって取得されるメモリは、Windows [globalunlock](/windows/win32/api/winbase/nf-winbase-globalunlock)関数を使用してロック解除する必要があります。これについては、Windows SDK を参照してください。

##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName

システム定義のプリンターデバイスドライバーの名前を取得するには、 [DoModal](#domodal)または[GetDefaults](#getdefaults)を呼び出した後にこの関数を呼び出します。

```
CString GetDriverName() const;
```

### <a name="return-value"></a>戻り値

システム定義のドライバー名を指定する。`CString`

### <a name="remarks"></a>Remarks

によって`GetDriverName`返され`CString`たオブジェクトへのポインターを、 [CDC:: createdc](../../mfc/reference/cdc-class.md#createdc)への呼び出しで*lpszdrivername*の値として使用します。

##  <a name="getportname"></a>  CPrintDialogEx::GetPortName

現在選択されているプリンターポートの名前を取得するために、 [DoModal](#domodal)または[GetDefaults](#getdefaults)を呼び出した後に、この関数を呼び出します。

```
CString GetPortName() const;
```

### <a name="return-value"></a>戻り値

現在選択されているプリンターポートの名前。

##  <a name="getprinterdc"></a>  CPrintDialogEx::GetPrinterDC

プリンターデバイスコンテキストへのハンドルを返します。

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>戻り値

プリンターデバイスコンテキストを処理するハンドル。

### <a name="remarks"></a>Remarks

使用が完了したら、Windows [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc)関数を呼び出して、デバイスコンテキストを削除する必要があります。

##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex

Dialog オブジェクトの特性を格納するメンバーを持つ PRINTDLGEX 構造体。

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>Remarks

`CPrintDialogEx`オブジェクトを構築した後、を`m_pdex`使用して、ダイアログボックスのさまざまな側面を設定してから、 [DoModal](#domodal)メンバー関数を呼び出すことができます。 `m_pdex`構造の詳細については、Windows SDK の「 [printdlgex](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) 」を参照してください。

`m_pdex`データメンバーを直接変更すると、すべての既定の動作がオーバーライドされます。

##  <a name="printall"></a>  CPrintDialogEx::PrintAll

を呼び出し`DoModal`た後に、ドキュメント内のすべてのページを印刷するかどうかを判断するために、この関数を呼び出します。

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>戻り値

ドキュメント内のすべてのページを印刷する場合は TRUE。それ以外の場合は FALSE。

##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate

を呼び出し`DoModal`た後に、この関数を呼び出して、プリンターがドキュメントのすべての印刷コピーを照合する必要があるかどうかを判断します。

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>戻り値

ユーザーがダイアログボックスの [部単位で印刷] チェックボックスをオンにする場合は TRUE。それ以外の場合は FALSE。

##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage

を呼び出し`DoModal`た後に、ドキュメント内の現在のページを印刷するかどうかを判断するために、この関数を呼び出します。

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>戻り値

[印刷] ダイアログボックスで [**現在のページを印刷**する] が選択されている場合は TRUE です。それ以外の場合は FALSE。

##  <a name="printrange"></a>  CPrintDialogEx::PrintRange

を呼び出し`DoModal`た後に、この関数を呼び出して、文書内のページの範囲だけを印刷するかどうかを決定します。

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>戻り値

ドキュメント内のページの範囲だけを印刷する場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

指定されたページ範囲は[m_pdex](#m_pdex)から判別でき`nPageRanges`ます`nMaxPageRanges`(Windows SDK `lpPageRanges`の[printdlgex](/windows/win32/api/commdlg/ns-commdlg-printdlgexw)構造体で、、およびを参照してください)。

##  <a name="printselection"></a>CPrintDialogEx::P rintSelection

を呼び出し`DoModal`た後に、現在選択されている項目だけを印刷するかどうかを判断するために、この関数を呼び出します。

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>戻り値

選択した項目のみを印刷する場合は TRUE。それ以外の場合は FALSE。

## <a name="see-also"></a>関連項目

[CCommonDialog クラス](../../mfc/reference/ccommondialog-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo 構造体](../../mfc/reference/cprintinfo-structure.md)
