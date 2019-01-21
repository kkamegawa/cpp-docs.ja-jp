---
title: COleDateTime クラス
ms.date: 11/04/2016
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
ms.openlocfilehash: 9791f1c59bb393f7de64ffb16ccb95e99928b04c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2018
ms.locfileid: "51525341"
---
# <a name="coledatetime-class"></a>COleDateTime クラス

カプセル化、 `DATE` OLE オートメーションで使用されているデータ型。

## <a name="syntax"></a>構文

```
class COleDateTime
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleDateTime::COleDateTime](#coledatetime)|`COleDateTime` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[近く](#format)|書式設定された文字列表現を生成、`COleDateTime`オブジェクト。|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|時刻を取得するには、このメソッドを呼び出す、`COleDateTime`オブジェクトとして、`DBTIMESTAMP`データ構造体。|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|時刻を取得するには、このメソッドを呼び出す、`COleDateTime`オブジェクトとして、 [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)データ構造体。|
|[COleDateTime::GetAsUDATE](#getasudate)|時刻を取得するには、このメソッドを呼び出す、`COleDateTime`として、`UDATE`データ構造体。|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|作成、 `COleDateTime` (静的メンバー関数) の現在の時刻を表すオブジェクト。|
|[COleDateTime::GetDay](#getday)|この日付を返します`COleDateTime`オブジェクトは (1 ~ 31) を表します。|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|この週の通算日を返す`COleDateTime`オブジェクトが表す (日曜 = 1)。|
|[COleDateTime::GetDayOfYear](#getdayofyear)|これで、年の通算日を返します`COleDateTime`オブジェクトが表す (1 月 1 日 = 1)。|
|[COleDateTime::GetHour](#gethour)|この時間が返されます`COleDateTime`オブジェクトが表す (0 - 23)。|
|[COleDateTime::GetMinute](#getminute)|これで分を返します`COleDateTime`オブジェクトが表す (0 - 59)。|
|[COleDateTime::GetMonth](#getmonth)|これで、1 か月を返します`COleDateTime`オブジェクトは (1 ~ 12) を表します。|
|[COleDateTime::GetSecond](#getsecond)|秒を返します。 この`COleDateTime`オブジェクトが表す (0 - 59)。|
|[「](#getstatus)|この状態 (有効) を取得`COleDateTime`オブジェクト。|
|[COleDateTime::GetYear](#getyear)|これは年を返します`COleDateTime`オブジェクトが表す。|
|[COleDateTime::ParseDateTime](#parsedatetime)|文字列から日付/時刻値を読み取っての値を設定`COleDateTime`します。|
|[COleDateTime::SetDate](#setdate)|この値を設定`COleDateTime`オブジェクト指定した日付のみの値から。|
|[COleDateTime::SetDateTime](#setdatetime)|この値を設定`COleDateTime`オブジェクト指定した日付/時刻値から。|
|[COleDateTime::SetStatus](#setstatus)|これのステータス (有効) を設定`COleDateTime`オブジェクト。|
|[COleDateTime::SetTime](#settime)|この値を設定`COleDateTime`オブジェクト指定の時間専用の値から。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[COleDateTime::operator COleDateTime::operator、= =、< など。](#coledatetime_relational_operators)|比較する 2 つ`COleDateTime`値。|
|[COleDateTime::operator +、- COleDateTime::operator](#operator_add_-)|加算および減算`COleDateTime`値。|
|[COleDateTime::operator + =、-= COleDateTime::operator](#operator_add_eq_-_eq)|加算および減算、`COleDateTime`値からこの`COleDateTime`オブジェクト。|
|[COleDateTime::operator =](#operator_eq)|コピーを`COleDateTime`値。|
|[COleDateTime::operator 日付、COleDateTime::operator 日付 *](#operator_date)|変換を`COleDateTime`値に、`DATE`または`DATE*`します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|基になるが含まれています。`DATE`この`COleDateTime`オブジェクト。|
|[COleDateTime::m_status](#m_status)|この状態を含む`COleDateTime`オブジェクト。|

## <a name="remarks"></a>Remarks

`COleDateTime` 基本クラスはありません。

使用可能な型の 1 つは、[バリアント](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)OLE オートメーションのデータ型。 A`COleDateTime`値は、絶対日付と時刻の値を表します。

`DATE`型が浮動小数点値として実装されます。 日は、1899 年 12 月 30 日の午前 0 時に測定されます。 次の表は、一部の日付と関連付けられた値を示します。

|日付|[値]|
|----------|-----------|
|1899 年 12 月 29 日、午前 0 時|-1.0|
|1899 年 12 月 29 日、午前 6 時|-1.25|
|1899 年 12 月 30 日の午前 0 時|0.0|
|1899 年 12 月 31 日の午前 0 時|1|
|1900 年 1 月 1 日、午前 6 時|2.25|

> [!CAUTION]
> 上記の表にことはできますが、1899 年 12 月 30 日の午前 0 時前に日付の値が負の値になる時刻の値はありませんに注意してください。 たとえば、午前 6 時では、日を表す整数が (1899 年 12 月 30 日) の後に正または負の値 (前に、1899 年 12 月 30 日) であっても小数部の値 0.25 で表される常にします。 つまり、単純な浮動ポイントの比較が並べ替えが誤って、 `COleDateTime` 12/29/1899 として 6時 00分 AM を表す**後**1 よりも、同じ日に 7時 00分 AM を表します。

`COleDateTime`クラスは、100、年 1 月 1 日 12 月 31 日から日付から 9999 を処理します。 `COleDateTime`クラスは、構成のグレゴリオ暦カレンダーを使用して、ユリウス暦はサポートされません。 `COleDateTime` 夏時間を無視します。 (を参照してください[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md))。

> [!NOTE]
> 使用することができます、`%y`形式の日付は 1900 年以降だけ 2 桁の年を取得します。 使用する場合、 `%y` 1900 年より前に、の日付、コードの形式でアサート エラーが生成されます。

この型は日付のみまたは時専用の値を表すも使用されます。 規則により、時間専用の値として 0 (1899 年 12 月 30 日) の日付を使用し、日付のみの値が時間 00:00 (午前 0 時) に使用します。

作成する場合、`COleDateTime`オブジェクトの日付を使用して 100 未満の日付が、許容されるが、後続の呼び出しを`GetYear`、 `GetMonth`、 `GetDay`、 `GetHour`、 `GetMinute`、および`GetSecond`失敗し、-1 を返します。 以前は、2 桁の日付を使用できますが、日付が 100 または大きい MFC 4.2 以降にする必要があります。

問題を回避するには、4 桁の日付を指定します。 例えば:

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

基本的な算術演算、`COleDateTime`コンパニオン クラスを使用して、値[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)します。 `COleDateTimeSpan` 値は、時間間隔を定義します。 これらのクラス間のリレーションシップが間に 1 つのような[CTime](../../atl-mfc-shared/reference/ctime-class.md)と[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)します。

詳細については、`COleDateTime`と`COleDateTimeSpan`クラスは、記事をご覧ください。[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** ATLComTime.h

##  <a name="coledatetime_relational_operators"></a>  COleDateTime 関係演算子

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

*日付*<br/>
比較される `COleDateTime` オブジェクト。

### <a name="remarks"></a>Remarks

> [!NOTE]
>  ATLASSERT が 2 つのオペランドのいずれかが有効でない場合に発生します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>例

演算子 **>=** 、 **\<=**、 **>**、および **<**、場合、アサートは、`COleDateTime`オブジェクトの設定を null にします。

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

##  <a name="coledatetime"></a>  COleDateTime::COleDateTime

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
COleDateTime(const DBTIMESTAMP& dbts) throw();
```

