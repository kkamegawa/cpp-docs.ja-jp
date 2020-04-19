---
title: OLE コントロールのダイアログ データ エクスチェンジ (DDX) 関数
ms.date: 11/04/2016
f1_keywords:
- AFXDISP/DDX_OCBool
- AFXDISP/DDX_OCBoolRO
- AFXDISP/DDX_OCColor
- AFXDISP/DDX_OCColorRO
- AFXDISP/DDX_OCFloat
- AFXDISP/DDX_OCFloatRO
- AFXDISP/DDX_OCInt
- AFXDISP/DDX_OCIntRO
- AFXDISP/DDX_OCShort
- AFXDISP/DDX_OCShortRO
- AFXDISP/DDX_OCText
- AFXDISP/DDX_OCTextRO
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
ms.openlocfilehash: df96d44cefeb15d89653538c3006d109a97a21a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322567"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>OLE コントロールのダイアログ データ エクスチェンジ (DDX) 関数

このトピックでは、OLE コントロールのプロパティ ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのデータ メンバーとの間のデータを交換するために使用する DDX_OC 関数を使用します。

### <a name="ddx_oc-functions"></a>DDX_OC 関数

|||
|-|-|
|[DDX_OCBool](#ddx_ocbool)|転送を管理**BOOL** OLE コントロールのプロパティの間のデータと**BOOL**データ メンバー。|
|[DDX_OCBoolRO](#ddx_ocboolro)|転送を管理**BOOL** OLE コントロールの読み取り専用プロパティの間でデータと**BOOL**データ メンバー。|
|[DDX_OCColor](#ddx_occolor)|転送を管理**OLE_COLOR** OLE コントロールのプロパティの間のデータと**OLE_COLOR**データ メンバー。|
|[DDX_OCColorRO](#ddx_occolorro)|転送を管理**OLE_COLOR** OLE コントロールの読み取り専用プロパティの間でデータと**OLE_COLOR**データ メンバー。|
|[DDX_OCFloat](#ddx_ocfloat)|転送を管理**float** (または**double**) OLE コントロールのプロパティの間のデータと**float** (または**double**) データ メンバー。|
|[DDX_OCFloatRO](#ddx_ocfloatro)|転送を管理**float** (または**double**) OLE コントロールの読み取り専用プロパティの間でデータと**float** (または**double**) データメンバー。|
|[DDX_OCInt](#ddx_ocint)|転送を管理**int** (または**long**) OLE コントロールのプロパティの間のデータと**int** (または**long**) データ メンバー。|
|[DDX_OCIntRO](#ddx_ocintro)|転送を管理**int** (または**long**) OLE コントロールの読み取り専用プロパティの間でデータと**int** (または**long**) データ メンバー。|
|[DDX_OCShort](#ddx_ocshort)|転送を管理**short**OLE コントロールのプロパティの間のデータと**short**データ メンバー。|
|[DDX_OCShortRO](#ddx_ocshortro)|転送を管理**short**OLE コントロールの読み取り専用プロパティの間でデータと**short**データ メンバー。|
|[DDX_OCText](#ddx_octext)|転送を管理**CString** OLE コントロールのプロパティの間のデータと**CString**データ メンバー。|
|[DDX_OCTextRO](#ddx_octextro)|転送を管理**CString** OLE コントロールの読み取り専用プロパティの間でデータと**CString**データ メンバー。|

##  <a name="ddx_ocbool"></a>  DDX_OCBool

`DDX_OCBool`関数の転送を管理**BOOL**  ダイアログ ボックスでは、OLE コントロールのプロパティの間のデータ ビュー、またはコントロール ビュー オブジェクトのフォームと**BOOL**  ダイアログ ボックス、フォーム ビューのデータ メンバーまたはコントロール ビュー オブジェクト。

```
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトの OLE コントロールの ID。

*dispid*<br/>
コントロールのプロパティのディスパッチ ID。

*value*<br/>
データの交換相手になるダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのメンバー変数への参照。

### <a name="remarks"></a>Remarks

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー :** afxdisp.h

##  <a name="ddx_ocboolro"></a>  DDX_OCBoolRO

`DDX_OCBoolRO`関数の転送を管理**BOOL**  ダイアログ ボックスでは、OLE コントロールの読み取り専用プロパティの間でデータ ビュー、またはコントロール ビュー オブジェクトのフォームと**BOOL**のダイアログ ボックスで、データ メンバーフォーム ビュー、またはコントロール ビュー オブジェクト。

```
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトの OLE コントロールの ID。

*dispid*<br/>
コントロールのプロパティのディスパッチ ID。

*value*<br/>
データの交換相手になるダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのメンバー変数への参照。

### <a name="remarks"></a>Remarks

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="ddx_occolor"></a>  DDX_OCColor

`DDX_OCColor` OLE_COLOR データのプロパティ ダイアログ ボックスで、フォーム ビューでは、OLE コントロールの間の転送を管理またはコントロール ビュー オブジェクトと、ダイアログ ボックスの OLE_COLOR データ メンバーは、フォーム ビュー、またはコントロール ビュー オブジェクト。

```
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトの OLE コントロールの ID。

*dispid*<br/>
コントロールのプロパティのディスパッチ ID。

*value*<br/>
データの交換相手になるダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのメンバー変数への参照。

### <a name="remarks"></a>Remarks

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="ddx_occolorro"></a>  DDX_OCColorRO

`DDX_OCColorRO`関数は、ダイアログ ボックスで、フォーム ビューでは、OLE コントロールの読み取り専用プロパティ間の OLE_COLOR データの転送を管理またはコントロール ビュー オブジェクトと、ダイアログ ボックスの OLE_COLOR データ メンバーは、フォーム ビュー、またはコントロール ビュー オブジェクト。

```
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトの OLE コントロールの ID。

*dispid*<br/>
コントロールのプロパティのディスパッチ ID。

*value*<br/>
データの交換相手になるダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのメンバー変数への参照。

### <a name="remarks"></a>Remarks

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="ddx_ocfloat"></a>  DDX_OCFloat

`DDX_OCFloat`関数の転送を管理**float** (または**double**) ダイアログ ボックスでは、OLE コントロールのプロパティの間のデータ ビュー、またはコントロール ビュー オブジェクトのフォームと**float**(または**double**) ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのデータ メンバー。

```
void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトの OLE コントロールの ID。

*dispid*<br/>
コントロールのプロパティのディスパッチ ID。

*value*<br/>
データの交換相手になるダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのメンバー変数への参照。

### <a name="remarks"></a>Remarks

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="ddx_ocfloatro"></a>  DDX_OCFloatRO

`DDX_OCFloatRO`関数の転送を管理**float** (または**double**) ダイアログ ボックスでは、OLE コントロールの読み取り専用プロパティの間でデータ ビュー、またはコントロール ビュー オブジェクトのフォームと**float** (または**double**) ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのデータ メンバー。

```
void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    float& value);

void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    double& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトの OLE コントロールの ID。

*dispid*<br/>
コントロールのプロパティのディスパッチ ID。

*value*<br/>
データの交換相手になるダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのメンバー変数への参照。

### <a name="remarks"></a>Remarks

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="ddx_ocint"></a>  DDX_OCInt

`DDX_OCInt`関数の転送を管理**int** (または**long**) ダイアログ ボックスでは、OLE コントロールのプロパティの間のデータ ビュー、またはコントロール ビュー オブジェクトのフォームと**int**(または**long**) ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのデータ メンバー。

```
void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCInt(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトの OLE コントロールの ID。

*dispid*<br/>
コントロールのプロパティのディスパッチ ID。

*value*<br/>
データの交換相手になるダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのメンバー変数への参照。

### <a name="remarks"></a>Remarks

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="ddx_ocintro"></a>  DDX_OCIntRO

`DDX_OCIntRO`関数の転送を管理**int** (または**long**) ダイアログ ボックスでは、OLE コントロールの読み取り専用プロパティの間でデータ ビュー、またはコントロール ビュー オブジェクトのフォームと**int**(または**long**) ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのデータ メンバー。

```
void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    int& value);

void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    long& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトの OLE コントロールの ID。

*dispid*<br/>
コントロールのプロパティのディスパッチ ID。

*value*<br/>
データの交換相手になるダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのメンバー変数への参照。

### <a name="remarks"></a>Remarks

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="ddx_ocshort"></a>  DDX_OCShort

`DDX_OCShort`  ダイアログ ボックスで、フォーム ビューでは、OLE コントロールのプロパティの間の短いデータの転送を管理またはコントロール ビュー オブジェクトと、ダイアログ ボックスの短いデータ メンバーは、フォーム ビュー、またはコントロール ビュー オブジェクト。

```
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトの OLE コントロールの ID。

*dispid*<br/>
コントロールのプロパティのディスパッチ ID。

*value*<br/>
データの交換相手になるダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのメンバー変数への参照。

### <a name="remarks"></a>Remarks

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="ddx_ocshortro"></a>  DDX_OCShortRO

`DDX_OCShortRO`関数は、ダイアログ ボックスで、フォーム ビューでは、OLE コントロールの読み取り専用プロパティ間の短いデータの転送を管理またはコントロール ビュー オブジェクトと、ダイアログ ボックスの短いデータ メンバーは、フォーム ビュー、またはコントロール ビュー オブジェクト。

```
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトの OLE コントロールの ID。

*dispid*<br/>
コントロールのプロパティのディスパッチ ID。

*value*<br/>
データの交換相手になるダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのメンバー変数への参照。

### <a name="remarks"></a>Remarks

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="ddx_octext"></a>  DDX_OCText

**DDX_OCText**関数の転送を管理**CString**  ダイアログ ボックスでは、OLE コントロールのプロパティの間のデータ ビュー、またはコントロール ビュー オブジェクトのフォームと**CString**データダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのメンバーです。

```
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
ポインターを**CDataExchange**オブジェクト。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトの OLE コントロールの ID。

*dispid*<br/>
コントロールのプロパティのディスパッチ ID。

*value*<br/>
データの交換相手になるダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのメンバー変数への参照。

### <a name="remarks"></a>Remarks

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="ddx_octextro"></a>  DDX_OCTextRO

`DDX_OCTextRO` 関数は、ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトの OLE コントロールの読み取り専用プロパティと、ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトの `CString` データ メンバーの間の `CString` データ転送を管理します。

```
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*nIDC*<br/>
ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトの OLE コントロールの ID。

*dispid*<br/>
コントロールのプロパティのディスパッチ ID。

*value*<br/>
データの交換相手になるダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのメンバー変数への参照。

### <a name="remarks"></a>Remarks

DDX の詳細については、「 [ダイアログ データ エクスチェンジとダイアログ データ バリデーション](../../mfc/dialog-data-exchange-and-validation.md)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
