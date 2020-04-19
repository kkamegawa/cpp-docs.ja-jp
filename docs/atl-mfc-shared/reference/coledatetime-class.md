---
title: COleDateTime クラス
ms.date: 03/27/2019
f1_keywords:
- COleDateTime
- ATLCOMTIME/ATL::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::Format
- ATLCOMTIME/ATL::COleDateTime::GetAsDBTIMESTAMP
- ATLCOMTIME/ATL::COleDateTime::GetAsSystemTime
- ATLCOMTIME/ATL::COleDateTime::GetAsUDATE
- ATLCOMTIME/ATL::COleDateTime::GetCurrentTime
- ATLCOMTIME/ATL::COleDateTime::GetDay
- ATLCOMTIME/ATL::COleDateTime::GetDayOfWeek
- ATLCOMTIME/ATL::COleDateTime::GetDayOfYear
- ATLCOMTIME/ATL::COleDateTime::GetHour
- ATLCOMTIME/ATL::COleDateTime::GetMinute
- ATLCOMTIME/ATL::COleDateTime::GetMonth
- ATLCOMTIME/ATL::COleDateTime::GetSecond
- ATLCOMTIME/ATL::COleDateTime::GetStatus
- ATLCOMTIME/ATL::COleDateTime::GetYear
- ATLCOMTIME/ATL::COleDateTime::ParseDateTime
- ATLCOMTIME/ATL::COleDateTime::SetDate
- ATLCOMTIME/ATL::COleDateTime::SetDateTime
- ATLCOMTIME/ATL::COleDateTime::SetStatus
- ATLCOMTIME/ATL::COleDateTime::SetTime
- ATLCOMTIME/ATL::COleDateTime::m_dt
- ATLCOMTIME/ATL::COleDateTime::m_status
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
ms.openlocfilehash: a254019d1efe916365799affa3d2c5271883bafb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491257"
---
# <a name="coledatetime-class"></a>COleDateTime クラス

OLE オートメーションで使用されるデータ型をカプセル化します。`DATE`

## <a name="syntax"></a>構文

