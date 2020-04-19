---
title: COleBusyDialog クラス
ms.date: 11/04/2016
f1_keywords:
- COleBusyDialog
- AFXODLGS/COleBusyDialog
- AFXODLGS/COleBusyDialog::COleBusyDialog
- AFXODLGS/COleBusyDialog::DoModal
- AFXODLGS/COleBusyDialog::GetSelectionType
- AFXODLGS/COleBusyDialog::m_bz
helpviewer_keywords:
- COleBusyDialog [MFC], COleBusyDialog
- COleBusyDialog [MFC], DoModal
- COleBusyDialog [MFC], GetSelectionType
- COleBusyDialog [MFC], m_bz
ms.assetid: c881a532-9672-4c41-b51b-5ce4a7246a6b
ms.openlocfilehash: aa3f0d85bcbf34d325125187b22b38c4da01fb43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504407"
---
# <a name="colebusydialog-class"></a>COleBusyDialog クラス

OLE の [サーバーが応答しません] ダイアログ ボックスまたは [サーバーを使用できません] ダイアログ ボックスに使用されます。

## <a name="syntax"></a>構文

```
class COleBusyDialog : public COleDialog
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleBusyDialog::COleBusyDialog](#colebusydialog)|`COleBusyDialog` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleBusyDialog::D oModal](#domodal)|[OLE サーバーのビジー状態] ダイアログボックスを表示します。|
|[COleBusyDialog::GetSelectionType](#getselectiontype)|ダイアログボックスでの選択内容を決定します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[COleBusyDialog::m_bz](#m_bz)|ダイアログボックスの動作を制御する OLEUIBUSY 型の構造体。|

## <a name="remarks"></a>Remarks

これらのダイアログボックスを`COleBusyDialog`呼び出す場合は、クラスのオブジェクトを作成します。 オブジェクトが構築されたら、[m_bz](#m_bz) 構造体を使用して、ダイアログボックス内のコントロールの値または状態を初期化できます。`COleBusyDialog` この`m_bz`構造体の型は oleuibusy です。 このダイアログクラスの使用方法の詳細については、「 [DoModal](#domodal)メンバー関数」を参照してください。

> [!NOTE]
>  アプリケーションウィザードで生成されたコンテナーコードは、このクラスを使用します。

詳細については、Windows SDK の[Oleuibusy](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)構造体を参照してください。

OLE 固有のダイアログボックスの詳細については、 [ole の記事のダイアログボックス](../../mfc/dialog-boxes-in-ole.md)を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleBusyDialog`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxodlgs

##  <a name="colebusydialog"></a>  COleBusyDialog::COleBusyDialog

この関数は、オブジェクト`COleBusyDialog`のみを構築します。

```
explicit COleBusyDialog(
    HTASK htaskBusy,
    BOOL bNotResponding = FALSE,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*htaskBusy*<br/>
ビジー状態のサーバータスクを処理します。

*bNotResponding*<br/>
TRUE の場合は、[サーバーのビジー状態] ダイアログボックスではなく、[応答なし] ダイアログボックスを呼び出します。 [応答なし] ダイアログボックスの表現は、[サーバーのビジー状態] ダイアログボックスの表現とは少し異なり、[キャンセル] ボタンは無効になっています。

*dwFlags*<br/>
作成フラグ。 には、ビットごとの OR 演算子と組み合わせて、次の値を0個以上含めることができます。

- BZ_DISABLECANCELBUTTON ダイアログボックスを呼び出すときに、[キャンセル] ボタンを無効にします。

- BZ_DISABLESWITCHTOBUTTON ダイアログボックスを呼び出すときに、[切り替え先] ボタンを無効にします。

- BZ_DISABLERETRYBUTTON ダイアログボックスを呼び出すときに、[再試行] ボタンを無効にします。

*pParentWnd*<br/>
ダイアログオブジェクトが属する親またはオーナーウィンドウオブジェクト ( `CWnd`型) を指します。 NULL の場合は、ダイアログオブジェクトの親ウィンドウがメインアプリケーションウィンドウに設定されます。

### <a name="remarks"></a>Remarks

ダイアログボックスを表示するには、 [DoModal](#domodal)を呼び出します。

詳細については、Windows SDK の[Oleuibusy](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)構造体を参照してください。

##  <a name="domodal"></a>COleBusyDialog::D oModal

この関数を呼び出して、[OLE サーバーのビジー状態またはサーバーが応答していません] ダイアログボックスを表示します。

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>戻り値

ダイアログボックスの完了ステータス。 次のいずれかの値です。

- IDOK ダイアログボックスが正常に表示された場合は。

- ユーザーがダイアログボックスをキャンセルした場合は IDCANCEL。

- エラーが発生した場合は IDABORT。 Idabort が返された場合は`COleDialog::GetLastError` 、メンバー関数を呼び出して、発生したエラーの種類に関する詳細情報を取得します。 考えられるエラーの一覧については、Windows SDK の[Oleuibusy](/windows/win32/api/oledlg/nf-oledlg-oleuibusyw)関数に関する記述を参照してください。

### <a name="remarks"></a>Remarks

[M_bz](#m_bz)構造体のメンバーを設定してさまざまなダイアログボックスコントロールを初期化する場合は、を呼び出す`DoModal`前に、ダイアログオブジェクトが構築された後に、この操作を行う必要があります。

が`DoModal` IDOK を返す場合は、他のメンバー関数を呼び出して、ダイアログボックスにユーザーが入力した設定または情報を取得できます。

##  <a name="getselectiontype"></a>  COleBusyDialog::GetSelectionType

[サーバーのビジー状態] ダイアログボックスでユーザーが選択した選択の種類を取得します。

```
UINT GetSelectionType() const;
```

### <a name="return-value"></a>戻り値

選択された種類。

### <a name="remarks"></a>Remarks

戻り値の型の値は、 `Selection` `COleBusyDialog`クラスで宣言された列挙型によって指定されます。

```
enum Selection {
    switchTo,
    retry,
    callUnblocked
    };
```

これらの値の簡単な説明を次に示します。

- `COleBusyDialog::switchTo`[切り替え] ボタンが押されました。

- `COleBusyDialog::retry`[再試行] ボタンが押されました。

- `COleBusyDialog::callUnblocked`サーバーのアクティブ化のための呼び出しがブロック解除されました。

##  <a name="m_bz"></a>COleBusyDialog::m_bz

[サーバーのビジー状態] ダイアログボックスの動作を制御するために使用される OLEUIBUSY 型の構造。

```
OLEUIBUSY m_bz;
```

### <a name="remarks"></a>Remarks

この構造体のメンバーは、直接、またはメンバー関数を使用して変更できます。

詳細については、Windows SDK の[Oleuibusy](/windows/win32/api/oledlg/ns-oledlg-oleuibusyw)構造体を参照してください。

## <a name="see-also"></a>関連項目

[COleDialog クラス](../../mfc/reference/coledialog-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleDialog クラス](../../mfc/reference/coledialog-class.md)
