---
title: CTime クラス
ms.date: 10/18/2018
f1_keywords:
- CTime
- ATLTIME/ATL::CTime
- ATLTIME/ATL::CTime::CTime
- ATLTIME/ATL::CTime::Format
- ATLTIME/ATL::CTime::FormatGmt
- ATLTIME/ATL::CTime::GetAsDBTIMESTAMP
- ATLTIME/ATL::CTime::GetAsSystemTime
- ATLTIME/ATL::CTime::GetCurrentTime
- ATLTIME/ATL::CTime::GetDay
- ATLTIME/ATL::CTime::GetDayOfWeek
- ATLTIME/ATL::CTime::GetGmtTm
- ATLTIME/ATL::CTime::GetHour
- ATLTIME/ATL::CTime::GetLocalTm
- ATLTIME/ATL::CTime::GetMinute
- ATLTIME/ATL::CTime::GetMonth
- ATLTIME/ATL::CTime::GetSecond
- ATLTIME/ATL::CTime::GetTime
- ATLTIME/ATL::CTime::GetYear
- ATLTIME/ATL::CTime::Serialize64
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
ms.openlocfilehash: a73baab3e43467b76c1b4e3592314a4323d22ffb
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893978"
---
# <a name="ctime-class"></a>CTime クラス

絶対時刻と日付を表します。

## <a name="syntax"></a>構文

```
class CTime
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CTime::CTime](#ctime)|構築`CTime`さまざまな方法でオブジェクト。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CTime::Format](#format)|変換を`CTime`オブジェクトを書式設定された文字列に、ローカル タイム ゾーンに基づいて。|
|[CTime::FormatGmt](#formatgmt)|変換を`CTime`オブジェクトを書式設定された文字列に、UTC に基づいています。|
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|格納されている時間の情報に変換、 `CTime` Win32 と互換性のある DBTIMESTAMP 構造体へのオブジェクト。|
|[CTime::GetAsSystemTime](#getassystemtime)|格納されている時間の情報に変換、 `CTime` Win32 互換性のあるオブジェクト[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)構造体。|
|[CTime::GetCurrentTime](#getcurrenttime)|作成、 `CTime` (静的メンバー関数) の現在の時刻を表すオブジェクト。|
|[CTime::GetDay](#getday)|によって表される日を返します、`CTime`オブジェクト。|
|[CTime::GetDayOfWeek](#getdayofweek)|によって表される週の通算日を返す、`CTime`オブジェクト。|
|[CTime::GetGmtTm](#getgmttm)|分割、`CTime`オブジェクトをコンポーネントに、UTC に基づいています。|
|[CTime::GetHour](#gethour)|によって表される時間を返します、`CTime`オブジェクト。|
|[CTime::GetLocalTm](#getlocaltm)|分割、`CTime`オブジェクトをコンポーネントに、ローカル タイム ゾーンに基づいて。|
|[CTime::GetMinute](#getminute)|によって表される分が返されます、`CTime`オブジェクト。|
|[CTime::GetMonth](#getmonth)|によって表される月を返します、`CTime`オブジェクト。|
|[CTime::GetSecond](#getsecond)|によって表される秒を返します、`CTime`オブジェクト。|
|[CTime::GetTime](#gettime)|返します、 **_ _time64_t**値、指定された`CTime`オブジェクト。|
|[CTime::GetYear](#getyear)|によって表される年を返します、`CTime`オブジェクト。|
|[CTime::Serialize64](#serialize64)|アーカイブからデータをシリアル化します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[演算子 + -](#operator_add_-)|これらの演算子は加算および減算`CTimeSpan`と`CTime`オブジェクト。|
|[operator +=, -=](#operator_add_eq_-_eq)|これらの演算子は加算および減算、`CTimeSpan`オブジェクトとの間この`CTime`オブジェクト。|
|[演算子 =](#operator_eq)|代入演算子です。|
|[演算子 = =、< など。](#ctime_comparison_operators)|比較演算子。|

## <a name="remarks"></a>Remarks

`CTime` 基本クラスはありません。

`CTime` 値は、世界協定時刻 (グリニッジ標準時 GMT) には、世界協定時刻 (UTC) に基づいています。 参照してください[時間管理](../../c-runtime-library/time-management.md)タイム ゾーンを決定する方法についてはします。

作成するときに、`CTime`オブジェクト、設定、`nDST`標準時では実際には、ことを示す 0 より大きい値をその夏時間が有効であるかを示す 0 または C ランタイム ライブラリ コードの最上の 0 未満の値のパラメーターe 標準時間または夏時間が有効にしてがするかどうか。 `tm_isdst` は必須フィールドです。 設定しないかどうか、その値はない定義からの戻り値および[mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)は予測できません。 場合`timeptr`tm 構造体を以前の呼び出しによって返される[asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)、 [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)、または[localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)、`tm_isdst`フィールドが含まれています、正確な値。

コンパニオン クラス、 [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)、時間間隔を表します。

`CTime`と`CTimeSpan`クラスが派生させるために設計されていません。 サイズの仮想関数が存在しないため`CTime`と`CTimeSpan`オブジェクトは、厳密に 8 バイト。 ほとんどのメンバー関数は、インラインです。

> [!NOTE]
>  日付の上限は、12/31/3000 です。 下限値は 1970 年 1 月 1/12時 00分: 00 AM GMT です。

使用しての詳細については`CTime`、記事を参照して[日付と時刻](../../atl-mfc-shared/date-and-time.md)、および[時間管理](../../c-runtime-library/time-management.md)ランタイム ライブラリのリファレンス。

> [!NOTE]
>  `CTime` MFC 8.0 から MFC 7.1 構造に変更します。 シリアル化する場合、`CTime`構造体を使用して、**演算子 <<** MFC 8.0 またはそれ以降のバージョンでは、結果のファイルが読み取れない MFC の以前のバージョン。

## <a name="requirements"></a>必要条件

**ヘッダー:** atltime.h

##  <a name="ctime_comparison_operators"></a>  CTime 比較演算子

比較演算子。

```
bool operator==(CTime time) const throw();
bool operator!=(CTime time) const throw();
bool operator<(CTime time) const throw();
bool operator>(CTime time) const throw();
bool operator<=(CTime time) const throw();
bool operator>=(CTime time) const throw();
```

### <a name="parameters"></a>パラメーター

*time*<br/>
比較される `CTime` オブジェクト。

### <a name="return-value"></a>戻り値

これらの演算子の比較 2 つの絶対時間と TRUE を返す、条件が true である場合それ以外の場合は FALSE です。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

##  <a name="ctime"></a>  CTime::CTime

新たに作成`CTime`オブジェクトが、指定した時間を使用して初期化します。

```
CTime() throw();
CTime(__time64_t time) throw();
CTime(int nYear, int nMonth, int nDay,
      int nHour, int nMin, int nSec, int nDST = -1);
