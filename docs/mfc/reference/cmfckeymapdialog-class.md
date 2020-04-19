---
title: CMFCKeyMapDialog クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::DoModal
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::FormatItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::GetCommandKeys
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnInsertItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintHeader
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnSetColumns
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::PrintKeyMap
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::SetColumnsWidth
helpviewer_keywords:
- CMFCKeyMapDialog [MFC], CMFCKeyMapDialog
- CMFCKeyMapDialog [MFC], DoModal
- CMFCKeyMapDialog [MFC], FormatItem
- CMFCKeyMapDialog [MFC], GetCommandKeys
- CMFCKeyMapDialog [MFC], OnInsertItem
- CMFCKeyMapDialog [MFC], OnPrintHeader
- CMFCKeyMapDialog [MFC], OnPrintItem
- CMFCKeyMapDialog [MFC], OnSetColumns
- CMFCKeyMapDialog [MFC], PrintKeyMap
- CMFCKeyMapDialog [MFC], SetColumnsWidth
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
ms.openlocfilehash: 65aa5ab0f24999ee23a97f383577b69584825502
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388502"
---
# <a name="cmfckeymapdialog-class"></a>CMFCKeyMapDialog クラス

`CMFCKeyMapDialog`クラスは、コマンドをキーボードのキーにマップされるコントロールをサポートしています。

## <a name="syntax"></a>構文

```
class CMFCKeyMapDialog : public CDialogEx
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|`CMFCKeyMapDialog` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCKeyMapDialog::DoModal](#domodal)|キーボード マッピングのダイアログ ボックスが表示されます。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCKeyMapDialog::FormatItem](#formatitem)|キーのマッピングを記述する文字列を作成するためにフレームワークによって呼び出されます。 既定では、文字列には、コマンド名、使用すると、ショートカット キー、およびショートカット キーの説明が含まれています。|
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|指定されたコマンドに関連付けられているショートカット キーの一覧を含む文字列を取得します。|
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|キーボード マップ コントロールをサポートする内部リスト コントロールに新しい項目が挿入される前に、フレームワークによって呼び出されます。|
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|新しいページのキーボード マップのヘッダーを印刷するためにフレームワークによって呼び出されます。|
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|キーボード マップ項目を印刷するためにフレームワークによって呼び出されます。|
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|キーボード マップ コントロールをサポートする内部リスト コントロール内の列のキャプションを設定するためにフレームワークによって呼び出されます。|
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|ユーザーがクリックしたときに、フレームワークによって呼び出されます、**印刷**ボタンをクリックします。|
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|キーボード マップ コントロールをサポートする内部リスト コントロール内の列の幅を設定するためにフレームワークによって呼び出されます。|

## <a name="remarks"></a>Remarks

使用して、`CMFCKeyMapDialog`サイズ変更可能なキーボード マッピング ダイアログ ボックスを実装するクラス。 ダイアログ ボックスでは、キーボード ショートカットとそれに関連付けられているコマンドを表示するのにリスト ビュー コントロールを使用します。

使用する、`CMFCKeyMapDialog`クラスのアプリケーションで、ポインターを渡すメイン フレーム ウィンドウにパラメーターとして、`CMFCKeyMapDialog`コンス トラクター。 呼び出して、`DoModal`モーダル ダイアログ ボックスを起動する方法。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxkeymapdialog.h

##  <a name="cmfckeymapdialog"></a>  CMFCKeyMapDialog::CMFCKeyMapDialog

`CMFCKeyMapDialog` オブジェクトを構築します。

```
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bEnablePrint=FALSE);
```

### <a name="parameters"></a>パラメーター

*pWndParentFrame*<br/>
[in]親ウィンドウへのポインター、`CMFCKeyMapDialog`オブジェクト。

*bEnablePrint*<br/>
[in]アクセラレータ キーの一覧を印刷する場合は TRUE。それ以外の場合、FALSE です。 既定では FALSE です。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

次の例のオブジェクトを構築する方法、`CMFCKeyMapDialog`クラス。 この例は、 [Visual Studio のデモ サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]

##  <a name="domodal"></a>  CMFCKeyMapDialog::DoModal

キーボード マッピングのダイアログ ボックスが表示されます。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>戻り値

IDOK、IDCANCEL に渡されるなどの符号付き整数の[CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog)メソッド。 メソッドは、さらに、ダイアログ ボックスを閉じます。 詳細については、次を参照してください。 [CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal)します。

### <a name="remarks"></a>Remarks

キーボード マッピングのダイアログ ボックスを使用すると、選択し、アクセラレータ キーをコマンドのさまざまなカテゴリに割り当てることができます。 さらに、選択したアクセラレータ キーとその説明をクリップボードにコピーできます。

##  <a name="formatitem"></a>  CMFCKeyMapDialog::FormatItem

キーのマッピングを記述する文字列を作成するためにフレームワークによって呼び出されます。 既定では、文字列には、コマンド名、使用すると、ショートカット キー、およびショートカット キーの説明が含まれています。

```
virtual CString FormatItem(int nItem) const;
```

### <a name="parameters"></a>パラメーター

*nItem*<br/>
[in]キー マッピングの内部リストの項目の 0 から始まるインデックス。

### <a name="return-value"></a>戻り値

A`CString`書式設定された項目のテキストを格納しているオブジェクト。

### <a name="remarks"></a>Remarks

##  <a name="getcommandkeys"></a>  CMFCKeyMapDialog::GetCommandKeys

文字列値を取得します。 文字列には、指定されたコマンドに関連付けられているショートカット キーの一覧が含まれています。

```
virtual CString GetCommandKeys(UINT uiCmdID) const;
```

### <a name="parameters"></a>パラメーター

*uiCmdID*<br/>
[in]コマンド id。

### <a name="return-value"></a>戻り値

セミコロンで区切られた、指定したコマンドに関連付けられているショートカット キーの (';') の一覧。

### <a name="remarks"></a>Remarks

##  <a name="oninsertitem"></a>  CMFCKeyMapDialog::OnInsertItem

キーボード マップ コントロールをサポートする内部リスト コントロールに新しい項目が挿入される前に、フレームワークによって呼び出されます。

```
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,
    int nItem);
