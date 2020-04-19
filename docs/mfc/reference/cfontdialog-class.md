---
title: CFontDialog クラス
ms.date: 11/04/2016
f1_keywords:
- CFontDialog
- AFXDLGS/CFontDialog
- AFXDLGS/CFontDialog::CFontDialog
- AFXDLGS/CFontDialog::DoModal
- AFXDLGS/CFontDialog::GetCharFormat
- AFXDLGS/CFontDialog::GetColor
- AFXDLGS/CFontDialog::GetCurrentFont
- AFXDLGS/CFontDialog::GetFaceName
- AFXDLGS/CFontDialog::GetSize
- AFXDLGS/CFontDialog::GetStyleName
- AFXDLGS/CFontDialog::GetWeight
- AFXDLGS/CFontDialog::IsBold
- AFXDLGS/CFontDialog::IsItalic
- AFXDLGS/CFontDialog::IsStrikeOut
- AFXDLGS/CFontDialog::IsUnderline
- AFXDLGS/CFontDialog::m_cf
helpviewer_keywords:
- CFontDialog [MFC], CFontDialog
- CFontDialog [MFC], DoModal
- CFontDialog [MFC], GetCharFormat
- CFontDialog [MFC], GetColor
- CFontDialog [MFC], GetCurrentFont
- CFontDialog [MFC], GetFaceName
- CFontDialog [MFC], GetSize
- CFontDialog [MFC], GetStyleName
- CFontDialog [MFC], GetWeight
- CFontDialog [MFC], IsBold
- CFontDialog [MFC], IsItalic
- CFontDialog [MFC], IsStrikeOut
- CFontDialog [MFC], IsUnderline
- CFontDialog [MFC], m_cf
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
ms.openlocfilehash: c0d0c37d055d9b337f7b709b4ee3d299daae7658
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741551"
---
# <a name="cfontdialog-class"></a>CFontDialog クラス

フォント選択ダイアログボックスをアプリケーションに組み込むことができます。

