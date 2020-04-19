---
title: CMonthCalCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::Create
- AFXDTCTL/CMonthCalCtrl::GetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::GetCalendarCount
- AFXDTCTL/CMonthCalCtrl::GetCalendarGridInfo
- AFXDTCTL/CMonthCalCtrl::GetCalID
- AFXDTCTL/CMonthCalCtrl::GetColor
- AFXDTCTL/CMonthCalCtrl::GetCurrentView
- AFXDTCTL/CMonthCalCtrl::GetCurSel
- AFXDTCTL/CMonthCalCtrl::GetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::GetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::GetMaxTodayWidth
- AFXDTCTL/CMonthCalCtrl::GetMinReqRect
- AFXDTCTL/CMonthCalCtrl::GetMonthDelta
- AFXDTCTL/CMonthCalCtrl::GetMonthRange
- AFXDTCTL/CMonthCalCtrl::GetRange
- AFXDTCTL/CMonthCalCtrl::GetSelRange
- AFXDTCTL/CMonthCalCtrl::GetToday
- AFXDTCTL/CMonthCalCtrl::HitTest
- AFXDTCTL/CMonthCalCtrl::IsCenturyView
- AFXDTCTL/CMonthCalCtrl::IsDecadeView
- AFXDTCTL/CMonthCalCtrl::IsMonthView
- AFXDTCTL/CMonthCalCtrl::IsYearView
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorderDefault
- AFXDTCTL/CMonthCalCtrl::SetCalID
- AFXDTCTL/CMonthCalCtrl::SetCenturyView
- AFXDTCTL/CMonthCalCtrl::SetColor
- AFXDTCTL/CMonthCalCtrl::SetCurrentView
- AFXDTCTL/CMonthCalCtrl::SetCurSel
- AFXDTCTL/CMonthCalCtrl::SetDayState
- AFXDTCTL/CMonthCalCtrl::SetDecadeView
- AFXDTCTL/CMonthCalCtrl::SetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::SetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::SetMonthDelta
- AFXDTCTL/CMonthCalCtrl::SetMonthView
- AFXDTCTL/CMonthCalCtrl::SetRange
- AFXDTCTL/CMonthCalCtrl::SetSelRange
- AFXDTCTL/CMonthCalCtrl::SetToday
- AFXDTCTL/CMonthCalCtrl::SetYearView
- AFXDTCTL/CMonthCalCtrl::SizeMinReq
- AFXDTCTL/CMonthCalCtrl::SizeRectToMin
helpviewer_keywords:
- CMonthCalCtrl [MFC], CMonthCalCtrl
- CMonthCalCtrl [MFC], Create
- CMonthCalCtrl [MFC], GetCalendarBorder
- CMonthCalCtrl [MFC], GetCalendarCount
- CMonthCalCtrl [MFC], GetCalendarGridInfo
- CMonthCalCtrl [MFC], GetCalID
- CMonthCalCtrl [MFC], GetColor
- CMonthCalCtrl [MFC], GetCurrentView
- CMonthCalCtrl [MFC], GetCurSel
- CMonthCalCtrl [MFC], GetFirstDayOfWeek
- CMonthCalCtrl [MFC], GetMaxSelCount
- CMonthCalCtrl [MFC], GetMaxTodayWidth
- CMonthCalCtrl [MFC], GetMinReqRect
- CMonthCalCtrl [MFC], GetMonthDelta
- CMonthCalCtrl [MFC], GetMonthRange
- CMonthCalCtrl [MFC], GetRange
- CMonthCalCtrl [MFC], GetSelRange
- CMonthCalCtrl [MFC], GetToday
- CMonthCalCtrl [MFC], HitTest
- CMonthCalCtrl [MFC], IsCenturyView
- CMonthCalCtrl [MFC], IsDecadeView
- CMonthCalCtrl [MFC], IsMonthView
- CMonthCalCtrl [MFC], IsYearView
- CMonthCalCtrl [MFC], SetCalendarBorder
- CMonthCalCtrl [MFC], SetCalendarBorderDefault
- CMonthCalCtrl [MFC], SetCalID
- CMonthCalCtrl [MFC], SetCenturyView
- CMonthCalCtrl [MFC], SetColor
- CMonthCalCtrl [MFC], SetCurrentView
- CMonthCalCtrl [MFC], SetCurSel
- CMonthCalCtrl [MFC], SetDayState
- CMonthCalCtrl [MFC], SetDecadeView
- CMonthCalCtrl [MFC], SetFirstDayOfWeek
- CMonthCalCtrl [MFC], SetMaxSelCount
- CMonthCalCtrl [MFC], SetMonthDelta
- CMonthCalCtrl [MFC], SetMonthView
- CMonthCalCtrl [MFC], SetRange
- CMonthCalCtrl [MFC], SetSelRange
- CMonthCalCtrl [MFC], SetToday
- CMonthCalCtrl [MFC], SetYearView
- CMonthCalCtrl [MFC], SizeMinReq
- CMonthCalCtrl [MFC], SizeRectToMin
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
ms.openlocfilehash: 963aecfed4f6eb67a0ab227df06fce98c0778f7f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504559"
---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl クラス

月間予定表コントロールの機能がカプセル化されています。

## <a name="syntax"></a>構文

