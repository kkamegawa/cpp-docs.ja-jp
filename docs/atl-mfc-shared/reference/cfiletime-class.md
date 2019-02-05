---
title: CFileTime クラス
ms.date: 10/18/2018
f1_keywords:
- CFileTime
- ATLTIME/ATL::CFileTime
- ATLTIME/ATL::CFileTime::CFileTime
- ATLTIME/ATL::CFileTime::GetCurrentTime
- ATLTIME/ATL::CFileTime::GetTime
- ATLTIME/ATL::CFileTime::LocalToUTC
- ATLTIME/ATL::CFileTime::SetTime
- ATLTIME/ATL::CFileTime::UTCToLocal
- ATLTIME/ATL::CFileTime::Day
- ATLTIME/ATL::CFileTime::Hour
- ATLTIME/ATL::CFileTime::Millisecond
- ATLTIME/ATL::CFileTime::Minute
- ATLTIME/ATL::CFileTime::Second
- ATLTIME/ATL::CFileTime::Week
helpviewer_keywords:
- CFileTime class
- shared classes, CFileTime
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
ms.openlocfilehash: 42c89bcfa064bbb151f9d110cbd25763dbd44185
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893939"
---
# <a name="cfiletime-class"></a>CFileTime クラス

このクラスは、ファイルに関連付けられている日付と時刻の値を管理するためのメソッドを提供します。

## <a name="syntax"></a>構文

