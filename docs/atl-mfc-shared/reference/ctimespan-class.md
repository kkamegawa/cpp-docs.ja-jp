---
title: CTimeSpan クラス
ms.date: 10/18/2018
f1_keywords:
- CTimeSpan
- ATLTIME/ATL::CTimeSpan
- ATLTIME/ATL::CTimeSpan::CTimeSpan
- ATLTIME/ATL::CTimeSpan::Format
- ATLTIME/ATL::CTimeSpan::GetDays
- ATLTIME/ATL::CTimeSpan::GetHours
- ATLTIME/ATL::CTimeSpan::GetMinutes
- ATLTIME/ATL::CTimeSpan::GetSeconds
- ATLTIME/ATL::CTimeSpan::GetTimeSpan
- ATLTIME/ATL::CTimeSpan::GetTotalHours
- ATLTIME/ATL::CTimeSpan::GetTotalMinutes
- ATLTIME/ATL::CTimeSpan::GetTotalSeconds
- ATLTIME/ATL::CTimeSpan::Serialize64
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
ms.openlocfilehash: 3c80260c1f57e49a34b4e9f3331f4d0d69ab30ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252534"
---
# <a name="ctimespan-class"></a>CTimeSpan クラス

時間間隔の秒数として内部的に格納されている、時間。

## <a name="syntax"></a>構文

```
class CTimeSpan
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CTimeSpan::CTimeSpan](#ctimespan)|構築`CTimeSpan`さまざまな方法でオブジェクト。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CTimeSpan::Format](#format)|変換を`CTimeSpan`書式設定された文字列にします。|
|[CTimeSpan::GetDays](#getdays)|この完全な日数を表す値を返します`CTimeSpan`します。|
|[CTimeSpan::GetHours](#gethours)|現在の日付 (-23 ~ 23) の時間数を表す値を返します。|
|[CTimeSpan::GetMinutes](#getminutes)|現在の時間 (-59 ~ 59) で分単位の数を表す値を返します。|
|[CTimeSpan::GetSeconds](#getseconds)|現在の分 (-59 ~ 59) の秒数を表す値を返します。|
|[CTimeSpan::GetTimeSpan](#gettimespan)|値を返します、`CTimeSpan`オブジェクト。|
|[CTimeSpan::GetTotalHours](#gettotalhours)|これで完了時間の合計数を表す値を返します`CTimeSpan`します。|
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|この分数の合計数を表す値を返します`CTimeSpan`します。|
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|これで完了秒の合計数を表す値を返します`CTimeSpan`します。|
|[CTimeSpan::Serialize64](#serialize64)|アーカイブからデータをシリアル化します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[演算子 + -](#operator_add_-)|追加し、減算`CTimeSpan`オブジェクト。|
|[operator + = =](#operator_add_eq_-_eq)|追加し、減算、`CTimeSpan`オブジェクトとの間この`CTimeSpan`します。|
|[演算子 = = < など。](#ctimespan_comparison_operators)|2 つの相対時刻値を比較します。|

## <a name="remarks"></a>Remarks

`CTimeSpan` 基本クラスはありません。

`CTimeSpan` 関数は、さまざまな組み合わせの日、時間、分、秒と秒に変換します。

`CTimeSpan`にオブジェクトが格納されている、 **_ _time64_t**構造体は、8 バイトです。

コンパニオン クラス、 [CTime](../../atl-mfc-shared/reference/ctime-class.md)、絶対時刻を表します。

`CTime`と`CTimeSpan`クラスが派生させるために設計されていません。 両方のサイズの仮想関数が存在しないため`CTime`と`CTimeSpan`オブジェクトは、厳密に 8 バイト。 ほとんどのメンバー関数は、インラインです。

使用しての詳細については`CTimeSpan`、記事を参照して[日付と時刻](../../atl-mfc-shared/date-and-time.md)、および[時間管理](../../c-runtime-library/time-management.md)で、*ランタイム ライブラリ リファレンス*します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atltime.h

##  <a name="ctimespan_comparison_operators"></a>  CTimeSpan 比較演算子

比較演算子。

```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
比較対象のオブジェクト。

### <a name="return-value"></a>戻り値

これらの演算子は、2 つの相対時間の値を比較します。 条件が true である場合は TRUE、返すそれ以外の場合は FALSE です。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

##  <a name="ctimespan"></a>  CTimeSpan::CTimeSpan

構築`CTimeSpan`さまざまな方法でオブジェクト。

```
CTimeSpan() throw();
CTimeSpan(__time64_t time) throw();

CTimeSpan(
    LONG lDays,
    int nHours,
    int nMins,
    int nSecs) throw();
```

### <a name="parameters"></a>パラメーター

*timeSpanSrc*<br/>
A`CTimeSpan`既に存在するオブジェクト。

*time*<br/>
A **_ _time64_t**時刻の値は、時間間隔の秒数です。

*lDays*、 *nHours*、 *nMins*、 *nSecs*<br/>
日数、時間、分、および秒に、それぞれします。

### <a name="remarks"></a>Remarks

これらすべてのコンス トラクターを作成する新しい`CTimeSpan`オブジェクトの指定された相対時間を使用して初期化します。 各コンス トラクターは、次に示します。

- `CTimeSpan( );` 作成、初期化されていない`CTimeSpan`オブジェクト。

- `CTimeSpan( const CTimeSpan& );` 構築、`CTimeSpan`から別のオブジェクト`CTimeSpan`値。