### <a name="parameters"></a>パラメーター

*dateSrc*<br/>
既存の`COleDateTime`新しいにコピーされるオブジェクト`COleDateTime`オブジェクト。

*varSrc*<br/>
既存の`VARIANT`データ構造 (可能性があります、`COleVariant`オブジェクト) を日付/時刻値 (VT_DATE) に変換し、新しいコピーを`COleDateTime`オブジェクト。

*dtSrc*<br/>
日付/時刻 (`DATE`)、新規にコピーされる値`COleDateTime`オブジェクト。

*timeSrc*<br/>
A`time_t`または`__time64_t`値を日付/時刻値に変換し、新しいコピー`COleDateTime`オブジェクト。

*systimeSrc*<br/>
A`SYSTEMTIME`構造体の日付/時刻値に変換して、新しいコピーを`COleDateTime`オブジェクト。

*filetimeSrc*<br/>
A`FILETIME`構造体の日付/時刻値に変換して、新しいコピーを`COleDateTime`オブジェクト。 なお`FILETIME`世界協定時刻 (UTC) を使用して、現地時刻を構造に渡す場合、結果は不正確になります。 参照してください[ファイル回](/windows/desktop/SysInfo/file-times)詳細については、Windows sdk。

*nYear*、 *nMonth*、 *%n%n*、*時間*、 *nMin*、 *nSec*<br/>
新しいにコピーされる日付と時刻の値を示す`COleDateTime`オブジェクト。

*wDosDate*、 *wDosTime*<br/>
日付と時刻の値を日付/時刻値に変換して、新しいコピーを MS-DOS`COleDateTime`オブジェクト。

*dbts*<br/>
参照を[DBTimeStamp](https://msdn.microsoft.com/library/system.data.oledb.oledbtype)現在の現地時刻を含む構造体。

### <a name="remarks"></a>Remarks

これらすべてのコンス トラクターが新規作成`COleDateTime`オブジェクトが、指定した値に初期化します。 次の表は、各日付と時刻のコンポーネントの有効な範囲を示しています。

|日付/時刻のコンポーネント|有効範囲|
|--------------------------|-----------------|
|年|100 - 9999|
|月|0 - 12|
|日|0 - 31|
|1 時間|0 - 23|
|1 分|0 - 59|
|1 秒|0 - 59|

注日付部分の実際の上限の境界が変化する月と年のコンポーネントに基づいています。 詳細については、次を参照してください。、`SetDate`または`SetDateTime`メンバー関数。

各コンス トラクターの簡単な説明を次に示します。

- `COleDateTime(` **)** を構築、`COleDateTime`オブジェクトの 0 (深夜、30 1899 年 12 月) に初期化します。

