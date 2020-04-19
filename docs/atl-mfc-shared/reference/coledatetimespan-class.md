---
title: COleDateTimeSpan クラス
ms.date: 03/27/2019
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
ms.openlocfilehash: b68a984488f37326f3b0c1249a5f17a3eb76548b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198201"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan クラス

時間間隔の相対的な時間を表します。

## <a name="syntax"></a>構文

```
class COleDateTimeSpan
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|`COleDateTimeSpan` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleDateTimeSpan::Format](#format)|書式設定された文字列表現を生成、`COleDateTimeSpan`オブジェクト。|
|[COleDateTimeSpan::GetDays](#getdays)|このスパンの日の部分を返します`COleDateTimeSpan`オブジェクトが表す。|
|[COleDateTimeSpan::GetHours](#gethours)|このスパンの時間部分を返します`COleDateTimeSpan`オブジェクトが表す。|
|[COleDateTimeSpan::GetMinutes](#getminutes)|このスパンの分部分を返します`COleDateTimeSpan`オブジェクトが表す。|
|[COleDateTimeSpan::GetSeconds](#getseconds)|このスパンの 2 番目の部分を返します`COleDateTimeSpan`オブジェクトが表す。|
|[COleDateTimeSpan::GetStatus](#getstatus)|この状態 (有効) を取得`COleDateTimeSpan`オブジェクト。|
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|この日数を返します`COleDateTimeSpan`オブジェクトが表す。|
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|この時間数を返します`COleDateTimeSpan`オブジェクトが表す。|
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|この分の数を返します`COleDateTimeSpan`オブジェクトが表す。|
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|この秒数を返します`COleDateTimeSpan`オブジェクトが表す。|
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|この値を設定`COleDateTimeSpan`オブジェクト。|
|[COleDateTimeSpan::SetStatus](#setstatus)|これのステータス (有効) を設定`COleDateTimeSpan`オブジェクト。|

### <a name="public-operators"></a>パブリック演算子

|||
|-|-|
|[operator +、-](#operator_add_-)|`COleDateTimeSpan`の値の加算、減算、および符号の変更。|
|[operator +=, -=](#operator_add_eq_-_eq)|加算および減算、`COleDateTimeSpan`値からこの`COleDateTimeSpan`値。|
|[operator=](#operator_eq)|コピーを`COleDateTimeSpan`値。|
|[operator ==、<、<=](#coledatetimespan_relational_operators)|2 つの`COleDateTimeSpan`の値の比較。|
|[operator double](#operator_double)|この`COleDateTimeSpan`の値を**double**に変換。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[COleDateTimeSpan::m_span](#m_span)|この`COleDateTimeSpan`オブジェクトの基になる**double**を含んでいます。|
|[COleDateTimeSpan::m_status](#m_status)|この状態を含む`COleDateTimeSpan`オブジェクト。|

## <a name="remarks"></a>Remarks

`COleDateTimeSpan` 基本クラスはありません。

A`COleDateTimeSpan`日で時間を保持します。

`COleDateTimeSpan` そのコンパニオン クラスと共に使用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)します。 `COleDateTime` カプセル化、 `DATE` OLE オートメーションのデータ型。 `COleDateTime` 絶対時刻値を表します。 すべて`COleDateTime`計算が含まれる`COleDateTimeSpan`値。 これらのクラス間の関係は、間に 1 つに似ています[CTime](../../atl-mfc-shared/reference/ctime-class.md)と[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)します。

詳細については、`COleDateTime`と`COleDateTimeSpan`クラスは、記事をご覧ください。[日付と時刻。オートメーションのサポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** ATLComTime.h

##  <a name="coledatetimespan_relational_operators"></a>  COleDateTimeSpan 関係演算子

比較演算子。

```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```

### <a name="parameters"></a>パラメーター

*dateSpan*<br/>
比較対象の `COleDateTimeSpan`。

### <a name="return-value"></a>戻り値

これらの演算子は 2 つの日付/時間値と戻り値は TRUE を比較条件が true である場合それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

> [!NOTE]
>  ATLASSERT がいずれかのオペランドが有効でない場合に発生します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

##  <a name="coledatetimespan"></a>  COleDateTimeSpan::COleDateTimeSpan

`COleDateTimeSpan` オブジェクトを構築します。

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>パラメーター

*dblSpanSrc*<br/>
新しいにコピーされる日数`COleDateTimeSpan`オブジェクト。

*lDays*、 *nHours*、 *nMins*、 *nSecs*<br/>
新しいにコピーされる日付と時刻の値を示す`COleDateTimeSpan`オブジェクト。

### <a name="remarks"></a>Remarks

これらのコンス トラクターのすべてが新規作成`COleDateTimeSpan`オブジェクトが、指定した値に初期化します。 これらのコンス トラクターのそれぞれの簡単な説明に従います。

- **COleDateTimeSpan ()** を構築、`COleDateTimeSpan`を 0 に初期化されるオブジェクト。

- **COleDateTimeSpan (** `dblSpanSrc` **)** を構築、`COleDateTimeSpan`浮動小数点値からのオブジェクト。

- **COleDateTimeSpan (** `lDays` **、** `nHours` **、** `nMins` **、** `nSecs` **)** 構築、`COleDateTimeSpan`オブジェクトの指定した数値の値に初期化します。

新しいステータス`COleDateTimeSpan`オブジェクトが有効に設定されます。

境界の詳細については`COleDateTimeSpan`、値は、記事をご覧ください。[日付と時刻。オートメーションのサポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

##  <a name="format"></a>  COleDateTimeSpan::Format

書式設定された文字列表現を生成、`COleDateTimeSpan`オブジェクト。

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>パラメーター

*pFormat*<br/>
ような文字列を書式設定、`printf`文字列の書式設定します。 割合に続くコードの書式設定 (`%`) 署名は、対応する置き換え`COleDateTimeSpan`コンポーネント。 その他の文字書式指定文字列では、返される文字列をそのままコピーされます。 値との書式設定コードの意味`Format`を以下に示します。

- **%H**は現在の日の時間

- **%M**現在の 1 時間分

- **%S**現在の時間 (秒)

- **%%** パーセント記号

上に示した 4 つの形式は、形式が受け入れる唯一のコードです。

-

*nID*<br/>
コントロールの書式設定文字列のリソース ID。

### <a name="return-value"></a>戻り値

A`CString`書式設定された日付/時間値を格納しています。

### <a name="remarks"></a>Remarks

時間間隔の値の書式設定された表現を作成するこれらの関数を呼び出します。 場合のこの状態`COleDateTimeSpan`オブジェクトが null、戻り値は空の文字列。 状態が有効でない場合は、戻り値の文字列が設定されている文字列リソースによって指定されます。

この関数の形式の簡単な説明に従います。

**Format(** *pFormat* **)**<br/>
この形式でパーセント記号 (%) が付いている特殊な書式設定コードを含む書式指定文字列を使用して値を書式化`printf`します。 書式指定文字列は、関数にパラメーターとして渡されます。

**Format(** *nID* **)**<br/>
この形式でパーセント記号 (%) が付いている特殊な書式設定コードを含む書式指定文字列を使用して値を書式化`printf`します。 書式指定文字列は、リソースです。 この文字列リソースの ID は、パラメーターとして渡されます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

##  <a name="getdays"></a>  COleDateTimeSpan::GetDays

この日付/時間値の日の部分を取得します。

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>戻り値

この日付/時間値の日付の部分。

### <a name="remarks"></a>Remarks

戻り値は、約 - この関数の範囲から 3,615,000 と 3,615,000 します。

その他の関数の値をクエリで、`COleDateTimeSpan`オブジェクト、メンバー関数は、次を参照してください。

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [従来](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

##  <a name="gethours"></a>  COleDateTimeSpan::GetHours

この日付/時間値の時間部分を取得します。

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>戻り値

この日付/時間値の時間部分。

### <a name="remarks"></a>Remarks

この関数の範囲 - 23 23 ~ からの戻り値。

その他の関数の値をクエリで、`COleDateTimeSpan`オブジェクト、メンバー関数は、次を参照してください。

- [GetDays](#getdays)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [従来](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

##  <a name="getminutes"></a>  COleDateTimeSpan::GetMinutes

この日付/時間値の分の部分を取得します。

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>戻り値

この日付/時間値の分の部分。

### <a name="remarks"></a>Remarks

この関数の範囲 - 59 59 ~ からの戻り値。

その他の関数の値をクエリで、`COleDateTimeSpan`オブジェクト、メンバー関数は、次を参照してください。

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [従来](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

##  <a name="getseconds"></a>  COleDateTimeSpan::GetSeconds

この日付/時間値の 2 番目の部分を取得します。

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>戻り値

この日付/時間値の秒の部分。

### <a name="remarks"></a>Remarks

この関数の範囲 - 59 59 ~ からの戻り値。

その他の関数の値をクエリで、`COleDateTimeSpan`オブジェクト、メンバー関数は、次を参照してください。

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetTotalDays](#gettotaldays)

- [従来](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

##  <a name="getstatus"></a>  COleDateTimeSpan::GetStatus

この状態 (有効) を取得`COleDateTimeSpan`オブジェクト。

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>戻り値

この状態`COleDateTimeSpan`値。

### <a name="remarks"></a>Remarks

戻り値は、`DateTimeSpanStatus`列挙型内で定義されている、`COleDateTimeSpan`クラス。

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

これらのステータス値の簡単な説明は、次の一覧を参照してください。

- `COleDateTimeSpan::valid` 示しますこの`COleDateTimeSpan`オブジェクトが無効です。

- `COleDateTimeSpan::invalid` 示しますこの`COleDateTimeSpan`オブジェクトは無効です。 つまり、その値誤りがあります。

- `COleDateTimeSpan::null` 示しますこの`COleDateTimeSpan`オブジェクトが null の場合は、このオブジェクトの値が指定されていないこと。 (これは"使用しない場合の値、"C++ の NULL ではなくデータベースという意味で"null")。

状態、`COleDateTimeSpan`オブジェクトが無効で、次の場合。

- このオブジェクトが、オーバーフローまたはアンダー フロー、代入演算操作中に具体的には場合、`+=`または`-=`します。

- 場合は、無効な値は、このオブジェクトに割り当てられました。

- このオブジェクトの状態が明示的に設定を使用して無効に`SetStatus`します。

無効な状態を設定することがありますのある操作の詳細については、次を参照してください。 [COleDateTimeSpan::operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)と[COleDateTimeSpan::operator + =、-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)します。

境界の詳細については`COleDateTimeSpan`、値は、記事をご覧ください。[日付と時刻。オートメーションのサポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

##  <a name="gettotaldays"></a>  COleDateTimeSpan::GetTotalDays

日数で表されるこの日付/時間値を取得します。

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>戻り値

この日付/時間間隔は、日数で表される値。 この関数は、double 型の値を返すようにプロトタイプ宣言は、常に整数値を返します。

### <a name="remarks"></a>Remarks

3\.65e6 と 3.65e6 約 - この関数の範囲からの戻り値。

その他の関数の値をクエリで、`COleDateTimeSpan`オブジェクト、メンバー関数は、次を参照してください。

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [従来](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

##  <a name="gettotalhours"></a>  COleDateTimeSpan::GetTotalHours

時間単位で表すこの日付/時間値を取得します。

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>戻り値

この日付/時間間隔は、時間単位で表す値。 この関数は、double 型の値を返すようにプロトタイプ宣言は、常に整数値を返します。

### <a name="remarks"></a>Remarks

8\.77e7 と 8.77e7 約 - この関数の範囲からの戻り値。

その他の関数の値をクエリで、`COleDateTimeSpan`オブジェクト、メンバー関数は、次を参照してください。

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>例

例をご覧ください[誤差](#gettotaldays)します。

##  <a name="gettotalminutes"></a>  COleDateTimeSpan::GetTotalMinutes

この日付/時間値を分単位で表現を取得します。

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>戻り値

この日付/時間値が分単位で表現します。 この関数は、double 型の値を返すようにプロトタイプ宣言は、常に整数値を返します。

### <a name="remarks"></a>Remarks

5\.26e9 と 5.26e9 約 - この関数の範囲からの戻り値。

その他の関数の値をクエリで、`COleDateTimeSpan`オブジェクト、メンバー関数は、次を参照してください。

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [従来](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>例

例をご覧ください[誤差](#gettotaldays)します。

##  <a name="gettotalseconds"></a>  COleDateTimeSpan::GetTotalSeconds

秒単位で表すこの日付/時間値を取得します。

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>戻り値

この日付/時間は、秒単位で表す値。 この関数は、double 型の値を返すようにプロトタイプ宣言は、常に整数値を返します。

### <a name="remarks"></a>Remarks

この関数からの戻り値の範囲の間で約 - 3.16e11 に 3.16e11 です。

その他の関数の値をクエリで、`COleDateTimeSpan`オブジェクト、メンバー関数は、次を参照してください。

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [従来](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>例

例をご覧ください[誤差](#gettotaldays)します。

##  <a name="m_span"></a>  COleDateTimeSpan::m_span

この`COleDateTimeSpan`オブジェクトの基になる**double**を含んでいます。

```
double m_span;
```

### <a name="remarks"></a>Remarks

この値は日の日付/時間を表します。

> [!CAUTION]
>  値を変更、**double**データ メンバーはこの値を変更`COleDateTimeSpan`オブジェクト。 この状態は変更されません`COleDateTimeSpan`オブジェクト。

##  <a name="m_status"></a>  COleDateTimeSpan::m_status

このデータ メンバーの型は、列挙型`DateTimeSpanStatus`、内で定義されている、`COleDateTimeSpan`クラス。

```
DateTimeSpanStatus m_status;
```

### <a name="remarks"></a>Remarks

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

これらのステータス値の簡単な説明は、次の一覧を参照してください。

- `COleDateTimeSpan::valid` 示しますこの`COleDateTimeSpan`オブジェクトが無効です。

- `COleDateTimeSpan::invalid` 示しますこの`COleDateTimeSpan`オブジェクトは無効です。 つまり、その値誤りがあります。

- `COleDateTimeSpan::null` 示しますこの`COleDateTimeSpan`オブジェクトが null の場合は、このオブジェクトの値が指定されていないこと。 (これは"使用しない場合の値、"C++ の NULL ではなくデータベースという意味で"null")。

状態、`COleDateTimeSpan`オブジェクトが無効で、次の場合。

- このオブジェクトが、オーバーフローまたはアンダー フロー、代入演算操作中に具体的には場合、`+=`または`-=`します。

- 場合は、無効な値は、このオブジェクトに割り当てられました。

- このオブジェクトの状態が明示的に設定を使用して無効に[SetStatus](#setstatus)します。

無効な状態を設定することがありますのある操作の詳細については、次を参照してください。 [COleDateTimeSpan::operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)と[COleDateTimeSpan::operator + =、-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)します。

> [!CAUTION]
>  このデータ メンバーは、高度なプログラミングに適しています。 インライン メンバー関数を使用する必要があります[GetStatus](#getstatus)と[SetStatus](#setstatus)します。 参照してください`SetStatus`の他の注意に関するこのデータ メンバーを明示的に設定します。

境界の詳細については`COleDateTimeSpan`、値は、記事をご覧ください。[日付と時刻。オートメーションのサポート](../../atl-mfc-shared/date-and-time-automation-support.md)します。

##  <a name="operator_eq"></a>  COleDateTimeSpan::operator =

コピーを`COleDateTimeSpan`値。

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>Remarks

このオーバー ロードされた代入演算子は、このソースの日付/時間値をコピー`COleDateTimeSpan`オブジェクト。

##  <a name="operator_add_-"></a>  COleDateTimeSpan::operator +, -

`COleDateTimeSpan`の値の加算、減算、および符号の変更。

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>Remarks

最初の 2 つの演算子を追加し、日付/時間値を減算できます。 3 つ目では、日付/時間間隔の値の符号を変更できます。

結果の状態は null オペランドのいずれかの場合`COleDateTimeSpan`値は null です。

オペランドのいずれかが有効ではないと、もう一方が null でない場合、結果の状態`COleDateTimeSpan`値が無効です。

有効、無効、および null 状態の値の詳細については、次を参照してください。、[ついて](#m_status)メンバー変数。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  COleDateTimeSpan::operator +=, -=

加算および減算、`COleDateTimeSpan`値からこの`COleDateTimeSpan`値。

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Remarks

これらの演算子では、追加し、これから日付/時間値を減算できます。`COleDateTimeSpan`オブジェクト。 結果の状態は null オペランドのいずれかの場合`COleDateTimeSpan`値は null です。

オペランドのいずれかが有効ではないと、もう一方が null でない場合、結果の状態`COleDateTimeSpan`値が無効です。

有効、無効、および null 状態の値の詳細については、次を参照してください。、[ついて](#m_status)メンバー変数。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

##  <a name="operator_double"></a>  COleDateTimeSpan::operator double

この変換`COleDateTimeSpan`値を**double**します。

```
operator double() const throw();
```

### <a name="remarks"></a>Remarks

この演算子は、この値を返します`COleDateTimeSpan`日間の浮動小数点数としての値。

##  <a name="setdatetimespan"></a>  COleDateTimeSpan::SetDateTimeSpan

この日付/時間値の値を設定します。

```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>パラメーター

