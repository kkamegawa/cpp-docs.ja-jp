---
title: CDateTimeCtrl クラス
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
ms.openlocfilehash: 5acac454bd0b22b994b74a052bd3cf0b0eee2614
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894342"
---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl クラス

日時指定コントロールの機能がカプセル化されています。

## <a name="syntax"></a>構文

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|`CDateTimeCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|現在の日付と時刻の選択コントロールを閉じます。|
|[CDateTimeCtrl::Create](#create)|日付と時刻の選択コントロールを作成しにアタッチします、`CDateTimeCtrl`オブジェクト。|
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|現在の日付と時刻の選択コントロールに関する情報を取得します。|
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|現在の日付または時刻を表示するために必要な日付と時刻の選択コントロールの適切なサイズを返します。|
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|月間予定表、日付と時刻の選択コントロール内の特定の部分の色を取得します。|
|[CDateTimeCtrl::GetMonthCalCtrl](#getmonthcalctrl)|取得、`CMonthCalCtrl`日付と時刻の選択コントロールに関連付けられているオブジェクト。|
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|現在日時指定コントロールの子月間予定表コントロールで使用するフォントを取得します。|
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|現在の日付と時刻の選択コントロールのスタイルを取得します。|
|[CDateTimeCtrl::GetRange](#getrange)|日付と時刻の選択コントロールのシステム時刻が許可されている現在の最小と最大値を取得します。|
|[CDateTimeCtrl::GetTime](#gettime)|日付と時刻の選択コントロールから現在選択されている時刻を取得し、指定した配置`SYSTEMTIME`構造体。|
|[CDateTimeCtrl::SetFormat](#setformat)|指定した書式指定文字列に従って日付と時刻の選択コントロールの表示を設定します。|
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|月間予定表の日付と時刻の選択コントロール内の特定の部分の色を設定します。|
|[CDateTimeCtrl::SetMonthCalFont](#setmonthcalfont)|日時指定コントロールの子月間予定表コントロールで使用するフォントを設定します。|
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|現在の日付と時刻の選択コントロールのスタイルを設定します。|
|[CDateTimeCtrl::SetRange](#setrange)|日付と時刻の選択コントロールの最小値と最大の許可されているシステム時刻を設定します。|
|[CDateTimeCtrl::SetTime](#settime)|日付と時刻の選択コントロールで、時間を設定します。|

## <a name="remarks"></a>Remarks

日付と時刻の選択コントロール (DTP コントロール) では、ユーザーに日付と時刻の情報を交換する単純なインターフェイスを提供します。 このインターフェイスには、コントロールに格納されている日付と時刻の情報の一部を表示フィールドが含まれています。 ユーザーには、特定のフィールドに文字列の内容を変更することで、コントロールに格納されている情報を変更できます。 ユーザーは、フィールドをマウスまたはキーボードを使用して移動できます。

作成するときに、オブジェクトにさまざまなスタイルを適用することで、日付と時刻の選択コントロールをカスタマイズできます。 参照してください[日付と時刻の選択コントロールのスタイル](/windows/desktop/Controls/date-and-time-picker-control-styles)日付と時刻の選択コントロールに固有のスタイルの詳細については、Windows sdk。 形式のスタイルを使用して DTP コントロールの表示形式を設定することができます。 これらの書式スタイルが Windows SDK のトピックで「スタイルの形式」で説明されている[日付と時刻の選択コントロールのスタイル](/windows/desktop/Controls/date-and-time-picker-control-styles)します。

日付と時刻の選択コントロールは、通知とは、後述のコールバックにも使用[を使用して CDateTimeCtrl](../../mfc/using-cdatetimectrl.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdtctl.h

##  <a name="cdatetimectrl"></a>  CDateTimeCtrl::CDateTimeCtrl

`CDateTimeCtrl` オブジェクトを構築します。

```
CDateTimeCtrl();
```

##  <a name="closemonthcal"></a>  CDateTimeCtrl::CloseMonthCal

現在の日付と時刻の選択コントロールを閉じます。

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [DTM_CLOSEMONTHCAL](/windows/desktop/Controls/dtm-closemonthcal)メッセージは、Windows SDK で説明します。

### <a name="example"></a>例

次のコード例は、変数を定義します。 *m_dateTimeCtrl*、つまり、日付と時刻の選択コントロールをプログラムでアクセスするために使用します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>例

次のコード例では、現在の日付と時刻の選択コントロールのドロップダウンの予定表を閉じます。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

##  <a name="create"></a>  CDateTimeCtrl::Create

日付と時刻の選択コントロールを作成しにアタッチします、`CDateTimeCtrl`オブジェクト。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
日付コントロールのスタイルの組み合わせを指定します。 参照してください[日付と時刻の選択コントロールのスタイル](/windows/desktop/Controls/date-and-time-picker-control-styles)日付と時刻の選択コントロール スタイルの詳細については、Windows SDK に含まれています。

*rect*<br/>
参照を[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)日付と時刻の選択コントロールのサイズと位置である構造体。

*pParentWnd*<br/>
ポインターを[CWnd](../../mfc/reference/cwnd-class.md)オブジェクトは、日付と時刻の選択コントロールの親ウィンドウです。 NULL は指定できません。

*nID*<br/>
日時指定コントロールのコントロール ID を指定します

### <a name="return-value"></a>戻り値

作成が成功した場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

##### <a name="to-create-a-date-and-time-picker-control"></a>日付と時刻の選択コントロールを作成するには

1. 呼び出す[CDateTimeCtrl](#cdatetimectrl)を構築する、`CDateTimeCtrl`オブジェクト。

1. このメンバー関数は、Windows の日付と時刻の選択コントロールの作成およびにアタッチしますを呼び出す、`CDateTimeCtrl`オブジェクト。

呼び出すと`Create`、一般的なコントロールが初期化されます。

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
|*pDateTimePickerInfo*|[out]ポインターを[DATETIMEPICKERINFO](/windows/desktop/api/commctrl/ns-commctrl-tagdatetimepickerinfo)を現在の日付と時刻の選択コントロールの説明を受け取る構造体。<br /><br /> 呼び出し元がこの構造体を割り当てる責任を負います。 ただし、このメソッドを初期化します、 *cbSize*構造体のメンバー。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [DTM_GETDATETIMEPICKERINFO](/windows/desktop/Controls/dtm-getdatetimepickerinfo)メッセージは、Windows SDK で説明します。

### <a name="example"></a>例

次のコード例は、変数を定義します。 *m_dateTimeCtrl*、つまり、日付と時刻の選択コントロールをプログラムでアクセスするために使用します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>例

次のコード例では、現在の日付と時刻の選択コントロールに関する情報が正常に取得するかどうかを示します。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

##  <a name="getmonthcalcolor"></a>  CDateTimeCtrl::GetMonthCalColor

月間予定表、日付と時刻の選択コントロール内の特定の部分の色を取得します。

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>パラメーター

*iColor*<br/>
**Int**を取得する月のカレンダーの色領域を指定する値。 値の一覧は、次を参照してください。、 *iColor*パラメーター [SetMonthCalColor](#setmonthcalcolor)します。

### <a name="return-value"></a>戻り値

成功した場合は、月間予定表のコントロールの指定した部分の色の設定を表す COLORREF 値。 関数は、失敗した場合は-1 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[DTM_GETMCCOLOR](/windows/desktop/Controls/dtm-getmccolor)」の説明に従って、Windows SDK。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

##  <a name="getmonthcalctrl"></a>  CDateTimeCtrl::GetMonthCalCtrl

取得、`CMonthCalCtrl`日付と時刻の選択コントロールに関連付けられているオブジェクト。

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>戻り値

ポインターを[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)オブジェクト、または失敗した場合、またはウィンドウが表示されない場合は NULL です。

### <a name="remarks"></a>Remarks

日付と時刻の選択コントロールは、ユーザーがドロップダウンの矢印をクリックすると、月間予定表の子コントロールを作成します。 ときに、`CMonthCalCtrl`オブジェクトが不要、破棄すると、アプリケーションは必要があります、日時指定コントロールの子か月カレンダーを表すオブジェクトを格納するのには依存しないようにします。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

##  <a name="getmonthcalfont"></a>  CDateTimeCtrl::GetMonthCalFont

現在日時指定コントロールの月間予定表コントロールで使用するフォントを取得します。

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>戻り値

ポインターを[CFont](../../mfc/reference/cfont-class.md)オブジェクト、または失敗した場合は NULL です。

### <a name="remarks"></a>Remarks

`CFont`戻り値によってポイントされるオブジェクトは一時オブジェクトし、[次へ] のアイドル状態の処理時に破棄します。

##  <a name="getmonthcalstyle"></a>  CDateTimeCtrl::GetMonthCalStyle

現在の日付と時刻の選択コントロールに関連付けられているドロップダウン リストの月間予定表コントロールのスタイルを取得します。

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>戻り値

日付と時刻の選択コントロールのスタイルのビットごとの組み合わせであるドロップダウン リストの月間予定表コントロールの (または) スタイル。 詳細については、次を参照してください。[月間予定表コントロールのスタイル](/windows/desktop/Controls/month-calendar-control-styles)します。

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [DTM_GETMCSTYLE](/windows/desktop/Controls/dtm-getmcstyle)メッセージは、Windows SDK で説明します。

##  <a name="getrange"></a>  CDateTimeCtrl::GetRange

日付と時刻の選択コントロールのシステム時刻が許可されている現在の最小と最大値を取得します。

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
ポインターを[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトまたは[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトで許可されている最も早い時刻を含む、`CDateTimeCtrl`オブジェクト。

*pMaxRange*<br/>
ポインターを`COleDateTime`オブジェクトまたは`CTime`オブジェクトで許可されている最新の時刻を含む、`CDateTimeCtrl`オブジェクト。

### <a name="return-value"></a>戻り値

設定されている範囲を示すフラグを含む DWORD 値です。 If

`return value & GDTR_MAX` == 0

2 番目のパラメーターは有効です。 同様に場合、

`return value & GDTR_MIN` == 0

最初のパラメーターは有効です。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[DTM_GETRANGE](/windows/desktop/Controls/dtm-getrange)」の説明に従って、Windows SDK。 MFC の実装で、いずれかを指定できます`COleDateTime`または`CTime`使用法。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

##  <a name="gettime"></a>  CDateTimeCtrl::GetTime

日付と時刻の選択コントロールから現在選択されている時刻を取得し、指定した配置`SYSTEMTIME`構造体。

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>パラメーター

*timeDest*<br/>
最初のバージョンへの参照を[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)システム時刻の情報を受け取るオブジェクト。 2 番目のバージョンへの参照で、 [CTime](../../atl-mfc-shared/reference/ctime-class.md)システム時刻の情報を受け取るオブジェクト。

*pTimeDest*<br/>
ポインター、 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)システム時刻の情報を受け取る構造体。 NULL は指定できません。

### <a name="return-value"></a>戻り値

時間が正常に書き込む場合は 0 以外の最初のバージョンで、`COleDateTime`オブジェクト。 それ以外の場合、0。 2 番目と 3 番目のバージョンでは、DWORD 値と等しく、 *dwFlag*セットのメンバー、[戻り](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange)構造体。 参照してください、**解説**詳細については後述します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[DTM_GETSYSTEMTIME](/windows/desktop/Controls/dtm-getsystemtime)」の説明に従って、Windows SDK。 MFC 実装で`GetTime`、使用することができます`COleDateTime`または`CTime`クラス、またはを使用できる、`SYSTEMTIME`時刻情報を格納するための構造。

戻り値の DWORD 2 番目と 3 番目のバージョン以降、かどうか、日付と時刻の選択コントロールに設定を示します「日付なし」状態に記載されている、[戻り](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange)構造体メンバー *dwFlags*. 返される値に等しい GDT_NONE、コントロールは「日付なし」の状態に設定されているし、DTS_SHOWNONE スタイルを使用します。 返される値には、戻りが達すると、システム時刻が正常に変換先の場所に格納されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

##  <a name="getidealsize"></a>  CDateTimeCtrl::GetIdealSize

現在の日付または時刻を表示するために必要な日付と時刻の選択コントロールの適切なサイズを返します。

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*psize*|[out]ポインターを[サイズ](/windows/desktop/api/windef/ns-windef-tagsize)コントロールの適切なサイズを含む構造体。|

### <a name="return-value"></a>戻り値

戻り値は、常に TRUE です。

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [DTM_GETIDEALSIZE](/windows/desktop/Controls/dtm-getidealsize)メッセージは、Windows SDK で説明します。

### <a name="example"></a>例

次のコード例は、変数を定義します。 *m_dateTimeCtrl*、つまり、日付と時刻の選択コントロールをプログラムでアクセスするために使用します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>例

次のコード例では、日付と時刻の選択コントロールを表示する適切なサイズを取得します。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

##  <a name="setformat"></a>  CDateTimeCtrl::SetFormat

指定した書式指定文字列に従って日付と時刻の選択コントロールの表示を設定します。

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>パラメーター

*pstrFormat*<br/>
必要な表示を定義する 0 で終わる書式文字列へのポインター。 このパラメーターを NULL に設定すると、現在のスタイルの既定の書式指定文字列に、コントロールがリセットされます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

> [!NOTE]
>  ユーザー入力は、この呼び出しの成功または失敗を特定できません。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[DTM_SETFORMAT](/windows/desktop/Controls/dtm-setformat)」の説明に従って、Windows SDK。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

##  <a name="setmonthcalcolor"></a>  CDateTimeCtrl::SetMonthCalColor

月間予定表の日付と時刻の選択コントロール内の特定の部分の色を設定します。

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>パラメーター

*iColor*<br/>
**int**を設定する月間予定表コントロールの領域を指定する値。 この値は、次のいずれかを指定できます。

|[値]|説明|
|-----------|-------------|
|MCSC_BACKGROUND|数か月間に表示される背景色を設定します。|
|MCSC_MONTHBK|1 か月内に表示される背景色を設定します。|
|MCSC_TEXT|1 か月のテキストの表示に使用する色を設定します。|
|MCSC_TITLEBK|カレンダーのタイトルに表示される背景色を設定します。|
|MCSC_TITLETEXT|予定表のタイトル内のテキストを表示するために使用する色を設定します。|
|MCSC_TRAILINGTEXT|ヘッダーと末尾の日付のテキスト表示に使用する色を設定します。 ヘッダーと後続の日は、現在の暦に表示される前および次の月単位から日が。|

*ref*<br/>
月間予定表の指定された領域に設定される色を表す COLORREF 値。

### <a name="return-value"></a>戻り値

成功した場合は、月間予定表のコントロールの指定した部分の前の色の設定を表す COLORREF 値。 それ以外の場合、メッセージは、-1 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[DTM_SETMCCOLOR](/windows/desktop/Controls/dtm-setmccolor)」の説明に従って、Windows SDK。

### <a name="example"></a>例

  例をご覧ください[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)します。

##  <a name="setmonthcalfont"></a>  CDateTimeCtrl::SetMonthCalFont

日時指定コントロールの子月間予定表コントロールで使用するフォントを設定します。

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>パラメーター

*hFont*<br/>
設定されるフォントへのハンドルします。

*bRedraw*<br/>
フォントを設定したときに、コントロールをすぐに描画する必要があるかどうかを指定します。 このパラメーターを TRUE に設定すると、自動的に再描画するコントロール。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[DTM_SETMCFONT](/windows/desktop/Controls/dtm-setmcfont)」の説明に従って、Windows SDK。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
>  このコードを使用する場合は、メンバーにするたい、 `CDialog`-という名前のクラスを派生*m_MonthFont*型の`CFont`します。

##  <a name="setmonthcalstyle"></a>  CDateTimeCtrl::SetMonthCalStyle

現在の日付と時刻の選択コントロールに関連付けられているドロップダウン リストの月間予定表コントロールのスタイルを設定します。

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*dwStyle*|[in]予定表コントロールのスタイルは、1 か月カレンダー コントロールのスタイルのビットごとの組み合わせ (OR) は、新しい 1 か月です。 詳細については、次を参照してください。[月間予定表コントロールのスタイル](/windows/desktop/Controls/month-calendar-control-styles)します。|

### <a name="return-value"></a>戻り値

ドロップダウン リストの月間予定表コントロールの以前のスタイル。

### <a name="remarks"></a>Remarks

このメソッドは、送信、 [DTM_SETMCSTYLE](/windows/desktop/Controls/dtm-setmcstyle)メッセージは、Windows SDK で説明します。

### <a name="example"></a>例

次のコード例は、変数を定義します。 *m_dateTimeCtrl*、つまり、日付と時刻の選択コントロールをプログラムでアクセスするために使用します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>例

次のコード例では、週番号、曜日、および指標を表示しない今日の日の省略名を表示する日付と時刻の選択コントロールを設定します。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

##  <a name="setrange"></a>  CDateTimeCtrl::SetRange

日付と時刻の選択コントロールの最小値と最大の許可されているシステム時刻を設定します。

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
ポインターを[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトまたは[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトで許可されている最も早い時刻を含む、`CDateTimeCtrl`オブジェクト。

*pMaxRange*<br/>
ポインターを`COleDateTime`オブジェクトまたは`CTime`オブジェクトで許可されている最新の時刻を含む、`CDateTimeCtrl`オブジェクト。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[DTM_SETRANGE](/windows/desktop/Controls/dtm-setrange)」の説明に従って、Windows SDK。 MFC の実装で、いずれかを指定できます`COleDateTime`または`CTime`使用法。 場合、`COleDateTime`オブジェクトが NULL の状態、範囲が削除されます。 場合、`CTime`ポインター、または`COleDateTime`ポインターが NULL、範囲が削除されます。

### <a name="example"></a>例

  例をご覧ください[CDateTimeCtrl::GetRange](#getrange)します。

##  <a name="settime"></a>  CDateTimeCtrl::SetTime

日付と時刻の選択コントロールで、時間を設定します。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>パラメーター

*timeNew*<br/>
参照を[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトを含む、コントロールを設定します。

*pTimeNew*<br/>
2 番目のバージョンへのポインターの上で、 [CTime](../../atl-mfc-shared/reference/ctime-class.md)コントロールを設定する時刻を含むオブジェクト。 3 番目のバージョンへのポインターの上で、 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)コントロールを設定する時刻を含む構造体。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Win32 メッセージの動作を実装[DTM_SETSYSTEMTIME](/windows/desktop/Controls/dtm-setsystemtime)」の説明に従って、Windows SDK。 MFC 実装で`SetTime`、使用することができます、`COleDateTime`または`CTime`クラス、またはを使用できる、`SYSTEMTIME`構造体には、時間情報を設定します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>関連項目

[MFC サンプル CMNCTRL1](../../visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl クラス](../../mfc/reference/cmonthcalctrl-class.md)
