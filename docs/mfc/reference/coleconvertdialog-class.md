---
title: COleConvertDialog クラス
ms.date: 11/04/2016
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
ms.openlocfilehash: ba57e756457fcffca806eeba7454ddf7bcf99d34
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504295"
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog クラス

詳細については、Windows SDK の[OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)構造体を参照してください。

## <a name="syntax"></a>構文

```
class COleConvertDialog : public COleDialog
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleConvertDialog:: COleConvertDialog](#coleconvertdialog)|`COleConvertDialog` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleConvertDialog::D oConvert](#doconvert)|ダイアログボックスで指定された変換を実行します。|
|[COleConvertDialog::D oModal](#domodal)|[OLE 項目の変更] ダイアログボックスを表示します。|
|[COleConvertDialog:: GetClassID](#getclassid)|選択した項目に関連付けられている CLSID を取得します。|
|[COleConvertDialog:: GetDrawAspect](#getdrawaspect)|項目をアイコンとして描画するかどうかを指定します。|
|[COleConvertDialog:: Geが Onicmetafile](#geticonicmetafile)|この項目のアイコン化形式に関連付けられているメタファイルへのハンドルを取得します。|
|[COleConvertDialog::GetSelectionType](#getselectiontype)|選択された選択の種類を取得します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[COleConvertDialog:: m_cv](#m_cv)|ダイアログボックスの動作を制御する構造体。|

## <a name="remarks"></a>Remarks

> [!NOTE]
>  アプリケーションウィザードで生成されたコンテナーコードは、このクラスを使用します。

OLE 固有のダイアログボックスの詳細については、 [ole の記事のダイアログボックス](../../mfc/dialog-boxes-in-ole.md)を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleConvertDialog`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxodlgs

##  <a name="coleconvertdialog"></a>COleConvertDialog:: COleConvertDialog

オブジェクトのみを`COleConvertDialog`構築します。

