---
title: プロパティ ページ (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 1c4e6c585bf216518e46109e88a2388da03a0496
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611783"
---
# <a name="property-pages-mfc"></a>プロパティ ページ (MFC)

プロパティ ページでは、表示および編集ダイアログ データ エクス (チェンジ DDX) に基づくデータ マッピング メカニズムをサポートすることでカスタマイズ可能なグラフィカル インターフェイスで特定の OLE コントロール プロパティの現在の値を表示します。

このデータ マッピング メカニズムは、プロパティ ページのコントロールを OLE コントロールの個々 のプロパティにマップします。 コントロールのプロパティの値には、状態やプロパティ ページのコントロールの内容が反映されます。 プロパティ ページのコントロールとプロパティ間のマッピングがで指定された**ddp _** 関数呼び出しにプロパティ ページの`DoDataExchange`メンバー関数。 一覧を次に**ddp _** コントロールのプロパティ ページを使用して入力データを交換する関数。

### <a name="property-page-data-transfer"></a>プロパティ ページのデータ転送

|||
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|コントロールのプロパティを使用してコンボ ボックスで選択した文字列のインデックスをリンクします。|
|[DDP_CBString](#ddp_cbstring)|コントロールのプロパティを使用してコンボ ボックスで選択された文字列をリンクします。 選択した文字列では、プロパティの値と同じ文字で始まることができますが、完全に一致する必要はありません。|
|[DDP_CBStringExact](#ddp_cbstringexact)|コントロールのプロパティを使用してコンボ ボックスで選択された文字列をリンクします。 選択した文字列とプロパティの文字列値が正確に一致する必要があります。|
|[DDP_Check](#ddp_check)|コントロールのプロパティ ページで、コントロールのプロパティのチェック ボックスをリンクします。|
|[DDP_LBIndex](#ddp_lbindex)|コントロールのプロパティをリスト ボックスで選択した文字列のインデックスをリンクします。|
|[DDP_LBString](#ddp_lbstring)|コントロールのプロパティをリスト ボックスで選択された文字列をリンクします。 選択した文字列は、プロパティの値と同じ文字で始まることができますが、完全には一致する必要があります。|
|[DDP_LBStringExact](#ddp_lbstringexact)|コントロールのプロパティをリスト ボックスで選択された文字列をリンクします。 選択した文字列とプロパティの文字列値が正確に一致する必要があります。|
|[DDP_PostProcessing](#ddp_postprocessing)|コントロールからプロパティ値の転送を完了します。|
|[DDP_Radio](#ddp_radio)|コントロールのプロパティを使用して、コントロールのプロパティ ページでラジオ ボタン グループのリンクです。|
|[DDP_Text](#ddp_text)|コントロールのプロパティを使用して、コントロールのプロパティ ページのコントロールをリンクします。 この関数はなどさまざまな種類のプロパティ] の [**double**、**short**、BSTR、および**long**します。|

詳細については、`DoDataExchange`関数やプロパティ ページでは、記事をご覧ください[ActiveX コントロール。プロパティ ページ](../../mfc/mfc-activex-controls-property-pages.md)します。

作成し、OLE コントロールのプロパティ ページを管理するために使用するマクロの一覧を次には。

### <a name="property-pages"></a>[プロパティ ページ]

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|プロパティ ページ Id の一覧を開始します。|
|[END_PROPPAGEIDS](#end_proppageids)|プロパティ ページ Id のリストを終了します。|
|[PROPPAGEID](#proppageid)|コントロール クラスのプロパティ ページを宣言します。|

##  <a name="ddp_cbindex"></a>  DDP_CBIndex

プロパティ ページのこの関数を呼び出す`DoDataExchange`プロパティ ページで、コンボ ボックスの現在の選択項目のインデックスを持つ整数のプロパティの値を同期する関数。

```
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
ポインターを`CDataExchange`オブジェクト。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*ID*<br/>
リソース ID のコンボ ボックスで指定されたコントロール プロパティに関連付けられたコントロール*pszPropName*します。

*member*<br/>
指定されたプロパティ ページのコントロールに関連付けられたメンバー変数*id*で指定されたプロパティと*pszPropName*します。

*pszPropName*<br/>
指定されたコンボ ボックス コントロールと交換されるコントロール プロパティのプロパティ名*id*します。

### <a name="remarks"></a>Remarks

この関数は、対応する前に呼び出す必要がある`DDX_CBIndex`関数呼び出し。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="ddp_cbstring"></a>  DDP_CBString

プロパティ ページのこの関数を呼び出す`DoDataExchange`文字列プロパティの値をプロパティ ページで、コンボ ボックスの現在の選択と同期する関数。

```
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
ポインターを`CDataExchange`オブジェクト。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*ID*<br/>
リソース ID のコンボ ボックスで指定されたコントロール プロパティに関連付けられたコントロール*pszPropName*します。

*member*<br/>
指定されたプロパティ ページのコントロールに関連付けられたメンバー変数*id*で指定されたプロパティと*pszPropName*します。

*pszPropName*<br/>
指定されたコンボ ボックスの文字列と交換されるコントロール プロパティのプロパティ名*id*します。

### <a name="remarks"></a>Remarks

この関数は、対応する前に呼び出す必要がある`DDX_CBString`関数呼び出し。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="ddp_cbstringexact"></a>  DDP_CBStringExact

プロパティ ページのこの関数を呼び出す`DoDataExchange`プロパティ ページで、コンボ ボックスの現在の選択を正確に一致する文字列プロパティの値を同期する関数。

```
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
ポインターを`CDataExchange`オブジェクト。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*ID*<br/>
リソース ID のコンボ ボックスで指定されたコントロール プロパティに関連付けられたコントロール*pszPropName*します。

*member*<br/>
指定されたプロパティ ページのコントロールに関連付けられたメンバー変数*id*で指定されたプロパティと*pszPropName*します。

*pszPropName*<br/>
指定されたコンボ ボックスの文字列と交換されるコントロール プロパティのプロパティ名*id*します。

### <a name="remarks"></a>Remarks

この関数は、対応する前に呼び出す必要がある`DDX_CBStringExact`関数呼び出し。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="ddp_check"></a>  DDP_Check

プロパティ ページのこの関数を呼び出す`DoDataExchange`関連付けられているプロパティ ページのチェック ボックス コントロールとプロパティの値を同期する関数。

```
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
ポインターを`CDataExchange`オブジェクト。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*ID*<br/>
指定されたコントロール プロパティに関連付けられているチェック ボックス コントロールのリソース ID *pszPropName*します。

*member*<br/>
指定されたプロパティ ページのコントロールに関連付けられたメンバー変数*id*で指定されたプロパティと*pszPropName*します。

*pszPropName*<br/>
指定されたチェック ボックス コントロールと交換されるコントロール プロパティのプロパティ名*id*します。

### <a name="remarks"></a>Remarks

この関数は、対応する前に呼び出す必要がある`DDX_Check`関数呼び出し。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="ddp_lbindex"></a>  DDP_LBIndex

プロパティ ページのこの関数を呼び出す`DoDataExchange`プロパティ ページでリスト ボックスの現在の選択項目のインデックスを持つ整数のプロパティの値を同期する関数。

```
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
ポインターを`CDataExchange`オブジェクト。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*ID*<br/>
リストのリソース ID で指定されたコントロール プロパティに関連付けられたコントロールのボックス*pszPropName*します。

*member*<br/>
指定されたプロパティ ページのコントロールに関連付けられたメンバー変数*id*で指定されたプロパティと*pszPropName*します。

*pszPropName*<br/>
指定されたリスト ボックスの文字列と交換されるコントロール プロパティのプロパティ名*id*します。

### <a name="remarks"></a>Remarks

この関数は、対応する前に呼び出す必要がある`DDX_LBIndex`関数呼び出し。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="ddp_lbstring"></a>  DDP_LBString

プロパティ ページのこの関数を呼び出す`DoDataExchange`文字列プロパティの値をプロパティ ページでリスト ボックスの現在の選択と同期する関数。

```
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
ポインターを`CDataExchange`オブジェクト。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*ID*<br/>
リストのリソース ID で指定されたコントロール プロパティに関連付けられたコントロールのボックス*pszPropName*します。

*member*<br/>
指定されたプロパティ ページのコントロールに関連付けられたメンバー変数*id*で指定されたプロパティと*pszPropName*します。

*pszPropName*<br/>
指定されたリスト ボックスの文字列と交換されるコントロール プロパティのプロパティ名*id*します。

### <a name="remarks"></a>Remarks

この関数は、対応する前に呼び出す必要がある`DDX_LBString`関数呼び出し。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="ddp_lbstringexact"></a>  DDP_LBStringExact

プロパティ ページのこの関数を呼び出す`DoDataExchange`プロパティ ページでリスト ボックスの現在の選択を正確に一致する文字列プロパティの値を同期する関数。

```
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
ポインターを`CDataExchange`オブジェクト。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*ID*<br/>
リストのリソース ID で指定されたコントロール プロパティに関連付けられたコントロールのボックス*pszPropName*します。

*member*<br/>
指定されたプロパティ ページのコントロールに関連付けられたメンバー変数*id*で指定されたプロパティと*pszPropName*します。

*pszPropName*<br/>
指定されたリスト ボックスの文字列と交換されるコントロール プロパティのプロパティ名*id*します。

### <a name="remarks"></a>Remarks

この関数は、対応する前に呼び出す必要がある`DDX_LBStringExact`関数呼び出し。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="ddp_postprocessing"></a>  DDP_PostProcessing

プロパティ ページのこの関数を呼び出す`DoDataExchange`プロパティの値を保存しているときに、コントロールにプロパティ ページからプロパティ値の転送を完了する関数。

```
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
ポインターを`CDataExchange`オブジェクト。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

### <a name="remarks"></a>Remarks

すべてのデータ交換関数が完了した後は、この関数を呼び出す必要があります。 例:

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="ddp_radio"></a>  DDP_Radio

コントロールのこの関数を呼び出す`DoPropExchange`関連付けられているプロパティ ページのオプション ボタン コントロールとプロパティの値を同期する関数。

```
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
ポインターを`CDataExchange`オブジェクト。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*ID*<br/>
オプションのリソース ID で指定されたコントロール プロパティに関連付けられたコントロールのボタン*pszPropName*します。

*member*<br/>
指定されたプロパティ ページのコントロールに関連付けられたメンバー変数*id*で指定されたプロパティと*pszPropName*します。

*pszPropName*<br/>
指定されたラジオ ボタン コントロールと交換されるコントロール プロパティのプロパティ名*id*します。

### <a name="remarks"></a>Remarks

この関数は、対応する前に呼び出す必要がある`DDX_Radio`関数呼び出し。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="ddp_text"></a>  DDP_Text

コントロールのこの関数を呼び出す`DoDataExchange`と関連付けられているプロパティ ページのコントロール プロパティの値を同期する関数。

```
void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    BYTE & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    UINT & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    long & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    DWORD & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    float & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    double & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    CString & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
ポインターを`CDataExchange`オブジェクト。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*ID*<br/>
指定されたコントロール プロパティに関連付けられたコントロールのリソース ID *pszPropName*します。

*member*<br/>
指定されたプロパティ ページのコントロールに関連付けられたメンバー変数*id*で指定されたプロパティと*pszPropName*します。

*pszPropName*<br/>
指定されたコントロールと交換されるコントロール プロパティのプロパティ名*id*します。

### <a name="remarks"></a>Remarks

この関数は、対応する前に呼び出す必要がある`DDX_Text`関数呼び出し。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="begin_proppageids"></a>  BEGIN_PROPPAGEIDS

プロパティ ページ Id のコントロールのリストの定義を開始します。

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>パラメーター

*class_name*<br/>
プロパティのページが指定されているコントロール クラスの名前。

*count*<br/>
コントロールのクラスによって使用されるプロパティ ページの数。

### <a name="remarks"></a>Remarks

クラスのメンバー関数を定義する、実装 (.cpp) ファイルで BEGIN_PROPPAGEIDS マクロでは、プロパティ ページの一覧を起動しの各プロパティ ページ、マクロのエントリを追加し、後でプロパティ ページのリストを完了マクロ。

プロパティ ページの詳細については、記事を参照してください。 [ActiveX コントロール。プロパティ ページ](../../mfc/mfc-activex-controls-property-pages.md)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="end_proppageids"></a>  END_PROPPAGEIDS

プロパティ ページ ID のリストの定義を終了します。

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>パラメーター

*class_name*<br/>
プロパティ ページを所有するコントロール クラスの名前。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="proppageid"></a>  PROPPAGEID

OLE コントロールが使用するためのプロパティ ページを追加します。

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>パラメーター

*clsid*<br/>
プロパティ ページの一意のクラス ID。

### <a name="remarks"></a>Remarks

すべて PROPPAGEID マクロは、コントロールの実装ファイルのほか、END_PROPPAGEIDS マクロの間に配置する必要があります。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