*lDays*、 *nHours*、 *nMins*、 *nSecs*<br/>
これにコピーされる日付範囲と時間範囲の値を示す`COleDateTimeSpan`オブジェクト。

### <a name="remarks"></a>Remarks

関数の値をクエリで、`COleDateTimeSpan`オブジェクト、メンバー関数は、次を参照してください。

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [従来](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

##  <a name="setstatus"></a>  COleDateTimeSpan::SetStatus

これのステータス (有効) を設定`COleDateTimeSpan`オブジェクト。

```
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>パラメーター

*status*<br/>
この新しいステータス値`COleDateTimeSpan`オブジェクト。

### <a name="remarks"></a>Remarks

*状態*パラメーターの値によって定義されます、`DateTimeSpanStatus`列挙型内で定義されている、`COleDateTimeSpan`クラス。

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

これらのステータス値の簡単な説明は、次の一覧を参照してください。

- `COleDateTimeSpan::valid` 示しますこの`COleDateTimeSpan`オブジェクトが無効です。

- `COleDateTimeSpan::invalid` 示しますこの`COleDateTimeSpan`オブジェクトは無効です。 つまり、その値誤りがあります。

- `COleDateTimeSpan::null` 示しますこの`COleDateTimeSpan`オブジェクトが null の場合は、このオブジェクトの値が指定されていないこと。 (これは"使用しない場合の値、"C++ の NULL ではなくデータベースという意味で"null")。

   > [!CAUTION]
   > この関数は、高度なプログラミングに適しています。 この関数では、このオブジェクトのデータは変更されません。 状態を設定に使用されるほとんどの場合、 **null**または**無効な**します。 なお、代入演算子 ([operator =](#operator_eq)) と[SetDateTimeSpan](#setdatetimespan)ソース値に基づいて、オブジェクトの状態を設定しないでください。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>関連項目

[COleDateTime クラス](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[CTime クラス](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan クラス](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)