```
class CMonthCalCtrl : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMonthCalCtrl:: CMonthCalCtrl](#cmonthcalctrl)|`CMonthCalCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMonthCalCtrl:: Create](#create)|月間予定表コントロールを作成し、 `CMonthCalCtrl`オブジェクトにアタッチします。|
|[CMonthCalCtrl:: GetCalendarBorder](#getcalendarborder)|現在の月間予定表コントロールの境界線の幅を取得します。|
|[CMonthCalCtrl:: GetCalendarCount](#getcalendarcount)|現在の月間予定表コントロールに表示されるカレンダーの数を取得します。|
|[CMonthCalCtrl:: GetCalendarGridInfo](#getcalendargridinfo)|現在の月間予定表コントロールに関する情報を取得します。|
|[CMonthCalCtrl:: GetCalID](#getcalid)|現在の月間予定表コントロールのカレンダー識別子を取得します。|
|[CMonthCalCtrl:: GetColor](#getcolor)|月間予定表コントロールの指定された領域の色を取得します。|
|[CMonthCalCtrl:: GetCurrentView](#getcurrentview)|現在の月間予定表コントロールによって現在表示されているビューを取得します。|
|[CMonthCalCtrl:: GetCurSel](#getcursel)|現在選択されている日付によって示されるシステム時刻を取得します。|
|[CMonthCalCtrl:: GetFirstDayOfWeek](#getfirstdayofweek)|カレンダーの左端の列に表示される週の最初の曜日を取得します。|
|[CMonthCalCtrl:: GetMaxSelCount](#getmaxselcount)|月間予定表コントロールで選択できる現在の最大日数を取得します。|
|[CMonthCalCtrl:: GetMaxTodayWidth](#getmaxtodaywidth)|現在の月間予定表コントロールの "今日" の文字列の最大の幅を取得します。|
|[CMonthCalCtrl:: GetMinReqRect](#getminreqrect)|月間予定表コントロールに月を表示するために必要な最小サイズを取得します。|
|[CMonthCalCtrl:: Get当月デルタ](#getmonthdelta)|月間予定表コントロールのスクロール率を取得します。|
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|月間予定表コントロールの表示の上限と下限を表す日付情報を取得します。|
|[CMonthCalCtrl:: GetRange](#getrange)|月間予定表コントロールに設定されている現在の最小および最大の日付を取得します。|
|[CMonthCalCtrl:: GetSelRange](#getselrange)|ユーザーによって現在選択されている日付範囲の上限と下限を表す日付情報を取得します。|
|[CMonthCalCtrl:: GetToday](#gettoday)|月間予定表コントロールの "今日" として指定された日付の日付情報を取得します。|
|[CMonthCalCtrl:: System.windows.media.visualtreehelper.hittest](#hittest)|画面上の特定の位置にある月間予定表コントロールのセクションを決定します。|
|[CMonthCalCtrl:: IsCenturyView](#iscenturyview)|現在の月間予定表コントロールの現在のビューが世紀ビューであるかどうかを示します。|
|[CMonthCalCtrl:: IsDecadeView](#isdecadeview)|現在の月間予定表コントロールの現在のビューが10年間ビューであるかどうかを示します。|
|[CMonthCalCtrl:: IsMonthView](#ismonthview)|現在の月間予定表コントロールの現在のビューが月ビューであるかどうかを示します。|
|[CMonthCalCtrl:: Isyのビュー](#isyearview)|現在の月間予定表コントロールの現在のビューが年ビューであるかどうかを示します。|
|[CMonthCalCtrl:: SetCalendarBorder](#setcalendarborder)|現在の月間予定表コントロールの境界線の幅を設定します。|
|[CMonthCalCtrl:: SetCalendarBorderDefault](#setcalendarborderdefault)|現在の月間予定表コントロールの境界線の既定の幅を設定します。|
|[CMonthCalCtrl:: SetCalID](#setcalid)|現在の月間予定表コントロールのカレンダー識別子を設定します。|
|[CMonthCalCtrl:: SetCenturyView](#setcenturyview)|現在の月間予定表コントロールに、世紀のビューを表示するように設定します。|
|[CMonthCalCtrl:: SetColor](#setcolor)|月間予定表コントロールの指定された領域の色を設定します。|
|[CMonthCalCtrl:: SetCurrentView](#setcurrentview)|指定されたビューを表示するために、現在の月間予定表コントロールを設定します。|
|[CMonthCalCtrl:: SetCurSel](#setcursel)|月間予定表コントロールの現在選択されている日付を設定します。|
|[CMonthCalCtrl:: SetDayState](#setdaystate)|月間予定表コントロールの日の表示を設定します。|
|[CMonthCalCtrl:: SetDecadeView](#setdecadeview)|現在の月間予定表コントロールを10年のビューに設定します。|
|[CMonthCalCtrl:: SetFirstDayOfWeek](#setfirstdayofweek)|カレンダーの左端の列に表示される曜日を設定します。|
|[CMonthCalCtrl:: SetMaxSelCount](#setmaxselcount)|月間予定表コントロールで選択できる日数の最大値を設定します。|
|[CMonthCalCtrl:: Set当月デルタ](#setmonthdelta)|月間予定表コントロールのスクロール率を設定します。|
|[CMonthCalCtrl:: SetMonthView](#setmonthview)|当月のビューを表示するために、現在の月間予定表コントロールを設定します。|
|[CMonthCalCtrl:: SetRange](#setrange)|月間予定表コントロールに許可される日付の最小値と最大値を設定します。|
|[CMonthCalCtrl:: SetSelRange](#setselrange)|月間予定表コントロールの選択範囲を、特定の日付範囲に設定します。|
|[CMonthCalCtrl:: SetToday](#settoday)|現在の日付のカレンダーコントロールを設定します。|
|[CMonthCalCtrl:: SetYearView](#setyearview)|現在の月間予定表コントロールを年間表示に設定します。|
|[CMonthCalCtrl:: SizeMinReq](#sizeminreq)|月間予定表コントロールを、1か月の最小サイズに再描画します。|
|[CMonthCalCtrl:: Sizer Tomin](#sizerecttomin)|現在の月間予定表コントロールの場合、は、指定された四角形に収めるすべての暦を含むことができる最小の四角形を計算します。|

## <a name="remarks"></a>Remarks

月間予定表コントロールは、ユーザーが日付を選択できる単純な calendar インターフェイスを提供します。 ユーザーは、次の方法で表示を変更できます。

- Month から month へ、前後にスクロールします。

- 今日のテキストをクリックすると、現在の日付が表示されます (MCS_NOTODAY スタイルが使用されていない場合)。

- ポップアップメニューから月または年を選択します。

月間予定表コントロールをカスタマイズするには、作成時にオブジェクトにさまざまなスタイルを適用します。 これらのスタイルは、Windows SDK の[月間予定表コントロールスタイル](/windows/win32/Controls/month-calendar-control-styles)で記述されています。

月間予定表コントロールは、複数の月を表示できます。また、日付を太字にすると、特別な日 (休日など) を示すことができます。

月間予定表コントロールの使用方法の詳細については、「 [Using CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdtctl

##  <a name="cmonthcalctrl"></a>CMonthCalCtrl:: CMonthCalCtrl

`CMonthCalCtrl` オブジェクトを構築します。

```
CMonthCalCtrl();
```

### <a name="remarks"></a>Remarks

オブジェクトを構築`Create`した後で、を呼び出す必要があります。

##  <a name="create"></a>CMonthCalCtrl:: Create

月間予定表コントロールを作成し、 `CMonthCalCtrl`オブジェクトにアタッチします。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(
    DWORD dwStyle,
    const POINT& pt,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
月間予定表コントロールに適用される Windows スタイルの組み合わせを指定します。 スタイルの詳細については、Windows SDK の「[月間予定表コントロールのスタイル](/windows/win32/Controls/month-calendar-control-styles)」を参照してください。

*rect*<br/>
[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。 月間予定表コントロールの位置とサイズを格納します。

*未満*<br/>
月間予定表コントロールの位置を識別する[ポイント](/previous-versions/dd162805\(v=vs.85\))構造体への参照。

*pParentWnd*<br/>
月間予定表コントロールの親ウィンドウである[CWnd](../../mfc/reference/cwnd-class.md)オブジェクトへのポインター。 NULL にすることはできません。

*nID*<br/>
月間予定表コントロールのコントロール ID を指定します。

### <a name="return-value"></a>戻り値

初期化が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

月間予定表コントロールを作成するには、次の2つの手順を実行します。

1. [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)を呼び出して、 `CMonthCalCtrl`オブジェクトを構築します。

1. このメンバー関数を呼び出して、月間予定表コントロールを作成し、 `CMonthCalCtrl`オブジェクトにアタッチします。

を呼び出す`Create`と、コモンコントロールが初期化されます。 呼び出しの`Create`バージョンによって、サイズの設定が決まります。

- MFC によってコントロールのサイズが1か月に自動的に設定されるようにするには、 *pt*パラメーターを使用するオーバーライドを呼び出します。

- コントロールのサイズを自分で変更するには、 *rect*パラメーターを使用するこの関数のオーバーライドを呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

##  <a name="getcalendarborder"></a>CMonthCalCtrl:: GetCalendarBorder

現在の月間予定表コントロールの境界線の幅を取得します。

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>戻り値

コントロールの境界線の幅 (ピクセル単位)。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[MCM_GETCALENDARBORDER](/windows/win32/Controls/mcm-getcalendarborder)メッセージを送信します。

##  <a name="getcalendarcount"></a>CMonthCalCtrl:: GetCalendarCount

現在の月間予定表コントロールに表示されるカレンダーの数を取得します。

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>戻り値

月間予定表コントロールに現在表示されているカレンダーの数。 カレンダーの最大許容数は12です。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[MCM_GETCALENDARCOUNT](/windows/win32/Controls/mcm-getcalendarcount)メッセージを送信します。

##  <a name="getcalendargridinfo"></a>CMonthCalCtrl:: GetCalendarGridInfo

現在の月間予定表コントロールに関する情報を取得します。

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pmcGridInfo*|入出力現在の月間予定表コントロールに関する情報を受け取る[Mcgridinfo](/windows/win32/api/commctrl/ns-commctrl-mcgridinfo)構造体へのポインター。 呼び出し元は、この構造体の割り当てと初期化を行います。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[MCM_GETCALENDARGRIDINFO](/windows/win32/Controls/mcm-getcalendargridinfo)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、月間`m_monthCalCtrl`予定表コントロールにプログラムでアクセスするために使用される変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>例

次のコード例では`GetCalendarGridInfo` 、メソッドを使用して、現在の月間予定表コントロールに表示されるカレンダーの日付を取得します。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

##  <a name="getcalid"></a>CMonthCalCtrl:: GetCalID

現在の月間予定表コントロールのカレンダー識別子を取得します。

```
CALID GetCalID() const;
```

### <a name="return-value"></a>戻り値

[カレンダー識別子](/windows/win32/Intl/calendar-identifiers)定数の1つ。

### <a name="remarks"></a>Remarks

カレンダー識別子は、グレゴリオ暦 (ローカライズ版)、日本語、またはイスラム暦など、地域固有の暦を表します。 アプリケーションでは、さまざまな言語サポート機能を持つカレンダー識別子を使用できます。

このメソッドは、Windows SDK で説明されている[MCM_GETCALID](/windows/win32/Controls/mcm-getcalid)メッセージを送信します。

##  <a name="getcolor"></a>CMonthCalCtrl:: GetColor

*Nregion*によって指定された月間予定表コントロールの領域の色を取得します。

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>パラメーター

*nRegion*<br/>
色の取得元となる月間予定表コントロールの領域。 値の一覧については、 [Setcolor](#setcolor)の*nregion*パラメーターを参照してください。

### <a name="return-value"></a>戻り値

正常終了した場合は、月間予定表コントロールの部分に関連付けられた色を指定する[COLORREF](/windows/win32/gdi/colorref)値。 それ以外の場合、このメンバー関数は-1 を返します。

##  <a name="getcurrentview"></a>CMonthCalCtrl:: GetCurrentView

現在の月間予定表コントロールによって現在表示されているビューを取得します。

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>戻り値

現在のビューは、次のいずれかの値によって示されます。

|[値]|説明|
|-----------|-------------|
|MCMV_MONTH|月単位のビュー|
|MCMV_YEAR|年間ビュー|
|MCMV_DECADE|10年表示|
|MCMV_CENTURY|世紀の表示|

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、月間`m_monthCalCtrl`予定表コントロールにプログラムでアクセスするために使用される変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>例

次のコード例では、現在表示されている月間予定表コントロールのビューを報告します。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

##  <a name="getcursel"></a>CMonthCalCtrl:: GetCurSel

現在選択されている日付によって示されるシステム時刻を取得します。

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>パラメーター

*refDateTime*<br/>
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトまたは[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへの参照。 現在の時刻を受け取ります。

*pDateTime*<br/>
現在選択されている日付情報を受け取る[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。 このパラメーターは有効なアドレスである必要があり、NULL にすることはできません。

### <a name="return-value"></a>戻り値

成功した場合は0以外の。otherwize 0.

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_GETCURSEL](/windows/win32/Controls/mcm-getcursel)の動作を実装します。

> [!NOTE]
>  このメンバー関数は、スタイル MCS_MULTISELECT が設定されている場合に失敗します。

MFC のの実装で`GetCurSel`は、 `COleDateTime`使用法、 `CTime`使用法、または`SYSTEMTIME`構造体の使用法を指定できます。

##  <a name="getfirstdayofweek"></a>CMonthCalCtrl:: GetFirstDayOfWeek

カレンダーの左端の列に表示される週の最初の曜日を取得します。

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>パラメーター

*pbLocal*<br/>
ブール値へのポインター。 値が0以外の場合、コントロールの設定がコントロールパネルの設定と一致しません。

### <a name="return-value"></a>戻り値

週の最初の曜日を表す整数値。 これらの整数が表す内容の詳細については、「**解説**」を参照してください。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_GETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-getfirstdayofweek)の動作を実装します。 曜日は、次のように整数で表されます。

|[値]|曜日|
|-----------|---------------------|
|0|月曜日|
|1|火曜日|
|2|水曜日|
|3|木曜日|
|4|金曜日|
|5|土曜日|
|6|日曜日|

### <a name="example"></a>例

  [CMonthCalCtrl:: SetFirstDayOfWeek](#setfirstdayofweek)の例を参照してください。

##  <a name="getmaxselcount"></a>CMonthCalCtrl:: GetMaxSelCount

月間予定表コントロールで選択できる現在の最大日数を取得します。

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>戻り値

コントロールに対して選択できる合計日数を表す整数値。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_GETMAXSELCOUNT](/windows/win32/Controls/mcm-getmaxselcount)の動作を実装します。 このメンバー関数は、MCS_MULTISELECT スタイルセットを持つコントロールに使用します。

### <a name="example"></a>例

  [CMonthCalCtrl:: SetMaxSelCount](#setmaxselcount)の例を参照してください。

##  <a name="getmaxtodaywidth"></a>CMonthCalCtrl:: GetMaxTodayWidth

現在の月間予定表コントロールの "今日" の文字列の最大の幅を取得します。

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>戻り値

"今日" の文字列の幅 (ピクセル単位)。

### <a name="example"></a>例

次のコード例では、月間`m_monthCalCtrl`予定表コントロールにプログラムでアクセスするために使用される変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>例

次のコード例は、 `GetMaxTodayWidth`メソッドを示しています。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>Remarks

ユーザーは現在の日付に戻ることができます。この文字列は、月間予定表コントロールの下部に表示されます。 "今日" の文字列には、ラベルテキストと日付テキストが含まれています。

このメソッドは、Windows SDK で説明されている[MCM_GETMAXTODAYWIDTH](/windows/win32/Controls/mcm-getmaxtodaywidth)メッセージを送信します。

##  <a name="getminreqrect"></a>CMonthCalCtrl:: GetMinReqRect

月間予定表コントロールに月を表示するために必要な最小サイズを取得します。

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>パラメーター

*pRect*<br/>
外接する四角形の情報を受け取る[RECT](/previous-versions/dd162897\(v=vs.85\))構造体へのポインター。 このパラメーターは有効なアドレスである必要があり、NULL にすることはできません。

### <a name="return-value"></a>戻り値

成功した場合、このメンバー関数は`lpRect` 0 以外の値を返し、該当する境界情報を受け取ります。 失敗した場合、メンバー関数は0を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_GETMINREQRECT](/windows/win32/Controls/mcm-getminreqrect)の動作を実装します。

##  <a name="getmonthdelta"></a>  CMonthCalCtrl::GetMonthDelta

月間予定表コントロールのスクロール率を取得します。

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>戻り値

月間予定表コントロールのスクロール率。 スクロール率は、ユーザーがスクロールボタンを1回クリックしたときにコントロールが表示を移動する月数です。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_GETMONTHDELTA](/windows/win32/Controls/mcm-getmonthdelta)の動作を実装します。

##  <a name="getmonthrange"></a>  CMonthCalCtrl::GetMonthRange

月間予定表コントロールの表示の上限と下限を表す日付情報を取得します。

```
int GetMonthRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    CTime& refMinRange,
    CTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange,
    DWORD dwFlags) const;
```

### <a name="parameters"></a>パラメーター

*refMinRange*<br/>
許容される日付の最小値を含む[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトまたは[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへの参照。

*refMaxRange*<br/>
許容される日付`COleDateTime`の`CTime`最大値を格納しているオブジェクトまたはオブジェクトへの参照。

*pMinRange*<br/>
範囲の下限の日付を格納している[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。

*pMaxRange*<br/>
範囲の最上位`SYSTEMTIME`の日付を格納している構造体へのポインター。

*dwFlags*<br/>
取得する範囲の制限のスコープを指定する値。 この値は、次のいずれかである必要があります。

|[値]|説明|
|-----------|-------------|
|GMR_DAYSTATE|部分的に表示される表示範囲の前後の月を含めます。|
|GMR_VISIBLE|完全に表示されている月だけを含めます。|

### <a name="return-value"></a>戻り値

によって示される 2 つの制限により展開されるか月で、範囲を表す整数を *refMinRange* と *refMaxRange* 最初と 2 番目のバージョン、または*pMinRange* *整数* で 3 番目のバージョン。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_GETMONTHRANGE](/windows/win32/Controls/mcm-getmonthrange)の動作を実装します。 MFC のの実装で`GetMonthRange`は、使用状況`COleDateTime` 、 `CTime`使用法、または`SYSTEMTIME`構造体の使用法を指定できます。

### <a name="example"></a>例

  [CMonthCalCtrl:: SetDayState](#setdaystate)の例を参照してください。

##  <a name="getrange"></a>  CMonthCalCtrl::GetRange

月間予定表コントロールに設定されている現在の最小および最大の日付を取得します。

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;

DWORD GetRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>パラメーター

*pMinRange*<br/>
範囲の下限の`COleDateTime`日付を格納`CTime`しているオブジェクト、オブジェクト、または[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。

*pMaxRange*<br/>
範囲の最上位`COleDateTime`の日付を`CTime`格納しているオブジェクト、オブジェクト、または[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。

### <a name="return-value"></a>戻り値

0 (制限は設定されません) または制限情報を指定する次の値の組み合わせを指定できる DWORD。

|[値]|説明|
|-----------|-------------|
|GDTR_MAX|コントロールに対して最大値が設定されています。*pMaxRange*は有効で、該当する日付情報が含まれています。|
|GDTR_MIN|コントロールに対して最小制限を設定します。*pMinRange*は有効で、該当する日付情報が含まれています。|

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_GETRANGE](/windows/win32/Controls/mcm-getrange)の動作を実装します。 MFC のの実装で`GetRange`は、 `COleDateTime`使用法、 `CTime`使用法、または`SYSTEMTIME`構造体の使用法を指定できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

##  <a name="getselrange"></a>CMonthCalCtrl:: GetSelRange

ユーザーによって現在選択されている日付範囲の上限と下限を表す日付情報を取得します。

```
BOOL GetSelRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange) const;

BOOL GetSelRange(
    CTime& refMinRange,
    CTime& refMaxRange) const;

BOOL GetSelRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>パラメーター

*refMinRange*<br/>
許容される日付の最小値を含む[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトまたは[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへの参照。

*refMaxRange*<br/>
許容される日付`COleDateTime`の`CTime`最大値を格納しているオブジェクトまたはオブジェクトへの参照。

*pMinRange*<br/>
範囲の下限の日付を格納している[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。

*pMaxRange*<br/>
範囲の最上位`SYSTEMTIME`の日付を格納している構造体へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_GETSELRANGE](/windows/win32/Controls/mcm-getselrange)の動作を実装します。 `GetSelRange`MCS_MULTISELECT スタイルを使用しない月間予定表コントロールに適用した場合、は失敗します。

MFC のの実装で`GetSelRange`は、使用状況`COleDateTime` 、 `CTime`使用法、または`SYSTEMTIME`構造体の使用法を指定できます。

##  <a name="gettoday"></a>CMonthCalCtrl:: GetToday

月間予定表コントロールの "今日" として指定された日付の日付情報を取得します。

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>パラメーター

*refDateTime*<br/>
現在の日付を示す[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトまたは[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへの参照。

*pDateTime*<br/>
日付情報を受け取る[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。 このパラメーターは有効なアドレスである必要があり、NULL にすることはできません。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_GETTODAY](/windows/win32/Controls/mcm-gettoday)の動作を実装します。 MFC のの実装で`GetToday`は、 `COleDateTime`使用法、 `CTime`使用法、または`SYSTEMTIME`構造体の使用法を指定できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

##  <a name="hittest"></a>CMonthCalCtrl:: System.windows.media.visualtreehelper.hittest

指定した位置にある月間予定表コントロール (存在する場合) を決定します。

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>パラメーター

*pMCHitTest*<br/>
月間予定表コントロールのヒットテストポイントを含む[MCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-mchittestinfo)構造体へのポインター。

### <a name="return-value"></a>戻り値

DWORD 値。 `MCHITTESTINFO`構造体の**uhit**メンバーと同じです。

### <a name="remarks"></a>Remarks

`HitTest`ヒットテスト`MCHITTESTINFO`に関する情報を格納する構造体を使用します。

##  <a name="iscenturyview"></a>CMonthCalCtrl:: IsCenturyView

現在の月間予定表コントロールの現在のビューが世紀ビューであるかどうかを示します。

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>戻り値

現在のビューが世紀ビューである場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)メッセージを送信します。 そのメッセージが MCMV_CENTURY を返す場合、このメソッドは TRUE を返します。

##  <a name="isdecadeview"></a>  CMonthCalCtrl::IsDecadeView

現在の月間予定表コントロールの現在のビューが10年間ビューであるかどうかを示します。

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>戻り値

現在のビューが10年のビューである場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)メッセージを送信します。 そのメッセージが MCMV_DECADE を返す場合、このメソッドは TRUE を返します。

##  <a name="ismonthview"></a>CMonthCalCtrl:: IsMonthView

現在の月間予定表コントロールの現在のビューが月ビューであるかどうかを示します。

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>戻り値

現在のビューが月ビューである場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)メッセージを送信します。 そのメッセージが MCMV_MONTH を返す場合、このメソッドは TRUE を返します。

##  <a name="isyearview"></a>CMonthCalCtrl:: Isyのビュー

現在の月間予定表コントロールの現在のビューが年ビューであるかどうかを示します。

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>戻り値

現在のビューが年ビューである場合は TRUE を返します。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)メッセージを送信します。 そのメッセージが MCMV_YEAR を返す場合、このメソッドは TRUE を返します。

##  <a name="setcalendarborder"></a>CMonthCalCtrl:: SetCalendarBorder

現在の月間予定表コントロールの境界線の幅を設定します。

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*cxyBorder*|から境界線の幅 (ピクセル単位)。|

### <a name="remarks"></a>Remarks

このメソッドが成功した場合、境界線の幅は*cxyBorder*パラメーターに設定されます。 それ以外の場合、罫線の幅は、現在の[テーマ](/windows/win32/Controls/visual-styles-overview)によって指定されている既定値にリセットされます。または、テーマを使用しない場合は0になります。

このメソッドは、Windows SDK で説明されている[MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、月間`m_monthCalCtrl`予定表コントロールにプログラムでアクセスするために使用される変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>例

次のコード例では、月間予定表コントロールの境界線の幅を8ピクセルに設定しています。 [CMonthCalCtrl:: GetCalendarBorder](#getcalendarborder)メソッドを使用して、このメソッドが成功したかどうかを確認します。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

##  <a name="setcalendarborderdefault"></a>CMonthCalCtrl:: SetCalendarBorderDefault

現在の月間予定表コントロールの境界線の既定の幅を設定します。

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>Remarks

境界線の幅は、現在の[テーマ](/windows/win32/Controls/visual-styles-overview)によって指定された既定値に設定されます。または、テーマを使用しない場合は0に設定されます。

このメソッドは、Windows SDK で説明されている[MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder)メッセージを送信します。

##  <a name="setcalid"></a>CMonthCalCtrl:: SetCalID

現在の月間予定表コントロールのカレンダー識別子を設定します。

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*calid*|から[カレンダー識別子](/windows/win32/Intl/calendar-identifiers)定数の1つ。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

カレンダー識別子では、グレゴリオ暦 (ローカライズ版)、日本語、またはイスラム暦など、地域固有の暦を指定します。 暦を含むロケールがコンピューターにインストールされている場合は、メソッドを使用して、calidパラメーターで指定された暦を表示し`SetCalID`ます。

このメソッドは、Windows SDK で説明されている[MCM_SETCALID](/windows/win32/Controls/mcm-setcalid)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、月間`m_monthCalCtrl`予定表コントロールにプログラムでアクセスするために使用される変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>例

次のコード例では、月間予定表コントロールを設定して、日本皇帝の時代 (年号) カレンダーを表示します。 この`SetCalID`メソッドは、そのカレンダーがコンピューターにインストールされている場合にのみ成功します。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

##  <a name="setcenturyview"></a>CMonthCalCtrl:: SetCenturyView

現在の月間予定表コントロールに、世紀のビューを表示するように設定します。

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、 [CMonthCalCtrl:: SetCurrentView](#setcurrentview)メソッドを使用して、 `MCMV_CENTURY`世紀ビューを表すビューをに設定します。

##  <a name="setcolor"></a>CMonthCalCtrl:: SetColor

月間予定表コントロールの指定された領域の色を設定します。

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>パラメーター

*nRegion*<br/>
設定する月のカレンダーの色を指定する整数値。 この値には、次のいずれかを指定できます。

|[値]|説明|
|-----------|-------------|
|MCSC_BACKGROUND|月の間に表示される背景色。|
|MCSC_MONTHBK|月内に表示される背景色。|
|MCSC_TEXT|月内のテキストの表示に使用する色。|
|MCSC_TITLEBK|予定表のタイトルに表示される背景色。|
|MCSC_TITLETEXT|カレンダーのタイトル内のテキストの表示に使用する色。|
|MCSC_TRAILINGTEXT|ヘッダーと末尾のテキストを表示するために使用する色。 ヘッダーと末尾の日付は、現在の暦に表示される前と後の月の日付です。|

*ref*<br/>
月間予定表コントロールの指定した部分の新しい色設定の COLORREF 値。

### <a name="return-value"></a>戻り値

正常終了した場合は、月間予定表コントロールの指定した部分の前の色設定を表す COLORREF 値。 それ以外の場合、このメッセージは-1 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_SETCOLOR](/windows/win32/Controls/mcm-setcolor)の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

##  <a name="setcurrentview"></a>CMonthCalCtrl:: SetCurrentView

指定されたビューを表示するために、現在の月間予定表コントロールを設定します。

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*dwNewView*|から月、年、年、または世紀のビューを指定する次のいずれかの値。<br /><br /> MCMV_MONTH:月単位のビュー<br /><br /> MCMV_YEAR:年間ビュー<br /><br /> MCMV_DECADE:10年表示<br /><br /> MCMV_CENTURY:世紀の表示|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[MCM_SETCURRENTVIEW](/windows/win32/Controls/mcm-setcurrentview)メッセージを送信します。

##  <a name="setcursel"></a>CMonthCalCtrl:: SetCurSel

月間予定表コントロールの現在選択されている日付を設定します。

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>パラメーター

*refDateTime*<br/>
現在選択されている月間予定表コントロールを示す[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトまたは[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへの参照。

*pDateTime*<br/>
現在の選択範囲として設定される日付を格納している[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_SETCURSEL](/windows/win32/Controls/mcm-setcursel)の動作を実装します。 MFC のの実装で`SetCurSel`は、 `COleDateTime`使用法、 `CTime`使用法、または`SYSTEMTIME`構造体の使用法を指定できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

##  <a name="setdaystate"></a>CMonthCalCtrl:: SetDayState

月間予定表コントロールの日の表示を設定します。

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>パラメーター

*nMonths*<br/>
*Pstates*が指す配列内の要素の数を示す値。

*pStates*<br/>
月間予定表コントロールが各日を表示する方法を定義する、値の[MONTHDAYSTATE](/windows/win32/Controls/monthdaystate)配列へのポインター。 MONTHDAYSTATE データ型はビットフィールドで、各ビット (1 ~ 31) は月の1日の状態を表します。 ビットがオンの場合は、対応する日が太字で表示されます。それ以外の場合は、何も強調表示されません。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_SETDAYSTATE](/windows/win32/Controls/mcm-setdaystate)の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

##  <a name="setdecadeview"></a>CMonthCalCtrl:: SetDecadeView

現在の月間予定表コントロールを10年のビューに設定します。

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、 [CMonthCalCtrl:: SetCurrentView](#setcurrentview)メソッドを使用して、 `MCMV_DECADE`10 年のビューを表すにビューを設定します。

##  <a name="setfirstdayofweek"></a>CMonthCalCtrl:: SetFirstDayOfWeek

カレンダーの左端の列に表示される曜日を設定します。

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>パラメーター

*iDay*<br/>
週の最初の曜日として設定する日付を表す整数値。 この値は、いずれかの日の数値である必要があります。 日番号の詳細については、「 [GetFirstDayOfWeek](#getfirstdayofweek) 」を参照してください。

*lpnOld*<br/>
以前に設定された週の最初の曜日を示す整数を指すポインターです。

### <a name="return-value"></a>戻り値

1週間の前の最初の曜日が、コントロールパネルの設定で指定された日である LOCALE_IFIRSTDAYOFWEEK の値以外の値に設定されている場合は0以外の値。 それ以外の場合、この関数は0を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_SETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-setfirstdayofweek)の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

##  <a name="setmaxselcount"></a>CMonthCalCtrl:: SetMaxSelCount

月間予定表コントロールで選択できる日数の最大値を設定します。

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>パラメーター

*N1 日*<br/>
選択可能な最大日数を表すために設定される値。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_SETMAXSELCOUNT](/windows/win32/Controls/mcm-setmaxselcount)の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

##  <a name="setmonthdelta"></a>  CMonthCalCtrl::SetMonthDelta

月間予定表コントロールのスクロール率を設定します。

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>パラメーター

*iDelta*<br/>
コントロールのスクロール率として設定される月数。 この値が0の場合、月のデルタは既定値にリセットされます。これは、コントロールに表示される月数です。

### <a name="return-value"></a>戻り値

前のスクロール速度。 スクロール率が以前に設定されていない場合、戻り値は0になります。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_SETMONTHDELTA](/windows/win32/Controls/mcm-setmonthdelta)の動作を実装します。

##  <a name="setmonthview"></a>CMonthCalCtrl:: SetMonthView

当月のビューを表示するために、現在の月間予定表コントロールを設定します。

```
BOOL SetMonthView();
```

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、 [CMonthCalCtrl:: SetCurrentView](#setcurrentview)メソッドを使用してビューを MCMV_MONTH に設定します。これは月ビューを表します。

### <a name="example"></a>例

次のコード例では、月間`m_monthCalCtrl`予定表コントロールにプログラムでアクセスするために使用される変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>例

次のコード例では、月、年、年、および4桁のビューを表示するように、月間予定表コントロールを設定します。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

##  <a name="setrange"></a>CMonthCalCtrl:: SetRange

月間予定表コントロールに許容される日付の最小値と最大値を設定します。

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);

BOOL SetRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>パラメーター

*pMinRange*<br/>
範囲の下限の`COleDateTime`日付を格納`CTime`しているオブジェクト、オブジェクト、または[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。

*pMaxRange*<br/>
範囲の最上位`COleDateTime`の日付を`CTime`格納して`SYSTEMTIME`いるオブジェクト、オブジェクト、または構造体へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_SETRANGE](/windows/win32/Controls/mcm-setrange)の動作を実装します。 MFC のの実装で`SetRange`は、使用状況`COleDateTime` 、 `CTime`使用法、または`SYSTEMTIME`構造体の使用法を指定できます。

### <a name="example"></a>例

  [CMonthCalCtrl:: GetRange](#getrange)の例を参照してください。

##  <a name="setselrange"></a>CMonthCalCtrl:: SetSelRange

月間予定表コントロールの選択範囲を、特定の日付範囲に設定します。

```
BOOL SetSelRange(
    const COleDateTime& pMinRange,
    const COleDateTime& pMaxRange);

BOOL SetSelRange(
    const CTime& pMinRange,
    const CTime& pMaxRange);

BOOL SetSelRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>パラメーター

*pMinRange*<br/>
範囲の下限の`COleDateTime`日付を格納`CTime`しているオブジェクト、オブジェクト、または[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。

*pMaxRange*<br/>
範囲の最上位`COleDateTime`の日付を`CTime`格納して`SYSTEMTIME`いるオブジェクト、オブジェクト、または構造体へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_SETSELRANGE](/windows/win32/Controls/mcm-setselrange)の動作を実装します。 MFC のの実装で`SetSelRange`は、使用状況`COleDateTime` 、 `CTime`使用法、または`SYSTEMTIME`構造体の使用法を指定できます。

##  <a name="settoday"></a>CMonthCalCtrl:: SetToday

現在の日付のカレンダーコントロールを設定します。

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>パラメーター

*refDateTime*<br/>
現在の日付を含む[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトへの参照。

*pDateTime*<br/>
2番目のバージョンでは、現在の日付情報を格納している[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへのポインター。 3番目のバージョンでは、現在の日付情報を格納している[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [MCM_SETTODAY](/windows/win32/Controls/mcm-settoday)の動作を実装します。

### <a name="example"></a>例

  [CMonthCalCtrl:: GetToday](#gettoday)の例を参照してください。

##  <a name="setyearview"></a>CMonthCalCtrl:: SetYearView

現在の月間予定表コントロールを年間表示に設定します。

```
BOOL SetYearView();
```

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、 [CMonthCalCtrl:: SetCurrentView](#setcurrentview)メソッドを使用してビューを MCMV_YEAR に設定します。これは年間ビューを表します。

##  <a name="sizeminreq"></a>CMonthCalCtrl:: SizeMinReq

月間予定表コントロールに、1か月を表示する最小サイズを表示します。

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>パラメーター

*塗装*<br/>
コントロールを再描画するかどうかを指定します。 既定値は TRUE です。 FALSE の場合、再描画は行われません。

### <a name="return-value"></a>戻り値

月間予定表コントロールのサイズが最小値に設定されている場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

を`SizeMinReq`正常に呼び出すと、1か月のカレンダーの月間予定表コントロール全体が表示されます。

##  <a name="sizerecttomin"></a>CMonthCalCtrl:: Sizer Tomin

現在の月間予定表コントロールの場合、は、指定された四角形に収めるすべての暦を含むことができる最小の四角形を計算します。

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*lpRect*|から必要な数のカレンダーを含む四角形を定義する[RECT](/previous-versions/dd162897\(v=vs.85\))構造体へのポインター。|

### <a name="return-value"></a>戻り値

サイズが*lpRect*パラメーターで定義された四角形以下である四角形を定義する[RECT](/previous-versions/dd162897\(v=vs.85\))構造体へのポインター。

### <a name="remarks"></a>Remarks

このメソッドは、 *lpRect*パラメーターによって指定された四角形に収めることができる暦の数を計算し、その数のカレンダーを格納できる最小の四角形を返します。 実際には、このメソッドは、指定された四角形を縮小して、必要な数のカレンダーにちょうど合わせるようにします。

このメソッドは、Windows SDK で説明されている[MCM_SIZERECTTOMIN](/windows/win32/Controls/mcm-sizerecttomin)メッセージを送信します。

## <a name="see-also"></a>関連項目

[MFC のサンプル CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl クラス](../../mfc/reference/cdatetimectrl-class.md)