```

### <a name="parameters"></a>パラメーター

*pButton*<br/>
[in]コマンドの名前と説明をキーボードのキーの組み合わせにマップするために使用するツール バー ボタンへのポインター。 キー マップ項目は、内部のリスト コントロールに格納されます。

*nItem*<br/>
[in]内部リスト コントロールに新しいキー マップ項目を挿入する場所を指定する 0 から始まるインデックス。

### <a name="remarks"></a>Remarks

##  <a name="onprintheader"></a>  CMFCKeyMapDialog::OnPrintHeader

新しいページのキーボード マップのヘッダーを印刷するためにフレームワークによって呼び出されます。

```
virtual int OnPrintHeader(
    CDC& dc,
    int nPage,
    int cx) const;
```

### <a name="parameters"></a>パラメーター

*dc*<br/>
[in]プリンター デバイス コンテキスト。

*nPage*<br/>
[in]印刷するページ番号。

*cx*<br/>
[in]ピクセル単位でヘッダーの水平オフセット。

### <a name="return-value"></a>戻り値

成功した場合、印刷したテキストの高さ。 詳細については、の戻り値のセクションを参照してください。 [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)します。

### <a name="remarks"></a>Remarks

フレームワークでは、このメソッドを使用して、キーボード マップを印刷します。 既定では、このメソッドは、ページ番号、アプリケーション名、およびダイアログ ボックスのタイトルを出力します。

##  <a name="onprintitem"></a>  CMFCKeyMapDialog::OnPrintItem

キーボード マップ項目を印刷するためにフレームワークによって呼び出されます。

```
virtual int OnPrintItem(
    CDC& dc,
    int nItem,
    int y,
    int cx,
    BOOL bCalcHeight) const;
```

### <a name="parameters"></a>パラメーター

*dc*<br/>
[in]プリンター デバイス コンテキスト。

*nItem*<br/>
[in]印刷する項目の 0 から始まるインデックス。

*y*<br/>
[in]ページの上部および項目の位置間の垂直オフセット。

*cx*<br/>
[in]ページの左側と項目の位置の水平オフセット。

*bCalcHeight*<br/>
[in]印刷の項目の最適な高さを計算する場合は TRUE既定の領域に収まるように、印刷の項目を切り捨てる場合は FALSE。

### <a name="return-value"></a>戻り値

印刷された項目の高さ。

### <a name="remarks"></a>Remarks

フレームワークは、キー マップ ダイアログ ボックスの項目を印刷するには、このメソッドを呼び出します。 既定では、このメソッドは、項目のコマンド名、ショートカット キー、およびコマンドの説明を出力します。

##  <a name="onsetcolumns"></a>  CMFCKeyMapDialog::OnSetColumns

キーボード マップ コントロールをサポートする内部リスト コントロール内の列のキャプションを設定するためにフレームワークによって呼び出されます。

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Remarks

既定では、このメソッドは、3 つのリソースからの列のキャプションを取得します。 コマンドの列のキャプションは IDS_AFXBARRES_COMMAND、IDS_AFXBARRES_KEYS からのキー列のキャプションは、説明の列のキャプションは IDS_AFXBARRES_DESCRIPTION から。

##  <a name="printkeymap"></a>  CMFCKeyMapDialog::PrintKeyMap

ユーザーがクリックしたときに、フレームワークによって呼び出されます、**印刷**ボタンをクリックします。

```
virtual void PrintKeyMap();
```

### <a name="remarks"></a>Remarks

`PrintKeyMap`メソッドは、キー マップを出力します。 新しい印刷ジョブを開始し、繰り返し呼び出し、 [CMFCKeyMapDialog::OnPrintHeader](#onprintheader)と[CMFCKeyMapDialog::OnPrintItem](#onprintitem)メソッドまで、キーのすべてのマッピングが出力されます。

##  <a name="setcolumnswidth"></a>  CMFCKeyMapDialog::SetColumnsWidth

キーボード マップ コントロールをサポートする内部リスト コントロール内の列の幅を設定するためにフレームワークによって呼び出されます。

```
virtual void SetColumnsWidth();
```

### <a name="remarks"></a>Remarks

このメソッドは、内部のリスト コントロールの列を既定の幅に設定します。 最初に、ショートカット キーの列の幅が計算されます。 残りの幅の 3 分の 1 つは、コマンドの列に割り当てられているし、残りの 2/3 は、[説明] 列に割り当てられています。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager クラス](../../mfc/reference/ckeyboardmanager-class.md)
