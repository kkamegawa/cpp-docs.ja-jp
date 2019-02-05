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
ms.openlocfilehash: abf230f8c9e68365f8d1db8b654174ad3e152862
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894407"
---
# <a name="cfindreplacedialog-class"></a>CFindReplaceDialog クラス

アプリケーションで標準的な文字列検索/置換ダイアログ ボックスを実装することができます。

## <a name="syntax"></a>構文

```
class CFindReplaceDialog : public CCommonDialog
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)|構築するには、この関数を呼び出して、`CFindReplaceDialog`オブジェクト。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CFindReplaceDialog::Create](#create)|作成し、表示、 `CFindReplaceDialog`  ダイアログ ボックス。|
|[CFindReplaceDialog::FindNext](#findnext)|ユーザーが検索文字列の次の出現箇所を検索するかどうかを判断するには、この関数を呼び出します。|
|[CFindReplaceDialog::GetFindString](#getfindstring)|現在の検索文字列を取得するには、この関数を呼び出します。|
|[CFindReplaceDialog::GetNotifier](#getnotifier)|取得するには、この関数を呼び出し、`FINDREPLACE`登録済みのメッセージ ハンドラーで構造体。|
|[CFindReplaceDialog::GetReplaceString](#getreplacestring)|現在の置換文字列を取得するには、この関数を呼び出します。|
|[CFindReplaceDialog::IsTerminating](#isterminating)|ダイアログ ボックスが終了したかどうかを判断するには、この関数を呼び出します。|
|[CFindReplaceDialog::MatchCase](#matchcase)|ユーザーが検索文字列の大文字と小文字を正確に一致するかどうかを判断するには、この関数を呼び出します。|
|[CFindReplaceDialog::MatchWholeWord](#matchwholeword)|ユーザーが単語のみと一致するかどうかを判断するには、この関数を呼び出します。|
|[CFindReplaceDialog::ReplaceAll](#replaceall)|置換される文字列のすべての出現箇所は、ユーザーがいるかどうかを判断するには、この関数を呼び出します。|
|[CFindReplaceDialog::ReplaceCurrent](#replacecurrent)|ユーザーが現在の単語を置換するかどうかを判断するには、この関数を呼び出します。|
|[CFindReplaceDialog::SearchDown](#searchdown)|下方向へ検索は、ユーザーがいるかどうかを判断するには、この関数を呼び出します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CFindReplaceDialog::m_fr](#m_fr)|構造体をカスタマイズするために使用する`CFindReplaceDialog`オブジェクト。|

## <a name="remarks"></a>Remarks

その他の Windows コモン ダイアログ ボックスとは異なり`CFindReplaceDialog`オブジェクトがモードレスでは、ユーザーが画面上にある他のウィンドウと対話できるようにします。 2 種類がありますの`CFindReplaceDialog`オブジェクト。ダイアログ ボックスおよび検索と置換 ダイアログ ボックスを検索します。 ダイアログ ボックスに、ユーザー入力の検索を検索/置換文字列は、ですが、検索や置換関数のいずれかの実行しません。 アプリケーションにこれらを追加する必要があります。

構築する、`CFindReplaceDialog`オブジェクト、(引数を持たない) を指定されたコンス トラクターを使用します。 これは、モードレス ダイアログ ボックスであるために、ヒープを使用して、オブジェクトの割り当て、**新しい**演算子、スタックではなく。

1 回、`CFindReplaceDialog`オブジェクトが構築された、呼び出す必要があります、[作成](#create)メンバー関数を作成し、ダイアログ ボックスを表示します。

使用して、 [m_fr](#m_fr)呼び出す前に ダイアログ ボックスを初期化するために`Create`します。 `m_fr`型の構造は、 [FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea)します。 この構造体の詳細については、Windows SDK を参照してください。

親ウィンドウの検索/置換要求の通知を受けるためには、Windows を使用する必要があります[を通じて](/windows/desktop/api/winuser/nf-winuser-registerwindowmessagea)関数を使用して、 [ON_REGISTERED_MESSAGE](message-map-macros-mfc.md#on_registered_message)フレームでメッセージ マップ マクロこの登録済みのメッセージを処理するウィンドウです。

ダイアログ ボックスを終了したかどうかを指定できます、`IsTerminating`メンバー関数。

`CFindReplaceDialog` COMMDLG に依存します。Windows 3.1 以降のバージョンに付属する DLL ファイルです。

ダイアログ ボックスをカスタマイズするには、派生クラスを`CFindReplaceDialog`独自のダイアログ テンプレートを提供し、拡張コントロールからの通知メッセージを処理するメッセージ マップを追加します。 基本クラスには、処理されないメッセージを渡す必要があります。

フック関数をカスタマイズする必要はありません。

使用しての詳細については`CFindReplaceDialog`を参照してください[コモン ダイアログ クラス](../../mfc/common-dialog-classes.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFindReplaceDialog`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdlgs.h

##  <a name="cfindreplacedialog"></a>  CFindReplaceDialog::CFindReplaceDialog