```
class CFileTime :  public FILETIME
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CFileTime::CFileTime](#cfiletime)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CFileTime::GetCurrentTime](#getcurrenttime)|この静的関数を取得する、`CFileTime`現在のシステム日付と時刻を表すオブジェクト。|
|[CFileTime::GetTime](#gettime)|時刻を取得するには、このメソッドを呼び出して、`CFileTime`オブジェクト。|
|[CFileTime::LocalToUTC](#localtoutc)|ローカル ファイル時刻を世界協定時刻 (UTC) のファイル時刻に変換するには、このメソッドを呼び出します。|
|[CFileTime::SetTime](#settime)|によって格納される日時を設定するには、このメソッドを呼び出す、`CFileTime`オブジェクト。|
|[CFileTime::UTCToLocal](#utctolocal)|時間ベースで、世界協定時刻 (UTC) ファイルのローカル時刻に変換するには、このメソッドを呼び出します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CFileTime::operator -](#operator_-)|この演算子を使用してで減算を実行する`CFileTime`または`CFileTimeSpan`オブジェクト。|
|[CFileTime::operator! =](#operator_neq)|2 つを比較して`CFileTime`非等値オブジェクトです。|
|[CFileTime::operator +](#operator_add)|この演算子は、`CFileTimeSpan` オブジェクトで加算を実行するために使用します。|
|[CFileTime::operator +=](#operator_add_eq)|この演算子は、`CFileTimeSpan` オブジェクトで加算を実行し、結果を現在のオブジェクトに代入するために使用します。|
|[CFileTime::operator &lt;](#operator_lt)|この演算子は、2 つの `CFileTime` オブジェクトを比較して、小さい方を決定します。|
|[CFileTime::operator &lt;=](#operator_lt_eq)|この演算子では、2 つの `CFileTime` オブジェクトを比較して、等しいかどうか、または小さい方を決定します。|
|[CFileTime::operator =](#operator_eq)|代入演算子です。|
|[CFileTime::operator -=](#operator_-_eq)|この演算子を使用してで減算を実行、`CFileTimeSpan`オブジェクトし、結果を現在のオブジェクトに割り当てます。|
|[CFileTime::operator ==](#operator_eq_eq)|この演算子は、2 つの `CFileTime` オブジェクトが等しいかどうかを比較します。|
|[CFileTime::operator &gt;](#operator_gt)|この演算子は、2 つの `CFileTime` オブジェクトを比較して、大きい方を決定します。|
|[CFileTime::operator &gt;=](#operator_gt_eq)|この演算子は、2 つの `CFileTime` オブジェクトを比較して、等しいかどうか、または大きい方を決定します。|

### <a name="public-constants"></a>パブリック定数

|名前|説明|
|----------|-----------------|
|[CFileTime::Day](#day)|1 日を構成するための 100 ナノ秒間隔の数を格納する静的データ メンバー。|
|[CFileTime::Hour](#hour)|1 時間を構成するための 100 ナノ秒間隔の数を格納する静的データ メンバー。|
|[CFileTime::Millisecond](#millisecond)|1 ミリ秒を構成するための 100 ナノ秒間隔の数を格納する静的データ メンバー。|
|[CFileTime::Minute](#minute)|1 分を構成するための 100 ナノ秒間隔の数を格納する静的データ メンバー。|
|[CFileTime::Second](#second)|1 秒間を構成するための 100 ナノ秒間隔の数を格納する静的データ メンバー。|
|[CFileTime::Week](#week)|1 週間を構成するための 100 ナノ秒間隔の数を格納する静的データ メンバー。|

## <a name="remarks"></a>Remarks

このクラスは、作成、アクセスおよびファイルの変更に関連付けられている日付と時刻の値を管理するためのメソッドを提供します。 メソッドとこのクラスのデータはと共にで頻繁に使用`CFileTimeSpan`相対時刻値を処理するオブジェクト。

日付と時刻の値は、1601 年 1 月 1 日から 100 ナノ秒間隔の数を表す 64 ビット値として格納されます。 これは、世界協定時刻 (UTC) 形式です。

Const 静的メンバー変数は、計算が簡単に用意されています。

|メンバー変数|100 ナノ秒間隔の数|
|---------------------|-----------------------------------------|
|Millisecond|10,000|
|Second|ミリ秒\*1,000|
|Minute|2 番目\*60|
|Hour|分\*60|
|Day|1 時間\*24|
|週|1 日\*7|

**注**作成を記録できるすべてのファイル システムと最終アクセス時刻およびすべてのファイル システム、同じ方法でそれらを記録します。 Windows NT FAT ファイル システム上の例の作成の時間が 10 ミリ秒の解像度、書き込み時間が 2 秒単位の解像度およびアクセス時間が 1 日 (アクセス日) の解像度。 NTFS では、アクセス時間は 1 時間の解像度が。 さらに、FAT ディスク上の時刻を現地時刻に記録するが、NTFS がディスク上の時刻を UTC に記録します。 詳細については、次を参照してください。[ファイル回](/windows/desktop/SysInfo/file-times)します。

## <a name="inheritance-hierarchy"></a>継承階層

`FILETIME`

`CFileTime`

## <a name="requirements"></a>必要条件

**ヘッダー:** atltime.h

##  <a name="cfiletime"></a>  CFileTime::CFileTime

コンストラクターです。

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>パラメーター

*ft*<br/>
A [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)構造体。

*nTime*<br/>
日付と時間を 64 ビット値として表されます。

### <a name="remarks"></a>Remarks

`CFileTime` 、既存の日付と時刻からを使用してオブジェクトを作成できる、`FILETIME`構造体、または (ローカルまたは世界協定時刻 (UTC) 時刻形式) での 64 ビット値として表されます。 既定のコンス トラクターは、時間を 0 に設定します。

##  <a name="day"></a>  CFileTime::Day

1 日を構成するための 100 ナノ秒間隔の数を格納する静的データ メンバー。

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>例

例をご覧ください[CFileTime::Millisecond](#millisecond)します。

##  <a name="getcurrenttime"></a>  CFileTime::GetCurrentTime

この静的関数を取得する、`CFileTime`現在のシステム日付と時刻を表すオブジェクト。

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>戻り値

現在のシステム日付と時刻を世界協定時刻 (UTC) 形式で返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

##  <a name="gettime"></a>  CFileTime::GetTime

時刻を取得するには、このメソッドを呼び出して、`CFileTime`オブジェクト。

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>戻り値

ローカルまたは世界協定時刻 (UTC) 形式のいずれかである可能性があります、64 ビットの数値として日付を返します。

##  <a name="hour"></a>  CFileTime::Hour

1 時間を構成するための 100 ナノ秒間隔の数を格納する静的データ メンバー。

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>例

例をご覧ください[CFileTime::Millisecond](#millisecond)します。

##  <a name="localtoutc"></a>  CFileTime::LocalToUTC

ローカル ファイル時刻を世界協定時刻 (UTC) のファイル時刻に変換するには、このメソッドを呼び出します。

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>戻り値

返します、 `CFileTime` UTC 形式で時刻を含むオブジェクト。

### <a name="example"></a>例

例をご覧ください[CFileTime::UTCToLocal](#utctolocal)します。

##  <a name="millisecond"></a>  CFileTime::Millisecond

1 ミリ秒を構成するための 100 ナノ秒間隔の数を格納する静的データ メンバー。

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

##  <a name="minute"></a>  CFileTime::Minute

1 分を構成するための 100 ナノ秒間隔の数を格納する静的データ メンバー。

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>例

例をご覧ください[CFileTime::Millisecond](#millisecond)します。

##  <a name="operator_-"></a>  CFileTime::operator -

この演算子を使用してで減算を実行する`CFileTime`または`CFileTimeSpan`オブジェクト。

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
`CFileTimeSpan` オブジェクト。

*ft*<br/>
`CFileTime` オブジェクト。

### <a name="return-value"></a>戻り値

返します、`CFileTime`オブジェクトまたは`CFileTimeSpan`2 つのオブジェクト間の時間差の結果を表すオブジェクト。

##  <a name="operator_neq"></a>  CFileTime::operator! =

2 つを比較して`CFileTime`非等値オブジェクトです。

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>パラメーター

*ft*<br/>
比較される `CFileTime` オブジェクト。

### <a name="return-value"></a>戻り値

比較対象となる項目が等しくない場合は TRUE を返します、`CFileTime`オブジェクトの場合は FALSE。

##  <a name="operator_add"></a>  CFileTime::operator +

この演算子は、`CFileTimeSpan` オブジェクトで加算を実行するために使用します。

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
`CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