```
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*pItem*<br/>
変換またはアクティブ化する項目をポイントします。

*dwFlags*<br/>
作成フラグ。ビットごとの or 演算子を使用して、次の値を組み合わせて指定します。

- CF_SELECTCONVERTTO ダイアログボックスが呼び出されたときに、最初に [変換先] オプションが選択されることを指定します。 既定値です。

- CF_SELECTACTIVATEAS を指定すると、ダイアログボックスが呼び出されたときに、最初に [アクティブ化] オプションが選択されます。

- CF_SETCONVERTDEFAULT は、 `clsidConvertDefault` `m_cv`構造体のメンバーによって指定された CLSID を持つクラスが、[変換先] オプションボタンが選択されている場合に、[クラス] リストボックスでの既定の選択として使用されることを指定します。

- CF_SETACTIVATEDEFAULT は、 `clsidActivateDefault` `m_cv`構造体のメンバーによって指定された CLSID を持つクラスが、[アクティブ化] ボタンが選択されている場合に、[クラス] ボックスの既定の選択として使用されることを指定します。

- CF_SHOWHELPBUTTON を指定すると、ダイアログボックスが呼び出されたときに [ヘルプ] ボタンが表示されます。

*pClassID*<br/>
変換またはアクティブ化する項目の CLSID を指します。 NULL の場合、 *pItem*に関連付けられている CLSID が使用されます。

*pParentWnd*<br/>
ダイアログオブジェクトが属する親またはオーナーウィンドウオブジェクト ( `CWnd`型) を指します。 NULL の場合は、ダイアログボックスの親ウィンドウがメインアプリケーションウィンドウに設定されます。

### <a name="remarks"></a>Remarks

ダイアログボックスを表示するには、 [DoModal](#domodal)関数を呼び出します。

詳細については、「 [CLSID キー](/windows/win32/com/clsid-key-hklm) 」と「 [OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)構造体」を参照してください。

##  <a name="doconvert"></a>COleConvertDialog::D oConvert

[COleClientItem](../../mfc/reference/coleclientitem-class.md)型のオブジェクトを変換またはアクティブ化するために、 [DoModal](#domodal)から正常に返された後に、この関数を呼び出します。

```
BOOL DoConvert(COleClientItem* pItem);
```

### <a name="parameters"></a>パラメーター

*pItem*<br/>
変換またはアクティブ化する項目をポイントします。 Nll は指定できません。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

項目は、[変換] ダイアログボックスでユーザーが選択した情報に従って変換またはアクティブ化されます。

##  <a name="domodal"></a>COleConvertDialog::D oModal

[OLE 変換] ダイアログボックスを表示するには、この関数を呼び出します。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>戻り値

ダイアログボックスの完了ステータス。 次のいずれかの値です。

- IDOK ダイアログボックスが正常に表示された場合は。

- ユーザーがダイアログボックスをキャンセルした場合は IDCANCEL。

- エラーが発生した場合は IDABORT。 IDABORT が返された場合は、 [COleDialog:: GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)メンバー関数を呼び出して、発生したエラーの種類に関する詳細情報を取得します。 考えられるエラーの一覧については、Windows SDK の「 [OleUIConvert](/windows/win32/api/oledlg/nf-oledlg-oleuiconvertw)関数」を参照してください。

### <a name="remarks"></a>Remarks

[M_cv](#m_cv)構造体のメンバーを設定してさまざまなダイアログボックスコントロールを初期化する場合は、を呼び出す`DoModal`前に、ダイアログオブジェクトが構築された後に、この操作を行う必要があります。

が`DoModal` IDOK を返す場合は、他のメンバー関数を呼び出して、ダイアログボックスにユーザーが入力した設定または情報を取得できます。

##  <a name="getclassid"></a>COleConvertDialog:: GetClassID

この関数を呼び出して、[変換] ダイアログボックスでユーザーが選択した項目に関連付けられている CLSID を取得します。

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>戻り値

[変換] ダイアログボックスで選択された項目に関連付けられている CLSID。

### <a name="remarks"></a>Remarks

[DoModal](#domodal)が IDOK を返す場合にのみ、この関数を呼び出します。

詳細については、Windows SDK の「 [CLSID キー](/windows/win32/com/clsid-key-hklm) 」を参照してください。

##  <a name="getdrawaspect"></a>COleConvertDialog:: GetDrawAspect

選択した項目をアイコンとして表示することをユーザーが選択したかどうかを判断するには、この関数を呼び出します。

```
DVASPECT GetDrawAspect() const;
```

### <a name="return-value"></a>戻り値

オブジェクトを表示するために必要なメソッド。

- [アイコンとして表示] チェックボックスがオンになっていない場合、DVASPECT_CONTENT が返されます。

- [アイコンとして表示] チェックボックスがオンになっている場合、DVASPECT_ICON が返されます。

### <a name="remarks"></a>Remarks

[DoModal](#domodal)が IDOK を返す場合にのみ、この関数を呼び出します。

アスペクトの描画の詳細については、Windows SDK の「 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)データ構造体」を参照してください。

##  <a name="geticonicmetafile"></a>COleConvertDialog:: Geが Onicmetafile

選択した項目のアイコンの側面を含むメタファイルへのハンドルを取得するには、この関数を呼び出します。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>戻り値

[OK] をクリックしてダイアログを閉じたときに [アイコンとして表示] チェックボックスがオンになっていた場合に、選択した項目のアイコンの側面を含むメタファイルへのハンドル。それ以外の場合は NULL。

##  <a name="getselectiontype"></a>COleConvertDialog:: GetSelectionType

[変換] ダイアログボックスで選択した変換の種類を確認するには、この関数を呼び出します。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>戻り値

選択された種類。

### <a name="remarks"></a>Remarks

戻り値の型の値は、 `Selection` `COleConvertDialog`クラスで宣言された列挙型によって指定されます。

```
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };
```

これらの値の簡単な説明を次に示します。

- `COleConvertDialog::noConversion`ダイアログボックスがキャンセルされたか、ユーザーが変換を選択しなかった場合に返されます。 IDOK `COleConvertDialog::DoModal`が返された場合は、ユーザーが以前に選択したものとは異なるアイコンを選択した可能性があります。

- `COleConvertDialog::convertItem`[変換先] オプションボタンがオンになっている場合、ユーザーが別の項目を選択`DoModal`して変換すると、IDOK が返された場合に返されます。

- `COleConvertDialog::activateAs`[アクティブ化] ラジオボタンがオンになっている場合、ユーザーが別の項目を`DoModal`選択してアクティブ化し、結果として IDOK を返した場合に返されます。

##  <a name="m_cv"></a>COleConvertDialog:: m_cv

[変換] ダイアログボックスの動作を制御するために使用される OLEUICONVERT 型の構造。

```
OLEUICONVERT m_cv;
```

### <a name="remarks"></a>Remarks

この構造体のメンバーは、直接またはメンバー関数を使用して変更できます。

詳細については、Windows SDK の[OLEUICONVERT](/windows/win32/api/oledlg/ns-oledlg-oleuiconvertw)構造体を参照してください。

## <a name="see-also"></a>関連項目

[COleDialog クラス](../../mfc/reference/coledialog-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleDialog クラス](../../mfc/reference/coledialog-class.md)
