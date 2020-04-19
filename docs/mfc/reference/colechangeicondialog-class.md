---
title: COleChangeIconDialog クラス
ms.date: 11/04/2016
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
ms.openlocfilehash: 4cbf1137a15a9f86a6377980526e6d188f4d0a69
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504778"
---
# <a name="colechangeicondialog-class"></a>COleChangeIconDialog クラス

OLE の [アイコンの変更] ダイアログ ボックスに使用します。

## <a name="syntax"></a>構文

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|`COleChangeIconDialog` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleChangeIconDialog::D oChangeIcon](#dochangeicon)|ダイアログボックスで指定された変更を実行します。|
|[COleChangeIconDialog::D oModal](#domodal)|OLE 2 の [アイコンの変更] ダイアログボックスを表示します。|
|[COleChangeIconDialog:: Geが Onicmetafile](#geticonicmetafile)|この項目のアイコン化形式に関連付けられているメタファイルへのハンドルを取得します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[COleChangeIconDialog::m_ci](#m_ci)|ダイアログボックスの動作を制御する構造体。|

## <a name="remarks"></a>Remarks

このダイアログボックスを呼び`COleChangeIconDialog`出す必要がある場合は、クラスのオブジェクトを作成します。 オブジェクトが構築されたら、[m_ci](#m_ci) 構造体を使用して、ダイアログボックス内のコントロールの値または状態を初期化できます。`COleChangeIconDialog` `m_ci`構造体の型は OLEUICHANGEICON です。 このダイアログクラスの使用方法の詳細については、「 [DoModal](#domodal)メンバー関数」を参照してください。

詳細については、Windows SDK の[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)構造体を参照してください。

OLE 固有のダイアログボックスの詳細については、 [ole の記事のダイアログボックス](../../mfc/dialog-boxes-in-ole.md)を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxodlgs

##  <a name="colechangeicondialog"></a>COleChangeIconDialog::COleChangeIconDialog

この関数は、オブジェクト`COleChangeIconDialog`のみを構築します。

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*pItem*<br/>
変換する項目をポイントします。

*dwFlags*<br/>
作成フラグ。ビットごとの or 演算子を使用して、次の値を組み合わせて指定します。

- CIF_SELECTCURRENT ダイアログボックスが呼び出されたときに、現在のオプションボタンが最初に選択されることを指定します。 既定値です。

- CIF_SELECTDEFAULT ダイアログボックスが呼び出されたときに、既定のオプションボタンが最初に選択されることを指定します。

- CIF_SELECTFROMFILE ダイアログボックスが呼び出されたときに、最初に [ファイルから] オプションボタンが選択されることを指定します。

- CIF_SHOWHELP を指定すると、ダイアログボックスが呼び出されたときに [ヘルプ] ボタンが表示されます。

- CIF_USEICONEXE は、型から取得するのではなく、 [m_ci](#m_ci)の`szIconExe`フィールドで指定された実行可能ファイルからアイコンを抽出するように指定します。 これは、OLE 以外のファイルの埋め込みまたはリンクに役立ちます。

*pParentWnd*<br/>
ダイアログオブジェクトが属する親またはオーナーウィンドウオブジェクト ( `CWnd`型) を指します。 NULL の場合は、ダイアログボックスの親ウィンドウがメインアプリケーションウィンドウに設定されます。

### <a name="remarks"></a>Remarks

ダイアログボックスを表示するには、 [DoModal](#domodal)関数を呼び出します。

詳細については、Windows SDK の[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)構造体を参照してください。

##  <a name="dochangeicon"></a>COleChangeIconDialog::D oChangeIcon

この関数を呼び出して、 [DoModal](#domodal)から IDOK が返された後に、項目を表すアイコンをダイアログボックスで選択したアイコンに変更します。

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>パラメーター

*pItem*<br/>
アイコンが変更されている項目を指します。

### <a name="return-value"></a>戻り値

変更が成功した場合は0以外の。それ以外の場合は0です。

##  <a name="domodal"></a>COleChangeIconDialog::D oModal

OLE の [アイコンの変更] ダイアログボックスを表示するには、この関数を呼び出します。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>戻り値

ダイアログボックスの完了ステータス。 次のいずれかの値です。

- IDOK ダイアログボックスが正常に表示された場合は。

- ユーザーがダイアログボックスをキャンセルした場合は IDCANCEL。

- エラーが発生した場合は IDABORT。 Idabort が返された場合は`COleDialog::GetLastError` 、メンバー関数を呼び出して、発生したエラーの種類に関する詳細情報を取得します。 考えられるエラーの一覧については、Windows SDK の「 [OleUIChangeIcon](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw)関数」を参照してください。

### <a name="remarks"></a>Remarks

[M_ci](#m_ci)構造体のメンバーを設定してさまざまなダイアログボックスコントロールを初期化する場合は、を呼び出す`DoModal`前に、ダイアログオブジェクトが構築された後に、この操作を行う必要があります。

が`DoModal` IDOK を返す場合は、他のメンバー関数を呼び出して、ダイアログボックスにユーザーが入力した設定または情報を取得できます。

##  <a name="geticonicmetafile"></a>COleChangeIconDialog:: Geが Onicmetafile

選択した項目のアイコンの側面を含むメタファイルへのハンドルを取得するには、この関数を呼び出します。

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>戻り値

**[OK**] をクリックしてダイアログボックスを閉じた場合の、新しいアイコンのアイコン化された側面を含むメタファイルへのハンドル。それ以外の場合は、ダイアログが表示される前のアイコンです。

##  <a name="m_ci"></a>COleChangeIconDialog::m_ci

[アイコンの変更] ダイアログボックスの動作を制御するために使用される OLEUICHANGEICON 型の構造。

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>Remarks

この構造体のメンバーは、直接またはメンバー関数を使用して変更できます。

詳細については、Windows SDK の[OLEUICHANGEICON](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw)構造体を参照してください。

## <a name="see-also"></a>関連項目

[COleDialog クラス](../../mfc/reference/coledialog-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleDialog クラス](../../mfc/reference/coledialog-class.md)
