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
ms.openlocfilehash: b24d1e4d3e670a820c41735617b7db6780ff137c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491477"
---
# <a name="cfiletime-class"></a>CFileTime クラス

このクラスには、ファイルに関連付けられた日付と時刻の値を管理するためのメソッドが用意されています。

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
|[CFileTime::GetCurrentTime](#getcurrenttime)|現在のシステム日付と時刻を`CFileTime`表すオブジェクトを取得するには、この静的関数を呼び出します。|
|[CFileTime::GetTime](#gettime)|`CFileTime`オブジェクトから時刻を取得するには、このメソッドを呼び出します。|
|[CFileTime::LocalToUTC](#localtoutc)|世界協定時刻 (UTC) に基づいてローカルファイル時刻をファイル時刻に変換するには、このメソッドを呼び出します。|
|[CFileTime::SetTime](#settime)|`CFileTime`オブジェクトによって格納された日付と時刻を設定するには、このメソッドを呼び出します。|
|[CFileTime::UTCToLocal](#utctolocal)|世界協定時刻 (UTC) に基づいて時刻をローカルファイル時刻に変換するには、このメソッドを呼び出します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CFileTime:: operator-](#operator_-)|この演算子は、 `CFileTime`オブジェクトまたは`CFileTimeSpan`オブジェクトに対して減算を実行するために使用されます。|
|[CFileTime:: operator! =](#operator_neq)|この演算子は、 `CFileTime` 2 つのオブジェクトが等しくないかどうかを比較します。|
|[CFileTime:: operator +](#operator_add)|この演算子は、`CFileTimeSpan` オブジェクトで加算を実行するために使用します。|
|[CFileTime:: operator + =](#operator_add_eq)|この演算子は、`CFileTimeSpan` オブジェクトで加算を実行し、結果を現在のオブジェクトに代入するために使用します。|
|[CFileTime:: operator&lt;](#operator_lt)|この演算子は、2 つの `CFileTime` オブジェクトを比較して、小さい方を決定します。|
|[CFileTime:: operator&lt;=](#operator_lt_eq)|この演算子では、2 つの `CFileTime` オブジェクトを比較して、等しいかどうか、または小さい方を決定します。|
|[CFileTime:: operator =](#operator_eq)|代入演算子。|
|[CFileTime:: operator-=](#operator_-_eq)|この演算子は、 `CFileTimeSpan`オブジェクトに対して減算を実行し、その結果を現在のオブジェクトに代入するために使用されます。|
|[CFileTime::operator ==](#operator_eq_eq)|この演算子は、2 つの `CFileTime` オブジェクトが等しいかどうかを比較します。|
|[CFileTime:: operator&gt;](#operator_gt)|この演算子は、2 つの `CFileTime` オブジェクトを比較して、大きい方を決定します。|
|[CFileTime:: operator&gt;=](#operator_gt_eq)|この演算子は、2 つの `CFileTime` オブジェクトを比較して、等しいかどうか、または大きい方を決定します。|

### <a name="public-constants"></a>パブリック定数

|名前|説明|
|----------|-----------------|
|[CFileTime::D ay](#day)|1日を構成する100ナノ秒間隔の数を格納する静的データメンバー。|
|[CFileTime::Hour](#hour)|1時間を構成する100ナノ秒間隔の数を格納する静的データメンバー。|
|[CFileTime:: ミリ秒](#millisecond)|1ミリ秒を構成する100ナノ秒間隔の数を格納する静的データメンバー。|
|[CFileTime:: Minute](#minute)|1分間に構成される100ナノ秒間隔の数を格納する静的データメンバー。|
|[CFileTime::Second](#second)|1秒間に構成される100ナノ秒間隔の数を格納する静的データメンバー。|
|[CFileTime:: Week](#week)|1週間を構成する100ナノ秒間隔の数を格納する静的データメンバー。|

## <a name="remarks"></a>Remarks

このクラスは、ファイルの作成、アクセス、および変更に関連付けられた日付と時刻の値を管理するためのメソッドを提供します。 このクラスのメソッドとデータは、相対的な時刻値を`CFileTimeSpan`処理するオブジェクトと共に頻繁に使用されます。

日付と時刻の値は、1601年1月1日以降の100ナノ秒間隔の数を表す64ビット値として格納されます。 これは世界協定時刻 (UTC) 形式です。

計算を簡略化するために、次の静的な定数メンバー変数が用意されています。

|メンバー変数|100ナノ秒間隔の数|
|---------------------|-----------------------------------------|
|Millisecond|10,000|
|Second|ミリ\*秒1000|
|Minute|2 \*番目の60|
|Hour|分\* 60|
|Day|時間\* 24|
|週|7 \*日目|

**メモ**すべてのファイルシステムで作成と最終アクセス時刻を記録することはできず、すべてのファイルシステムが同じ方法でそれらを記録するわけではありません。 たとえば、Windows NT FAT ファイルシステムでは、作成時刻には10ミリ秒の解像度、書き込み時間は2秒の解像度、アクセス時間には1日 (アクセス日) の解決方法があります。 NTFS では、アクセス時間に1時間の解決策があります。 さらに、FAT はディスク上の時刻をローカル時刻に記録しますが、NTFS は時刻を UTC でディスクに記録します。 詳細については、「[ファイル時間](/windows/win32/SysInfo/file-times)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`FILETIME`

`CFileTime`

## <a name="requirements"></a>必要条件

**ヘッダー:** atltime. h

##  <a name="cfiletime"></a>CFileTime::CFileTime

コンストラクターです。

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>パラメーター

*cm*<br/>
[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)構造体。

*nTime*<br/>
64ビット値で表される日付と時刻。

### <a name="remarks"></a>Remarks

オブジェクト`CFileTime`は、 `FILETIME`構造体の既存の日付と時刻を使用して作成することも、64ビット値 (現地時刻形式または世界協定時刻 (UTC) の時刻形式) として表すこともできます。 既定のコンストラクターは、時刻を0に設定します。

##  <a name="day"></a>CFileTime::D ay

1日を構成する100ナノ秒間隔の数を格納する静的データメンバー。

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>例

[CFileTime:: ミリ秒](#millisecond)の例を参照してください。

##  <a name="getcurrenttime"></a>  CFileTime::GetCurrentTime

現在のシステム日付と時刻を`CFileTime`表すオブジェクトを取得するには、この静的関数を呼び出します。

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>戻り値

現在のシステム日付と時刻を世界協定時刻 (UTC) 形式で返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

##  <a name="gettime"></a>  CFileTime::GetTime

`CFileTime`オブジェクトから時刻を取得するには、このメソッドを呼び出します。

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>戻り値

日付と時刻を64ビットの数値として返します。現地時刻または世界協定時刻 (UTC) 形式で指定できます。

##  <a name="hour"></a>  CFileTime::Hour

1時間を構成する100ナノ秒間隔の数を格納する静的データメンバー。

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>例

[CFileTime:: ミリ秒](#millisecond)の例を参照してください。

##  <a name="localtoutc"></a>  CFileTime::LocalToUTC

世界協定時刻 (UTC) に基づいてローカルファイル時刻をファイル時刻に変換するには、このメソッドを呼び出します。

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>戻り値

時刻を UTC 形式で格納しているオブジェクトを返します。`CFileTime`

### <a name="example"></a>例

[CFileTime:: UTCToLocal](#utctolocal)の例を参照してください。

##  <a name="millisecond"></a>  CFileTime::Millisecond

1ミリ秒を構成する100ナノ秒間隔の数を格納する静的データメンバー。

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

##  <a name="minute"></a>  CFileTime::Minute

1分間に構成される100ナノ秒間隔の数を格納する静的データメンバー。

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>例

[CFileTime:: ミリ秒](#millisecond)の例を参照してください。

##  <a name="operator_-"></a>  CFileTime::operator -

この演算子は、 `CFileTime`オブジェクトまたは`CFileTimeSpan`オブジェクトに対して減算を実行するために使用されます。

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>パラメーター

*スパン*<br/>
`CFileTimeSpan` オブジェクト。

*cm*<br/>
`CFileTime` オブジェクト。

### <a name="return-value"></a>戻り値

2つのオブジェクト間`CFileTimeSpan`の時差の結果を表すオブジェクトまたはオブジェクトを返します。`CFileTime`

##  <a name="operator_neq"></a>CFileTime:: operator! =

この演算子は、 `CFileTime` 2 つのオブジェクトが等しくないかどうかを比較します。

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>パラメーター

*cm*<br/>
比較される `CFileTime` オブジェクト。

### <a name="return-value"></a>戻り値

比較対象の項目が`CFileTime`オブジェクトと等しくない場合は TRUE、それ以外の場合は FALSE を返します。

##  <a name="operator_add"></a>CFileTime:: operator +

この演算子は、`CFileTimeSpan` オブジェクトで加算を実行するために使用します。

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*スパン*<br/>
`CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

元の時刻に相対的な時間を加えた結果を表すオブジェクトを返します。`CFileTime`

##  <a name="operator_add_eq"></a>CFileTime:: operator + =

この演算子は、`CFileTimeSpan` オブジェクトで加算を実行し、結果を現在のオブジェクトに代入するために使用します。

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>パラメーター

*スパン*<br/>
`CFileTimeSpan` オブジェクト。

### <a name="return-value"></a>戻り値

元の時刻`CFileTime`に相対的な時間を加えた結果を表す、更新されたオブジェクトを返します。

##  <a name="operator_lt"></a>  CFileTime::operator &lt;

この演算子は、2 つの `CFileTime` オブジェクトを比較して、小さい方を決定します。

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>パラメーター

*cm*<br/>
比較される `CFileTime` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトが2番目のオブジェクトよりも古い場合は TRUE、それ以外の場合は FALSE を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

##  <a name="operator_lt_eq"></a>  CFileTime::operator &lt;=

この演算子では、2 つの `CFileTime` オブジェクトを比較して、等しいかどうか、または小さい方を決定します。

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>パラメーター

*cm*<br/>
比較される `CFileTime` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトが (前の時刻) より小さいか、2番目のオブジェクトと等しい場合は TRUE、それ以外の場合は FALSE を返します。

##  <a name="operator_eq"></a>  CFileTime::operator =

代入演算子。

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>パラメーター

*cm*<br/>
新しい日時を格納しているオブジェクト。`CFileTime`

### <a name="return-value"></a>戻り値

更新さ`CFileTime`れたオブジェクトを返します。

##  <a name="operator_-_eq"></a>CFileTime:: operator-=

この演算子は、 `CFileTimeSpan`オブジェクトに対して減算を実行し、その結果を現在のオブジェクトに代入するために使用されます。

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>パラメーター

*スパン*<br/>
減算する相対時間を格納しているオブジェクト。`CFileTimeSpan`

### <a name="return-value"></a>戻り値

更新さ`CFileTime`れたオブジェクトを返します。

##  <a name="operator_eq_eq"></a>  CFileTime::operator ==

この演算子は、2 つの `CFileTime` オブジェクトが等しいかどうかを比較します。

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>パラメーター

*cm*<br/>
比較`CFileTime`するオブジェクト。

### <a name="return-value"></a>戻り値

オブジェクトが等しい場合は TRUE、それ以外の場合は FALSE を返します。

##  <a name="operator_gt"></a>  CFileTime::operator &gt;

この演算子は、2 つの `CFileTime` オブジェクトを比較して、大きい方を決定します。

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>パラメーター

*cm*<br/>
比較される `CFileTime` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトが2番目のオブジェクトよりも大きい (後の時刻) の場合は TRUE、それ以外の場合は FALSE を返します。

##  <a name="operator_gt_eq"></a>  CFileTime::operator &gt;=

この演算子は、2 つの `CFileTime` オブジェクトを比較して、等しいかどうか、または大きい方を決定します。

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>パラメーター

*cm*<br/>
比較される `CFileTime` オブジェクト。

### <a name="return-value"></a>戻り値

最初のオブジェクトが (後の時刻) よりも大きいか、または2番目のオブジェクトと等しい場合は TRUE、それ以外の場合は FALSE を返します。

##  <a name="second"></a>  CFileTime::Second

1日を構成する100ナノ秒間隔の数を格納する静的データメンバー。

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>例

[CFileTime:: ミリ秒](#millisecond)の例を参照してください。

##  <a name="settime"></a>  CFileTime::SetTime

`CFileTime`オブジェクトによって格納された日付と時刻を設定するには、このメソッドを呼び出します。

```
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>パラメーター

*nTime*<br/>
日付と時刻を現地形式または世界協定時刻 (UTC) 形式で表す64ビット値。

##  <a name="utctolocal"></a>  CFileTime::UTCToLocal

世界協定時刻 (UTC) に基づいて時刻をローカルファイル時刻に変換するには、このメソッドを呼び出します。

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>戻り値

ローカルファイルの時刻形式で時刻を格納しているオブジェクトを返します。`CFileTime`

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

##  <a name="week"></a>CFileTime:: Week

1週間を構成する100ナノ秒間隔の数を格納する静的データメンバー。

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>例

[CFileTime:: ミリ秒](#millisecond)の例を参照してください。

## <a name="see-also"></a>関連項目

[返る](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTimeSpan クラス](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)