- `COleDateTime(` `dateSrc` **)** を構築、`COleDateTime`既存のオブジェクト`COleDateTime`オブジェクト。

- `COleDateTime(` *varSrc* **)** を構築、`COleDateTime`オブジェクト。 変換を試みます、`VARIANT`構造または[COleVariant](../../mfc/reference/colevariant-class.md)日付/時刻へのオブジェクト ( `VT_DATE`) 値。 新しい変換後の値がコピーされるこの変換が成功した場合は、`COleDateTime`オブジェクト。 値ではそうでない場合、`COleDateTime`オブジェクトが 0 (深夜、30 1899 年 12 月) とその状態を無効に設定します。

- `COleDateTime(` `dtSrc` **)** を構築、`COleDateTime`オブジェクトから、`DATE`値。

- `COleDateTime(` `timeSrc` **)** を構築、`COleDateTime`オブジェクトから、`time_t`値。

- `COleDateTime(` *systimeSrc* **)** を構築、`COleDateTime`オブジェクトから、`SYSTEMTIME`値。

- `COleDateTime(` `filetimeSrc` **)** を構築、`COleDateTime`オブジェクトから、`FILETIME`値。 . なお`FILETIME`世界協定時刻 (UTC) を使用して、現地時刻を構造に渡す場合、結果は不正確になります。 参照してください[ファイル回](/windows/desktop/SysInfo/file-times)詳細については、Windows sdk。

- `COleDateTime(` `nYear`、 `nMonth`、 `nDay`、 `nHour`、 `nMin`、 `nSec` **)** を構築、`COleDateTime`オブジェクトから指定した数値。

- `COleDateTime(` `wDosDate`、 `wDosTime` **)** を構築、`COleDateTime`オブジェクト指定した MS-DOS の日付と時刻の値から。

詳細については、`time_t`データ型を参照してください、[時間](../../c-runtime-library/reference/time-time32-time64.md)で機能、*ランタイム ライブラリ リファレンス*します。

詳細については、次を参照してください。、 [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)と[FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) Windows SDK 内の構造体。