```
class COleDateTime
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleDateTime:: COleDateTime](#coledatetime)|`COleDateTime` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleDateTime:: Format](#format)|`COleDateTime`オブジェクトの書式設定された文字列形式を生成します。|
|[COleDateTime:: GetAsDBTIMESTAMP](#getasdbtimestamp)|`COleDateTime`オブジェクトの時刻を`DBTIMESTAMP`データ構造体として取得するには、このメソッドを呼び出します。|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|このメソッドを呼び出して、オブジェクトの`COleDateTime`時刻を[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)データ構造体として取得します。|
|[COleDateTime:: GetAsUDATE](#getasudate)|`UDATE`データ構造体としての時間を`COleDateTime`取得するには、このメソッドを呼び出します。|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|現在の`COleDateTime`時刻 (静的メンバー関数) を表すオブジェクトを作成します。|
|[COleDateTime:: GetDay](#getday)|この`COleDateTime`オブジェクトが表す日 (1-31) を返します。|
|[COleDateTime:: GetDayOfWeek](#getdayofweek)|この`COleDateTime`オブジェクトが表す曜日 (日曜日 = 1) を返します。|
|[COleDateTime:: GetDayOfYear](#getdayofyear)|この`COleDateTime`オブジェクトが表す年の日付を返します (1 月1日 = 1)。|
|[COleDateTime:: Gethour:](#gethour)|この`COleDateTime`オブジェクトが表す時間 (0-23) を返します。|
|[COleDateTime:: GetMinute](#getminute)|この`COleDateTime`オブジェクトが表す分 (0-59) を返します。|
|[COleDateTime:: GetMonth](#getmonth)|この`COleDateTime`オブジェクトが表す月を返します (1-12)。|
|[COleDateTime:: GetSecond](#getsecond)|この`COleDateTime`オブジェクトが表す2番目のオブジェクト (0-59) を返します。|
|[COleDateTime:: GetStatus](#getstatus)|この`COleDateTime`オブジェクトの状態 (有効) を取得します。|
|[COleDateTime:: GetYear](#getyear)|この`COleDateTime`オブジェクトが表す年を返します。|
|[COleDateTime::P arseDateTime](#parsedatetime)|文字列から日付/時刻値を読み取り、の`COleDateTime`値を設定します。|
|[COleDateTime:: SetDate](#setdate)|この`COleDateTime`オブジェクトの値を、指定した日付専用の値に設定します。|
|[COleDateTime:: SetDateTime](#setdatetime)|この`COleDateTime`オブジェクトの値を、指定した日付/時刻値に設定します。|
|[COleDateTime:: SetStatus](#setstatus)|この`COleDateTime`オブジェクトの状態 (有効性) を設定します。|
|[COleDateTime:: SetTime](#settime)|この`COleDateTime`オブジェクトの値を、指定した時間専用の値に設定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[COleDateTime:: operator = =、COleDateTime:: operator < など。](#coledatetime_relational_operators)|2つ`COleDateTime`の値を比較します。|
|[COleDateTime:: operator +, COleDateTime:: operator-](#operator_add_-)|値を加算`COleDateTime`および減算します。|
|[COleDateTime:: operator + =、COleDateTime:: operator-=](#operator_add_eq_-_eq)|`COleDateTime` この`COleDateTime`オブジェクトの値を加算および減算します。|
|[COleDateTime:: operator =](#operator_eq)|値を`COleDateTime`コピーします。|
|[COleDateTime:: operator DATE、COleDateTime:: operator Date *](#operator_date)|値`COleDateTime` を`DATE`または`DATE*`に変換します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[COleDateTime:: m_dt](#m_dt)|`DATE` この`COleDateTime`オブジェクトの基になるを格納します。|
|[COleDateTime:: m_status](#m_status)|この`COleDateTime`オブジェクトの状態を格納します。|

## <a name="remarks"></a>Remarks

`COleDateTime`に基底クラスがありません。

これは、OLE オートメーションの[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)データ型に使用できる型の1つです。 値`COleDateTime`は、絶対日付と時刻の値を表します。

型`DATE`は、浮動小数点値として実装されます。 日数は、1899年12月30日午前0時に測定されます。 次の表に、日付とそれに関連付けられた値を示します。

|Date|[値]|
|----------|-----------|
|1899年12月29日午前0時|-1.0|
|1899年12月29日、6. M|-1.25|
|1899年12月30日午前0時|0.0|
|1899年12月31日午前0時|1|
|1900年1月1日、午前6時|2.25|

> [!CAUTION]
> 上の表では、日の値が1899年12月30日の午前0時よりも負の値になりますが、時刻の値にはなりません。 たとえば、日付を表す整数が正 (12 月 1899 30 日以降) または負 (12 月 1899 30 日より前) であるかどうかにかかわらず、6:00 AM は常に小数値0.25 によって表されます。 これは、単純な浮動小数点比較では、 `COleDateTime` 12/29/1899 上の 6:00 am を表すを、同じ日に 7:00 AM を表すものとして誤って並べ替えられることを意味します。

クラス`COleDateTime`は、100年1月1日から9999年12月31日までの日付を処理します。 クラス`COleDateTime`はグレゴリオ暦を使用します。ユリウス暦はサポートしていません。 `COleDateTime`夏時間を無視します。 (日付[と時刻を参照:オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。)

> [!NOTE]
> 形式を使用する`%y`と、1900から始まる日付の場合にのみ、2桁の年を取得できます。 1900より前の`%y`日付で形式を使用すると、コードによってアサートエラーが生成されます。

この型は、日付のみまたは時間専用の値を表すためにも使用されます。 慣例により、日付 0 (1899 年12月30日) が時間のみの値に使用され、時刻 00:00 (午前0時) が日付専用の値に使用されます。

100未満の日付`COleDateTime`を使用してオブジェクトを作成した場合、その日付は受け入れられますが、 `GetDay`、、 `GetMinute`、 `GetHour`、 `GetSecond` 、およびへの後続の`GetMonth`呼び出しは失敗し、-1 を`GetYear`返します。 以前は、2桁の日付を使用できましたが、MFC 4.2 以降では、日付は100以上である必要があります。

問題を回避するには、4桁の日付を指定します。 例:

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

`COleDateTime`値の基本算術演算では、コンパニオンクラス[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)が使用されます。 `COleDateTimeSpan`値は時間間隔を定義します。 これらのクラス間のリレーションシップは、 [CTime](../../atl-mfc-shared/reference/ctime-class.md)と[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)の間の関係に似ています。

クラスと`COleDateTime` `COleDateTimeSpan`クラスの詳細については、「日付と時刻:[オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。

## <a name="requirements"></a>必要条件

**ヘッダー:** ATLComTime .h

##  <a name="coledatetime_relational_operators"></a>COleDateTime 関係演算子

比較演算子。

```
bool operator==(const COleDateTime& date) const throw();
bool operator!=(const COleDateTime& date) const throw();
bool operator<(const COleDateTime& date) const throw();
bool operator>(const COleDateTime& date) const throw();
bool operator<=(const COleDateTime& date) const throw();
bool operator>=(const COleDateTime& date) const throw();
```

### <a name="parameters"></a>パラメーター

*date*<br/>
比較される `COleDateTime` オブジェクト。

### <a name="remarks"></a>Remarks

> [!NOTE]
>  2つのオペランドのいずれかが無効な場合、ATLASSERT が発生します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>例

演算子 **>=** 、 **\<=** 、 **>** 、および **<** 、場合、アサートは、`COleDateTime`オブジェクトの設定を null にします。

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

##  <a name="coledatetime"></a>COleDateTime:: COleDateTime

`COleDateTime` オブジェクトを構築します。

```
COleDateTime() throw();
COleDateTime(const VARIANT& varSrc) throw();
COleDateTime(DATE dtSrc) throw();
COleDateTime(time_t timeSrc) throw();
COleDateTime(__time64_t timeSrc) throw();
COleDateTime(const SYSTEMTIME& systimeSrc) throw();
COleDateTime(const FILETIME& filetimeSrc) throw();

