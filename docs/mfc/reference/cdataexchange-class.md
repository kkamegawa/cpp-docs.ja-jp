---
title: CDataExchange クラス
ms.date: 11/04/2016
f1_keywords:
- CDataExchange
- AFXWIN/CDataExchange
- AFXWIN/CDataExchange::CDataExchange
- AFXWIN/CDataExchange::Fail
- AFXWIN/CDataExchange::PrepareCtrl
- AFXWIN/CDataExchange::PrepareEditCtrl
- AFXWIN/CDataExchange::PrepareOleCtrl
- AFXWIN/CDataExchange::m_bSaveAndValidate
- AFXWIN/CDataExchange::m_pDlgWnd
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
ms.openlocfilehash: 0e7a9d429acb1acd72942e5f10ac0815232ddc69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253570"
---
# <a name="cdataexchange-class"></a>CDataExchange クラス

MFC で使われているダイアログ データ エクスチェンジ (DDX) およびダイアログ データ検証 (DDV) の両ルーチンをサポートします。

## <a name="syntax"></a>構文

```
class CDataExchange
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDataExchange::CDataExchange](#cdataexchange)|`CDataExchange` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDataExchange::Fail](#fail)|検証が失敗したときに呼び出されます。 前のコントロールにフォーカスをリセットし、例外をスローします。|
|[CDataExchange::PrepareCtrl](#preparectrl)|データ交換または検証用に、指定したコントロールを準備します。非エディット コントロールに使用してください。|
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|データ交換または検証用に、指定したエディット コントロールを準備します。|
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|データ交換または検証用に、指定した OLE コントロールを準備します。非エディット コントロールに使用してください。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|DDX ルーチンおよび DDV の方向を示すフラグです。|
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|データ交換がダイアログ ボックスまたはウィンドウが行われます。|

## <a name="remarks"></a>Remarks

`CDataExchange` 基本クラスはありません。

カスタム データ型またはコントロールに対してデータ エクス チェンジ ルーチンを記述する場合は、このクラスを使用して、独自のデータ検証ルーチンを記述する場合またはします。 DDX ルーチンおよび DDV ルーチンを記述の詳細については、次を参照してください。[テクニカル ノート 26](../../mfc/tn026-ddx-and-ddv-routines.md)します。 DDX ルーチンおよび DDV の概要については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)と[ ダイアログ ボックス](../../mfc/dialog-boxes.md)します。

A`CDataExchange`オブジェクト DDX ルーチンおよび DDV を配置するために必要なコンテキスト情報を提供します。 フラグ*m_bSaveAndValidate* DDX を使用してデータ メンバーからダイアログ コントロールの初期値を入力する場合に、FALSE です。 フラグ*m_bSaveAndValidate* DDX を使用して、データ メンバーおよび DDV をデータ値の検証に使用するときにダイアログ コントロールの現在の値を設定する場合は TRUE になります。 DDV 検証が失敗した場合、ddv 入力エラーを示すメッセージ ボックスが表示されます。 Ddv を呼び出して`Fail`に問題が発生したコントロールにフォーカスをリセットし、検証プロセスを停止する例外をスローします。

## <a name="inheritance-hierarchy"></a>継承階層

`CDataExchange`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="cdataexchange"></a>  CDataExchange::CDataExchange

作成するには、このメンバー関数を呼び出す、`CDataExchange`オブジェクト。

```
CDataExchange(
    CWnd* pDlgWnd,
    BOOL bSaveAndValidate);
