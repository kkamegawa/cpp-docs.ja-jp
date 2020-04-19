---
title: 標準的なダイアログ データ検証ルーチン
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 77b08945c99b9e9e2652a40e5710d8c4e89846b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309994"
---
# <a name="standard-dialog-data-validation-routines"></a>標準的なダイアログ データ検証ルーチン

このトピックでは、共通の MFC ダイアログ コントロールの使用される標準的なダイアログ データ検証 (DDV) ルーチンを使用します。

> [!NOTE]
>  標準的なダイアログ データ エクス チェンジ ルーチンは、ヘッダー ファイル afxdd_.h で定義されます。 ただし、アプリケーションでは、afxwin.h を含める必要があります。

### <a name="ddv-functions"></a>DDV 関数

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|指定されたコントロール値の文字の数が、指定された最大を超えていないことを確認します。|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|指定されたコントロール値を超えていないことを確認、指定された**バイト**範囲。|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|指定されたコントロール値が指定された時間範囲を超えないことを確認します。|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|指定されたコントロール値を超えていないことを確認、指定された**double**範囲。|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|指定されたコントロール値を超えていないことを確認、指定された**DWORD**範囲。|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|指定されたコントロール値を超えていないことを確認、指定された**float**範囲。|
|[DDV_MinMaxInt](#ddv_minmaxint)|指定されたコントロール値を超えていないことを確認、指定された**int**範囲。|
|[DDV_MinMaxLong](#ddv_minmaxlong)|指定されたコントロール値を超えていないことを確認、指定された**long**範囲。|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|指定されたコントロール値を超えていないことを確認、指定された**LONGLONG**範囲。|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|指定されたコントロール値が指定した日付範囲を超えていないことを確認します。|
|[DDV_MinMaxShort](#ddv_minmaxshort)|指定されたコントロール値を超えていないことを確認、指定された**short**範囲。|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|特定のスライダー コントロールの値が指定された範囲内にあることを確認します。|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|指定されたコントロール値を超えていないことを確認、指定された**UINT**範囲。|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|指定されたコントロール値がある 2 つの指定した値を確認します。|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|指定されたコントロール値を超えていないことを確認、指定された**ULONGLONG**範囲。|

##  <a name="ddv_maxchars"></a>  DDV_MaxChars

呼び出す`DDV_MaxChars`コントロール内の文字の量に関連付けられていることを確認する*値*超えない*文字数*します。

```
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*value*<br/>
ダイアログ ボックス、フォーム ビュー、またはデータを検証するコントロール ビュー オブジェクトのメンバー変数への参照。

*文字数*<br/>
使用できる文字の最大数。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdd_.h

##  <a name="ddv_minmaxbyte"></a>  DDV_MinMaxByte

呼び出す`DDV_MinMaxByte`にコントロールの値が関連付けられていることを確認する*値*間*minVal*と*maxVal*します。

```
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*value*<br/>
ダイアログ ボックス、フォーム ビュー、またはデータを検証するコントロール ビュー オブジェクトのメンバー変数への参照。

*minVal*<br/>
(型バイト) の最小値。

*maxVal*<br/>
(型バイト) の最大値。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdd_.h

##  <a name="ddv_minmaxdatetime"></a>  DDV_MinMaxDateTime

呼び出す`DDV_MinMaxDateTime`日付と時刻の選択で日付/時刻値が制御することを確認する ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) に関連付けられている*refValue*間*refMinRange*と*refMaxRange*します。

```
void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
ポインターを[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクト。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。 このオブジェクトを削除する必要はありません。

*refValue*<br/>
参照を[CTime](../../atl-mfc-shared/reference/ctime-class.md)または[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)  ダイアログ ボックス、フォーム ビュー、またはコントロール ビュー オブジェクトのメンバー変数に関連付けられているオブジェクト。 このオブジェクトには、検証するデータが含まれています。

*refMinRange*<br/>
最小許容値の日付/時刻。

*refMaxRange*<br/>
許容される最大の日付/時刻値。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdd_.h

##  <a name="ddv_minmaxdouble"></a>  DDV_MinMaxDouble

呼び出す`DDV_MinMaxDouble`にコントロールの値が関連付けられていることを確認する*値*間*minVal*と*maxVal*します。

```
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*value*<br/>
ダイアログ ボックス、フォーム ビュー、またはデータを検証するコントロール ビュー オブジェクトのメンバー変数への参照。

*minVal*<br/>
最小値 (型の**double**) 許可します。

*maxVal*<br/>
最大値 (型の**double**) 許可します。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdd_.h

##  <a name="ddv_minmaxdword"></a>  DDV_MinMaxDWord

呼び出す`DDV_MinMaxDWord`にコントロールの値が関連付けられていることを確認する*値*間*minVal*と*maxVal*します。

```
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*value*<br/>
ダイアログ ボックス、フォーム ビュー、またはデータを検証するコントロール ビュー オブジェクトのメンバー変数への参照。

*minVal*<br/>
(DWORD 型) の最小値。

*maxVal*<br/>
(DWORD 型) の最大値。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdd_.h

##  <a name="ddv_minmaxfloat"></a>  DDV_MinMaxFloat

呼び出す`DDV_MinMaxFloat`にコントロールの値が関連付けられていることを確認する*値*間*minVal*と*maxVal*します。

```
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*value*<br/>
ダイアログ ボックス、フォーム ビュー、またはデータを検証するコントロール ビュー オブジェクトのメンバー変数への参照。

*minVal*<br/>
最小値 (型の**float**) 許可します。

*maxVal*<br/>
最大値 (型の**float**) 許可します。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdd_.h

##  <a name="ddv_minmaxint"></a>  DDV_MinMaxInt

呼び出す`DDV_MinMaxInt`にコントロールの値が関連付けられていることを確認する*値*間*minVal*と*maxVal*します。

```
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*value*<br/>
ダイアログ ボックス、フォーム ビュー、またはデータを検証するコントロール ビュー オブジェクトのメンバー変数への参照。

*minVal*<br/>
最小値 (型の**int**) 許可します。

*maxVal*<br/>
最大値 (型の**int**) 許可します。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdd_.h

##  <a name="ddv_minmaxlong"></a>  DDV_MinMaxLong

呼び出す`DDV_MinMaxLong`にコントロールの値が関連付けられていることを確認する*値*間*minVal*と*maxVal*します。

```
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*value*<br/>
ダイアログ ボックス、フォーム ビュー、またはデータを検証するコントロール ビュー オブジェクトのメンバー変数への参照。

*minVal*<br/>
最小値 (型の**long**) 許可します。

*maxVal*<br/>
最大値 (型の**long**) 許可します。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdd_.h

##  <a name="ddv_minmaxlonglong"></a>  DDV_MinMaxLongLong

呼び出す`DDV_MinMaxLongLong`にコントロールの値が関連付けられていることを確認する*値*間*minVal*と*maxVal*します。

```
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*value*<br/>
ダイアログ ボックス、フォーム ビュー、またはデータを検証するコントロール ビュー オブジェクトのメンバー変数への参照。

*minVal*<br/>
(型 LONGLONG) の最小値。

*maxVal*<br/>
(型 LONGLONG) の最大値。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdd_.h

##  <a name="ddv_minmaxmonth"></a>  DDV_MinMaxMonth

呼び出す`DDV_MinMaxMonth`か月カレンダーで日付/時刻値が制御することを確認する ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) に関連付けられている*refValue*間*refMinRange*と*refMaxRange*します。

```
void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
ポインターを[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクト。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*refValue*<br/>
型のオブジェクトへの参照を`CTime`または`COleDateTime` ダイアログ ボックスのメンバー変数に関連付けられている、フォーム ビュー、またはコントロール ビュー オブジェクト。 このオブジェクトには、検証するデータが含まれています。 これは、ときに参照 MFC パス`DDV_MinMaxMonth`が呼び出されます。

*refMinRange*<br/>
最小許容値の日付/時刻。

*refMaxRange*<br/>
許容される最大の日付/時刻値。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdd_.h

##  <a name="ddv_minmaxshort"></a>  DDV_MinMaxShort

呼び出す`DDV_MinMaxShort`にコントロールの値が関連付けられていることを確認する*値*間*minVal*と*maxVal*します。

```
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*value*<br/>
ダイアログ ボックス、フォーム ビュー、またはデータを検証するコントロール ビュー オブジェクトのメンバー変数への参照。

*minVal*<br/>
最小値 (型の**short**) 許可します。

*maxVal*<br/>
最大値 (型の**short**) 許可します。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdd_.h

##  <a name="ddv_minmaxslider"></a>  DDV_MinMaxSlider

呼び出す`DDV_MinMaxSlider`にコントロールの値が関連付けられていることを確認する*値*間*minVal*と*maxVal*します。

```
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
ポインターを[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクト。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*value*<br/>
検証する値への参照。 このパラメーターを保持またはスライダー コントロールのつまみの現在の位置を設定します。

*minVal*<br/>
許容される最小値。

*maxVal*<br/>
許容される最大値。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)です。 スライダー コントロールの概要については、次を参照してください。[を使用して CSliderCtrl](../../mfc/using-csliderctrl.md)します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdd_.h

##  <a name="ddv_minmaxuint"></a>  DDV_MinMaxUInt

呼び出す`DDV_MinMaxUInt`にコントロールの値が関連付けられていることを確認する*値*間*minVal*と*maxVal*します。

```
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*value*<br/>
ダイアログ ボックス、フォーム ビュー、またはデータを検証するコントロール ビュー オブジェクトのメンバー変数への参照。

*minVal*<br/>
(UINT 型) の最小値。

*maxVal*<br/>
(UINT 型) の最大値。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdd_.h

##  <a name="ddv_minmaxulonglong"></a>  DDV_MinMaxULongLong

呼び出す`DDV_MinMaxULongLong`にコントロールの値が関連付けられていることを確認する*値*間*minVal*と*maxVal*します。

```
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*value*<br/>
ダイアログ ボックス、フォーム ビュー、またはデータを検証するコントロール ビュー オブジェクトのメンバー変数への参照。

*minVal*<br/>
(型 ULONGLONG) の最小値。

*maxVal*<br/>
(型 ULONGLONG) の最大値。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../../mfc/dialog-data-exchange-and-validation.md)です。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdd_.h

## <a name="ddv_minmaxunsigned"></a>DDV_MinMaxUnsigned

呼び出す`DDV_MinMaxUnsigned`にコントロールの値が関連付けられていることを確認する*値*間*minVal*と*maxVal*します。

### <a name="syntax"></a>構文

```
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
`CDataExchange` オブジェクトへのポインター。 フレームワークは、データ交換のコンテキスト (交換方向を含みます) を確定するためにこのオブジェクトを提供します。

*value*<br/>
ダイアログ ボックス、フォーム ビュー、またはデータを検証するコントロール ビュー オブジェクトのメンバー変数への参照。

*minVal*<br/>
最小値 (型の**符号なし**) 許可します。

*maxVal*<br/>
最大値 (型の**符号なし**) 許可します。

### <a name="remarks"></a>Remarks

DDV の詳細については、次を参照してください。[ダイアログ データ エクス チェンジと検証](../dialog-data-exchange-and-validation.md)です。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxdd_.h

## <a name="see-also"></a>関連項目

[標準的なダイアログ データ エクスチェンジ ルーチン](standard-dialog-data-exchange-routines.md)<br/>
[マクロとグローバル](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
