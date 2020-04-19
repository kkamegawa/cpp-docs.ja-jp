---
title: CFindReplaceDialog クラス
ms.date: 11/04/2016
f1_keywords:
- CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::CFindReplaceDialog
- AFXDLGS/CFindReplaceDialog::Create
- AFXDLGS/CFindReplaceDialog::FindNext
- AFXDLGS/CFindReplaceDialog::GetFindString
- AFXDLGS/CFindReplaceDialog::GetNotifier
- AFXDLGS/CFindReplaceDialog::GetReplaceString
- AFXDLGS/CFindReplaceDialog::IsTerminating
- AFXDLGS/CFindReplaceDialog::MatchCase
- AFXDLGS/CFindReplaceDialog::MatchWholeWord
- AFXDLGS/CFindReplaceDialog::ReplaceAll
- AFXDLGS/CFindReplaceDialog::ReplaceCurrent
- AFXDLGS/CFindReplaceDialog::SearchDown
- AFXDLGS/CFindReplaceDialog::m_fr
helpviewer_keywords:
- CFindReplaceDialog [MFC], CFindReplaceDialog
- CFindReplaceDialog [MFC], Create
- CFindReplaceDialog [MFC], FindNext
- CFindReplaceDialog [MFC], GetFindString
- CFindReplaceDialog [MFC], GetNotifier
- CFindReplaceDialog [MFC], GetReplaceString
- CFindReplaceDialog [MFC], IsTerminating
- CFindReplaceDialog [MFC], MatchCase
- CFindReplaceDialog [MFC], MatchWholeWord
- CFindReplaceDialog [MFC], ReplaceAll
- CFindReplaceDialog [MFC], ReplaceCurrent
- CFindReplaceDialog [MFC], SearchDown
- CFindReplaceDialog [MFC], m_fr
ms.assetid: 610f0b5d-b398-4ef6-8c05-e9d6641e50a8
ms.openlocfilehash: 71234adec214bcbf5d42090edb582a7e5dd552b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506527"
---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog クラス

アプリケーションで、標準的な文字列の [検索と置換] ダイアログボックスを実装できます。

