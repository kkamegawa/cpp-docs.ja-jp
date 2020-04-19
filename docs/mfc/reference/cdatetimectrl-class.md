---
title: Cdatetimectrl 使い方クラス
ms.date: 11/04/2016
f1_keywords:
- CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CloseMonthCal
- AFXDTCTL/CDateTimeCtrl::Create
- AFXDTCTL/CDateTimeCtrl::GetDateTimePickerInfo
- AFXDTCTL/CDateTimeCtrl::GetIdealSize
- AFXDTCTL/CDateTimeCtrl::GetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::GetMonthCalCtrl
- AFXDTCTL/CDateTimeCtrl::GetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::GetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::GetRange
- AFXDTCTL/CDateTimeCtrl::GetTime
- AFXDTCTL/CDateTimeCtrl::SetFormat
- AFXDTCTL/CDateTimeCtrl::SetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::SetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::SetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::SetRange
- AFXDTCTL/CDateTimeCtrl::SetTime
helpviewer_keywords:
- CDateTimeCtrl [MFC], CDateTimeCtrl
- CDateTimeCtrl [MFC], CloseMonthCal
- CDateTimeCtrl [MFC], Create
- CDateTimeCtrl [MFC], GetDateTimePickerInfo
- CDateTimeCtrl [MFC], GetIdealSize
- CDateTimeCtrl [MFC], GetMonthCalColor
- CDateTimeCtrl [MFC], GetMonthCalCtrl
- CDateTimeCtrl [MFC], GetMonthCalFont
- CDateTimeCtrl [MFC], GetMonthCalStyle
- CDateTimeCtrl [MFC], GetRange
- CDateTimeCtrl [MFC], GetTime
- CDateTimeCtrl [MFC], SetFormat
- CDateTimeCtrl [MFC], SetMonthCalColor
- CDateTimeCtrl [MFC], SetMonthCalFont
- CDateTimeCtrl [MFC], SetMonthCalStyle
- CDateTimeCtrl [MFC], SetRange
- CDateTimeCtrl [MFC], SetTime
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
ms.openlocfilehash: ec9060ba60c4d9877e5ee32bc68da0134f0ccf20
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506996"
---
# <a name="cdatetimectrl-class"></a>Cdatetimectrl 使い方クラス

日時指定コントロールの機能がカプセル化されています。