COleDateTime(int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();

COleDateTime(WORD wDosDate,
    WORD wDosTime) throw();
COleDateTime(const DBTIMESTAMP& timeStamp) throw();
```

### <a name="parameters"></a>パラメーター

*dateSrc*<br/>
`COleDateTime` 新しい`COleDateTime`オブジェクトにコピーされる既存のオブジェクト。

*varSrc*<br/>
日付/ `VARIANT`時刻値 (VT_DATE) `COleVariant`に変換して新しい`COleDateTime`オブジェクトにコピーする既存のデータ構造 (場合によってはオブジェクト)。

*dtSrc*<br/>
`DATE`新しい`COleDateTime`オブジェクトにコピーされる日付/時刻 () 値。

*timeSrc*<br/>
日付/ `__time64_t`時刻値に変換され、新しい`COleDateTime`オブジェクトにコピーされる値または値。`time_t`

*systimeSrc*<br/>
日付/時刻値に変換され、新しい`COleDateTime`オブジェクトにコピーされる構造体。`SYSTEMTIME`

*filetimeSrc*<br/>
日付/時刻値に変換され、新しい`COleDateTime`オブジェクトにコピーされる構造体。`FILETIME` は`FILETIME`世界協定時刻 (UTC) を使用するため、構造体にローカル時刻を渡すと、結果は正しくありません。 詳細については、「Windows SDK の[ファイル時刻](/windows/win32/SysInfo/file-times)」を参照してください。

*Nyear*、 *nyear*、 *nyear*、 *nyear*、 *nyear*、 *nSec*<br/>
新しい`COleDateTime`オブジェクトにコピーする日付と時刻の値を示します。

*Wdosdate*、 *wDosTime*<br/>
日付/時刻値に変換され、新しい`COleDateTime`オブジェクトにコピーされる MS-DOS の日付と時刻の値。

*タイムスタンプ*<br/>
現在の現地時刻を格納している[Dbtimestamp](/dotnet/api/system.data.oledb.oledbtype)構造体への参照。

### <a name="remarks"></a>Remarks

これらのすべてのコンストラクター `COleDateTime`は、指定された値に初期化された新しいオブジェクトを作成します。 次の表は、各日付と時刻のコンポーネントの有効な範囲を示しています。

|日付/時刻コンポーネント|有効範囲|
|--------------------------|-----------------|
|年|100 - 9999|
|月|0 - 12|
|日|0 - 31|
|時|0 - 23|
|数分|0 - 59|
|second|0 - 59|

日の部分の実際の上限は、月と年のコンポーネントによって異なることに注意してください。 詳細について`SetDate`は、「」または`SetDateTime` 「メンバー関数」を参照してください。

各コンストラクターの簡単な説明を次に示します。

- `COleDateTime(` **)** 0 に`COleDateTime`初期化されたオブジェクトを構築します (1899 年12月30日午前0時)。

- `COleDateTime(`) 既存`COleDateTime`のオブジェクトからオブジェクトを構築します。 `dateSrc` `COleDateTime`

- `COleDateTime(`*Varsrc* **)** オブジェクトを`COleDateTime`構築します。 構造体または[COleVariant](../../mfc/reference/colevariant-class.md)オブジェクトから日付/時刻 ( `VT_DATE`) 値への変換を試みます。 `VARIANT` この変換が成功した場合は、変換後の値が`COleDateTime`新しいオブジェクトにコピーされます。 そうでない場合、 `COleDateTime`オブジェクトの値は 0 (午前0時、1899年12月30日) に設定され、その状態は無効になります。

- `COleDateTime(`) 値から`COleDateTime`オブジェクトを構築します。 `DATE` `dtSrc`

- `COleDateTime(`) 値から`COleDateTime`オブジェクトを構築します。 `time_t` `timeSrc`

- `COleDateTime(`*systimeSrc* `COleDateTime` )値`SYSTEMTIME`からオブジェクトを構築します。

- `COleDateTime(`) 値から`COleDateTime`オブジェクトを構築します。 `FILETIME` `filetimeSrc` . は`FILETIME`世界協定時刻 (UTC) を使用するため、構造体にローカル時刻を渡すと、結果は正しくありません。 詳細については、「Windows SDK の[ファイル時間](/windows/win32/SysInfo/file-times)」を参照してください。

- `COleDateTime(``nYear` 、`nMonth`、 、`nHour`、 `COleDateTime` 、 )は、指定された数値からオブジェクトを構築します。`nSec` `nDay` `nMin`

- `COleDateTime(``wDosDate`、 )`wDosTime`指定し`COleDateTime`た MS-DOS の日付と時刻の値からオブジェクトを構築します。

`time_t`データ型の詳細については、「ランタイム*ライブラリリファレンス*」の「 [time](../../c-runtime-library/reference/time-time32-time64.md)関数」を参照してください。

詳細については、Windows SDK の「 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)および[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)構造体」を参照してください。

値の`COleDateTime`境界の詳細については、「 [日付と時刻:オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。

> [!NOTE]
> パラメーターを使用`DBTIMESTAMP`するコンストラクターは、OLEDB が含まれている場合にのみ使用できます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

##  <a name="format"></a>  COleDateTime::Format

日付/時刻値の書式設定された表現を作成します。

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>パラメーター

*dwFlags*<br/>
次のいずれかのロケールフラグを示します。

- LOCALE_NOUSEROVERRIDE カスタムユーザー設定ではなく、システムの既定のロケール設定を使用します。

- VAR_TIMEVALUEONLY は、解析中に日付部分を無視します。

- VAR_DATEVALUEONLY は、解析中に時間部分を無視します。

*lcid*<br/>
変換に使用するロケール ID を示します。 言語識別子の詳細については、「[言語識別子](/windows/win32/Intl/language-identifiers)」を参照してください。

*lpszFormat*<br/>
書式`printf`設定文字列に類似した書式設定文字列。 各書式指定コードは、前にパーセント`%`() 記号を付けて、対応`COleDateTime`するコンポーネントに置き換えられます。 書式設定文字列内のその他の文字は、返された文字列にそのままコピーされます。 詳細については、「ランタイム関数[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)」を参照してください。 の`Format`書式設定コードの値と意味は次のとおりです。

- `%H`現在の日の時間

- `%M`現在の時間 (分)

- `%S`現在の1分間の秒数

- `%%`パーセント記号

*nFormatID*<br/>
書式制御文字列のリソース ID。

### <a name="return-value"></a>戻り値

書式設定された日付/時刻値を格納している。`CString`

### <a name="remarks"></a>Remarks

この`COleDateTime`オブジェクトの状態が null の場合、戻り値は空の文字列になります。 状態が無効である場合は、文字列リソース ATL_IDS_DATETIME_INVALID によって返される文字列が指定されます。

この関数の3つの形式の簡単な説明を次に示します。

`Format`( *dwFlags*、 *lcid*)<br/>
このフォームでは、日付と時刻の言語仕様 (ロケール Id) を使用して値の書式を設定します。 このフォームでは、既定のパラメーターを使用して日付と時刻を出力します。ただし、時刻部分が 0 (深夜) である場合は、日付のみが出力されます。日付部分が 0 (1899 12 月30日) の場合は、時刻だけが出力されます。 日付/時刻値が 0 (1899 年12月30日午前0時) の場合、既定のパラメーターを持つこのフォームは午前0時に印刷されます。

`Format`( *Lpszformat*)<br/>
このフォームでは、書式設定文字列を使用して値の書式を設定します。書式指定コードの前に`printf`は、パーセント記号 (%) が付きます。 書式設定文字列は、パラメーターとして関数に渡されます。 書式設定コードの詳細については、「 [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) In The ランタイム Library Reference」を参照してください。

`Format`( *nFormatID*)<br/>
このフォームでは、書式設定文字列を使用して値の書式を設定します。書式指定コードの前に`printf`は、パーセント記号 (%) が付きます。 書式設定文字列はリソースです。 この文字列リソースの ID は、パラメーターとして渡されます。 書式設定コードの詳細については、「 [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) In The*ランタイム Library Reference*」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

##  <a name="getasdbtimestamp"></a>COleDateTime:: GetAsDBTIMESTAMP

`COleDateTime`オブジェクトの時刻を`DBTIMESTAMP`データ構造体として取得するには、このメソッドを呼び出します。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>パラメーター

*タイムスタンプ*<br/>
[Dbtimestamp](/dotnet/api/system.data.oledb.oledbtype)構造体への参照。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

結果として得られた時間を参照された*タイムスタンプ*構造体に格納します。 この`DBTIMESTAMP`関数によって初期化されるデータ構造`fraction`体は、メンバーが0に設定されます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

##  <a name="getassystemtime"></a>  COleDateTime::GetAsSystemTime

`COleDateTime`オブジェクトの時刻を`SYSTEMTIME`データ構造体として取得するには、このメソッドを呼び出します。

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>パラメーター

*sysTime*<br/>
`COleDateTime`オブジェクトから変換された日付/時刻値を受け取るための[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体への参照。

### <a name="return-value"></a>戻り値

成功した場合は TRUE を返します。変換に失敗した場合は FALSE。 `COleDateTime`オブジェクトが NULL または無効の場合は。

### <a name="remarks"></a>Remarks

`GetAsSystemTime`結果として得られた時間を参照先の*sysTime*オブジェクトに格納します。 この`SYSTEMTIME`関数によって初期化されるデータ構造`wMilliseconds`体は、メンバーが0に設定されます。

`COleDateTime`オブジェクトに保持されているステータス情報の詳細については、「 [GetStatus](#getstatus)」を参照してください。

##  <a name="getasudate"></a>  COleDateTime::GetAsUDATE

`COleDateTime`オブジェクトの時刻を`UDATE`データ構造体として取得するには、このメソッドを呼び出します。

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>パラメーター

*uDate*<br/>
オブジェクトから変換さ`UDATE`れた日付/時刻値を受け取る構造体への参照。 `COleDateTime`

### <a name="return-value"></a>戻り値

成功した場合は TRUE を返します。変換に失敗した場合は FALSE。 `COleDateTime`オブジェクトが NULL または無効の場合は。

### <a name="remarks"></a>Remarks

構造`UDATE`体は、"アンパック済み" の日付を表します。

##  <a name="getcurrenttime"></a>  COleDateTime::GetCurrentTime

現在の日付/時刻値を返すには、この静的メンバー関数を呼び出します。

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

##  <a name="getday"></a>COleDateTime:: GetDay

この日付/時刻値によって表される月の日付を取得します。

```
int GetDay() const throw();
```

### <a name="return-value"></a>戻り値

この`COleDateTime`オブジェクトの値で表される月の日付、または`COleDateTime::error`日を取得できなかった場合は。

### <a name="remarks"></a>Remarks

有効な戻り値の範囲は 1 ~ 31 です。

この`COleDateTime`オブジェクトの値を照会するその他のメンバー関数の詳細については、次のメンバー関数を参照してください。

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour:](#gethour)

- [Getminute:](#getminute)

- [Getsecond:](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

##  <a name="getdayofweek"></a>COleDateTime:: GetDayOfWeek

この日付/時刻値によって表される月の日付を取得します。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>戻り値

この`COleDateTime`オブジェクトの値で表される曜日、または曜日を`COleDateTime::error`取得できなかった場合は。

### <a name="remarks"></a>Remarks

有効な戻り値の範囲は 1 ~ 7 です。1は日曜日、2 = 月曜日のようになります。

この`COleDateTime`オブジェクトの値を照会するその他のメンバー関数の詳細については、次のメンバー関数を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour:](#gethour)

- [Getminute:](#getminute)

- [Getsecond:](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

##  <a name="getdayofyear"></a>COleDateTime:: GetDayOfYear

この日付/時刻値によって表される年の通算日を取得します。

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>戻り値

この`COleDateTime`オブジェクトの値で表される年の日付、または`COleDateTime::error`年の通算日を取得できなかった場合は。

### <a name="remarks"></a>Remarks

有効な戻り値の範囲は 1 ~ 366 で、1月1日です。

この`COleDateTime`オブジェクトの値を照会するその他のメンバー関数の詳細については、次のメンバー関数を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour:](#gethour)

- [Getminute:](#getminute)

- [Getsecond:](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

##  <a name="gethour"></a>COleDateTime:: Gethour:

この日付/時刻値によって表される時間を取得します。

```
int GetHour() const throw();
```

### <a name="return-value"></a>戻り値

この`COleDateTime`オブジェクトの値で表される時間。また`COleDateTime::error`は時間を取得できなかった場合は。

### <a name="remarks"></a>Remarks

有効な戻り値の範囲は 0 ~ 23 です。

この`COleDateTime`オブジェクトの値を照会するその他のメンバー関数の詳細については、次のメンバー関数を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Getminute:](#getminute)

- [Getsecond:](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

##  <a name="getminute"></a>  COleDateTime::GetMinute

この日付/時刻値によって表される分を取得します。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>戻り値

この`COleDateTime`オブジェクトの値で表される分、また`COleDateTime::error`は分を取得できなかった場合は。

### <a name="remarks"></a>Remarks

有効な戻り値の範囲は 0 ~ 59 です。

この`COleDateTime`オブジェクトの値を照会するその他のメンバー関数の詳細については、次のメンバー関数を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour:](#gethour)

- [Getsecond:](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>例

[Gethour:](#gethour)の例を参照してください。

##  <a name="getmonth"></a>  COleDateTime::GetMonth

この日付/時刻値によって表される月を取得します。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>戻り値

この`COleDateTime`オブジェクトの値で表される月。月`COleDateTime::error`を取得できなかった場合は。

### <a name="remarks"></a>Remarks

有効な戻り値の範囲は 1 ~ 12 です。

この`COleDateTime`オブジェクトの値を照会するその他のメンバー関数の詳細については、次のメンバー関数を参照してください。

- [GetDay](#getday)

- [GetYear](#getyear)

- [Gethour:](#gethour)

- [Getminute:](#getminute)

- [Getsecond:](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>例

[Getday](#getday)の例を参照してください。

##  <a name="getsecond"></a>  COleDateTime::GetSecond

この日付/時刻値によって表される秒を取得します。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>戻り値

この`COleDateTime`オブジェクトの値で表される2番目`COleDateTime::error`の。2番目のを取得できなかった場合は。

### <a name="remarks"></a>Remarks

有効な戻り値の範囲は 0 ~ 59 です。

> [!NOTE]
>  クラス`COleDateTime`は、うるう秒をサポートしていません。

の`COleDateTime`実装の詳細については、「 [日付と時刻:オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。

この`COleDateTime`オブジェクトの値を照会するその他のメンバー関数の詳細については、次のメンバー関数を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour:](#gethour)

- [Getminute:](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>例

[Gethour:](#gethour)の例を参照してください。

##  <a name="getstatus"></a>  COleDateTime::GetStatus

指定さ`COleDateTime`れたオブジェクトの状態 (有効性) を取得します。

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>戻り値

この`COleDateTime`値の状態を返します。 既定のを`GetStatus`使用し`COleDateTime`て構築されたオブジェクトでを呼び出すと、有効なが返されます。 コンストラクターを null `GetStatus`に設定`COleDateTime`して初期化されたオブジェクトでを`GetStatus`呼び出すと、は null を返します。

### <a name="remarks"></a>Remarks

戻り値は、 `DateTimeStatus` `COleDateTime`クラス内で定義されている列挙型によって定義されます。

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

これらの状態値の簡単な説明については、次の一覧を参照してください。

- `COleDateTime::error`日付/時刻値の一部を取得しようとしているときにエラーが発生したことを示します。

- `COleDateTime::valid`この`COleDateTime`オブジェクトが有効であることを示します。

- `COleDateTime::invalid`この`COleDateTime`オブジェクトが無効であることを示します。つまり、値が正しくない可能性があります。

- `COleDateTime::null`この`COleDateTime`オブジェクトが null であること、つまり、このオブジェクトに値が指定されていないことを示します。 ( C++ Null ではなく、"値がない" というデータベースの意味では "null" になります)。

`COleDateTime`オブジェクトの状態は、次の場合には無効です。

- 値が、 `VARIANT`日付/時刻値に`COleVariant`変換できなかった値または値から設定されている場合は。

- 有効な日付/時刻値に`time_t`変換`SYSTEMTIME`できない`FILETIME` 、、またはの値から値が設定されている場合は。

- 値が無効なパラメーター値`SetDateTime`を使用して設定されている場合は。

- このオブジェクトの算術演算の実行中にオーバーフローまたはアンダーフローが発生し`+=`た`-=`場合 (つまり、または)。

- 無効な値がこのオブジェクトに割り当てられた場合は。

- このオブジェクトの状態が、を使用して`SetStatus`明示的に無効に設定された場合は。

状態が無効に設定されている可能性のある操作の詳細については、次のメンバー関数を参照してください。

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [演算子 +、-](#operator_add_-)

- [operator + =、-=](#operator_add_eq_-_eq)

値の`COleDateTime`境界の詳細については、「 [日付と時刻:オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

##  <a name="getyear"></a>COleDateTime:: GetYear

この日付/時刻値によって表される年を取得します。

```
int GetYear() const throw();
```

### <a name="return-value"></a>戻り値

この`COleDateTime`オブジェクトの値で表される年。また`COleDateTime::error`は年を取得できなかった場合は。

### <a name="remarks"></a>Remarks

有効な戻り値の範囲は 100 ~ 9999 です。これには、世紀が含まれます。

この`COleDateTime`オブジェクトの値を照会するその他のメンバー関数の詳細については、次のメンバー関数を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [Gethour:](#gethour)

- [Getminute:](#getminute)

- [Getsecond:](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

値の`COleDateTime`境界の詳細については、「 [日付と時刻:オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。

### <a name="example"></a>例

[Getday](#getday)の例を参照してください。

##  <a name="m_dt"></a>COleDateTime:: m_dt

`DATE` この`COleDateTime`オブジェクトの基になる構造体。

```
DATE m_dt;
```

### <a name="remarks"></a>Remarks

> [!CAUTION]
>  この関数によって`DATE`返されるポインターによってアクセスされるオブジェクトの値を変更する`COleDateTime`と、このオブジェクトの値が変更されます。 この`COleDateTime`オブジェクトの状態は変更されません。

`DATE`オブジェクトの実装の詳細については、「 [日付と時刻:オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。

##  <a name="m_status"></a>COleDateTime:: m_status

この`COleDateTime`オブジェクトの状態を格納します。

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Remarks

このデータメンバーの型は列挙型`DateTimeStatus`であり、 `COleDateTime`クラス内で定義されています。 詳細については、「 [COleDateTime:: GetStatus](#getstatus)」を参照してください。

> [!CAUTION]
>  このデータメンバーは、高度なプログラミングの状況を対象としています。 インラインメンバー関数[GetStatus](#getstatus)および[SetStatus](#setstatus)を使用する必要があります。 この`SetStatus`データメンバーを明示的に設定する方法については、「」を参照してください。

##  <a name="operator_eq"></a>COleDateTime:: operator =

値を`COleDateTime`コピーします。

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& uDate) throw();
```

### <a name="remarks"></a>Remarks

これらのオーバーロードされた代入演算子は、ソースの日付`COleDateTime` /時刻値をこのオブジェクトにコピーします。 これらのオーバーロードされた代入演算子の簡単な説明を次に示します。

- **operator = (** `dateSrc` **)** オペランドの値と状態がこの`COleDateTime`オブジェクトにコピーされます。

- **operator = (** *varsrc* **)** [バリアント](/windows/win32/api/oaidl/ns-oaidl-variant)値 (または[COleVariant](../../mfc/reference/colevariant-class.md)オブジェクト) から日付/時刻 (VT_DATE) への変換が成功すると、変換された値がこの`COleDateTime`オブジェクトにコピーされ、その状態が有効に設定されます。 変換が成功しなかった場合、このオブジェクトの値は 0 (1899 年12月30日午前0時) に設定され、その状態は無効になります。

- **operator = (** `dtSrc` **)** `DATE`このオブジェクトに値がコピーされ、その状態が有効に設定されます。`COleDateTime`

- **operator = (** `timeSrc` `__time64_t` **)** この`time_t` オブジェクトには、値または値が変換されてコピーされます。`COleDateTime` 変換が成功した場合、このオブジェクトの状態は valid に設定されます。失敗した場合は、無効に設定されます。

- **operator = (** *systimeSrc* **)** [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)値が変換され、この`COleDateTime`オブジェクトにコピーされます。 変換が成功した場合、このオブジェクトの状態は valid に設定されます。失敗した場合は、無効に設定されます。

- **operator = (** `uDate` **)** 値`UDATE`が変換され、この`COleDateTime`オブジェクトにコピーされます。 変換が成功した場合、このオブジェクトの状態は valid に設定されます。失敗した場合は、無効に設定されます。 構造`UDATE`体は、"アンパック済み" の日付を表します。 詳細については、「 [Vardatefromudate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate)関数」を参照してください。

- **operator = (** `filetimeSrc` **)** [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)値が変換され、この`COleDateTime`オブジェクトにコピーされます。 変換が成功した場合、このオブジェクトの状態は valid に設定されます。それ以外の場合は、無効に設定されます。 `FILETIME`世界協定時刻 (UTC) を使用します。そのため、構造体に UTC 時刻を渡すと、結果は UTC 時刻から現地時刻に変換され、バリアント時刻として格納されます。 この動作は、Visual C++ 6.0 および visual C++.net 2003 SP2 と同じです。 詳細については、「Windows SDK の[ファイル時間](/windows/win32/SysInfo/file-times)」を参照してください。

詳細については、Windows SDK の[バリアント](/windows/win32/api/oaidl/ns-oaidl-variant)エントリを参照してください。

`time_t`データ型の詳細については、「ランタイム*ライブラリリファレンス*」の「 [time](../../c-runtime-library/reference/time-time32-time64.md)関数」を参照してください。

詳細については、Windows SDK の「 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)および[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)構造体」を参照してください。

値の`COleDateTime`境界の詳細については、「 [日付と時刻:オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。

##  <a name="operator_add_-"></a>COleDateTime:: operator +、-

値を加算`ColeDateTime`および減算します。

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Remarks

`COleDateTime`オブジェクトは絶対時刻を表します。 [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)オブジェクトは相対時刻を表します。 最初の2つの演算子を使用すると、 `COleDateTimeSpan`値の値`COleDateTime`を加算および減算できます。 3番目の演算子を使用する`COleDateTime`と、ある値を別`COleDateTimeSpan`の値から減算して値を生成することができます。

オペランドのいずれかが null の場合、結果`COleDateTime`の値の状態は null になります。

結果`COleDateTime`の値が許容される値の範囲外になる場合、その`COleDateTime`値の状態は無効になります。

オペランドのいずれかが無効で、もう一方が null でない場合、結果`COleDateTime`の値の状態は無効になります。

**+** と **-** 場合演算子はアサート、`COleDateTime`オブジェクトの設定を null にします。 例については、「 [COleDateTime 関係演算子](#coledatetime_relational_operators)」を参照してください。

有効、無効、および null 状態の値の詳細については、 [m_status](#m_status)メンバー変数を参照してください。

値の`COleDateTime`境界の詳細については、「 [日付と時刻:オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>COleDateTime:: operator + =、-=

`ColeDateTime` この`COleDateTime`オブジェクトの値を加算および減算します。

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Remarks

これらの演算子を使用すると、この`COleDateTimeSpan` `COleDateTime`に対して値を加算および減算できます。 オペランドのいずれかが null の場合、結果`COleDateTime`の値の状態は null になります。

結果`COleDateTime`の値が許容値の範囲外になる場合、この`COleDateTime`値の状態は無効に設定されます。

オペランドのいずれかが無効で、その他のが null でない場合、結果`COleDateTime`の値の状態は無効になります。

有効、無効、および null 状態の値の詳細については、 [m_status](#m_status)メンバー変数を参照してください。

**+=** と **-=** 場合演算子はアサート、`COleDateTime`オブジェクトの設定を null にします。 例については、「 [COleDateTime 関係演算子](#coledatetime_relational_operators)」を参照してください。

値の`COleDateTime`境界の詳細については、「 [日付と時刻:オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。

##  <a name="operator_date"></a>COleDateTime:: operator DATE

`ColeDateTime` 値`DATE`をに変換します。

```
operator DATE() const throw();
```

### <a name="remarks"></a>Remarks

この演算子は、 `DATE`この`COleDateTime`オブジェクトから値がコピーされるオブジェクトを返します。 `DATE`オブジェクトの実装の詳細については、「 [日付と時刻:オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。

オブジェクトが null に設定されて`DATE`いる場合、演算子はをアサートします。 `COleDateTime` 例については、「 [COleDateTime 関係演算子](#coledatetime_relational_operators)」を参照してください。

##  <a name="parsedatetime"></a>COleDateTime::P arseDateTime

文字列を解析して、日付/時刻値を読み取ります。

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>パラメーター

*lpszDate*<br/>
解析される null で終わる文字列へのポインター。 詳細については、「解説」を参照してください。

*dwFlags*<br/>
ロケール設定および解析のフラグを示します。 次のフラグの1つまたは複数を実行します。

- LOCALE_NOUSEROVERRIDE カスタムユーザー設定ではなく、システムの既定のロケール設定を使用します。

- VAR_TIMEVALUEONLY は、解析中に日付部分を無視します。

- VAR_DATEVALUEONLY は、解析中に時間部分を無視します。

*lcid*<br/>
変換に使用するロケール ID を示します。

### <a name="return-value"></a>戻り値

文字列が日付/時刻値に正常に変換された場合は TRUE を返し、それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

文字列が日付/時刻値に正常に変換された場合、この`COleDateTime`オブジェクトの値はその値に設定され、その状態が有効になります。

> [!NOTE]
>  年の値は、100 ~ 9999 の範囲で指定する必要があります。

*Lpszdate*パラメーターには、さまざまな形式を使用できます。 たとえば、次の文字列には、許容される日付/時刻書式が含まれています。

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

ロケール ID は、文字列形式を日付/時刻値への変換に使用できるかどうかにも影響します。

VAR_DATEVALUEONLY の場合、時刻値は time 0 または深夜に設定されます。 VAR_TIMEVALUEONLY の場合、date 値は date 0 に設定されます。つまり、1899年12月30日に設定されます。

文字列を日付/時刻値に変換できなかった場合、または数値のオーバーフローがあった場合、この`COleDateTime`オブジェクトの状態は無効になります。

値の`COleDateTime`境界と実装の詳細については、「 [日付と時刻:オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。

##  <a name="setdate"></a>  COleDateTime::SetDate

この`COleDateTime`オブジェクトの日付を設定します。

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>パラメーター

*Nyear*、 *nyear*、 *nyear*<br/>
この`COleDateTime`オブジェクトにコピーする日付部分を示します。

### <a name="return-value"></a>戻り値

この`COleDateTime`オブジェクトの値が正常に設定された場合は0。それ以外の場合は1。 この戻り値は、 `DateTimeStatus`列挙型に基づいています。 詳細については、「 [SetStatus](#setstatus)メンバー関数」を参照してください。

### <a name="remarks"></a>Remarks

日付は、指定した値に設定されます。 時刻は、時刻 0 (午前0時) に設定されます。

パラメーター値の境界については、次の表を参照してください。

|パラメーター|線|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|

月の日付がオーバーフローした場合は、翌月の正しい日付に変換され、それに応じて月や年が加算されます。 日の値が0の場合は、前月の最後の日を示します。 動作はと`SystemTimeToVariantTime`同じです。

パラメーターで指定した日付値が有効でない場合、このオブジェクトの状態はに`COleDateTime::invalid`設定されます。 [GetStatus](#getstatus)を使用して`DATE`値の有効性を確認し、 [m_dt](#m_dt)の値が変更されないことを想定してはいけません。

日付値の例をいくつか次に示します。

|*nYear*|*nMonth*|*nDay*|[値]|
|-------------|--------------|------------|-----------|
|2000|2|29|2000年2月29日|
|1776|7|4|4 1776 年7月|
|1925|4|35|35年4月 1925 (無効な日付)|
|10000|1|1|1万年1月1日 (無効な日付)|

日付と時刻の両方を設定するには、「 [COleDateTime:: SetDateTime](#setdatetime)」を参照してください。

この`COleDateTime`オブジェクトの値に対してクエリを実行するメンバー関数の詳細については、次のメンバー関数を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour:](#gethour)

- [Getminute:](#getminute)

- [Getsecond:](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

値の`COleDateTime`境界の詳細については、「 [日付と時刻:オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

##  <a name="setdatetime"></a>  COleDateTime::SetDateTime

この`COleDateTime`オブジェクトの日付と時刻を設定します。

```
int SetDateTime(
    int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>パラメーター

*Nyear*、 *nyear*、 *nyear*、 *nyear*、 *nyear*、 *nSec*<br/>
この`COleDateTime`オブジェクトにコピーする日付と時刻のコンポーネントを示します。

### <a name="return-value"></a>戻り値

この`COleDateTime`オブジェクトの値が正常に設定された場合は0。それ以外の場合は1。 この戻り値は、 `DateTimeStatus`列挙型に基づいています。 詳細については、「 [SetStatus](#setstatus)メンバー関数」を参照してください。

### <a name="remarks"></a>Remarks

パラメーター値の境界については、次の表を参照してください。

|パラメーター|線|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|
|*nHour*|0 - 23|
|*N1 日*|0 - 59|
|*nSec*|0 - 59|

月の日付がオーバーフローした場合は、翌月の正しい日付に変換され、それに応じて月や年が加算されます。 日の値が0の場合は、前月の最後の日を示します。 動作は[SystemTimeToVariantTime](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime)と同じです。

パラメーターで指定した日付または時刻の値が無効である場合、このオブジェクトの状態は無効に設定され、このオブジェクトの値は変更されません。

次に、時刻値の例をいくつか示します。

|*nHour*|*N1 日*|*nSec*|[値]|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|無効|
|9|60|0|無効|

日付値の例をいくつか次に示します。

|*nYear*|*nMonth*|*nDay*|[値]|
|-------------|--------------|------------|-----------|
|1995|4|15|1995年4月15日|
|1789|7|14|1789年7月17日|
|1925|2|30|無効|
|10000|1|1|無効|

日付のみを設定するには、「 [COleDateTime:: SetDate](#setdate)」を参照してください。 時刻のみを設定するには、「 [COleDateTime:: SetTime](#settime)」を参照してください。

この`COleDateTime`オブジェクトの値に対してクエリを実行するメンバー関数の詳細については、次のメンバー関数を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour:](#gethour)

- [Getminute:](#getminute)

- [Getsecond:](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

値の`COleDateTime`境界の詳細については、「 [日付と時刻:オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。

### <a name="example"></a>例

[GetStatus](#getstatus)の例を参照してください。

##  <a name="setstatus"></a>COleDateTime:: SetStatus

この`COleDateTime`オブジェクトの状態を設定します。

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>パラメーター

*status*<br/>
この`COleDateTime`オブジェクトの新しいステータス値。

### <a name="remarks"></a>Remarks

*Status*パラメーターの値は、 `DateTimeStatus` `COleDateTime`クラス内で定義されている列挙型によって定義されます。 詳細については、「 [COleDateTime:: GetStatus](#getstatus) 」を参照してください。

> [!CAUTION]
>  この関数は、高度なプログラミングの状況に適しています。 この関数は、このオブジェクトのデータを変更しません。 この値は、通常、状態を**null**または**無効**に設定するために使用されます。 代入演算子 ([operator =](#operator_eq)) と[setdatetime](#setdatetime)は、ソース値に基づいてオブジェクトの状態を設定します。

### <a name="example"></a>例

[GetStatus](#getstatus)の例を参照してください。

##  <a name="settime"></a>  COleDateTime::SetTime

この`COleDateTime`オブジェクトの時刻を設定します。

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>パラメーター

*Nhour*、 *nhour*、 *nSec*<br/>
この`COleDateTime`オブジェクトにコピーされる時刻部分を示します。

### <a name="return-value"></a>戻り値

この`COleDateTime`オブジェクトの値が正常に設定された場合は0。それ以外の場合は1。 この戻り値は、 `DateTimeStatus`列挙型に基づいています。 詳細については、「 [SetStatus](#setstatus)メンバー関数」を参照してください。

### <a name="remarks"></a>Remarks

時刻は、指定された値に設定されます。 日付は、1899年12月30日の日付0に設定されます。

パラメーター値の境界については、次の表を参照してください。

|パラメーター|線|
|---------------|------------|
|*nHour*|0 - 23|
|*N1 日*|0 - 59|
|*nSec*|0 - 59|

パラメーターで指定した時刻値が有効でない場合、このオブジェクトの状態は無効に設定され、このオブジェクトの値は変更されません。

次に、時刻値の例をいくつか示します。

|*nHour*|*N1 日*|*nSec*|[値]|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|無効|
|9|60|0|無効|

日付と時刻の両方を設定するには、「 [COleDateTime:: SetDateTime](#setdatetime)」を参照してください。

この`COleDateTime`オブジェクトの値に対してクエリを実行するメンバー関数の詳細については、次のメンバー関数を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Gethour:](#gethour)

- [Getminute:](#getminute)

- [Getsecond:](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

値の`COleDateTime`境界の詳細については、「 [日付と時刻:オートメーションの](../../atl-mfc-shared/date-and-time-automation-support.md)サポート。

### <a name="example"></a>例

[SetDate](#setdate)の例を参照してください。

## <a name="see-also"></a>関連項目

[COleVariant クラス](../../mfc/reference/colevariant-class.md)<br/>
[CTime クラス](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan クラス](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)