## <a name="syntax"></a>構文

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|オブジェクトを構築するには`CFindReplaceDialog` 、この関数を呼び出します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CFindReplaceDialog::Create](#create)|ダイアログボックスを`CFindReplaceDialog`作成して表示します。|
|[CFindReplaceDialog::FindNext](#findnext)|この関数を呼び出して、ユーザーが次に見つかった検索文字列を検索するかどうかを判断します。|
|[CFindReplaceDialog::GetFindString](#getfindstring)|現在の検索文字列を取得するには、この関数を呼び出します。|
|[CFindReplaceDialog::GetNotifier](#getnotifier)|登録されているメッセージ`FINDREPLACE`ハンドラーの構造体を取得するには、この関数を呼び出します。|
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|現在の置換文字列を取得するには、この関数を呼び出します。|
|[CFindReplaceDialog::IsTerminating](#isterminating)|ダイアログボックスが終了しているかどうかを判断するには、この関数を呼び出します。|
|[CFindReplaceDialog::MatchCase](#matchcase)|ユーザーが検索文字列の大文字と小文字を正確に一致させるかどうかを判断するには、この関数を呼び出します。|
|[CFindReplaceDialog:: MatchWholeWord](#matchwholeword)|ユーザーが単語全体を照合するかどうかを判断するには、この関数を呼び出します。|
|[CFindReplaceDialog::ReplaceAll](#replaceall)|この関数を呼び出して、ユーザーがすべての文字列を置換する必要があるかどうかを判断します。|
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|ユーザーが現在の単語を置き換える必要があるかどうかを判断するには、この関数を呼び出します。|
|[CFindReplaceDialog:: SearchDown](#searchdown)|ユーザーが検索を下方向に進めることを希望するかどうかを判断するには、この関数を呼び出します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CFindReplaceDialog:: m_fr](#m_fr)|オブジェクトを`CFindReplaceDialog`カスタマイズするために使用される構造体。|

## <a name="remarks"></a>Remarks

他のウィンドウのコモンダイアログボックスと`CFindReplaceDialog`は異なり、オブジェクトはモードレスであり、ユーザーは画面上に他のウィンドウと対話できます。 オブジェクトには、次`CFindReplaceDialog`の2種類があります。ダイアログボックスを検索し、ダイアログボックスを検索/置換します。 ダイアログボックスでは、検索の入力や文字列の検索/置換を行うことができますが、検索または置換関数は実行されません。 これらは、アプリケーションに追加する必要があります。

`CFindReplaceDialog`オブジェクトを構築するには、指定されたコンストラクター (引数を持たない) を使用します。 これはモードレスダイアログボックスであるため、スタックではなく、 **new**演算子を使用してヒープにオブジェクトを割り当てます。

オブジェクトが構築されたら、[Create](#create) member 関数を呼び出してダイアログボックスを作成し、表示する必要があります。`CFindReplaceDialog`

を呼び出す `Create`前に、[m_fr](#m_fr) 構造体を使用してダイアログボックスを初期化します。 構造`m_fr`体の型は、 [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)です。 この構造の詳細については、Windows SDK を参照してください。

親ウィンドウに検索/置換要求が通知されるようにするには、Windows [Registerwindowmessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)関数を使用し、この登録されたメッセージを処理するフレームウィンドウで[ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message)マクロを使用する必要があります。

ユーザーが`IsTerminating`メンバー関数を使用してダイアログボックスを終了するかどうかを決定できます。

`CFindReplaceDialog`は、COMMDLG に依存します。Windows バージョン3.1 以降に付属している DLL ファイル。

ダイアログボックスをカスタマイズするには、から`CFindReplaceDialog`クラスを派生させ、カスタムダイアログテンプレートを指定して、拡張コントロールからの通知メッセージを処理するメッセージマップを追加します。 未処理のメッセージは、基本クラスに渡す必要があります。

フック関数のカスタマイズは必要ありません。

の使用方法`CFindReplaceDialog`の詳細については、「[コモンダイアログクラス](../../mfc/common-dialog-classes.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdlgs

##  <a name="cfindreplacedialog"></a>  CFindReplaceDialog::CFindReplaceDialog

`CFindReplaceDialog` オブジェクトを構築します。

```
CFindReplaceDialog();
```

### <a name="remarks"></a>Remarks

オブジェクトはモードレスダイアログボックスであるため、new 演算子を使用してヒープ上に作成する必要があります。 `CFindReplaceDialog`

破棄中、フレームワークはダイアログボックスへのポインターに対して**delete this**を実行しようとします。 スタックにダイアログボックスを作成した場合、**this**ポインターは存在せず、未定義の動作が発生する可能性があります。

オブジェクトの`CFindReplaceDialog`構築の詳細については、「 [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)の概要」を参照してください。 ダイアログボックスを表示するには、 [CFindReplaceDialog:: Create](#create) member 関数を使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

##  <a name="create"></a>  CFindReplaceDialog::Create

の値に応じて、[検索] または [検索と置換] のいずれか`bFindDialogOnly`のダイアログボックスオブジェクトを作成して表示します。

```
virtual BOOL Create(
    BOOL bFindDialogOnly,
    LPCTSTR lpszFindWhat,
    LPCTSTR lpszReplaceWith = NULL,
    DWORD dwFlags = FR_DOWN,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*Bfindの場合のみ*<br/>
**[検索]** ダイアログボックスを表示するには、このパラメーターを TRUE に設定します。 **[検索と置換]** ダイアログボックスを表示するには、FALSE に設定します。

*lpszFindWhat*<br/>
ダイアログボックスが表示されるときの既定の検索文字列へのポインター。 NULL の場合、ダイアログボックスには既定の検索文字列が含まれません。

*lpszReplaceWith*<br/>
ダイアログボックスが表示されたときの既定の置換文字列へのポインター。 NULL の場合、ダイアログボックスには既定の置換文字列が含まれていません。

*dwFlags*<br/>
ダイアログボックスの設定をカスタマイズするために使用できる1つ以上のフラグ。ビットごとの OR 演算子を使用して結合します。 既定値は FR_DOWN で、検索が下方向に進むことを指定します。 これらのフラグの詳細については、Windows SDK の[FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)構造体を参照してください。

*pParentWnd*<br/>
ダイアログボックスの親またはオーナーウィンドウへのポインター。 これは、検索と置換の操作が要求されたことを示す特別なメッセージを受信するウィンドウです。 NULL の場合、アプリケーションのメインウィンドウが使用されます。

### <a name="return-value"></a>戻り値

ダイアログボックスオブジェクトが正常に作成された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

親ウィンドウに検索/置換要求が通知されるようにするには、Windows [Registerwindowmessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)関数を使用する必要があります。この関数の戻り値は、アプリケーションのインスタンスに固有のメッセージ番号になります。 フレームウィンドウには、この登録されたメッセージを処理するコール`OnFindReplace`バック関数 (次の例では) を宣言するメッセージマップエントリが必要です。 次のコードフラグメントは、という名前`CMyRichEditView`のフレームウィンドウクラスに対してこれを実行する方法の例です。

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

関数内では、 [CFindReplaceDialog:: FindNext](#findnext)メソッドと[CFindReplaceDialog:: IsTerminating](#isterminating)メソッドを使用してユーザーの意図を解釈し、検索/置換操作のためのコードを作成します。 `OnFindReplace`

### <a name="example"></a>例

  [CFindReplaceDialog:: CFindReplaceDialog](#cfindreplacedialog)の例を参照してください。

##  <a name="findnext"></a>  CFindReplaceDialog::FindNext

コールバック関数からこの関数を呼び出して、ユーザーが次に出現する検索文字列の検索を希望するかどうかを判断します。

```
BOOL FindNext() const;
```

### <a name="return-value"></a>戻り値

ユーザーが検索文字列の次の出現箇所を検索する場合は0以外の値。それ以外の場合は0です。

##  <a name="getfindstring"></a>  CFindReplaceDialog::GetFindString

コールバック関数からこの関数を呼び出して、検索する既定の文字列を取得します。

```
CString GetFindString() const;
```

### <a name="return-value"></a>戻り値

検索する既定の文字列。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getnotifier"></a>  CFindReplaceDialog::GetNotifier

現在の [検索置換] ダイアログボックスへのポインターを取得するには、この関数を呼び出します。

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>パラメーター

*lParam*<br/>
フレームウィンドウの`OnFindReplace`メンバー関数に渡される lparam 値。

### <a name="return-value"></a>戻り値

現在のダイアログボックスへのポインター。

### <a name="remarks"></a>Remarks

現在のダイアログボックスにアクセスし、そのメンバー関数を呼び出して、 `m_fr`構造体にアクセスするには、コールバック関数内で使用する必要があります。

### <a name="example"></a>例

[検索する文字列] ダイアログボックスから通知を受信するために OnFindReplace ハンドラーを登録する方法の例については、「 [CFindReplaceDialog:: Create](#create) 」を参照してください。

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getreplacestring"></a>  CFindReplaceDialog::GetReplaceString

現在の置換文字列を取得するには、この関数を呼び出します。

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>戻り値

検出された文字列を置き換える既定の文字列。

### <a name="example"></a>例

  [CFindReplaceDialog:: GetFindString](#getfindstring)の例を参照してください。

##  <a name="isterminating"></a>  CFindReplaceDialog::IsTerminating

ユーザーがダイアログボックスを終了するかどうかを判断するには、コールバック関数内でこの関数を呼び出します。

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>戻り値

ユーザーがダイアログボックスを終了することを決定した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

この関数が0以外の値を返す場合`DestroyWindow`は、現在のダイアログボックスのメンバー関数を呼び出し、ダイアログボックスのポインター変数を NULL に設定する必要があります。 必要に応じて、最後に入力した検索テキストと置換テキストを格納し、それを使用して次の [検索と置換] ダイアログボックスを初期化することもできます。

### <a name="example"></a>例

  [CFindReplaceDialog:: GetFindString](#getfindstring)の例を参照してください。

##  <a name="m_fr"></a>CFindReplaceDialog:: m_fr

オブジェクトを`CFindReplaceDialog`カスタマイズするために使用します。

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>Remarks

`m_fr`は、 [FINDREPLACE](/windows/win32/api/commdlg/ns-commdlg-findreplacew)型の構造体です。 そのメンバーは、ダイアログボックスオブジェクトの特性を格納します。 `CFindReplaceDialog`オブジェクトを構築した後、を`m_fr`使用してダイアログボックスのさまざまな値を変更できます。

この構造体の詳細については`FINDREPLACE` 、Windows SDK の構造体を参照してください。

### <a name="example"></a>例

  [CFindReplaceDialog:: CFindReplaceDialog](#cfindreplacedialog)の例を参照してください。

##  <a name="matchcase"></a>  CFindReplaceDialog::MatchCase

ユーザーが検索文字列の大文字と小文字を正確に一致させるかどうかを判断するには、この関数を呼び出します。

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>戻り値

検索文字列の大文字と小文字を正確に一致する検索文字列の出現箇所を検索する場合は0以外の値。それ以外の場合は0です。

##  <a name="matchwholeword"></a>  CFindReplaceDialog::MatchWholeWord

ユーザーが単語全体を照合するかどうかを判断するには、この関数を呼び出します。

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>戻り値

検索文字列の単語全体だけを照合する場合は0以外の値。それ以外の場合は0です。

##  <a name="replaceall"></a>  CFindReplaceDialog::ReplaceAll

この関数を呼び出して、ユーザーがすべての文字列を置換する必要があるかどうかを判断します。

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>戻り値

置換文字列に一致するすべての文字列を置換するようユーザーが要求した場合は0以外の値。それ以外の場合は0です。

##  <a name="replacecurrent"></a>  CFindReplaceDialog::ReplaceCurrent

ユーザーが現在の単語を置き換える必要があるかどうかを判断するには、この関数を呼び出します。

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>戻り値

現在選択されている文字列を置換文字列に置換するようユーザーが要求した場合は0以外の値。それ以外の場合は0です。

##  <a name="searchdown"></a>  CFindReplaceDialog::SearchDown

ユーザーが検索を下方向に進めることを希望するかどうかを判断するには、この関数を呼び出します。

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>戻り値

ユーザーが検索を下方向に進める場合は0以外。ユーザーが検索を上方向に進める場合は0。

## <a name="see-also"></a>関連項目

[CCommonDialog クラス](../../mfc/reference/ccommondialog-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