## <a name="syntax"></a>構文

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[Cdatetimectrl 使い方:: Cdatetimectrl 使い方](#cdatetimectrl)|`CDateTimeCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[Cdatetimectrl 使い方:: Close当月 Cal](#closemonthcal)|現在の日付と時刻の選択コントロールを閉じます。|
|[CDateTimeCtrl::Create](#create)|日付と時刻の選択コントロールを作成し、 `CDateTimeCtrl`オブジェクトにアタッチします。|
|[Cdatetimectrl 使い方:: GetDateTimePickerInfo](#getdatetimepickerinfo)|現在の日付と時刻の選択コントロールに関する情報を取得します。|
|[Cdatetimectrl 使い方:: GetIdealSize](#getidealsize)|現在の日付または時刻を表示するために必要な、日付と時刻の選択コントロールの理想的なサイズを返します。|
|[Cdatetimectrl 使い方:: GetMonthCalColor](#getmonthcalcolor)|日付と時刻の選択コントロール内の月間予定表の特定の部分の色を取得します。|
|[Cdatetimectrl 使い方:: GetMonthCalCtrl](#getmonthcalctrl)|日付と時刻の選択コントロールに関連付けられたオブジェクトを取得します。`CMonthCalCtrl`|
|[Cdatetimectrl 使い方:: GetMonthCalFont](#getmonthcalfont)|日付と時刻の選択コントロールの子月間予定表コントロールで現在使用されているフォントを取得します。|
|[Cdatetimectrl 使い方:: GetMonthCalStyle](#getmonthcalstyle)|現在の日付と時刻の選択コントロールのスタイルを取得します。|
|[CDateTimeCtrl::GetRange](#getrange)|日付と時刻の選択コントロールで許容される現在の最小値と最大システム時刻を取得します。|
|[CDateTimeCtrl::GetTime](#gettime)|日付と時刻の選択コントロールから現在選択されている時刻を取得し、 `SYSTEMTIME`指定した構造体に格納します。|
|[Cdatetimectrl 使い方:: SetFormat](#setformat)|指定された書式指定文字列に従って、日付と時刻の選択コントロールの表示を設定します。|
|[Cdatetimectrl 使い方:: SetMonthCalColor](#setmonthcalcolor)|日付と時刻の選択コントロール内の月間予定表の特定の部分の色を設定します。|
|[Cdatetimectrl 使い方:: SetMonthCalFont](#setmonthcalfont)|日付と時刻の選択コントロールの子の月間予定表コントロールが使用するフォントを設定します。|
|[Cdatetimectrl 使い方:: SetMonthCalStyle](#setmonthcalstyle)|現在の日付と時刻の選択コントロールのスタイルを設定します。|
|[CDateTimeCtrl::SetRange](#setrange)|日付と時刻の選択コントロールに許容されるシステム時間の最小値と最大値を設定します。|
|[Cdatetimectrl 使い方:: SetTime](#settime)|日時指定コントロールの時刻を設定します。|

## <a name="remarks"></a>Remarks

日付と時刻の選択コントロール (DTP コントロール) は、ユーザーとの日付と時刻の情報を交換するための簡単なインターフェイスを提供します。 このインターフェイスには、コントロールに格納されている日付と時刻の情報の一部を表示するフィールドが含まれています。 ユーザーは、指定されたフィールド内の文字列の内容を変更することによって、コントロールに格納されている情報を変更できます。 ユーザーは、マウスまたはキーボードを使用してフィールド間を移動できます。

日付と時刻の選択コントロールをカスタマイズするには、作成時にオブジェクトにさまざまなスタイルを適用します。 日付と時刻の選択コントロールに固有のスタイルの詳細については、Windows SDK の「[日付と時刻の選択コントロールスタイル](/windows/win32/Controls/date-and-time-picker-control-styles)」を参照してください。 書式スタイルを使用して、DTP コントロールの表示形式を設定できます。 これらの書式スタイルについては、Windows SDK トピックの[日付と時刻の選択コントロールスタイル](/windows/win32/Controls/date-and-time-picker-control-styles)の「書式スタイル」で説明されています。

日付と時刻の選択コントロールは、「 [cdatetimectrl 使い方の使用](../../mfc/using-cdatetimectrl.md)」で説明されている通知とコールバックも使用します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdtctl

##  <a name="cdatetimectrl"></a>  CDateTimeCtrl::CDateTimeCtrl

`CDateTimeCtrl` オブジェクトを構築します。

```
CDateTimeCtrl();
```

##  <a name="closemonthcal"></a>Cdatetimectrl 使い方:: Close当月 Cal

現在の日付と時刻の選択コントロールを閉じます。

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[DTM_CLOSEMONTHCAL](/windows/win32/Controls/dtm-closemonthcal)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、 *m_dateTimeCtrl*変数を定義しています。この変数は、[日時指定コントロール] コントロールにプログラムでアクセスするために使用されます。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>例

次のコード例では、現在の日付と時刻の選択コントロールのドロップダウンカレンダーを閉じます。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

##  <a name="create"></a>  CDateTimeCtrl::Create

日付と時刻の選択コントロールを作成し、 `CDateTimeCtrl`オブジェクトにアタッチします。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
日付と時刻のコントロールスタイルの組み合わせを指定します。 日付と時刻の選択のスタイルの詳細については、Windows SDK の「[日付と時刻の選択コントロールスタイル](/windows/win32/Controls/date-and-time-picker-control-styles)」を参照してください。

*rect*<br/>
日付と時刻の選択コントロールの位置とサイズである[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。

*pParentWnd*<br/>
日付と時刻の選択コントロールの親ウィンドウである[CWnd](../../mfc/reference/cwnd-class.md)オブジェクトへのポインター。 NULL にすることはできません。

*nID*<br/>
日付と時刻の選択コントロールのコントロール ID を指定します。

### <a name="return-value"></a>戻り値

作成が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

##### <a name="to-create-a-date-and-time-picker-control"></a>日付と時刻の選択コントロールを作成するには

1. [Cdatetimectrl 使い方](#cdatetimectrl)を呼び出して、 `CDateTimeCtrl`オブジェクトを構築します。

1. このメンバー関数を呼び出します。これにより、Windows の日付と時刻の選択コントロール`CDateTimeCtrl`が作成され、オブジェクトにアタッチされます。

を呼び出す`Create`と、コモンコントロールが初期化されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

##  <a name="getdatetimepickerinfo"></a>  CDateTimeCtrl::GetDateTimePickerInfo

現在の日付と時刻の選択コントロールに関する情報を取得します。

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pDateTimePickerInfo*|入出力現在の日付と時刻の選択コントロールの説明を受け取る[DATETIMEPICKERINFO](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo)構造体へのポインター。<br /><br /> 呼び出し元は、この構造体の割り当てを行います。 ただし、このメソッドは、構造体の*cbSize*メンバーを初期化します。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[DTM_GETDATETIMEPICKERINFO](/windows/win32/Controls/dtm-getdatetimepickerinfo)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、 *m_dateTimeCtrl*変数を定義しています。この変数は、[日時指定コントロール] コントロールにプログラムでアクセスするために使用されます。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>例

次のコード例では、現在の日時指定コントロールに関する情報が正常に取得されたかどうかを示します。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

##  <a name="getmonthcalcolor"></a>Cdatetimectrl 使い方:: GetMonthCalColor

日付と時刻の選択コントロール内の月間予定表の特定の部分の色を取得します。

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>パラメーター

*iColor*<br/>
取得する月のカレンダーの色領域を指定する**整数**値。 値の一覧については、 [SetMonthCalColor](#setmonthcalcolor)の*iColor*パラメーターを参照してください。

### <a name="return-value"></a>戻り値

正常終了した場合は、月間予定表コントロールの指定した部分の色設定を表す COLORREF 値。 関数は、失敗した場合は-1 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [DTM_GETMCCOLOR](/windows/win32/Controls/dtm-getmccolor)の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

##  <a name="getmonthcalctrl"></a>Cdatetimectrl 使い方:: GetMonthCalCtrl

日付と時刻の選択コントロールに関連付けられたオブジェクトを取得します。`CMonthCalCtrl`

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>戻り値

[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)オブジェクトへのポインター。失敗した場合は NULL、ウィンドウが表示されていない場合は NULL。

### <a name="remarks"></a>Remarks

日付と時刻の選択コントロールユーザーがドロップダウン矢印をクリックしたときに、月間予定表の子コントロールが作成されます。 `CMonthCalCtrl`オブジェクトが不要になった場合は破棄されるため、アプリケーションは、日付と時刻の選択コントロールの子月カレンダーを表すオブジェクトの格納に依存しないようにする必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

##  <a name="getmonthcalfont"></a>  CDateTimeCtrl::GetMonthCalFont

日付と時刻の選択コントロールの月間予定表コントロールで現在使用されているフォントを取得します。

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>戻り値

[CFont](../../mfc/reference/cfont-class.md)オブジェクトへのポインター。失敗した場合は NULL。

### <a name="remarks"></a>Remarks

戻り値が指すオブジェクトは一時オブジェクトであり、次のアイドル処理時に破棄されます。`CFont`

##  <a name="getmonthcalstyle"></a>Cdatetimectrl 使い方:: GetMonthCalStyle

現在の日付と時刻の選択コントロールに関連付けられているドロップダウン月間予定表コントロールのスタイルを取得します。

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>戻り値

ドロップダウン月間予定表コントロールのスタイル。日付と時刻の選択コントロールスタイルのビットごとの組み合わせ (または) です。 詳細については、「[月間予定表コントロールスタイル](/windows/win32/Controls/month-calendar-control-styles)」を参照してください。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[DTM_GETMCSTYLE](/windows/win32/Controls/dtm-getmcstyle)メッセージを送信します。

##  <a name="getrange"></a>  CDateTimeCtrl::GetRange

日付と時刻の選択コントロールで許容される現在の最小値と最大システム時刻を取得します。

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;
```

### <a name="parameters"></a>パラメーター

*pMinRange*<br/>
オブジェクト`CDateTimeCtrl`で許可されている最も早い時刻を格納している、 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトまたは[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへのポインター。

*pMaxRange*<br/>
オブジェクトへのポインター `COleDateTime` 、 `CTime`またはオブジェクト内で`CDateTimeCtrl`許可されている最新の時間を格納しているオブジェクトへのポインター。

### <a name="return-value"></a>戻り値

どの範囲が設定されているかを示すフラグを含む DWORD 値です。 If

`return value & GDTR_MAX` == 0

次に、2番目のパラメーターが有効になります。 同様に、

`return value & GDTR_MIN` == 0

次に、最初のパラメーターが有効になります。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [DTM_GETRANGE](/windows/win32/Controls/dtm-getrange)の動作を実装します。 MFC の実装では、または`COleDateTime` `CTime`のいずれかを指定できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

##  <a name="gettime"></a>  CDateTimeCtrl::GetTime

日付と時刻の選択コントロールから現在選択されている時刻を取得し、 `SYSTEMTIME`指定した構造体に格納します。

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>パラメーター

*timeDest*<br/>
最初のバージョンでは、システム時刻情報を受け取る[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトへの参照。 2番目のバージョンでは、システム時刻情報を受け取る[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへの参照。

*pTimeDest*<br/>
システム時刻情報を受け取る[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。 NULL にすることはできません。

### <a name="return-value"></a>戻り値

最初のバージョンでは、時刻が`COleDateTime`オブジェクトに正常に書き込まれた場合は0以外の場合は0。それ以外の場合は0。 2番目と3番目のバージョンでは、 [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)構造体の*dwflag*メンバーセットと同じ DWORD 値が設定されています。 詳細については、後述の「**解説**」を参照してください。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime)の動作を実装します。 の`GetTime`MFC 実装では、クラスまたは`COleDateTime` `CTime`クラスを使用するか、 `SYSTEMTIME`構造体を使用して時刻情報を格納できます。

上記の2番目と3番目のバージョンの戻り値 DWORD は、 [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) structure メンバーの*dwFlags*に示されているように、日付と時刻の選択コントロールが "日付なし" の状態に設定されているかどうかを示します。 返される値が GDT_NONE の場合、コントロールは "no date" 状態に設定され、DTS_SHOWNONE スタイルを使用します。 返される値が GDT_VALID の場合は、システム時刻がコピー先の場所に正常に格納されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

##  <a name="getidealsize"></a>  CDateTimeCtrl::GetIdealSize

現在の日付または時刻を表示するために必要な、日付と時刻の選択コントロールの理想的なサイズを返します。

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*psize*|入出力コントロールの理想的なサイズを格納している[サイズ](/windows/win32/api/windef/ns-windef-size)構造体へのポインター。|

### <a name="return-value"></a>戻り値

戻り値は常に TRUE です。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[DTM_GETIDEALSIZE](/windows/win32/Controls/dtm-getidealsize)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、 *m_dateTimeCtrl*変数を定義しています。この変数は、[日時指定コントロール] コントロールにプログラムでアクセスするために使用されます。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>例

次のコード例では、日付と時刻の選択コントロールを表示するのに最適なサイズを取得します。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

##  <a name="setformat"></a>  CDateTimeCtrl::SetFormat

指定された書式指定文字列に従って、日付と時刻の選択コントロールの表示を設定します。

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>パラメーター

*pstrFormat*<br/>
目的の表示を定義する、0で終わる書式指定文字列へのポインター。 このパラメーターを NULL に設定すると、コントロールが現在のスタイルの既定の書式設定文字列にリセットされます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

> [!NOTE]
>  ユーザー入力では、この呼び出しの成功または失敗は判断されません。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat)の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

##  <a name="setmonthcalcolor"></a>Cdatetimectrl 使い方:: SetMonthCalColor

日付と時刻の選択コントロール内の月間予定表の特定の部分の色を設定します。

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>パラメーター

*iColor*<br/>
設定する月間予定表コントロールの領域を指定する**int**値。 この値には、次のいずれかを指定できます。

|[値]|説明|
|-----------|-------------|
|MCSC_BACKGROUND|月の間に表示される背景色を設定します。|
|MCSC_MONTHBK|月内に表示される背景色を設定します。|
|MCSC_TEXT|月内のテキストの表示に使用する色を設定します。|
|MCSC_TITLEBK|予定表のタイトルに表示される背景色を設定します。|
|MCSC_TITLETEXT|カレンダーのタイトル内のテキストの表示に使用する色を設定します。|
|MCSC_TRAILINGTEXT|ヘッダーと末尾のテキストの表示に使用する色を設定します。 ヘッダーと末尾の日付は、現在の暦に表示される前と後の月の日付です。|

*ref*<br/>
月間予定表の指定した領域に対して設定される色を表す COLORREF 値。

### <a name="return-value"></a>戻り値

正常終了した場合に、月間予定表コントロールの指定した部分の前の色設定を表す COLORREF 値。 それ以外の場合、メッセージは-1 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [DTM_SETMCCOLOR](/windows/win32/Controls/dtm-setmccolor)の動作を実装します。

### <a name="example"></a>例

  [Cdatetimectrl 使い方:: GetMonthCalColor](#getmonthcalcolor)の例を参照してください。

##  <a name="setmonthcalfont"></a>  CDateTimeCtrl::SetMonthCalFont

日付と時刻の選択コントロールの子の月間予定表コントロールが使用するフォントを設定します。

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>パラメーター

*hFont*<br/>
設定されるフォントを処理します。

*より描画*<br/>
フォントの設定時にコントロールをすぐに再描画するかどうかを指定します。 このパラメーターを TRUE に設定すると、コントロール自体が再描画されます。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont)の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
>  このコードを使用する場合は、 `CDialog` *m_MonthFont*型`CFont`の派生クラスのメンバーを作成することをお勧めします。

##  <a name="setmonthcalstyle"></a>Cdatetimectrl 使い方:: SetMonthCalStyle

現在の日付と時刻の選択コントロールに関連付けられているドロップダウンの月間予定表コントロールのスタイルを設定します。

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*dwStyle*|からMonth calendar コントロールスタイルのビットごとの組み合わせである、新しい月間予定表コントロールスタイル。 詳細については、「[月間予定表コントロールスタイル](/windows/win32/Controls/month-calendar-control-styles)」を参照してください。|

### <a name="return-value"></a>戻り値

ドロップダウン月間予定表コントロールの以前のスタイル。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[DTM_SETMCSTYLE](/windows/win32/Controls/dtm-setmcstyle)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、 *m_dateTimeCtrl*変数を定義しています。この変数は、[日時指定コントロール] コントロールにプログラムでアクセスするために使用されます。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>例

次のコード例では、日付と時刻の選択コントロールを設定して、週の番号、曜日の省略名、および今日のインジケーターを表示しないようにします。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

##  <a name="setrange"></a>  CDateTimeCtrl::SetRange

日付と時刻の選択コントロールに許容されるシステム時間の最小値と最大値を設定します。

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);
```

### <a name="parameters"></a>パラメーター

*pMinRange*<br/>
オブジェクト`CDateTimeCtrl`で許可されている最も早い時刻を格納している、 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトまたは[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへのポインター。

*pMaxRange*<br/>
オブジェクトへのポインター `COleDateTime` 、 `CTime`またはオブジェクト内で`CDateTimeCtrl`許可されている最新の時間を格納しているオブジェクトへのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [DTM_SETRANGE](/windows/win32/Controls/dtm-setrange)の動作を実装します。 MFC の実装では、または`COleDateTime` `CTime`のいずれかを指定できます。 オブジェクトの`COleDateTime`状態が NULL の場合は、範囲が削除されます。 `CTime`ポインターまたはポインターがNULLの場合、範囲は`COleDateTime`削除されます。

### <a name="example"></a>例

  [Cdatetimectrl 使い方:: GetRange](#getrange)の例を参照してください。

##  <a name="settime"></a>  CDateTimeCtrl::SetTime

日時指定コントロールの時刻を設定します。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>パラメーター

*timeNew*<br/>
コントロールが設定されるを格納する[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトへの参照。

*pTimeNew*<br/>
上記の2番目のバージョンでは、コントロールが設定される時間を含む[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへのポインターです。 上記の3番目のバージョンでは、コントロールが設定される時刻を含む[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime)の動作を実装します。 の`SetTime`MFC 実装で`COleDateTime`は、クラスまたは`CTime`クラスを使用するか、 `SYSTEMTIME`構造体を使用して時刻情報を設定できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>関連項目

[MFC のサンプル CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl クラス](../../mfc/reference/cmonthcalctrl-class.md)