- `CTimeSpan( __time64_t );` 構築、`CTimeSpan`オブジェクトから、 **_ _time64_t**型。

- `CTimeSpan( LONG, int, int, int );` 構築、`CTimeSpan`の各構成要素からオブジェクトが、次の範囲に制限されます。

   |コンポーネント|範囲|
   |---------------|-----------|
   |*lDays*|0 ~ 25,000 (概算)|
   |*nHours*|0-23|
   |*nMins*|0-59|
   |*nSecs*|0-59|

Microsoft Foundation Class ライブラリのデバッグ バージョンのかどうか、時刻のコンポーネントの 1 つ以上が範囲外ですがアサートすることに注意してください。 呼び出す前に引数を検証するユーザーの責任になります。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

##  <a name="format"></a>  CTimeSpan::Format

これに対応する書式設定された文字列を生成`CTimeSpan`します。

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>パラメーター

*pFormat*, *pszFormat*<br/>
ような文字列を書式設定、`printf`文字列の書式設定します。 割合に続くコードの書式設定 (`%`) 署名は、対応する置き換え`CTimeSpan`コンポーネント。 その他の文字書式指定文字列では、返される文字列をそのままコピーされます。 値との書式設定コードの意味`Format`を以下に示します。

- **%D**この日の合計 `CTimeSpan`

- **%H**は現在の日の時間

- **%M**現在の 1 時間分

- **%S**現在の時間 (秒)

- **%%** パーセント記号

*nID*<br/>
この形式を識別する文字列の ID。

### <a name="return-value"></a>戻り値

A`CString`書式設定された時刻を表すオブジェクト。

### <a name="remarks"></a>Remarks

ライブラリのデバッグ バージョンは、書式設定コードをチェックし、コードは、上記の一覧にないかどうかをアサートします。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

##  <a name="getdays"></a>  CTimeSpan::GetDays

この完全な日数を表す値を返します`CTimeSpan`します。

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>戻り値

時間範囲内の 24 時間の完全な日数を返します。 この値は、時間間隔が負の場合は負にあります。

### <a name="remarks"></a>Remarks

夏時間を引き起こす可能性のある注`GetDays`可能性のある意外な結果が返されます。 たとえば、ときに DST が有効で`GetDays`年 4 月の 1 日 1 時間を短縮し、そのため、完了日とは見なされませんので、29、30、として 4 月 1 日と月 1 日の数を報告します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

##  <a name="gethours"></a>  CTimeSpan::GetHours

現在の日付 (-23 ~ 23) の時間数を表す値を返します。

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>戻り値

現在の日付、時間数を返します。 範囲は、-23 ~ 23 です。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

##  <a name="getminutes"></a>  CTimeSpan::GetMinutes

現在の時間 (-59 ~ 59) で分単位の数を表す値を返します。

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>戻り値

現在の時間の分数を返します。 範囲は、-59 ~ 59 です。

### <a name="example"></a>例

例をご覧ください[GetHours](#gethours)します。

##  <a name="getseconds"></a>  CTimeSpan::GetSeconds

現在の分 (-59 ~ 59) の秒数を表す値を返します。

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>戻り値

現在の分の秒数を返します。 範囲は、-59 ~ 59 です。

### <a name="example"></a>例

例をご覧ください[GetHours](#gethours)します。

##  <a name="gettimespan"></a>  CTimeSpan::GetTimeSpan

値を返します、`CTimeSpan`オブジェクト。

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>戻り値

現在の値を返します、`CTimeSpan`オブジェクト。

##  <a name="gettotalhours"></a>  CTimeSpan::GetTotalHours

これで完了時間の合計数を表す値を返します`CTimeSpan`します。

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>戻り値

これで完了時間の合計数を返します`CTimeSpan`します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

##  <a name="gettotalminutes"></a>  CTimeSpan::GetTotalMinutes

この分数の合計数を表す値を返します`CTimeSpan`します。

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>戻り値

この分数の合計数を返します`CTimeSpan`します。

### <a name="example"></a>例

例をご覧ください[従来](#gettotalhours)します。

##  <a name="gettotalseconds"></a>  CTimeSpan::GetTotalSeconds

これで完了秒の合計数を表す値を返します`CTimeSpan`します。

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>戻り値

これで完了秒の合計数を返します`CTimeSpan`します。

### <a name="example"></a>例

例をご覧ください[従来](#gettotalhours)します。

##  <a name="operator_add_-"></a>  CTimeSpan::operator +, -

追加し、減算`CTimeSpan`オブジェクト。

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
追加する値、`CTimeSpan`オブジェクト。

### <a name="return-value"></a>戻り値

A`CTimeSpan`操作の結果を表すオブジェクト。

### <a name="remarks"></a>Remarks

これら 2 つの演算子を許可する加算および減算`CTimeSpan`との相互間のオブジェクト。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  CTimeSpan::operator +=, -=

追加し、減算、`CTimeSpan`オブジェクトとの間この`CTimeSpan`します。

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>パラメーター

*span*<br/>
追加する値、`CTimeSpan`オブジェクト。

### <a name="return-value"></a>戻り値

更新された`CTimeSpan`オブジェクト。

### <a name="remarks"></a>Remarks

これらの演算子を許可する加算および減算にする、`CTimeSpan`オブジェクトとの間この`CTimeSpan`します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

##  <a name="serialize64"></a>  CTimeSpan::Serialize64

> [!NOTE]
>  このメソッドは、MFC プロジェクトで使用できるだけです。

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

[asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)
