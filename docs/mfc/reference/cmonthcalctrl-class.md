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
ms.openlocfilehash: 48b02843cc957994aa3f3109a82cb2188dd9acff
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894199"
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
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|`CMonthCalCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMonthCalCtrl::Create](#create)|1 か月カレンダー コントロールを作成しにアタッチします、`CMonthCalCtrl`オブジェクト。|
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|現在の月のカレンダー コントロールの境界線の幅を取得します。|
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|現在の月のカレンダー コントロールに表示されるカレンダーの数を取得します。|
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|現在の月のカレンダー コントロールに関する情報を取得します。|
|[CMonthCalCtrl::GetCalID](#getcalid)|現在の月のカレンダー コントロールのカレンダーの識別子を取得します。|
|[CMonthCalCtrl::GetColor](#getcolor)|月間予定表コントロールの指定した領域の色を取得します。|
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|現在の月のカレンダー コントロールで現在表示されているビューを取得します。|
|[CMonthCalCtrl::GetCurSel](#getcursel)|現在選択されている日付で示されている、システム時刻を取得します。|
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|予定表の左端の列に表示される週の最初の日を取得します。|
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|月間予定表コントロールで選択できる日数の現在の最大数を取得します。|
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|現在の月のカレンダー コントロールの"Today"文字列の最大の幅を取得します。|
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|月間予定表コントロールで完全な月を表示するために必要な最小サイズを取得します。|
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|月間予定表コントロールのスクロール速度を取得します。|
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|日付の月のカレンダー コントロールの表示の高値と安値の制限を表す情報を取得します。|
|[CMonthCalCtrl::GetRange](#getrange)|1 か月カレンダー コントロールに設定する現在の最小値と最大の日付を取得します。|
|[CMonthCalCtrl::GetSelRange](#getselrange)|ユーザーが現在選択されている日付の範囲の上限と下限を表す日付情報を取得します。|
|[CMonthCalCtrl::GetToday](#gettoday)|月間予定表コントロールの「現在」として指定された日付の日付の情報を取得します。|
|[CMonthCalCtrl::HitTest](#hittest)|月間予定表コントロールのどのセクションは、画面上の特定の時点を決定します。|
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|現在の月のカレンダー コントロールの現在のビューが 2 桁の年のビューであるかどうかを示します。|
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|現在の月のカレンダー コントロールの現在のビューが 10 年のビューであるかどうかを示します。|
|[CMonthCalCtrl::IsMonthView](#ismonthview)|現在の月のカレンダー コントロールの現在のビューが 1 か月のビューであるかどうかを示します。|
|[CMonthCalCtrl::IsYearView](#isyearview)|現在の月のカレンダー コントロールの現在のビューがある年のビューであるかどうかを示します。|
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|現在の月のカレンダー コントロールの境界線の幅を設定します。|
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|現在の月のカレンダー コントロールの枠線の既定の幅を設定します。|
|[CMonthCalCtrl::SetCalID](#setcalid)|現在の月のカレンダー コントロールのカレンダーの識別子を設定します。|
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|2 桁の年のビューを表示する現在の月のカレンダー コントロールを設定します。|
|[CMonthCalCtrl::SetColor](#setcolor)|月間予定表コントロールの指定した領域の色を設定します。|
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|指定されたビューを表示する現在の月のカレンダー コントロールを設定します。|
|[CMonthCalCtrl::SetCurSel](#setcursel)|月間予定表コントロールの現在選択されている日付を設定します。|
|[CMonthCalCtrl::SetDayState](#setdaystate)|月間予定表コントロールでの日付の表示を設定します。|
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|10 年のビューに現在の月のカレンダー コントロールを設定します。|
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|予定表の左端の列に表示する曜日を設定します。|
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|月間予定表コントロールで選択できる最大日数を設定します。|
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|月間予定表コントロールのスクロール速度を設定します。|
|[CMonthCalCtrl::SetMonthView](#setmonthview)|1 か月のビューを表示する現在の月のカレンダー コントロールを設定します。|
|[CMonthCalCtrl::SetRange](#setrange)|最小値と最大の値は、月間予定表コントロールの日付を設定します。|
|[CMonthCalCtrl::SetSelRange](#setselrange)|指定した日付範囲を 1 か月カレンダーの選択コントロールを設定します。|
|[CMonthCalCtrl::SetToday](#settoday)|現在の日付の予定表コントロールを設定します。|
|[CMonthCalCtrl::SetYearView](#setyearview)|年のビューに現在の月のカレンダー コントロールを設定します。|
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|再描画、月間予定表は、1 か月間の最小サイズに制御します。|
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|現在の月間予定表コントロールで、指定した四角形に収まるすべてのカレンダーを含むことのできる最も小さな四角形を計算します。|

## <a name="remarks"></a>Remarks

月間予定表コントロールでは、ユーザーが日付を選択できる単純なカレンダー インターフェイスを持つユーザーを提供します。 ユーザーは別に表示を変更できます。

- 月に前後をスクロールします。

- (MCS_NOTODAY スタイルを使用しない) 場合は、現在の日付を表示する現在のテキストをクリックします。

- 1 か月またはポップアップ メニューからの年を選択します。

月をカスタマイズするカレンダー コントロールを作成するときに、オブジェクトにさまざまなスタイルを適用することで。 これらのスタイルが記載されて[月間予定表コントロールのスタイル](/windows/desktop/Controls/month-calendar-control-styles)Windows SDK にします。

月間予定表コントロールは、1 か月以上を表示し、(祝日) などの特別な日を太字で示している可能性、日付。

月間予定表コントロールの使用に関する詳細については、次を参照してください。[を使用して CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdtctl.h

##  <a name="cmonthcalctrl"></a>  CMonthCalCtrl::CMonthCalCtrl

`CMonthCalCtrl` オブジェクトを構築します。

```
CMonthCalCtrl();
```

### <a name="remarks"></a>Remarks

呼び出す必要があります`Create`オブジェクトを構築した後。

##  <a name="create"></a>  CMonthCalCtrl::Create

1 か月カレンダー コントロールを作成しにアタッチします、`CMonthCalCtrl`オブジェクト。

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
月間予定表のコントロールに適用された Windows スタイルの組み合わせを指定します。 参照してください[月間予定表コントロールのスタイル](/windows/desktop/Controls/month-calendar-control-styles)スタイルの詳細については、Windows SDK に含まれています。

*rect*<br/>
参照を[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)構造体。 月間予定表コントロールのサイズと位置が含まれています。

*pt*<br/>
参照を[ポイント](https://msdn.microsoft.com/library/windows/desktop/dd162805)月間予定表コントロールの場所を識別する構造体。

*pParentWnd*<br/>
ポインターを[CWnd](../../mfc/reference/cwnd-class.md)オブジェクトは、月間予定表コントロールの親ウィンドウです。 NULL は指定できません。

*nID*<br/>
月間予定表コントロールのコントロール ID を指定します

### <a name="return-value"></a>戻り値

初期化が成功した場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

1 か月を作成するカレンダー コントロールで 2 つの手順。

1. 呼び出す[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)を構築する、`CMonthCalCtrl`オブジェクト。

1. 月間予定表コントロールの作成およびにアタッチしますこのメンバー関数の呼び出し、`CMonthCalCtrl`オブジェクト。

呼び出すと`Create`、一般的なコントロールが初期化されます。 バージョンの`Create`する呼び出しでは、サイズがどのように決定します。

- 1 か月にコントロールのサイズを自動的に MFC には、使用するオーバーライドを呼び出し、 *pt*パラメーター。

- 自分でコントロールのサイズ、使用するこの関数のオーバーライドを呼び出し、 *rect*パラメーター。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

##  <a name="getcalendarborder"></a>  CMonthCalCtrl::GetCalendarBorder

現在の月のカレンダー コントロールの境界線の幅を取得します。

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>戻り値

ピクセル単位で、コントロールの境界線の幅。

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [MCM_GETCALENDARBORDER](/windows/desktop/Controls/mcm-getcalendarborder)メッセージは、Windows SDK で説明します。

##  <a name="getcalendarcount"></a>  CMonthCalCtrl::GetCalendarCount

現在の月のカレンダー コントロールに表示されるカレンダーの数を取得します。

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>戻り値

月間予定表コントロールで現在表示されているカレンダーの数。 予定表の許容最大数には 12 です。

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [MCM_GETCALENDARCOUNT](/windows/desktop/Controls/mcm-getcalendarcount)メッセージは、Windows SDK で説明します。

##  <a name="getcalendargridinfo"></a>  CMonthCalCtrl::GetCalendarGridInfo

現在の月のカレンダー コントロールに関する情報を取得します。

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pmcGridInfo*|[out]ポインターを[受け取る](/windows/desktop/api/commctrl/ns-commctrl-tagmcgridinfo)現在の月のカレンダー コントロールに関する情報を受け取る構造体。 呼び出し元は、割り当てと、この構造体を初期化します。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [MCM_GETCALENDARGRIDINFO](/windows/desktop/Controls/mcm-getcalendargridinfo)メッセージは、Windows SDK で説明します。

### <a name="example"></a>例

次のコード例は、変数を定義します。 `m_monthCalCtrl`、つまり、月間予定表コントロールをプログラムでアクセスするために使用します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>例

次のコード例では、`GetCalendarGridInfo`現在の月のカレンダー コントロールを表示するカレンダーの日付を取得します。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

##  <a name="getcalid"></a>  CMonthCalCtrl::GetCalID

現在の月のカレンダー コントロールのカレンダーの識別子を取得します。

```
CALID GetCalID() const;
```

### <a name="return-value"></a>戻り値

1 つ、[カレンダー識別子](/windows/desktop/Intl/calendar-identifiers)定数。

### <a name="remarks"></a>Remarks

カレンダーの識別子を表しますグレゴリオ暦 (ローカライズ済み)、日本語、イスラム暦など、リージョン固有のカレンダーの予定表。 アプリケーションには、さまざまな言語の関数がサポートされているカレンダーの識別子を使用できます。

このメソッドは、送信、 [MCM_GETCALID](/windows/desktop/Controls/mcm-getcalid)メッセージは、Windows SDK で説明します。

##  <a name="getcolor"></a>  CMonthCalCtrl::GetColor

予定表で指定されたコントロールの 1 か月の領域の色を取得します*nRegion*します。

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>パラメーター

*nRegion*<br/>
色の取得元となる月間予定表コントロールの領域。 値の一覧は、次を参照してください。、 *nRegion*パラメーターの[SetColor](#setcolor)します。

### <a name="return-value"></a>戻り値

A [COLORREF](/windows/desktop/gdi/colorref)成功した場合は、月間予定表コントロールの部分に関連付けられている色を指定する値。 それ以外の場合、このメンバー関数は-1 を返します。

##  <a name="getcurrentview"></a>  CMonthCalCtrl::GetCurrentView

現在の月のカレンダー コントロールで現在表示されているビューを取得します。

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>戻り値

次の値のいずれかで示される現在ビュー:

|[値]|説明|
|-----------|-------------|
|MCMV_MONTH|月単位ビュー|
|MCMV_YEAR|年のビュー|
|MCMV_DECADE|10 年のビュー|
|MCMV_CENTURY|2 桁の年のビュー|

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)メッセージは、Windows SDK で説明します。

### <a name="example"></a>例

次のコード例は、変数を定義します。 `m_monthCalCtrl`、つまり、月間予定表コントロールをプログラムでアクセスするために使用します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>例

1 か月カレンダーを表示する次のコード例のレポート コントロールに現在表示をします。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

##  <a name="getcursel"></a>  CMonthCalCtrl::GetCurSel

現在選択されている日付で示されている、システム時刻を取得します。

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>パラメーター

*refDateTime*<br/>
参照を[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトまたは[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクト。 現在の時刻を受け取ります。

*pDateTime*<br/>
ポインターを[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)現在選択されている日付の情報を受け取る構造体。 このパラメーターは、有効なアドレスである必要があります、NULL にすることはできません。

### <a name="return-value"></a>戻り値

成功した場合、0 以外の場合otherwize 0。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_GETCURSEL](/windows/desktop/Controls/mcm-getcursel)」の説明に従って、Windows SDK。

> [!NOTE]
>  このメンバー関数は、スタイル MCS_MULTISELECT が設定されている場合に失敗します。

MFC の実装で`GetCurSel`、指定することができます、`COleDateTime`の使用状況、`CTime`使用状況、または`SYSTEMTIME`使用状況を構造体します。

##  <a name="getfirstdayofweek"></a>  CMonthCalCtrl::GetFirstDayOfWeek

予定表の左端の列に表示される週の最初の日を取得します。

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>パラメーター

*pbLocal*<br/>
ブール値へのポインター。 コントロールの設定の値が 0 以外の場合に、コントロール パネルの設定が一致しません。

### <a name="return-value"></a>戻り値

週の最初の曜日を表す整数値。 参照してください**解説**整数値の詳細についてはします。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_GETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-getfirstdayofweek)」の説明に従って、Windows SDK。 週の曜日は、としては、次のように、整数として表されます。

|[値]|週の曜日|
|-----------|---------------------|
|0|月曜日|
|1|火曜日|
|2|水曜日|
|3|木曜日|
|4|金曜日|
|5|土曜日|
|6|日曜日|

### <a name="example"></a>例

  例をご覧ください[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)します。

##  <a name="getmaxselcount"></a>  CMonthCalCtrl::GetMaxSelCount

月間予定表コントロールで選択できる日数の現在の最大数を取得します。

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>戻り値

コントロールの選択可能な日の間の合計数を表す整数値。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_GETMAXSELCOUNT](/windows/desktop/Controls/mcm-getmaxselcount)」の説明に従って、Windows SDK。 コントロールには、MCS_MULTISELECT スタイルの設定には、このメンバー関数を使用します。

### <a name="example"></a>例

  例をご覧ください[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)します。

##  <a name="getmaxtodaywidth"></a>  CMonthCalCtrl::GetMaxTodayWidth

現在の月のカレンダー コントロールの"Today"文字列の最大の幅を取得します。

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>戻り値

"Today"内の文字列、ピクセルの幅。

### <a name="example"></a>例

次のコード例は、変数を定義します。 `m_monthCalCtrl`、つまり、月間予定表コントロールをプログラムでアクセスするために使用します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>例

次のコード例に示します、`GetMaxTodayWidth`メソッド。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>Remarks

ユーザーは、"Today"、文字列が、月間予定表コントロールの下部に表示されます をクリックして、現在の日付に戻ることができます。 "Today"文字列には、ラベルのテキストと日付のテキストが含まれています。

このメソッドは、送信、 [MCM_GETMAXTODAYWIDTH](/windows/desktop/Controls/mcm-getmaxtodaywidth)メッセージは、Windows SDK で説明します。

##  <a name="getminreqrect"></a>  CMonthCalCtrl::GetMinReqRect

月間予定表コントロールで完全な月を表示するために必要な最小サイズを取得します。

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>パラメーター

*pRect*<br/>
ポインターを[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)外接する四角形の情報を受信する構造体。 このパラメーターは、有効なアドレスである必要があります、NULL にすることはできません。

### <a name="return-value"></a>戻り値

かどうかは成功すると、このメンバー関数は 0 以外を返すと`lpRect`該当する境界情報を受信します。 失敗した場合、メンバー関数は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_GETMINREQRECT](/windows/desktop/Controls/mcm-getminreqrect)」の説明に従って、Windows SDK。

##  <a name="getmonthdelta"></a>  CMonthCalCtrl::GetMonthDelta

月間予定表コントロールのスクロール速度を取得します。

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>戻り値

月間予定表コントロールのスクロール率。 スクロール率とは、ユーザーがスクロール ボタンを 1 回クリックしたときに、コントロールが表示を移動する月数です。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_GETMONTHDELTA](/windows/desktop/Controls/mcm-getmonthdelta)」の説明に従って、Windows SDK。

##  <a name="getmonthrange"></a>  CMonthCalCtrl::GetMonthRange

日付の月のカレンダー コントロールの表示の高値と安値の制限を表す情報を取得します。

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
参照を[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)または[CTime](../../atl-mfc-shared/reference/ctime-class.md)許可されている日付の最小値を格納しているオブジェクト。

*refMaxRange*<br/>
参照を`COleDateTime`または`CTime`使用できる最大の日付を含むオブジェクト。

*pMinRange*<br/>
ポインターを[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)範囲の最下位の最後に日付を含む構造体。

*pMaxRange*<br/>
ポインター、`SYSTEMTIME`範囲の最上位の最後に日付を含む構造体。

*dwFlags*<br/>
取得する範囲の制限の範囲を指定する値。 この値は、次のいずれかである必要があります。

|[値]|説明|
|-----------|-------------|
|GMR_DAYSTATE|前と末尾の部分的にのみ表示される表示範囲の月が含まれます。|
|GMR_VISIBLE|完全に表示されるか月のみが含まれます。|

### <a name="return-value"></a>戻り値

によって示される 2 つの制限により展開されるか月で、範囲を表す整数を *refMinRange* と *refMaxRange* 最初と 2 番目のバージョン、または*pMinRange* *整数* で 3 番目のバージョン。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_GETMONTHRANGE](/windows/desktop/Controls/mcm-getmonthrange)」の説明に従って、Windows SDK。 MFC の実装で`GetMonthRange`を指定できます`COleDateTime`の使用状況、`CTime`使用状況、または`SYSTEMTIME`使用状況を構造体します。

### <a name="example"></a>例

  例をご覧ください[CMonthCalCtrl::SetDayState](#setdaystate)します。

##  <a name="getrange"></a>  CMonthCalCtrl::GetRange

1 か月カレンダー コントロールに設定する現在の最小値と最大の日付を取得します。

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
ポインターを`COleDateTime`オブジェクト、`CTime`オブジェクト、または[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)範囲の最下位の最後に日付を含む構造体。

*pMaxRange*<br/>
ポインターを`COleDateTime`オブジェクト、`CTime`オブジェクト、または[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)範囲の最上位の最後に日付を含む構造体。

### <a name="return-value"></a>戻り値

DWORD を 0 にすることができます (制限が設定されていない) または制限情報を指定する値は次の組み合わせ。

|[値]|説明|
|-----------|-------------|
|GDTR_MAX|コントロールの最大値を設定します。*整数*が有効であり、適用可能な日付情報が含まれています。|
|GDTR_MIN|コントロールの最小値を設定します。*pMinRange*が有効であり、適用可能な日付情報が含まれています。|

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_GETRANGE](/windows/desktop/Controls/mcm-getrange)」の説明に従って、Windows SDK。 MFC の実装で`GetRange`、指定することができます、`COleDateTime`の使用状況、`CTime`使用状況、または`SYSTEMTIME`使用状況を構造体します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

##  <a name="getselrange"></a>  CMonthCalCtrl::GetSelRange

ユーザーが現在選択されている日付の範囲の上限と下限を表す日付情報を取得します。

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
参照を[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)または[CTime](../../atl-mfc-shared/reference/ctime-class.md)許可されている日付の最小値を格納しているオブジェクト。

*refMaxRange*<br/>
参照を`COleDateTime`または`CTime`使用できる最大の日付を含むオブジェクト。

*pMinRange*<br/>
ポインターを[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)範囲の最下位の最後に日付を含む構造体。

*pMaxRange*<br/>
ポインター、`SYSTEMTIME`範囲の最上位の最後に日付を含む構造体。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_GETSELRANGE](/windows/desktop/Controls/mcm-getselrange)」の説明に従って、Windows SDK。 `GetSelRange` MCS_MULTISELECT スタイルを使用しない月間予定表コントロールに適用される場合は失敗します。

MFC の実装で`GetSelRange`を指定できます`COleDateTime`の使用状況、`CTime`使用状況、または`SYSTEMTIME`使用状況を構造体します。

##  <a name="gettoday"></a>  CMonthCalCtrl::GetToday

月間予定表コントロールの「現在」として指定された日付の日付の情報を取得します。

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>パラメーター

*refDateTime*<br/>
参照を[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)または[CTime](../../atl-mfc-shared/reference/ctime-class.md)現在の日付を示すオブジェクト。

*pDateTime*<br/>
ポインターを[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)日付情報を受け取る構造体。 このパラメーターは、有効なアドレスである必要があります、NULL にすることはできません。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_GETTODAY](/windows/desktop/Controls/mcm-gettoday)」の説明に従って、Windows SDK。 MFC の実装で`GetToday`、指定することができます、`COleDateTime`の使用状況、`CTime`使用状況、または`SYSTEMTIME`使用状況を構造体します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

##  <a name="hittest"></a>  CMonthCalCtrl::HitTest

、のいずれかが指定した位置にある場合は、どの月間予定表コントロールを決定します。

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>パラメーター

*pMCHitTest*<br/>
ポインターを[MCHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-mchittestinfo)月間予定表コントロールのポイントをヒット テストを含む構造体。

### <a name="return-value"></a>戻り値

DWORD 値です。 等しい、 **uHit**のメンバー、`MCHITTESTINFO`構造体。

### <a name="remarks"></a>Remarks

`HitTest` 使用して、`MCHITTESTINFO`ヒット テストに関する情報を格納する構造体。

##  <a name="iscenturyview"></a>  CMonthCalCtrl::IsCenturyView

現在の月のカレンダー コントロールの現在のビューが 2 桁の年のビューであるかどうかを示します。

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>戻り値

現在のビューが、2 桁の年のビューは、TRUE を返します。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)メッセージは、Windows SDK で説明します。 そのメッセージ MCMV_CENTURY を返す場合、このメソッドは TRUE を返します。

##  <a name="isdecadeview"></a>  CMonthCalCtrl::IsDecadeView

現在の月のカレンダー コントロールの現在のビューが 10 年のビューであるかどうかを示します。

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>戻り値

現在のビューが 10 年のビューは、TRUE を返します。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)メッセージは、Windows SDK で説明します。 そのメッセージ MCMV_DECADE を返す場合、このメソッドは TRUE を返します。

##  <a name="ismonthview"></a>  CMonthCalCtrl::IsMonthView

現在の月のカレンダー コントロールの現在のビューが 1 か月のビューであるかどうかを示します。

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>戻り値

現在のビューが月のビューは、TRUE を返します。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)メッセージは、Windows SDK で説明します。 そのメッセージ MCMV_MONTH を返す場合、このメソッドは TRUE を返します。

##  <a name="isyearview"></a>  CMonthCalCtrl::IsYearView

現在の月のカレンダー コントロールの現在のビューがある年のビューであるかどうかを示します。

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>戻り値

現在のビューが年のビューは、TRUE を返します。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)メッセージは、Windows SDK で説明します。 そのメッセージ MCMV_YEAR を返す場合、このメソッドは TRUE を返します。

##  <a name="setcalendarborder"></a>  CMonthCalCtrl::SetCalendarBorder

現在の月のカレンダー コントロールの境界線の幅を設定します。

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*cxyBorder*|[in]ピクセル単位で、罫線の幅。|

### <a name="remarks"></a>Remarks

このメソッドが成功すると、罫線の幅に設定されて、 *cxyBorder*パラメーター。 境界線の幅は、現在指定されている既定値にリセットするそれ以外の場合、[テーマ](/windows/desktop/Controls/visual-styles-overview)テーマが使用されていない場合は 0。

このメソッドは、送信、 [MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder)メッセージは、Windows SDK で説明します。

### <a name="example"></a>例

次のコード例は、変数を定義します。 `m_monthCalCtrl`、つまり、月間予定表コントロールをプログラムでアクセスするために使用します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>例

8 ピクセル、月間予定表の境界線の幅を制御、次のコード例を設定します。 使用して、 [CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)メソッドをこのメソッドが成功したかどうかを判断します。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

##  <a name="setcalendarborderdefault"></a>  CMonthCalCtrl::SetCalendarBorderDefault

現在の月のカレンダー コントロールの枠線の既定の幅を設定します。

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>Remarks

境界線の幅は、現在指定された既定値に設定されて[テーマ](/windows/desktop/Controls/visual-styles-overview)テーマが使用されていない場合は 0。

このメソッドは、送信、 [MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder)メッセージは、Windows SDK で説明します。

##  <a name="setcalid"></a>  CMonthCalCtrl::SetCalID

現在の月のカレンダー コントロールのカレンダーの識別子を設定します。

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*calid*|[in]1 つ、[カレンダー識別子](/windows/desktop/Intl/calendar-identifiers)定数。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

カレンダーの識別子を指定グレゴリオ暦 (ローカライズ済み)、日本語、イスラム暦など、リージョン固有のカレンダーの予定表。 使用して、`SetCalID`メソッドで指定されているカレンダーを表示する、 *calid*パラメーター、予定表を含むロケールがコンピューターにインストールされている場合。

このメソッドは、送信、 [MCM_SETCALID](/windows/desktop/Controls/mcm-setcalid)メッセージは、Windows SDK で説明します。

### <a name="example"></a>例

次のコード例は、変数を定義します。 `m_monthCalCtrl`、つまり、月間予定表コントロールをプログラムでアクセスするために使用します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>例

次のコード例では、和暦カレンダーを表示する月のカレンダー コントロールを設定します。 `SetCalID`メソッドは、その暦がコンピューターにインストールされている場合にのみが成功しました。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

##  <a name="setcenturyview"></a>  CMonthCalCtrl::SetCenturyView

2 桁の年のビューを表示する現在の月のカレンダー コントロールを設定します。

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドを使用して、 [CMonthCalCtrl::SetCurrentView](#setcurrentview)ビューを設定するメソッドを`MCMV_CENTURY`を表す 2 桁の年のビュー。

##  <a name="setcolor"></a>  CMonthCalCtrl::SetColor

月間予定表コントロールの指定した領域の色を設定します。

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>パラメーター

*nRegion*<br/>
1 か月カレンダーを設定する色を指定する整数値。 この値は、次のいずれかを指定できます。

|[値]|説明|
|-----------|-------------|
|MCSC_BACKGROUND|背景色は、数か月間に表示されます。|
|MCSC_MONTHBK|背景色は、1 か月です。|
|MCSC_TEXT|1 か月のテキストを表示するために使用する色です。|
|MCSC_TITLEBK|カレンダーのタイトルに表示される背景色です。|
|MCSC_TITLETEXT|予定表のタイトル内のテキストを表示するために使用する色です。|
|MCSC_TRAILINGTEXT|ヘッダーと末尾の日のテキストを表示するために使用する色です。 ヘッダーと後続の日は、現在の暦に表示される前および次の月単位から日が。|

*ref*<br/>
月間予定表コントロールの指定した部分の新しい色の設定の COLORREF 値。

### <a name="return-value"></a>戻り値

COLORREF 値を表す、月間予定表コントロールの指定した部分の前のカラー設定成功した場合。 それ以外の場合は-1 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_SETCOLOR](/windows/desktop/Controls/mcm-setcolor)」の説明に従って、Windows SDK。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

##  <a name="setcurrentview"></a>  CMonthCalCtrl::SetCurrentView

指定されたビューを表示する現在の月のカレンダー コントロールを設定します。

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*dwNewView*|[in]毎月、毎年、10 年間、または 2 桁の年のビューを指定する値は次のいずれか。<br /><br /> MCMV_MONTH:月単位ビュー<br /><br /> MCMV_YEAR:年のビュー<br /><br /> MCMV_DECADE:10 年のビュー<br /><br /> MCMV_CENTURY:2 桁の年のビュー|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [MCM_SETCURRENTVIEW](/windows/desktop/Controls/mcm-setcurrentview)メッセージは、Windows SDK で説明します。

##  <a name="setcursel"></a>  CMonthCalCtrl::SetCurSel

月間予定表コントロールの現在選択されている日付を設定します。

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
  BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>パラメーター

*refDateTime*<br/>
参照を[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)または[CTime](../../atl-mfc-shared/reference/ctime-class.md)現在選択されている月のカレンダー コントロールを示すオブジェクト。

*pDateTime*<br/>
ポインターを[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)を現在の選択項目として設定する日付を含む構造体。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_SETCURSEL](/windows/desktop/Controls/mcm-setcursel)」の説明に従って、Windows SDK。 MFC の実装で`SetCurSel`、指定することができます、`COleDateTime`の使用状況、`CTime`使用状況、または`SYSTEMTIME`使用状況を構造体します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

##  <a name="setdaystate"></a>  CMonthCalCtrl::SetDayState

月間予定表コントロールでの日付の表示を設定します。

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>パラメーター

*nMonths*<br/>
配列内の要素の数を示す値を*pStates*を指します。

*pStates*<br/>
ポインターを[月数](/windows/desktop/Controls/monthdaystate)月間予定表コントロールの表示で毎日を描画できる方法を定義する値の配列。 月数のデータ型は、(1 ~ 31) の各ビットが 1 か月の 1 日の状態を表す、ビット フィールドです。 対応する日が表示されます、ビットが上にある場合は、太字で。それ以外の場合、太字で表示されます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_SETDAYSTATE](/windows/desktop/Controls/mcm-setdaystate)」の説明に従って、Windows SDK。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

##  <a name="setdecadeview"></a>  CMonthCalCtrl::SetDecadeView

10 年のビューに現在の月のカレンダー コントロールを設定します。

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドを使用して、 [CMonthCalCtrl::SetCurrentView](#setcurrentview)ビューを設定するメソッドを`MCMV_DECADE`、10 年のビューを表します。

##  <a name="setfirstdayofweek"></a>  CMonthCalCtrl::SetFirstDayOfWeek

予定表の左端の列に表示する曜日を設定します。

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>パラメーター

*iDay*<br/>
曜日を表す整数値では、週の最初の曜日として設定します。 この値は、曜日の番号のいずれかを指定する必要があります。 参照してください[については、「](#getfirstdayofweek)の曜日番号の説明。

*lpnOld*<br/>
以前の週の最初の日を示す整数値へのポインターを設定します。

### <a name="return-value"></a>戻り値

LOCALE_IFIRSTDAYOFWEEK の以外の値に設定されている前の最初の日、週の場合 0 以外の場合、これは、日、コントロール パネルの設定に示されているです。 それ以外の場合、この関数は、0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_SETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-setfirstdayofweek)」の説明に従って、Windows SDK。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

##  <a name="setmaxselcount"></a>  CMonthCalCtrl::SetMaxSelCount

月間予定表コントロールで選択できる最大日数を設定します。

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>パラメーター

*nMax*<br/>
選択可能な日数の最大数を表すように設定された値。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_SETMAXSELCOUNT](/windows/desktop/Controls/mcm-setmaxselcount)」の説明に従って、Windows SDK。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

##  <a name="setmonthdelta"></a>  CMonthCalCtrl::SetMonthDelta

月間予定表コントロールのスクロール速度を設定します。

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>パラメーター

*iDelta*<br/>
コントロールのスクロール率として設定するには、数か月の数。 この値が 0 の場合は、1 か月の差分が、コントロールに表示される月の数は、既定値にリセットされます。

### <a name="return-value"></a>戻り値

以前のスクロール率。 スクロール率が設定されていない場合、戻り値は 0 です。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_SETMONTHDELTA](/windows/desktop/Controls/mcm-setmonthdelta)」の説明に従って、Windows SDK。

##  <a name="setmonthview"></a>  CMonthCalCtrl::SetMonthView

1 か月のビューを表示する現在の月のカレンダー コントロールを設定します。

```
BOOL SetMonthView();
```

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドを使用して、 [CMonthCalCtrl::SetCurrentView](#setcurrentview)月のビューを表す MCMV_MONTH にビューを設定します。

### <a name="example"></a>例

次のコード例は、変数を定義します。 `m_monthCalCtrl`、つまり、月間予定表コントロールをプログラムでアクセスするために使用します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>例

次のコード例では、月、年、10 年間、および 2 桁の年のビューを表示する月のカレンダー コントロールを設定します。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

##  <a name="setrange"></a>  CMonthCalCtrl::SetRange

月間予定表コントロールの最小値と最大許容される日付を設定します。

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
ポインターを`COleDateTime`オブジェクト、`CTime`オブジェクト、または[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)範囲の最下位の最後に日付を含む構造体。

*pMaxRange*<br/>
ポインターを`COleDateTime`オブジェクト、`CTime`オブジェクト、または`SYSTEMTIME`範囲の最上位の最後に日付を含む構造体。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_SETRANGE](/windows/desktop/Controls/mcm-setrange)」の説明に従って、Windows SDK。 MFC の実装で`SetRange`を指定できます`COleDateTime`の使用状況、`CTime`使用状況、または`SYSTEMTIME`使用状況を構造体します。

### <a name="example"></a>例

  例をご覧ください[CMonthCalCtrl::GetRange](#getrange)します。

##  <a name="setselrange"></a>  CMonthCalCtrl::SetSelRange

指定した日付範囲を 1 か月カレンダーの選択コントロールを設定します。

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
ポインターを`COleDateTime`オブジェクト、`CTime`オブジェクト、または[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)範囲の最下位の最後に日付を含む構造体。

*pMaxRange*<br/>
ポインターを`COleDateTime`オブジェクト、`CTime`オブジェクト、または`SYSTEMTIME`範囲の最上位の最後に日付を含む構造体。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_SETSELRANGE](/windows/desktop/Controls/mcm-setselrange)」の説明に従って、Windows SDK。 MFC の実装で`SetSelRange`を指定できます`COleDateTime`の使用状況、`CTime`使用状況、または`SYSTEMTIME`使用状況を構造体します。

##  <a name="settoday"></a>  CMonthCalCtrl::SetToday

現在の日付の予定表コントロールを設定します。

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
  void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>パラメーター

*refDateTime*<br/>
参照を[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)現在の日付を格納しているオブジェクト。

*pDateTime*<br/>
2 番目のバージョンへのポインターで、 [CTime](../../atl-mfc-shared/reference/ctime-class.md)現在の日付情報を含むオブジェクト。 3 番目のバージョンへのポインターを[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)現在の日付情報を含む構造体。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[MCM_SETTODAY](/windows/desktop/Controls/mcm-settoday)」の説明に従って、Windows SDK。

### <a name="example"></a>例

  例をご覧ください[CMonthCalCtrl::GetToday](#gettoday)します。

##  <a name="setyearview"></a>  CMonthCalCtrl::SetYearView

年のビューに現在の月のカレンダー コントロールを設定します。

```
BOOL SetYearView();
```

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドを使用して、 [CMonthCalCtrl::SetCurrentView](#setcurrentview) MCMV_YEAR で、年間のビューを表しますにビューを設定します。

##  <a name="sizeminreq"></a>  CMonthCalCtrl::SizeMinReq

表示、最小限の予定表コントロールのサイズを 1 か月には、1 か月が表示されます。

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>パラメーター

*bRepaint*<br/>
コントロールが再描画するかどうかを指定します。 既定では、次のように TRUE です。 FALSE の場合、再描画は行われません。

### <a name="return-value"></a>戻り値

月間予定表コントロールのサイズは最小にする場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

呼び出す`SizeMinReq`正常に 1 か月のカレンダーの月単位の予定表コントロールが表示されます。

##  <a name="sizerecttomin"></a>  CMonthCalCtrl::SizeRectToMin

現在の月間予定表コントロールで、指定した四角形に収まるすべてのカレンダーを含むことのできる最も小さな四角形を計算します。

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*lpRect*|[in]ポインターを[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)カレンダーの必要な数を含む四角形を定義する構造体。|

### <a name="return-value"></a>戻り値

ポインターを[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)によってサイズが小さい四角形、四角形を定義する構造が定義されている、 *lpRect*パラメーター。

### <a name="remarks"></a>Remarks

このメソッドは計算によって指定される四角形に収まる数カレンダー、 *lpRect*パラメーター、し、その数のカレンダーを含むことのできる最も小さな四角形を返します。 実際には、このメソッドは、カレンダーの必要な数に合うように指定した四角形を縮小します。

このメソッドは、送信、 [MCM_SIZERECTTOMIN](/windows/desktop/Controls/mcm-sizerecttomin)メッセージは、Windows SDK で説明します。

## <a name="see-also"></a>関連項目

[MFC サンプル CMNCTRL1](../../visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl クラス](../../mfc/reference/cdatetimectrl-class.md)
