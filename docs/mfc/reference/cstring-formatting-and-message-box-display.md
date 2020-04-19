---
title: CString の書式指定とメッセージ ボックスの表示
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: ad880c5302fd2274c5d46719e912461fd7497f10
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611016"
---
# <a name="cstring-formatting-and-message-box-display"></a>CString の書式指定とメッセージ ボックスの表示

書式設定および解析する多くの機能が提供されている`CString`オブジェクト。 これらの関数を使用するには、操作する必要があるたびに`CString`いますが、オブジェクトのメッセージ ボックスのテキストに表示される文字列の書式設定に特に便利です。

このグループの関数には、メッセージ ボックスを表示するためのグローバル関数も含まれています。

### <a name="cstring-functions"></a>CString 関数

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|指定されたソース文字列から 1 つの文字で区切られた部分文字列を抽出します。|
|[AfxFormatString1](#afxformatstring1)|文字列テーブルに置換には文字列の書式指定文字"%1"の指定した文字列が含まれています。|
|[AfxFormatString2](#afxformatstring2)|形式については、2 つの代替文字列は、「1」と"%2"、文字列の文字列テーブルに含まれる文字します。|
|[AfxMessageBox](#afxmessagebox)|メッセージ ボックスを表示します。|

### <a name="requirements"></a>必要条件

  **ヘッダー** afxwin.h

##  <a name="afxextractsubstring"></a>  AfxExtractSubString

このグローバル関数は、指定されたソース文字列から部分文字列を抽出して使用できます。

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>パラメーター

*rString*<br/>
参照を[CString](../../atl-mfc-shared/using-cstring.md)を個々 の部分文字列を受け取るオブジェクト。

*lpszFullString*<br/>
抽出する文字列の完全なテキストを表す文字列です。

*iSubString*<br/>
抽出する部分文字列の 0 から始まるインデックス*lpszFullString*します。

*chSep*<br/>
部分文字列を区切るために使用される区切り記号。

### <a name="return-value"></a>戻り値

関数は、指定されたインデックスにある部分文字列を正常に展開する場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

この関数は、既知の単一の文字は、各サブ文字列を区切るときに、ソース文字列から複数の部分文字列を抽出するために便利です。 この関数は検索の先頭から、 *lpszFullString*パラメーターたびに呼び出されます。

場合、この関数は FALSE を返すは*lpszFullString*を NULL に設定されている関数の末尾に到達または*lpszFullString*検索せず*iSubString*+1指定した区切り記号の文字が出現します。 *RString*場合パラメーターは元の値から変更されません*lpszFullString*に NULL それ以外の場合、設定された、 *rString*場合、パラメーターが空の文字列に設定されます。指定されたインデックスの部分文字列を抽出できませんでした。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>必要条件

  **ヘッダー** afxwin.h

##  <a name="afxformatstring1"></a>  AfxFormatString1

指す文字列に置換されます*lpsz1*で識別されるテンプレート文字列のリソースで文字"%1"のすべてのインスタンスに対して*nIDS*します。

```
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>パラメーター

*rString*<br/>
参照を`CString`置換が実行された後に、結果の文字列を格納するオブジェクト。

*nIDS*<br/>
置換を実行する、テンプレート文字列のリソース ID。

*lpsz1*<br/>
「1」は、テンプレート文字列に文字形式を置き換える文字列。

### <a name="remarks"></a>Remarks

新しく生成された文字列が格納されている*rString*します。 たとえば、文字列テーブル内の文字列が「ファイル %1 が見つかりません」と*lpsz1*と等しい"C:\MYFILE します。TXT"、し*rString*文字列"File C:\MYFILE には。TXT が見つかりません。"です。 この関数は、メッセージ ボックスおよびその他のウィンドウに送信される文字列を書式設定するために便利です。

書式指定文字"%1"は文字列で複数回表示される、複数の置き換えが行われます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>必要条件

  **ヘッダー** afxwin.h

##  <a name="afxformatstring2"></a>  AfxFormatString2

指す文字列に置換されます*lpsz1* "%1"、文字のすべてのインスタンスと、文字列の指す*lpsz2*テンプレート文字列リソース内の文字"%2"のインスタンス識別される*nIDS*します。

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>パラメーター

*rString*<br/>
参照、`CString`置換が実行された後、結果の文字列が含まれる。

*nIDS*<br/>
置換を実行する、テンプレート文字列の文字列テーブルの ID。

*lpsz1*<br/>
「1」は、テンプレート文字列に文字形式を置き換える文字列。

*lpsz2*<br/>
"%2"は、テンプレート文字列に文字形式を置き換える文字列。

### <a name="remarks"></a>Remarks

新しく生成された文字列が格納されている*rString*します。 たとえば、文字列テーブル内の文字列が「ファイル %1 がディレクトリ %2 で見つかりません」 *lpsz1* "MYFILE 指します。TXT"、および*lpsz2*し"C:\MYDIR"を指す*rString*文字列"File MYFILE には。TXT C:\MYDIR ディレクトリに見つかりませんでした"

形式の文字"%1"または"%2"は文字列で複数回表示される、複数の置き換えになります。 数値の順序でこれらがありません。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>必要条件

  **ヘッダー** afxwin.h

##  <a name="afxmessagebox"></a>  AfxMessageBox

画面にメッセージ ボックスを表示します。

```
int AfxMessageBox(
    LPCTSTR lpszText,
    UINT nType = MB_OK,
    UINT nIDHelp = 0);

int AFXAPI AfxMessageBox(
    UINT nIDPrompt,
    UINT nType = MB_OK,
    UINT nIDHelp = (UINT) -1);
```

### <a name="parameters"></a>パラメーター

*lpszText*<br/>
`CString` オブジェクト、またはメッセージ ボックスに表示されるメッセージを含む null で終了する文字列をポイントします。

*nType*<br/>
メッセージ ボックスのスタイル。 任意の適用、[メッセージ ボックス スタイル](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)をボックスにします。

*nIDHelp*<br/>
メッセージのヘルプ コンテキスト ID。0 は、アプリケーションの既定のヘルプ コンテキストが使用されることを示します。

*nIDPrompt*<br/>
文字列テーブル内の文字列の参照に使用される一意の ID。

### <a name="return-value"></a>戻り値

メッセージ ボックスを表示する十分なメモリがない場合は 0。それ以外の場合、次のいずれかの値が返されます。

- IDABORT 中止 ボタンが選択されました。

- IDCANCEL キャンセル ボタンが選択されました。

- IDIGNORE 無視 ボタンが選択されました。

- IDNO、ボタンが選択されます。

- IDOK、[ok] ボタンが選択されました。

- IDRETRY 再試行 ボタンが選択されました。

- IDYES [はい] ボタンが選択されました。

メッセージ ボックスに [キャンセル] ボタンがある場合は、ESC キーが押されたか、[キャンセル] ボタンが選択されている場合に IDCANCEL 値が返されます。 メッセージ ボックスに [キャンセル] ボタンがない場合、Esc キーを押しても効果はありません。

関数は、 [AfxFormatString1](#afxformatstring1)と[AfxFormatString2](#afxformatstring2)メッセージ ボックスに表示されるテキストの書式設定で役に立ちます。

### <a name="remarks"></a>Remarks

これの最初のフォームには、関数の表示によって示されるテキスト文字列がオーバー ロードされた*lpszText*使用してメッセージ ボックス*nIDHelp*ヘルプ コンテキストを記述します。 ヘルプ コンテキストは、ユーザーがヘルプ キー (通常は F1 キー) を押したときに関連するヘルプ トピックにジャンプするために使用されます。

関数の 2 番目の形式は文字列リソースを使用して ID を持つ*nIDPrompt*メッセージ ボックスに、メッセージを表示します。 値によって、関連するヘルプ ページが検出された*nIDHelp*します。 場合の既定値*nIDHelp*に使用される (-1) は、文字列リソース ID、 *nIDPrompt*、ヘルプ コンテキストを使用します。 ヘルプ コンテキストの定義の詳細については、次を参照してください。[テクニカル ノート 28:](../../mfc/tn028-context-sensitive-help-support.md)します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT クラス](../../atl-mfc-shared/reference/cstringt-class.md)