`CFindReplaceDialog` オブジェクトを構築します。

```
CFindReplaceDialog();
```

### <a name="remarks"></a>Remarks

`CFindReplaceDialog`オブジェクトは、モードレス ダイアログ ボックスを使用して、ヒープ上で構築する必要があります、**新しい**演算子。

破棄、中に、framework が実行しよう、**削除** ダイアログ ボックスへのポインターでします。 スタックで、ダイアログ ボックスを作成した場合、**この**ポインターが存在しないと、未定義の動作が発生する可能性があります。

構築の詳細については`CFindReplaceDialog`、オブジェクトを参照してください、 [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)の概要。 使用して、 [CFindReplaceDialog::Create](#create)メンバー関数は、ダイアログ ボックスを表示します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#170](../../mfc/codesnippet/cpp/cfindreplacedialog-class_1.cpp)]

##  <a name="create"></a>  CFindReplaceDialog::Create

作成し、[検索] または [検索と置換] ダイアログ ボックス オブジェクトの値に応じて表示`bFindDialogOnly`します。

```
virtual BOOL Create(
    BOOL bFindDialogOnly,
    LPCTSTR lpszFindWhat,
    LPCTSTR lpszReplaceWith = NULL,
    DWORD dwFlags = FR_DOWN,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*bFindDialogOnly*<br/>
このパラメーターを表示する場合は TRUE に設定する**検索** ダイアログ ボックス。 表示する場合は FALSE に設定する**検索/置換** ダイアログ ボックス。

*lpszFindWhat*<br/>
ダイアログ ボックスが表示されたら、既定の検索文字列へのポインター。 NULL の場合は、ダイアログ ボックスには既定の検索文字列が含まれていません。

*lpszReplaceWith*<br/>
ダイアログ ボックスが表示されたら、既定の置換文字列へのポインター。 NULL の場合は、ダイアログ ボックスには既定の置換文字列が含まれていません。

*dwFlags*<br/>
1 つまたは複数のフラグがダイアログ ボックスで、ビットごとの OR 演算子を使用して結合の設定のカスタマイズに使用することができます。 既定値は、示すで、検索が下方向に続行することを指定します。 参照してください、 [FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea)これらのフラグの詳細については、Windows SDK で構造体。

*pParentWnd*<br/>
ウィンドウ、ダイアログ ボックスの親またはオーナー ウィンドウへのポインター。 これは、検索/置換操作を要求することを示す特殊なメッセージを受信するウィンドウです。 NULL の場合、アプリケーションのメイン ウィンドウを使用します。

### <a name="return-value"></a>戻り値

ダイアログ ボックスのオブジェクトが作成された場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

親ウィンドウの検索/置換要求の通知を受けるためには、Windows を使用する必要があります[を通じて](/windows/desktop/api/winuser/nf-winuser-registerwindowmessagea)関数の戻り値は、アプリケーションのインスタンスに固有のメッセージ番号。 フレーム ウィンドウは、コールバック関数を宣言するメッセージ マップ エントリが必要 (`OnFindReplace`次の例で) この登録済みのメッセージを処理します。 次のコード フラグメントは、という名前のフレーム ウィンドウ クラスをこれを行う方法の例を示します`CMyRichEditView`:

[!code-cpp[NVC_MFCDocView#171](../../mfc/codesnippet/cpp/cfindreplacedialog-class_2.h)]

[!code-cpp[NVC_MFCDocView#172](../../mfc/codesnippet/cpp/cfindreplacedialog-class_3.cpp)]

[!code-cpp[NVC_MFCDocView#173](../../mfc/codesnippet/cpp/cfindreplacedialog-class_4.cpp)]

内で、`OnFindReplace`関数を使用して、ユーザーの意図を解釈する、 [CFindReplaceDialog::FindNext](#findnext)と[CFindReplaceDialog::IsTerminating](#isterminating)メソッドとするコードを作成します。検索/置換操作。

### <a name="example"></a>例

  例をご覧ください[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)します。

##  <a name="findnext"></a>  CFindReplaceDialog::FindNext

この関数、ユーザーが検索文字列の次の出現箇所を検索するかどうかを決定するコールバック関数を呼び出します。

```
BOOL FindNext() const;
```

### <a name="return-value"></a>戻り値

ユーザーが検索文字列の次の出現箇所を検索する場合は 0 以外それ以外の場合 0 を返します。

##  <a name="getfindstring"></a>  CFindReplaceDialog::GetFindString

この関数を検索する既定の文字列を取得するコールバック関数を呼び出します。

```
CString GetFindString() const;
```

### <a name="return-value"></a>戻り値

既定の文字列を検索します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getnotifier"></a>  CFindReplaceDialog::GetNotifier

現在の検索置換 ダイアログ ボックスへのポインターを取得するには、この関数を呼び出します。

```
static CFindReplaceDialog* PASCAL GetNotifier(LPARAM lParam);
```

### <a name="parameters"></a>パラメーター

*lParam*<br/>
*Lparam*フレーム ウィンドウの値が渡される`OnFindReplace`メンバー関数。

### <a name="return-value"></a>戻り値

現在のダイアログ ボックスへのポインター。

### <a name="remarks"></a>Remarks

現在のダイアログ ボックスにアクセスするには、関数、およびアクセス、そのメンバーを呼び出して、コールバック関数内で使用する必要があります、`m_fr`構造体。

### <a name="example"></a>例

参照してください[CFindReplaceDialog::Create](#create)検索置換 ダイアログ ボックスから通知を受け取る次 OnFindReplace ハンドラーを登録する方法の例についてはします。

[!code-cpp[NVC_MFCDocView#69](../../mfc/codesnippet/cpp/cfindreplacedialog-class_5.cpp)]

##  <a name="getreplacestring"></a>  CFindReplaceDialog::GetReplaceString

現在の置換文字列を取得するには、この関数を呼び出します。

```
CString GetReplaceString() const;
```

### <a name="return-value"></a>戻り値

検索した文字列を置き換える既定の文字列。

### <a name="example"></a>例

  例をご覧ください[CFindReplaceDialog::GetFindString](#getfindstring)します。

##  <a name="isterminating"></a>  CFindReplaceDialog::IsTerminating

ダイアログ ボックスを終了したかどうかを決定するコールバック関数内でこの関数を呼び出します。

```
BOOL IsTerminating() const;
```

### <a name="return-value"></a>戻り値

以外の場合は、ユーザーは、ダイアログ ボックスを終了することにしましたそれ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

この関数は 0 以外の値を返す場合を呼び出す必要があります、`DestroyWindow`メンバー関数は、現在のダイアログ ボックスのボックスし、ダイアログ ボックスのポインター変数は NULL に設定します。 必要に応じて、最後に入力された検索/置換テキストを格納し、次へ の検索と置換 ダイアログ ボックスを初期化するために使用することができますも。

### <a name="example"></a>例

  例をご覧ください[CFindReplaceDialog::GetFindString](#getfindstring)します。

##  <a name="m_fr"></a>  CFindReplaceDialog::m_fr

カスタマイズするために使用する`CFindReplaceDialog`オブジェクト。

```
FINDREPLACE m_fr;
```

### <a name="remarks"></a>Remarks

`m_fr` 型の構造体は、 [FINDREPLACE](/windows/desktop/api/commdlg/ns-commdlg-tagfindreplacea)します。 そのメンバーは、ダイアログ ボックスのオブジェクトの特性を格納します。 構築した後、`CFindReplaceDialog`オブジェクトを使用することができます`m_fr` ダイアログ ボックスのさまざまな値を変更します。

この構造体の詳細については、次を参照してください。、 `FINDREPLACE` Windows SDK の構造体。

### <a name="example"></a>例

  例をご覧ください[CFindReplaceDialog::CFindReplaceDialog](#cfindreplacedialog)します。

##  <a name="matchcase"></a>  CFindReplaceDialog::MatchCase

ユーザーが検索文字列の大文字と小文字を正確に一致するかどうかを判断するには、この関数を呼び出します。

```
BOOL MatchCase() const;
```

### <a name="return-value"></a>戻り値

ユーザーが検索文字列の大文字と小文字を正確に一致する検索文字列の出現箇所を検索する場合は 0 以外それ以外の場合 0 を返します。

##  <a name="matchwholeword"></a>  CFindReplaceDialog::MatchWholeWord

ユーザーが単語のみと一致するかどうかを判断するには、この関数を呼び出します。

```
BOOL MatchWholeWord() const;
```

### <a name="return-value"></a>戻り値

ユーザーが検索文字列の単語に一致する場合は 0 以外それ以外の場合 0 を返します。

##  <a name="replaceall"></a>  CFindReplaceDialog::ReplaceAll

置換される文字列のすべての出現箇所は、ユーザーがいるかどうかを判断するには、この関数を呼び出します。

```
BOOL ReplaceAll() const;
```

### <a name="return-value"></a>戻り値

置換文字列に一致するすべての文字列が置き換えられることは、ユーザーが要求した場合、0 以外の場合それ以外の場合 0 を返します。

##  <a name="replacecurrent"></a>  CFindReplaceDialog::ReplaceCurrent

ユーザーが現在の単語を置換するかどうかを判断するには、この関数を呼び出します。

```
BOOL ReplaceCurrent() const;
```

### <a name="return-value"></a>戻り値

ユーザーが現在選択されている文字列を置換文字列で置き換えられることを要求された場合、0 以外の場合それ以外の場合 0 を返します。

##  <a name="searchdown"></a>  CFindReplaceDialog::SearchDown

下方向へ検索は、ユーザーがいるかどうかを判断するには、この関数を呼び出します。

```
BOOL SearchDown() const;
```

### <a name="return-value"></a>戻り値

ユーザーが、検索、下方向に続行する場合は 0 以外ユーザーが上向きの方向を検索する場合は 0。

## <a name="see-also"></a>関連項目

[CCommonDialog クラス](../../mfc/reference/ccommondialog-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