CTime(WORD wDosDate, WORD wDosTime, int nDST = -1);
CTime(const SYSTEMTIME& st, int nDST = - 1) throw();
CTime(const FILETIME& ft, int nDST = - 1);
CTime(const DBTIMESTAMP& dbts, int nDST = -1) throw();
```

### <a name="parameters"></a>パラメーター

*timeSrc*<br/>
示す、`CTime`既に存在するオブジェクト。

*time*<br/>
A`__time64_t`時刻の値は UTC 1970 年 1 月 1 日の後の秒数です。 これが、現地時刻に調整されることに注意してください。 たとえば、ニューヨークにして作成した場合、 `CTime` 0 の場合のパラメーターを渡すことによってオブジェクト[渡して](#getmonth)は 12 を返します。

*nYear*、 *nMonth*、 *%n%n*、*時間*、 *nMin*、 *nSec*<br/>
新しいにコピーされる日付と時刻の値を示す`CTime`オブジェクト。

*nDST*<br/>
夏時間が有効になっているかどうかを示します。 次の 3 つの値のいずれかを設定できます。

- *nDST* 0Standard 時間に設定が有効になっています。

- *nDST* 0Daylight の期間が有効になってより大きい値に設定します。

- *nDST* 0 the 既定よりも小さい値に設定します。 標準時間または夏時間が有効ではかどうかを自動的に計算します。

*wDosDate*、 *wDosTime*<br/>
日付と時刻の値を日付/時刻値に変換して、新しいコピーを MS-DOS`CTime`オブジェクト。

*st*<br/>
A [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)構造体の日付/時刻値に変換して、新しいコピーを`CTime`オブジェクト。

*ft*<br/>
A [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)構造体の日付/時刻値に変換して、新しいコピーを`CTime`オブジェクト。

*dbts*<br/>
現在の現地時刻を含む DBTIMESTAMP 構造体への参照。

### <a name="remarks"></a>Remarks

各コンス トラクターは、次に示します。

- `CTime();` 作成、初期化されていない`CTime`オブジェクト。 このコンス トラクターを定義することにより`CTime`オブジェクトの配列。 使用する前に有効な値では、このような配列を初期化する必要があります。

- `CTime( const CTime& );` 構築、`CTime`から別のオブジェクト`CTime`値。

- `CTime( __time64_t );` 構築、`CTime`オブジェクトから、 **_ _time64_t**型。 このコンス トラクターは、UTC 時刻が必要ですし、結果を格納する前に、結果をローカル時刻に変換します。

- `CTime( int, int, ...);` 構築、`CTime`各コンポーネントのローカル時刻のコンポーネントからのオブジェクトは、次の範囲に制限します。

   |コンポーネント|範囲|
   |---------------|-----------|
   |*nYear*|1970-3000|
   |*nMonth*|1-12|
   |*%n%n*|1-31|
   |*時間*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   このコンス トラクターは、UTC への適切な変換です。 1 つの場合、Microsoft Foundation Class ライブラリのデバッグ バージョンがアサートまたは範囲外の時間コンポーネントの詳細。 呼び出しの前に引数を検証する必要があります。 このコンス トラクターには、現地時刻が必要です。

- `CTime( WORD, WORD );` 構築、`CTime`オブジェクト指定した MS-DOS の日付と時刻の値から。 このコンス トラクターには、現地時刻が必要です。

- `CTime( const SYSTEMTIME& );` 構築、`CTime`オブジェクトから、`SYSTEMTIME`構造体。 このコンス トラクターには、現地時刻が必要です。

- `CTime( const FILETIME& );` 構築、`CTime`オブジェクトから、`FILETIME`構造体。 多くの場合は使用しません`CTime FILETIME`直接の初期化。 使用する場合、`CFile`にファイルを操作するオブジェクト`CFile::GetStatus`ファイルのタイムスタンプを取得する手順を`CTime`オブジェクトを初期化して、`FILETIME`構造体。 このコンス トラクターは、UTC に基づく時間と想定し、結果を格納する前にローカル時刻に自動的に値に変換します。

   > [!NOTE]
   > コンス トラクターを使用して、`DBTIMESTAMP`パラメーターは、OLEDB.h が含まれる場合にのみ使用できます。

詳細については、次を参照してください。、 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)と[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) Windows SDK の構造体。 参照してください、 [MS-DOS の日付と時刻](/windows/desktop/SysInfo/ms-dos-date-and-time)Windows SDK 内のエントリ。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

##  <a name="format"></a>  CTime::Format

日付/時刻値の書式設定された表現を作成するには、このメンバー関数を呼び出します。

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>パラメーター

*pszFormat*<br/>
ような文字列を書式設定、`printf`文字列の書式設定します。 割合に続くコードの書式設定 (`%`) 署名は、対応する置き換え`CTime`コンポーネント。 その他の文字書式指定文字列では、返される文字列をそのままコピーされます。 実行時の関数を参照してください。 [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)コードの書式設定の一覧についてはします。

*nFormatID*<br/>
この形式を識別する文字列の ID。

### <a name="return-value"></a>戻り値

A [CString](../../atl-mfc-shared/reference/cstringt-class.md)書式設定された時刻を格納しています。

### <a name="remarks"></a>Remarks

場合のこの状態`CTime`オブジェクトが null、戻り値は空の文字列。

書式設定する日付と時刻の値が午前 0 時から 3000 年 12 月 31 日、1970 年 1 の範囲外の場合、このメソッドが例外をスロー世界協定時刻 (UTC)。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

##  <a name="formatgmt"></a>  CTime::FormatGmt

これに対応する書式設定された文字列を生成`CTime`オブジェクト。

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>パラメーター

*pszFormat*<br/>
ような書式設定文字列を指定します、`printf`文字列の書式設定します。 実行時の関数を参照してください。 [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)詳細についてはします。

*nFormatID*<br/>
この形式を識別する文字列の ID。

### <a name="return-value"></a>戻り値

A [CString](../../atl-mfc-shared/reference/cstringt-class.md)書式設定された時刻を格納しています。

### <a name="remarks"></a>Remarks

時刻の値は変換されませんし、UTC に基づいて生成されます。

書式設定する日付と時刻の値が午前 0 時から 3000 年 12 月 31 日、1970 年 1 の範囲外の場合、このメソッドが例外をスロー世界協定時刻 (UTC)。

### <a name="example"></a>例

例をご覧ください[CTime::Format](#format)します。

##  <a name="getasdbtimestamp"></a>  CTime::GetAsDBTIMESTAMP

格納されている時間の情報に変換するには、このメンバー関数を呼び出す、 `CTime` Win32 と互換性のある DBTIMESTAMP 構造体へのオブジェクト。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>パラメーター

*dbts*<br/>
現在の現地時刻を含む DBTIMESTAMP 構造体への参照。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

参照先の結果として得られる時刻を格納*dbts*構造体。 `DBTIMESTAMP`この関数によって初期化されたデータ構造体は必要があります。 その`fraction`メンバーは 0 に設定します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

##  <a name="getassystemtime"></a>  CTime::GetAsSystemTime

格納されている時間の情報に変換するには、このメンバー関数を呼び出す、 `CTime` Win32 互換性のあるオブジェクト[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)構造体。

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>パラメーター

*timeDest*<br/>
参照を[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)の変換後の日付/時刻値を保持する構造体、`CTime`オブジェクト。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

`GetAsSystemTime` 参照先の結果として得られる時刻を格納*timeDest*構造体。 `SYSTEMTIME`この関数によって初期化されたデータ構造体は必要があります。 その`wMilliseconds`メンバーは 0 に設定します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

##  <a name="getcurrenttime"></a>  CTime::GetCurrentTime

返します、`CTime`現在の時刻を表すオブジェクト。

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>Remarks

現在のシステム日付と時刻を世界協定時刻 (UTC) で返します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

##  <a name="getday"></a>  CTime::GetDay

によって表される日を返します、`CTime`オブジェクト。

```
int GetDay() const throw();
```

### <a name="return-value"></a>戻り値

1 ~ 31 の範囲内のローカル時刻に基づき、月の日を返します。

### <a name="remarks"></a>Remarks

この関数を呼び出す`GetLocalTm`、内部の静的に割り当てられたバッファーを使用します。 このバッファーのデータには、他の呼び出しによって上書きされます`CTime`メンバー関数。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

##  <a name="getdayofweek"></a>  CTime::GetDayOfWeek

によって表される週の通算日を返す、`CTime`オブジェクト。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>戻り値

ローカル時刻に基づいて週の曜日を返します。1 = 日曜日、2 = 月曜日、7 = 土曜日。

### <a name="remarks"></a>Remarks

この関数を呼び出す`GetLocalTm`バッファーは内部静的に割り当てられます。 このバッファーのデータには、他の呼び出しによって上書きされます`CTime`メンバー関数。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

##  <a name="getgmttm"></a>  CTime::GetGmtTm

取得、 **struct tm**これに含まれる時間の分解を格納している`CTime`オブジェクト。

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>パラメーター

*ptm*<br/>
時刻のデータを受け取るバッファーへのポインター。 このポインターが NULL の場合は、例外がスローされます。

### <a name="return-value"></a>戻り値

入力へのポインター **struct tm**時にインクルード ファイルで定義されています。H. 参照してください[gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)構造体。

### <a name="remarks"></a>Remarks

`GetGmtTm` UTC を返します。

*ptm* NULL にすることはできません。 これで、以前の動作に戻す場合*ptm* _SECURE_ATL 未定義状態にし、内部ことを示す NULL は、静的に割り当てられたバッファーを使用する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

##  <a name="gethour"></a>  CTime::GetHour

によって表される時間を返します、`CTime`オブジェクト。

```
int GetHour() const throw();
```

### <a name="return-value"></a>戻り値

0 ~ 23 の範囲内のローカル時刻に基づいて、時間を返します。

### <a name="remarks"></a>Remarks

この関数を呼び出す`GetLocalTm`バッファーは内部静的に割り当てられます。 このバッファーのデータには、他の呼び出しによって上書きされます`CTime`メンバー関数。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

##  <a name="getlocaltm"></a>  CTime::GetLocalTm

取得、 **struct tm**これに含まれる時間の分解の含む`CTime`オブジェクト。

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>パラメーター

*ptm*<br/>
時刻のデータを受け取るバッファーへのポインター。 このポインターが NULL の場合は、例外がスローされます。

### <a name="return-value"></a>戻り値

入力へのポインター **struct tm**時にインクルード ファイルで定義されています。H. 参照してください[gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)構造体。

### <a name="remarks"></a>Remarks

`GetLocalTm` ローカル時刻を返します。

*ptm* NULL にすることはできません。 これで、以前の動作に戻す場合*ptm* _SECURE_ATL 未定義状態にし、内部ことを示す NULL は、静的に割り当てられたバッファーを使用する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

##  <a name="getminute"></a>  CTime::GetMinute

によって表される分が返されます、`CTime`オブジェクト。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>戻り値

0 ~ 59 の範囲内のローカル時刻に基づいて、分を返します。

### <a name="remarks"></a>Remarks

この関数を呼び出す`GetLocalTm`バッファーは内部静的に割り当てられます。 このバッファーのデータには、他の呼び出しによって上書きされます`CTime`メンバー関数。

### <a name="example"></a>例

例をご覧ください[GetHour](#gethour)します。

##  <a name="getmonth"></a>  CTime::GetMonth

によって表される月を返します、`CTime`オブジェクト。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>戻り値

1 ~ 12 の範囲内のローカル時刻に基づいて 1 か月を返します (1 年 1 月 =)。

### <a name="remarks"></a>Remarks

この関数を呼び出す`GetLocalTm`バッファーは内部静的に割り当てられます。 このバッファーのデータには、他の呼び出しによって上書きされます`CTime`メンバー関数。

### <a name="example"></a>例

例をご覧ください[GetDay](#getday)します。

##  <a name="getsecond"></a>  CTime::GetSecond

によって表される秒を返します、`CTime`オブジェクト。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>戻り値

秒を返します。 0 ~ 59 の範囲内のローカル時間に基づきます。

### <a name="remarks"></a>Remarks

この関数を呼び出す`GetLocalTm`バッファーは内部静的に割り当てられます。 このバッファーのデータには、他の呼び出しによって上書きされます`CTime`メンバー関数。

### <a name="example"></a>例

例をご覧ください[GetHour](#gethour)します。

##  <a name="gettime"></a>  CTime::GetTime

返します、 **_ _time64_t**値、指定された`CTime`オブジェクト。

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>戻り値

`GetTime` 現在までの秒数を返します`CTime`オブジェクトと 1970 年 1 月 1 日です。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

##  <a name="getyear"></a>  CTime::GetYear

によって表される年を返します、`CTime`オブジェクト。

```
int GetYear();
```

### <a name="return-value"></a>戻り値

年 1 月の範囲内のローカル時刻に基づいて、年を返します 1,1970、2038 年 1 月 18日 (両端を含む) にします。

### <a name="remarks"></a>Remarks

この関数を呼び出す`GetLocalTm`バッファーは内部静的に割り当てられます。 このバッファーのデータには、他の呼び出しによって上書きされます`CTime`メンバー関数。

### <a name="example"></a>例

例をご覧ください[GetDay](#getday)します。

##  <a name="operator_eq"></a>  CTime::operator =

代入演算子です。

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>パラメーター

*time*<br/>
新しい日付/時刻値。

### <a name="return-value"></a>戻り値

更新された`CTime`オブジェクト。

### <a name="remarks"></a>Remarks

このオーバー ロードされた代入演算子は、これに、元の時刻をコピー`CTime`オブジェクト。 時刻を内部ストレージを`CTime`オブジェクトはタイム ゾーンに依存しません。 タイム ゾーンの変換は、割り当ての際に必要ではありません。

##  <a name="operator_add_-"></a>  CTime::operator +、-

これらの演算子は加算および減算`CTimeSpan`と`CTime`オブジェクト。

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>パラメーター

*timeSpan*<br/>
`CTimeSpan`加算または減算するオブジェクト。

*time*<br/>
`CTime`減算するオブジェクト。

### <a name="return-value"></a>戻り値

A`CTime`または`CTimeSpan`操作の結果を表すオブジェクト。

### <a name="remarks"></a>Remarks

`CTime` オブジェクトが絶対的な時間を表す`CTimeSpan`オブジェクトは、相対時間を表します。 最初の 2 つの演算子を使用する加算および減算できます`CTimeSpan`オブジェクトとの間`CTime`オブジェクト。 3 番目の演算子では、1 を減算できます。`CTime`を生成する別のオブジェクトを`CTimeSpan`オブジェクト。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  CTime::operator +=, -=

これらの演算子は加算および減算、`CTimeSpan`オブジェクトとの間この`CTime`オブジェクト。

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
`CTimeSpan`加算または減算するオブジェクト。

### <a name="return-value"></a>戻り値

更新された`CTime`オブジェクト。

### <a name="remarks"></a>Remarks

これらの演算子を許可する加算および減算にする、`CTimeSpan`オブジェクトとの間この`CTime`オブジェクト。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

##  <a name="serialize64"></a>  CTime::Serialize64

> [!NOTE]
> このメソッドは、MFC プロジェクトで使用できるだけです。

関連付けられたメンバー変数に、アーカイブからデータをシリアル化します。

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>パラメーター

*ar*<br/>
`CArchive`を更新するオブジェクト。

### <a name="return-value"></a>戻り値

更新された`CArchive`オブジェクト。

## <a name="see-also"></a>関連項目

[asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s、_ftime32_s、_ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[CTimeSpan クラス](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)