境界の詳細については`COleDateTime`、値は、記事をご覧ください。[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

> [!NOTE]
> コンス トラクターを使用して、`DBTIMESTAMP`パラメーターは、OLEDB.h が含まれる場合にのみ使用できます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

##  <a name="format"></a>  近く

日付/時刻値の書式設定された表現を作成します。

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>パラメーター

*dwFlags*<br/>
次のロケールのフラグのいずれかを示します。

- LOCALE_NOUSEROVERRIDE は、カスタム ユーザー設定ではなく、システムの既定のロケール設定を使用します。

- VAR_TIMEVALUEONLY は、解析中に、日付部分を無視します。

- VAR_DATEVALUEONLY は、解析中に時刻部分を無視します。

*lcid*<br/>
変換に使用するロケール ID を示します。 言語識別子の詳細については、次を参照してください。[言語識別子](/windows/desktop/Intl/language-identifiers)します。

*lpszFormat*<br/>
ような文字列を書式設定、`printf`文字列の書式設定します。 各パーセントで前に、コードの書式設定 ( `%`) 署名は、対応する置き換え`COleDateTime`コンポーネント。 その他の文字書式指定文字列では、返される文字列をそのままコピーされます。 実行時の関数を参照してください。 [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)詳細についてはします。 値との書式設定コードの意味`Format`は。

- `%H` 現在の日の時間

- `%M` 現在、1 時間分

- `%S` 現在の時間 (秒)

- `%%` パーセント記号

*nFormatID*<br/>
コントロールの書式設定文字列のリソース ID。

### <a name="return-value"></a>戻り値

A`CString`書式設定された日付/時刻値を格納します。

### <a name="remarks"></a>Remarks

場合のこの状態`COleDateTime`オブジェクトが null、戻り値は空の文字列。 状態が有効でない場合、戻り値の文字列は、文字列リソース ATL_IDS_DATETIME_INVALID によって指定されます。

この関数の 3 つの形式の簡単な説明に従います。

`Format`( *dwFlags*、 *lcid*)<br/>
このフォームでは、日付と時刻の言語仕様 (ロケール Id) を使用して、値を形式です。 既定のパラメーターを使用して、このフォームで印刷されます、日付と時刻、時刻部分が 0 (深夜) である場合、日付のみが出力されますまたは日付部分が 0 (30 1899 年 12 月)、しない限り、この場合、時間だけが出力されます。 日付/時刻値が 0 (30 1899 年 12 月、午前 0 時) の場合、既定のパラメーターには、このフォームは午前 0 時を印刷します。

`Format`( *lpszFormat*)<br/>
このフォームはパーセント記号 (%) が付いている特殊な書式設定コードを含む書式指定文字列を使用して値を書式設定と`printf`します。 書式指定文字列は、関数にパラメーターとして渡されます。 書式設定コードの詳細については、次を参照してください。 [strftime、wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)ランタイム ライブラリのリファレンス。

`Format`( *nFormatID*)<br/>
このフォームはパーセント記号 (%) が付いている特殊な書式設定コードを含む書式指定文字列を使用して値を書式設定と`printf`します。 書式指定文字列は、リソースです。 この文字列リソースの ID は、パラメーターとして渡されます。 書式設定コードの詳細については、次を参照してください。 [strftime、wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)で、*ランタイム ライブラリ リファレンス*します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

##  <a name="getasdbtimestamp"></a>  COleDateTime::GetAsDBTIMESTAMP

時刻を取得するには、このメソッドを呼び出す、`COleDateTime`オブジェクトとして、`DBTIMESTAMP`データ構造体。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>パラメーター

*dbts*<br/>
参照を[DBTimeStamp](https://msdn.microsoft.com/library/system.data.oledb.oledbtype)構造体。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

参照先の結果として得られる時刻を格納*dbts*構造体。 `DBTIMESTAMP`この関数によって初期化されたデータ構造体は必要があります。 その`fraction`メンバーは 0 に設定します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

##  <a name="getassystemtime"></a>  COleDateTime::GetAsSystemTime

時刻を取得するには、このメソッドを呼び出す、`COleDateTime`オブジェクトとして、`SYSTEMTIME`データ構造体。

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>パラメーター

*sysTime*<br/>
参照を[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)から変換された日付/時刻値を受け取る、`COleDateTime`オブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、TRUE を返しますFALSE、変換に失敗した場合、または場合、`COleDateTime`オブジェクトが NULL または無効です。

### <a name="remarks"></a>Remarks

`GetAsSystemTime` 参照先の結果として得られる時刻を格納*sysTime*オブジェクト。 `SYSTEMTIME`この関数によって初期化されたデータ構造体は必要があります。 その`wMilliseconds`メンバーは 0 に設定します。

参照してください[GetStatus](#getstatus)の詳細については、状態情報が保持されているため、`COleDateTime`オブジェクト。

##  <a name="getasudate"></a>  COleDateTime::GetAsUDATE

時刻を取得するには、このメソッドを呼び出す、`COleDateTime`オブジェクトとして、`UDATE`データ構造体。

```
bool GetAsUDATE(UDATE& udate) const throw();
```

### <a name="parameters"></a>パラメーター

*udate*<br/>
参照を`UDATE`から変換された日付/時刻値を受け取る、`COleDateTime`オブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、TRUE を返しますFALSE、変換に失敗した場合、または場合、`COleDateTime`オブジェクトが NULL または無効です。

### <a name="remarks"></a>Remarks

A`UDATE`構造体は、「開」の日付を表します。

##  <a name="getcurrenttime"></a>  COleDateTime::GetCurrentTime

現在の日付/時刻値を返すには、この静的メンバー関数を呼び出します。

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

##  <a name="getday"></a>  COleDateTime::GetDay

この日付/時刻値で表される月の日を取得します。

```
int GetDay() const throw();
```

### <a name="return-value"></a>戻り値

この値によって表される月の日にち`COleDateTime`オブジェクトまたは`COleDateTime::error`場合は、1 日を取得できませんでした。

### <a name="remarks"></a>Remarks

有効な戻り値の 1 ~ 31 の範囲です。

この値をクエリする他のメンバー関数について`COleDateTime`オブジェクト、メンバー関数は、次を参照してください。

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [曜日](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

##  <a name="getdayofweek"></a>  COleDateTime::GetDayOfWeek

この日付/時刻値で表される月の日を取得します。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>戻り値

この値によって表される曜日`COleDateTime`オブジェクトまたは`COleDateTime::error`場合は、曜日を取得できませんでした。

### <a name="remarks"></a>Remarks

有効な戻り値の範囲 1 ~ 7、ここで、1 = 日曜日、2 = 月曜日、具合です。

この値をクエリする他のメンバー関数について`COleDateTime`オブジェクト、メンバー関数は、次を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

##  <a name="getdayofyear"></a>  COleDateTime::GetDayOfYear

この日付/時刻値で表される年の通算日を取得します。

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>戻り値

この値によって表される年の通算日`COleDateTime`オブジェクトまたは`COleDateTime::error`場合は、年の通算日を取得できませんでした。

### <a name="remarks"></a>Remarks

有効な戻り値は 1 ~ 366 の範囲を 1 月 1 日に 1 を = です。

この値をクエリする他のメンバー関数について`COleDateTime`オブジェクト、メンバー関数は、次を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [曜日](#getdayofweek)

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

##  <a name="gethour"></a>  COleDateTime::GetHour

この日付/時刻値で表される時間を取得します。

```
int GetHour() const throw();
```

### <a name="return-value"></a>戻り値

この値によって表される時間`COleDateTime`オブジェクトまたは`COleDateTime::error`場合は、時間を取得できませんでした。

### <a name="remarks"></a>Remarks

有効な戻り値の 0 から 23 までの範囲。

この値をクエリする他のメンバー関数について`COleDateTime`オブジェクト、メンバー関数は、次を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [曜日](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

##  <a name="getminute"></a>  COleDateTime::GetMinute

この日付/時刻値によって表される分を取得します。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>戻り値

この値によって表される分`COleDateTime`オブジェクトまたは`COleDateTime::error`場合は、分単位を取得できませんでした。

### <a name="remarks"></a>Remarks

有効な戻り値の 0 から 59 までの範囲です。

この値をクエリする他のメンバー関数について`COleDateTime`オブジェクト、メンバー関数は、次を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [曜日](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>例

例をご覧ください[GetHour](#gethour)します。

##  <a name="getmonth"></a>  COleDateTime::GetMonth

この日付/時刻値で表される月を取得します。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>戻り値

この値によって表される月`COleDateTime`オブジェクトまたは`COleDateTime::error`場合は、1 か月を取得できませんでした。

### <a name="remarks"></a>Remarks

有効な戻り値の 1 から 12 までの範囲。

この値をクエリする他のメンバー関数について`COleDateTime`オブジェクト、メンバー関数は、次を参照してください。

- [GetDay](#getday)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [曜日](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>例

例をご覧ください[GetDay](#getday)します。

##  <a name="getsecond"></a>  COleDateTime::GetSecond

この日付/時刻値によって表される秒を取得します。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>戻り値

この値によって表される秒`COleDateTime`オブジェクトまたは`COleDateTime::error`場合は、2 つ目を取得できませんでした。

### <a name="remarks"></a>Remarks

有効な戻り値の 0 から 59 までの範囲です。

> [!NOTE]
>  `COleDateTime`クラスはうるう秒をサポートしていません。

実装の詳細については`COleDateTime`、記事をご覧ください[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

この値をクエリする他のメンバー関数について`COleDateTime`オブジェクト、メンバー関数は、次を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [曜日](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>例

例をご覧ください[GetHour](#gethour)します。

##  <a name="getstatus"></a>  「

状態 (有効) を取得する指定された`COleDateTime`オブジェクト。

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>戻り値

この状態を返します`COleDateTime`値。 呼び出す場合`GetStatus`上、`COleDateTime`オブジェクトは、既定値は、構築が返されます無効です。 呼び出す場合`GetStatus`上、`COleDateTime`は null に設定するコンス トラクターで初期化されたオブジェクト`GetStatus`は null を返します。 参照してください**解説**詳細についてはします。

### <a name="remarks"></a>Remarks

戻り値は、`DateTimeStatus`列挙型内で定義されている、`COleDateTime`クラス。

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

これらのステータス値の簡単な説明は、次の一覧を参照してください。

- `COleDateTime::error` 日付/時刻値の一部を取得中にエラーが発生したことを示します。

- `COleDateTime::valid` 示しますこの`COleDateTime`オブジェクトが無効です。

- `COleDateTime::invalid` 示しますこの`COleDateTime`オブジェクトは無効です。 つまり、その値誤りがあります。

- `COleDateTime::null` 示しますこの`COleDateTime`オブジェクトが null の場合は、このオブジェクトの値が指定されていないこと。 (これは"使用しない場合の値、"C++ の NULL ではなくデータベースという意味で"null")。

状態、`COleDateTime`オブジェクトが無効で、次の場合。

- その値が設定されている場合、`VARIANT`または`COleVariant`値を日付/時刻値に変換できませんでした。

- その値が設定されている場合、 `time_t`、 `SYSTEMTIME`、または`FILETIME`値を有効な日付/時刻値に変換できませんでした。

- その値が設定されている場合`SetDateTime`無効なパラメーター値を使用します。

- このオブジェクトが、オーバーフローまたはアンダー フロー、代入演算操作中に具体的には場合、`+=`または`-=`します。

- 場合は、無効な値は、このオブジェクトに割り当てられました。

- このオブジェクトの状態が明示的に設定を使用して無効に`SetStatus`します。

操作の詳細については、無効なメンバー関数は、次を参照して状態を設定する可能性があります。

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [演算子 +、-](#operator_add_-)

- [演算子 + =、=](#operator_add_eq_-_eq)

境界の詳細については`COleDateTime`、値は、記事をご覧ください。[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

##  <a name="getyear"></a>  COleDateTime::GetYear

この日付/時刻値で表される年を取得します。

```
int GetYear() const throw();
```

### <a name="return-value"></a>戻り値

この値によって表される年間積算`COleDateTime`オブジェクトまたは`COleDateTime::error`場合は、年を取得できませんでした。

### <a name="remarks"></a>Remarks

有効な戻り値は、世紀を含む 100 ~ 9999 の範囲の範囲。

この値をクエリする他のメンバー関数について`COleDateTime`オブジェクト、メンバー関数は、次を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [曜日](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

境界の詳細については`COleDateTime`、値は、記事をご覧ください。[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

### <a name="example"></a>例

例をご覧ください[GetDay](#getday)します。

##  <a name="m_dt"></a>  COleDateTime::m_dt

基になる`DATE`この構造体`COleDateTime`オブジェクト。

```
DATE m_dt;
```

### <a name="remarks"></a>Remarks

> [!CAUTION]
>  値を変更、`DATE`この関数によって返されるポインターによってアクセスされるオブジェクトがこの値を変更`COleDateTime`オブジェクト。 この状態は変更されません`COleDateTime`オブジェクト。

実装の詳細については、`DATE`オブジェクトは、「[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

##  <a name="m_status"></a>  COleDateTime::m_status

この状態を含む`COleDateTime`オブジェクト。

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Remarks

このデータ メンバーの型は、列挙型`DateTimeStatus`、内で定義されている、`COleDateTime`クラス。 参照してください[は、「](#getstatus)詳細についてはします。

> [!CAUTION]
>  このデータ メンバーは、高度なプログラミングに適しています。 インライン メンバー関数を使用する必要があります[GetStatus](#getstatus)と[SetStatus](#setstatus)します。 参照してください`SetStatus`の他の注意に関するこのデータ メンバーを明示的に設定します。

##  <a name="operator_eq"></a>  COleDateTime::operator =

コピーを`COleDateTime`値。

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& udate) throw();
```

### <a name="remarks"></a>Remarks

これらのオーバー ロードされた代入演算子は、このソースの日付/時刻値をコピー`COleDateTime`オブジェクト。 これらのそれぞれの簡単な説明では、代入演算子のオーバー ロード。

- **operator = (** `dateSrc` **)** 値とオペランドの状態は、これにコピーされます`COleDateTime`オブジェクト。

- **operator = (** *varSrc* **)** 場合の変換、[バリアント](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)値 (または[COleVariant](../../mfc/reference/colevariant-class.md)オブジェクト) を日付/時刻 (vt _ を付けます日付) が成功すると、変換後の値がこれにコピー`COleDateTime`オブジェクトとその状態が有効に設定されます。 このオブジェクトの値が 0 (1899 年 12 月 30 日午前 0 時) に設定されている変換が成功しなかった場合、その状態は無効にします。

- **演算子 = (** `dtSrc` **)** 、`DATE`値にこのコピー`COleDateTime`オブジェクトとその状態が有効に設定されます。

- **operator = (** `timeSrc` **)** 、`time_t`または`__time64_t`値が変換され、これにコピー`COleDateTime`オブジェクト。 変換が成功した場合は、このオブジェクトの状態が設定無効です。失敗した場合は、設定されているかどうかが無効です。

- **operator = (** *systimeSrc* **)** 、 [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)値が変換され、これにコピー`COleDateTime`オブジェクト。 変換が成功した場合は、このオブジェクトの状態が設定無効です。失敗した場合は、設定されているかどうかが無効です。

- **operator = (** `udate` **)** 、`UDATE`値が変換され、これにコピー`COleDateTime`オブジェクト。 変換が成功した場合は、このオブジェクトの状態が設定無効です。失敗した場合は、設定されているかどうかが無効です。 A`UDATE`構造体は、「開」の日付を表します。 関数を参照してください。 [VarDateFromUdate](/windows/desktop/api/oleauto/nf-oleauto-vardatefromudate)の詳細。

- **operator = (** `filetimeSrc` **)** 、 [FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284)値が変換され、これにコピー`COleDateTime`オブジェクト。 変換が成功した場合は、このオブジェクトの状態が設定無効です。それ以外の場合に設定されている無効にします。 `FILETIME` 世界協定時刻 (UTC) を使用するは、ため、UTC 時刻を構造に渡す場合、結果は UTC 時刻を現地時刻に変換され、バリアントの時刻として格納されます。 この動作は、Visual C 6.0 および Visual C .NET 2003 SP2 のように同じです。 参照してください[ファイル回](/windows/desktop/SysInfo/file-times)詳細については、Windows sdk。

詳細については、次を参照してください。、[バリアント](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)Windows SDK 内のエントリ。

詳細については、`time_t`データ型を参照してください、[時間](../../c-runtime-library/reference/time-time32-time64.md)で機能、*ランタイム ライブラリ リファレンス*します。

詳細については、次を参照してください。、 [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)と[FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) Windows SDK 内の構造体。

境界の詳細については`COleDateTime`、値は、記事をご覧ください。[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

##  <a name="operator_add_-"></a>  COleDateTime::operator +、-

加算および減算`ColeDateTime`値。

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Remarks

`COleDateTime` オブジェクトは、絶対時刻を表します。 [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)オブジェクトは、相対時間を表します。 加算および減算することは、最初の 2 つの演算子、`COleDateTimeSpan`から値を`COleDateTime`値。 3 番目の演算子では、1 を減算できます。`COleDateTime`を生成する別の値を`COleDateTimeSpan`値。

結果の状態は null オペランドのいずれかの場合`COleDateTime`値は null です。

場合、その結果`COleDateTime`値が許容される値、状態の範囲外になる`COleDateTime`値が無効です。

オペランドのいずれかが有効ではないと、もう一方が null でない場合、結果の状態`COleDateTime`値が無効です。

**+** と**-** 場合演算子はアサート、`COleDateTime`オブジェクトの設定を null にします。 参照してください[COleDateTime 関係演算子](#coledatetime_relational_operators)例についてはします。

有効、無効、および null 状態の値の詳細については、次を参照してください。、[ついて](#m_status)メンバー変数。

境界の詳細については`COleDateTime`、値は、記事をご覧ください。[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  COleDateTime::operator + =、=

加算および減算、`ColeDateTime`値からこの`COleDateTime`オブジェクト。

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Remarks

これらの演算子を許可する加算および減算にする、`COleDateTimeSpan`値との間この`COleDateTime`します。 結果の状態は null オペランドのいずれかの場合`COleDateTime`値は null です。

場合、その結果`COleDateTime`値が許容される値、この状態の範囲外になる`COleDateTime`値が設定されて無効にします。

オペランドのいずれかが有効ではないと他が null でない場合、結果の状態`COleDateTime`値が無効です。

有効、無効、および null 状態の値の詳細については、次を参照してください。、[ついて](#m_status)メンバー変数。

**+=** と **-=** 場合演算子はアサート、`COleDateTime`オブジェクトの設定を null にします。 参照してください[COleDateTime 関係演算子](#coledatetime_relational_operators)例についてはします。

境界の詳細については`COleDateTime`、値は、記事をご覧ください。[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

##  <a name="operator_date"></a>  COleDateTime::operator 日付

変換を`ColeDateTime`値に、`DATE`します。

```
operator DATE() const throw();
```

### <a name="remarks"></a>Remarks

この演算子を返します、`DATE`値がこれからコピーしたオブジェクト`COleDateTime`オブジェクト。 実装の詳細については、`DATE`オブジェクトは、「[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

`DATE`場合演算子はアサート、`COleDateTime`オブジェクトの設定を null にします。 参照してください[COleDateTime 関係演算子](#coledatetime_relational_operators)例についてはします。

##  <a name="parsedatetime"></a>  COleDateTime::ParseDateTime

日付/時刻値を読み取るための文字列を解析します。

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>パラメーター

*lpszDate*<br/>
解析するには null で終わる文字列へのポインター。 詳細については、「解説」を参照してください。

*dwFlags*<br/>
ロケールの設定と解析のフラグを示します。 1 つ以上の次のフラグ:

- LOCALE_NOUSEROVERRIDE では、カスタム ユーザー設定ではなく、システムの既定のロケール設定を使用します。

- VAR_TIMEVALUEONLY は、解析中に、日付部分を無視します。

- VAR_DATEVALUEONLY は、解析中に時刻部分を無視します。

*lcid*<br/>
変換に使用するロケール ID を示します。

### <a name="return-value"></a>戻り値

文字列が FALSE の場合は、日付/時刻値に変換が正常にかどうかは TRUE を返します。

### <a name="remarks"></a>Remarks

文字列が日付/時刻に変換できた場合の値、この値`COleDateTime`オブジェクトが有効な値をその状態を設定します。

> [!NOTE]
>  100 ~ 9999 の範囲の年の値が範囲になければなりません。

*LpszDate*パラメーターは、さまざまな形式を取ることができます。 たとえば、次の文字列には、許容される日付/時刻書式が含まれます。

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

文字列の形式は日付/時刻値に変換できるかどうかのロケール ID にも影響に注意してください。

VAR_DATEVALUEONLY の場合は、時間の値は 0、または午前 0 時にかかる時間を設定します。 VAR_TIMEVALUEONLY の場合は、日付の値が日付 0、つまり 30 1899 年 12 月に設定されます。

文字列を日付/時刻値に変換できませんでしたか、この数値のオーバーフローがあった場合`COleDateTime`オブジェクトが無効です。

境界と実装の詳細については`COleDateTime`、値は、記事をご覧ください。[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

##  <a name="setdate"></a>  COleDateTime::SetDate

この日付を設定`COleDateTime`オブジェクト。

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>パラメーター

*nYear*、 *nMonth*、 *%n%n*<br/>
これにコピーされる日付の構成要素を示す`COleDateTime`オブジェクト。

### <a name="return-value"></a>戻り値

場合は 0 の値`COleDateTime`オブジェクトが設定された正常。 それ以外の場合、1。 この戻り値がに基づいて、`DateTimeStatus`列挙型。 詳細については、次を参照してください。、 [SetStatus](#setstatus)メンバー関数。

### <a name="remarks"></a>Remarks

日付は、指定した値に設定されます。 時間は、時間が 0、午前 0 時に設定されます。

パラメーター値の範囲は次の表を参照してください。

|パラメーター|境界|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*%n%n*|0 - 31|

月の日がオーバーフローした場合に、次の月と、1 か月の正しい日付に変換されますや年がインクリメントされます。 ゼロの日付の値では、前の月の最終日を示します。 動作は同じ`SystemTimeToVariantTime`します。

このオブジェクトの状態に設定して、パラメーターで指定された日付の値が有効でない場合`COleDateTime::invalid`します。 使用する必要があります[GetStatus](#getstatus)の有効性を確認、`DATE`値し、想定する必要があります、値の[m_dt](#m_dt)変更されないままになります。

日付値の例を次に示します。

|*nYear*|*nMonth*|*%n%n*|[値]|
|-------------|--------------|------------|-----------|
|2000|2|29|2000 年 2 月の 29|
|1776|7|4|1776 年 7 月 4 日|
|1925|4|35|35 年 1925年 4 月 (無効な日付)|
|10000|1|1|1 年 1 月 10000 (無効な日付)|

日付と時刻の両方を設定するを参照してください。 [COleDateTime::SetDateTime](#setdatetime)します。

この値をクエリするメンバー関数について`COleDateTime`オブジェクト、メンバー関数は、次を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [曜日](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

境界の詳細については`COleDateTime`、値は、記事をご覧ください。[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

##  <a name="setdatetime"></a>  COleDateTime::SetDateTime

この日時を設定`COleDateTime`オブジェクト。

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

*nYear*、 *nMonth*、 *%n%n*、*時間*、 *nMin*、 *nSec*<br/>
これにコピーされる日付と時刻のコンポーネントを示す`COleDateTime`オブジェクト。

### <a name="return-value"></a>戻り値

場合は 0 の値`COleDateTime`オブジェクトが設定された正常。 それ以外の場合、1。 この戻り値がに基づいて、`DateTimeStatus`列挙型。 詳細については、次を参照してください。、 [SetStatus](#setstatus)メンバー関数。

### <a name="remarks"></a>Remarks

パラメーター値の範囲は次の表を参照してください。

|パラメーター|境界|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*%n%n*|0 - 31|
|*時間*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

月の日がオーバーフローした場合に、次の月と、1 か月の正しい日付に変換されますや年がインクリメントされます。 ゼロの日付の値では、前の月の最終日を示します。 動作は同じ[SystemTimeToVariantTime](/windows/desktop/api/oleauto/nf-oleauto-systemtimetovarianttime)します。

パラメーターによって指定された日付または時刻の値が無効ですが、このオブジェクトの状態が無効ですし、このオブジェクトの値に設定する場合は変更されません。

時刻値のいくつかの例を次に示します。

|*時間*|*nMin*|*nSec*|[値]|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|無効|
|9|60|0|無効|

日付値の例を次に示します。

|*nYear*|*nMonth*|*%n%n*|[値]|
|-------------|--------------|------------|-----------|
|1995|4|16|1995 年 4 月 15日|
|1789|7|14|1789 の 17 年 7 月|
|1925|2|30|無効|
|10000|1|1|無効|

日付のみを設定するを参照してください。 [COleDateTime::SetDate](#setdate)します。 時刻のみを設定するを参照してください。 [COleDateTime::SetTime](#settime)します。

この値をクエリするメンバー関数について`COleDateTime`オブジェクト、メンバー関数は、次を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [曜日](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

境界の詳細については`COleDateTime`、値は、記事をご覧ください。[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

### <a name="example"></a>例

例をご覧ください[GetStatus](#getstatus)します。

##  <a name="setstatus"></a>  COleDateTime::SetStatus

この状態を設定`COleDateTime`オブジェクト。

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>パラメーター

*status*<br/>
この新しいステータス値`COleDateTime`オブジェクト。

### <a name="remarks"></a>Remarks

*状態*パラメーターの値によって定義されます、`DateTimeStatus`列挙型内で定義されている、`COleDateTime`クラス。 参照してください[は、「](#getstatus)詳細についてはします。

> [!CAUTION]
>  この関数は、高度なプログラミングに適しています。 この関数では、このオブジェクトのデータは変更されません。 状態を設定に使用されるほとんどの場合、 **null**または**無効な**します。 なお、代入演算子 ([演算子 =](#eq)) と[SetDateTime](#setdatetime)ソース値に基づいて、オブジェクトの状態を設定しないでください。

### <a name="example"></a>例

例をご覧ください[GetStatus](#getstatus)します。

##  <a name="settime"></a>  COleDateTime::SetTime

この時間を設定`COleDateTime`オブジェクト。

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>パラメーター

*時間*、 *nMin*、 *nSec*<br/>
これにコピーされる時間コンポーネントを示す`COleDateTime`オブジェクト。

### <a name="return-value"></a>戻り値

場合は 0 の値`COleDateTime`オブジェクトが設定された正常。 それ以外の場合、1。 この戻り値がに基づいて、`DateTimeStatus`列挙型。 詳細については、次を参照してください。、 [SetStatus](#setstatus)メンバー関数。

### <a name="remarks"></a>Remarks

時間は、指定した値に設定されます。 日付は、日 0、つまり 30 1899 年 12 月に設定されます。

パラメーター値の範囲は次の表を参照してください。

|パラメーター|境界|
|---------------|------------|
|*時間*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

パラメーターによって指定された値が有効でない時間 invalid であり、このオブジェクトの値をこのオブジェクトの状態が設定されている場合は変更されません。

時刻値のいくつかの例を次に示します。

|*時間*|*nMin*|*nSec*|[値]|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|無効|
|9|60|0|無効|

日付と時刻の両方を設定するを参照してください。 [COleDateTime::SetDateTime](#setdatetime)します。

この値をクエリするメンバー関数について`COleDateTime`オブジェクト、メンバー関数は、次を参照してください。

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [曜日](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

境界の詳細については`COleDateTime`、値は、記事をご覧ください。[日付と時刻: オートメーション サポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

### <a name="example"></a>例

例をご覧ください[SetDate](#setdate)します。

## <a name="see-also"></a>関連項目

[COleVariant クラス](../../mfc/reference/colevariant-class.md)<br/>
[CTime クラス](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan クラス](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)