## <a name="syntax"></a>構文

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|`CFontDialog` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CFontDialog::D oModal](#domodal)|ダイアログを表示し、ユーザーが選択できるようにします。|
|[CFontDialog::GetCharFormat](#getcharformat)|選択したフォントの文字書式を取得します。|
|[CFontDialog::GetColor](#getcolor)|選択したフォントの色を返します。|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|現在選択されているフォントの特性を`LOGFONT`構造体に割り当てます。|
|[CFontDialog::GetFaceName](#getfacename)|選択したフォントの書体名を返します。|
|[CFontDialog::GetSize](#getsize)|選択されたフォントのポイントサイズを返します。|
|[CFontDialog::GetStyleName](#getstylename)|選択されたフォントのスタイル名を返します。|
|[CFontDialog::GetWeight](#getweight)|選択したフォントの太さを返します。|
|[CFontDialog::IsBold](#isbold)|フォントが太字かどうかを判断します。|
|[CFontDialog::IsItalic](#isitalic)|フォントが斜体かどうかを判断します。|
|[CFontDialog::IsStrikeOut](#isstrikeout)|フォントが取り消し線と共に表示されるかどうかを決定します。|
|[CFontDialog:: IsUnderline](#isunderline)|フォントに下線を付けているかどうかを判断します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|オブジェクトを`CFontDialog`カスタマイズするために使用される構造体。|

## <a name="remarks"></a>Remarks

`CFontDialog`オブジェクトは、現在システムにインストールされているフォントの一覧を含むダイアログボックスです。 ユーザーは、一覧から特定のフォントを選択すると、アプリケーションにレポートが返されます。

`CFontDialog`オブジェクトを構築するには、指定されたコンストラクターを使用するか、新しいサブクラスを派生し、独自のカスタムコンストラクターを使用します。

オブジェクトが構築されたら、 `m_cf`構造体を使用して、ダイアログボックス内のコントロールの値または状態を初期化できます。 `CFontDialog` [M_cf](#m_cf)構造体の型は、型の種類を持つ[フォント](/windows/win32/api/commdlg/ns-commdlg-choosefontw)です。 この構造の詳細については、Windows SDK を参照してください。

ダイアログオブジェクトのコントロールを初期化した後、 `DoModal`メンバー関数を呼び出してダイアログボックスを表示し、ユーザーがフォントを選択できるようにします。 `DoModal` ユーザーが [ok] \(IDOK) またはキャンセル (IDCANCEL) ボタンを選択するかどうかを返します。

が`DoModal` IDOK を返す場合は、のメンバー `CFontDialog`関数のいずれかを使用して、ユーザーが入力した情報を取得できます。

Windows の[Commdlgextendederror](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)関数を使用すると、ダイアログボックスの初期化中にエラーが発生したかどうかを確認し、エラーの詳細を調べることができます。 この関数の詳細については、Windows SDK を参照してください。

`CFontDialog`は、COMMDLG に依存します。Windows バージョン3.1 以降に付属している DLL ファイル。

ダイアログボックスをカスタマイズするには、から`CFontDialog`クラスを派生させ、カスタムダイアログテンプレートを指定して、拡張コントロールからの通知メッセージを処理するためのメッセージマップを追加します。 未処理のメッセージは、基本クラスに渡す必要があります。

フック関数のカスタマイズは必要ありません。

の使用方法`CFontDialog`の詳細については、「[コモンダイアログクラス](../../mfc/common-dialog-classes.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdlgs

##  <a name="cfontdialog"></a>  CFontDialog::CFontDialog

`CFontDialog` オブジェクトを構築します。

```
CFontDialog(
    LPLOGFONT lplfInitial = NULL,
    DWORD dwFlags = CF_EFFECTS | CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);

CFontDialog(
    const CHARFORMAT& charformat,
    DWORD dwFlags = CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*plfInitial*<br/>
フォントの特性の一部を設定できる[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)データ構造体へのポインター。

*charFormat*<br/>
リッチエディットコントロールでフォントの特性を設定できるようにする[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)データ構造体へのポインター。

*dwFlags*<br/>
1 つ以上のフォント選択フラグを指定します。 ビットごとの OR 演算子を使用して、1 つ以上の事前設定値を組み合わせることができます。 `m_cf.Flag`s 構造体メンバーを変更する場合は、変更内容でビットごとの OR 演算子を使用して、既定の動作をそのままにします。 これらの各フラグの詳細については、Windows SDK での [[フォント](/windows/win32/api/commdlg/ns-commdlg-choosefontw)の構成] の説明を参照してください。

*pdcPrinter*<br/>
プリンター デバイス コンテキストへのポインター。 指定すると、このパラメーターはフォントが選択されるプリンターのプリンター デバイス コンテキストを指します。

*pParentWnd*<br/>
フォント ダイアログ ボックスの親ウィンドウまたはオーナー ウィンドウへのポインター。

### <a name="remarks"></a>Remarks

`CHOOSEFONT` 構造体のメンバーはコンストラクターによって自動的に入力されることに注意してください。 既定とは異なるフォント ダイアログが必要な場合にのみ、これらを変更する必要があります。

> [!NOTE]
>  この関数の最初のバージョンは、リッチ エディット コントロールのサポートがない場合にのみ存在します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

##  <a name="domodal"></a>  CFontDialog::DoModal

この関数を呼び出して、[Windows コモンフォント] ダイアログボックスを表示し、ユーザーがフォントを選択できるようにします。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>戻り値

IDOK または IDCANCEL。 IDCANCEL が返された場合は、Windows の[Commdlgextendederror](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror)関数を呼び出して、エラーが発生したかどうかを確認します。

IDOK と IDCANCEL は、ユーザーが [OK] または [キャンセル] ボタンを選択したかどうかを示す定数です。

### <a name="remarks"></a>Remarks

[M_cf](#m_cf)構造体のメンバーを設定してさまざまなフォントダイアログコントロールを初期化する場合は、を呼び出す`DoModal`前に、ダイアログオブジェクトが構築された後に、この操作を行う必要があります。

が`DoModal` IDOK を返す場合は、他のメンバー関数を呼び出して、ユーザーがダイアログボックスに入力した設定または情報を取得できます。

### <a name="example"></a>例

  [CFontDialog:: CFontDialog](#cfontdialog)と[CFontDialog:: getcolor](#getcolor)の例を参照してください。

##  <a name="getcharformat"></a>  CFontDialog::GetCharFormat

選択したフォントの文字書式を取得します。

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>パラメーター

*cf*<br/>
選択されたフォントの文字書式に関する情報を格納している[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)構造体。

##  <a name="getcolor"></a>  CFontDialog::GetColor

選択したフォントの色を取得します。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>戻り値

選択したフォントの色。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

##  <a name="getcurrentfont"></a>  CFontDialog::GetCurrentFont

現在選択されているフォントの特性を[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)構造体のメンバーに割り当てるには、この関数を呼び出します。

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>パラメーター

*lplf*<br/>
`LOGFONT`構造体へのポインター。

### <a name="remarks"></a>Remarks

現在`CFontDialog`のフォントの個々の特性にアクセスするために、他のメンバー関数が用意されています。

この関数が[DoModal](#domodal)の呼び出し中に呼び出された場合は、現在の選択範囲がダイアログでユーザーに表示されるか、または変更されたかが返されます。 の呼び出し後に`DoModal`この関数が呼び出された場合 (が IDOK を返した場合`DoModal`のみ)、ユーザーが実際に選択した内容が返されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

##  <a name="getfacename"></a>  CFontDialog::GetFaceName

選択したフォントのフェイス名を取得します。

```
CString GetFaceName() const;
```

### <a name="return-value"></a>戻り値

`CFontDialog`ダイアログボックスで選択されたフォントの書体名。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

##  <a name="getsize"></a>  CFontDialog::GetSize

選択したフォントのサイズを取得します。

```
int GetSize() const;
```

### <a name="return-value"></a>戻り値

フォントのサイズ (1/10 ポイント単位)。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

##  <a name="getstylename"></a>  CFontDialog::GetStyleName

選択したフォントのスタイル名を取得します。

```
CString GetStyleName() const;
```

### <a name="return-value"></a>戻り値

フォントのスタイル名。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

##  <a name="getweight"></a>  CFontDialog::GetWeight

選択したフォントの太さを取得します。

```
int GetWeight() const;
```

### <a name="return-value"></a>戻り値

選択されたフォントの太さ。

### <a name="remarks"></a>Remarks

フォントの太さの詳細については、「 [CFont:: CreateFont](../../mfc/reference/cfont-class.md#createfont)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

##  <a name="isbold"></a>  CFontDialog::IsBold

選択したフォントが太字かどうかを判断するには、この関数を呼び出します。

```
BOOL IsBold() const;
```

### <a name="return-value"></a>戻り値

選択したフォントで太字の特性が有効になっている場合は0以外の。それ以外の場合は0です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

##  <a name="isitalic"></a>  CFontDialog::IsItalic

選択したフォントが斜体かどうかを判断するには、この関数を呼び出します。

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>戻り値

選択したフォントで斜体の特性が有効になっている場合は0以外の。それ以外の場合は0です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

##  <a name="isstrikeout"></a>  CFontDialog::IsStrikeOut

選択したフォントが取り消し線付きで表示されているかどうかを判断するには、この関数を呼び出します。

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>戻り値

選択したフォントで取り消し線の特性が有効になっている場合は0以外の。それ以外の場合は0です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

##  <a name="isunderline"></a>  CFontDialog::IsUnderline

選択したフォントに下線が引かれているかどうかを判断するには、この関数を呼び出します。

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>戻り値

選択されたフォントで下線特性が有効になっている場合は0以外の。それ以外の場合は0です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

##  <a name="m_cf"></a>CFontDialog::m_cf

ダイアログオブジェクトの特性を格納するメンバーを持つ構造体。

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>Remarks

`CFontDialog`オブジェクトを構築した後は、 `m_cf`を使用して、 `DoModal`メンバー関数を呼び出す前にダイアログボックスのさまざまな側面を変更できます。 この構造の詳細については、「Windows SDK での[フォント](/windows/win32/api/commdlg/ns-commdlg-choosefontw)の追加」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>関連項目

[MFC サンプル HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog クラス](../../mfc/reference/ccommondialog-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