```

### <a name="parameters"></a>パラメーター

*pDlgWnd*<br/>
コントロールを格納する親ウィンドウへのポインター。 通常、これは、 [CDialog](../../mfc/reference/cdialog-class.md)の派生オブジェクト。

*bSaveAndValidate*<br/>
TRUE の場合、このオブジェクトは、データを検証し、メンバーに、コントロールからデータを書き込みます。 FALSE の場合、このオブジェクトはデータをコントロールにメンバーを移動します。

### <a name="remarks"></a>Remarks

構築、`CDataExchange`オブジェクトに渡す、ウィンドウのデータの exchange オブジェクトに追加情報を格納する自分で[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)メンバー関数。

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]

##  <a name="fail"></a>  CDataExchange::Fail

ダイアログ データ検証 (DDV) 操作が失敗したときに、フレームワークはこのメンバー関数を呼び出します。

```
void Fail();
```

### <a name="remarks"></a>Remarks

`Fail` 検証には、(復元するコントロールがある場合) が失敗しました。 コントロールにフォーカスと選択を復元します。 `Fail` 型の例外がスロー [CUserException](../../mfc/reference/cuserexception-class.md)検証プロセスを停止します。 例外により、メッセージ ボックスが表示されるエラーを説明します。 DDV 検証が失敗した後、ユーザーは、問題のあるコントロールのデータの再入力できます。

DDV ルーチンのカスタム実装を呼び出すことができます`Fail`検証が失敗したときに、ルーチンから。

DDX ルーチンおよび DDV ルーチンを記述の詳細については、次を参照してください。[テクニカル ノート 26](../../mfc/tn026-ddx-and-ddv-routines.md)します。 DDX ルーチンおよび DDV の概要については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)と[ダイアログ ボックスに関するトピック](../../mfc/dialog-boxes.md)します。

##  <a name="m_bsaveandvalidate"></a>  CDataExchange::m_bSaveAndValidate

このフラグは、ダイアログ データ エクス (チェンジ DDX) 操作の方向を示します。

```
BOOL m_bSaveAndValidate;
```

### <a name="remarks"></a>Remarks

フラグが 0 以外の値が場合、`CDataExchange`オブジェクトは、ユーザーがコントロールを編集した後は、ダイアログ クラスのデータ メンバーにダイアログのコントロールからデータを移動に使用されています。 ダイアログ クラスのデータ メンバーからダイアログ コントロールを初期化するために使用されている場合、フラグは 0 を使用します。

ダイアログ データ検証 (DDV) 中には、フラグを 0 以外の場合もします。

DDX ルーチンおよび DDV ルーチンを記述の詳細については、次を参照してください。[テクニカル ノート 26](../../mfc/tn026-ddx-and-ddv-routines.md)します。 DDX ルーチンおよび DDV の概要については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)と[ダイアログ ボックスに関するトピック](../../mfc/dialog-boxes.md)します。

##  <a name="m_pdlgwnd"></a>  CDataExchange::m_pDlgWnd

ポインターが含まれています、 [CWnd](../../mfc/reference/cwnd-class.md)オブジェクト ダイアログ データ エクス (チェンジ DDX) または検証 (DDV) が行われています。

```
CWnd* m_pDlgWnd;
```

### <a name="remarks"></a>Remarks

このオブジェクトは、通常、 [CDialog](../../mfc/reference/cdialog-class.md)オブジェクト。 DDX または DDV ルーチンのカスタム実装する場合は、このポインターを使用して、操作するコントロールを格納しているダイアログ ウィンドウにアクセス権を取得します。

DDX ルーチンおよび DDV ルーチンを記述の詳細については、次を参照してください。[テクニカル ノート 26](../../mfc/tn026-ddx-and-ddv-routines.md)します。 DDX ルーチンおよび DDV の概要については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)と[ダイアログ ボックスに関するトピック](../../mfc/dialog-boxes.md)します。

##  <a name="preparectrl"></a>  CDataExchange::PrepareCtrl

フレームワークは、ダイアログ データ エクス (チェンジ DDX) と検証 (DDV) の指定したコントロールを準備するには、このメンバー関数を呼び出します。

```
HWND PrepareCtrl(int nIDC);
```

### <a name="parameters"></a>パラメーター

*nIDC*<br/>
DDX DDV 用に準備するコントロールの ID。

### <a name="return-value"></a>戻り値

DDX DDV 用に準備されているコントロールの HWND。

### <a name="remarks"></a>Remarks

使用して、[性チェックされる](#prepareeditctrl)代わりにエディット コントロールを他のすべてのコントロールのこのメンバー関数を使用します。

コントロールの HWND を格納するは、準備、`CDataExchange`クラス。 フレームワークでは、このハンドルを使用して、DDX または DDV 障害以前フォーカスされたコントロールにフォーカスを復元します。

カスタムの DDX または DDV ルーチンの実装を呼び出す必要があります`PrepareCtrl`を DDX を使用してデータを交換するまたは DDV を使用してデータを検証していますが、すべての非編集コントロール。

DDX ルーチンおよび DDV ルーチンを記述の詳細については、次を参照してください。[テクニカル ノート 26](../../mfc/tn026-ddx-and-ddv-routines.md)します。 DDX ルーチンおよび DDV の概要については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)と[ダイアログ ボックスに関するトピック](../../mfc/dialog-boxes.md)します。

##  <a name="prepareeditctrl"></a>  CDataExchange::PrepareEditCtrl

フレームワークは、ダイアログ データ エクス (チェンジ DDX) と検証 (DDV) を指定した編集コントロールを準備するには、このメンバー関数を呼び出します。

```
HWND PrepareEditCtrl(int nIDC);
```

### <a name="parameters"></a>パラメーター

*nIDC*<br/>
DDX または DDV を準備するエディット コントロールの ID。

### <a name="return-value"></a>戻り値

DDX DDV 用に準備されているエディット コントロールの HWND。

### <a name="remarks"></a>Remarks

使用[記述](#preparectrl)代わりにすべての非編集コントロール。

準備は、次の 2 つで構成されます。 まず、`PrepareEditCtrl`でコントロールの HWND を格納、`CDataExchange`クラス。 フレームワークでは、このハンドルを使用して、DDX または DDV 障害以前フォーカスされたコントロールにフォーカスを復元します。 2 番目、`PrepareEditCtrl`にフラグを設定、`CDataExchange`ことを示すデータが交換または編集コントロールは、検証コントロール。

カスタムの DDX または DDV ルーチンの実装を呼び出す必要があります`PrepareEditCtrl`のすべての編集コントロールは DDX を使用してデータを交換する、または DDV を使用してデータを検証しています。

DDX ルーチンおよび DDV ルーチンを記述の詳細については、次を参照してください。[テクニカル ノート 26](../../mfc/tn026-ddx-and-ddv-routines.md)します。 DDX ルーチンおよび DDV の概要については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)と[ダイアログ ボックスに関するトピック](../../mfc/dialog-boxes.md)します。

##  <a name="prepareolectrl"></a>  CDataExchange::PrepareOleCtrl

フレームワークは、指定の OLE コントロール ダイアログ データ エクス (チェンジ DDX) と検証 (DDV) を準備するには、このメンバー関数を呼び出します。

```
COleControlSite* PrepareOleCtrl(int nIDC);
```

### <a name="parameters"></a>パラメーター

*nIDC*<br/>
DDX または DDV を準備する OLE コントロールの ID。

### <a name="return-value"></a>戻り値

OLE コントロール サイトへのポインター。

### <a name="remarks"></a>Remarks

使用[性チェックされる](#prepareeditctrl)代わりに編集コントロールのまたは[記述](#preparectrl)他のすべての非 OLE コントロール。

カスタムの DDX または DDV ルーチンの実装を呼び出す必要があります`PrepareOleCtrl`を DDX を使用してデータを交換するまたは DDV を使用してデータを検証していますが、すべての OLE コントロール。

DDX ルーチンおよび DDV ルーチンを記述の詳細については、次を参照してください。[テクニカル ノート 26](../../mfc/tn026-ddx-and-ddv-routines.md)します。 DDX ルーチンおよび DDV の概要については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)と[ダイアログ ボックスに関するトピック](../../mfc/dialog-boxes.md)します。

## <a name="see-also"></a>関連項目

[MFC サンプル VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)<br/>
[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)