返します、`CFileTime`元の時刻と相対時刻の結果を表すオブジェクト。

##  <a name="operator_add_eq"></a>  CFileTime::operator +=

この演算子は、`CFileTimeSpan` オブジェクトで加算を実行し、結果を現在のオブジェクトに代入するために使用します。

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
`CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

更新された返します`CFileTime`元の時刻と相対時刻の結果を表すオブジェクト。

##  <a name="operator_lt"></a>  CFileTime::operator &lt;

この演算子は、2 つの `CFileTime` オブジェクトを比較して、小さい方を決定します。

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>パラメーター

*ft*<br/>
比較される `CFileTime` オブジェクト。

### <a name="return-value"></a>戻り値

かどうか、最初のオブジェクトが、2 番目より小さい (前の時刻) FALSE それ以外の場合は TRUE を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

##  <a name="operator_lt_eq"></a>  CFileTime::operator &lt;=

この演算子では、2 つの `CFileTime` オブジェクトを比較して、等しいかどうか、または小さい方を決定します。

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>パラメーター

*ft*<br/>
比較される `CFileTime` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトが (前の時刻) よりも小さいか、2 番目に等しい場合は TRUE を返しますそれ以外の場合は FALSE。

##  <a name="operator_eq"></a>  CFileTime::operator =

代入演算子です。

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>パラメーター

*ft*<br/>
A`CFileTime`新しい時刻と日付を含むオブジェクト。

### <a name="return-value"></a>戻り値

更新された返します`CFileTime`オブジェクト。

##  <a name="operator_-_eq"></a>  CFileTime::operator -=

この演算子を使用してで減算を実行、`CFileTimeSpan`オブジェクトし、結果を現在のオブジェクトに割り当てます。

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
A`CFileTimeSpan`減算する相対的な時間を含むオブジェクト。

### <a name="return-value"></a>戻り値

更新された返します`CFileTime`オブジェクト。

##  <a name="operator_eq_eq"></a>  CFileTime::operator ==

この演算子は、2 つの `CFileTime` オブジェクトが等しいかどうかを比較します。

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>パラメーター

*ft*<br/>
`CFileTime`と比較するオブジェクト。

### <a name="return-value"></a>戻り値

オブジェクトが等しい場合は、TRUE を返します。

##  <a name="operator_gt"></a>  CFileTime::operator &gt;

この演算子は、2 つの `CFileTime` オブジェクトを比較して、大きい方を決定します。

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>パラメーター

*ft*<br/>
比較される `CFileTime` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトが (後の時刻) より大きい場合は TRUE を返します 2 番目のそれ以外の場合は FALSE。

##  <a name="operator_gt_eq"></a>  CFileTime::operator &gt;=

この演算子は、2 つの `CFileTime` オブジェクトを比較して、等しいかどうか、または大きい方を決定します。

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>パラメーター

*ft*<br/>
比較される `CFileTime` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトが (後の時刻) より大きいか、2 番目に等しい場合は TRUE を返しますそれ以外の場合は FALSE。

##  <a name="second"></a>  CFileTime::Second

1 日を構成するための 100 ナノ秒間隔の数を格納する静的データ メンバー。

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>例

例をご覧ください[CFileTime::Millisecond](#millisecond)します。

##  <a name="settime"></a>  CFileTime::SetTime

によって格納される日時を設定するには、このメソッドを呼び出す、`CFileTime`オブジェクト。

```
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>パラメーター

*nTime*<br/>
日付と時刻、世界協定時刻 (UTC) 形式またはローカルのいずれかを表す 64 ビット値。

##  <a name="utctolocal"></a>  CFileTime::UTCToLocal

時間ベースで、世界協定時刻 (UTC) ファイルのローカル時刻に変換するには、このメソッドを呼び出します。

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>戻り値

返します、`CFileTime`ファイルのローカル時刻の形式で時刻を含むオブジェクト。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

##  <a name="week"></a>  CFileTime::Week

1 週間を構成するための 100 ナノ秒間隔の数を格納する静的データ メンバー。

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>例

例をご覧ください[CFileTime::Millisecond](#millisecond)します。

## <a name="see-also"></a>関連項目

[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTimeSpan クラス](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)
