---
title: time_get クラス
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get
- locale/std::time_get::char_type
- locale/std::time_get::iter_type
- locale/std::time_get::date_order
- locale/std::time_get::do_date_order
- locale/std::time_get::do_get
- locale/std::time_get::do_get_date
- locale/std::time_get::do_get_monthname
- locale/std::time_get::do_get_time
- locale/std::time_get::do_get_weekday
- locale/std::time_get::do_get_year
- locale/std::time_get::get
- locale/std::time_get::get_date
- locale/std::time_get::get_monthname
- locale/std::time_get::get_time
- locale/std::time_get::get_weekday
- locale/std::time_get::get_year
helpviewer_keywords:
- std::time_get [C++]
- std::time_get [C++], char_type
- std::time_get [C++], iter_type
- std::time_get [C++], date_order
- std::time_get [C++], do_date_order
- std::time_get [C++], do_get
- std::time_get [C++], do_get_date
- std::time_get [C++], do_get_monthname
- std::time_get [C++], do_get_time
- std::time_get [C++], do_get_weekday
- std::time_get [C++], do_get_year
- std::time_get [C++], get
- std::time_get [C++], get_date
- std::time_get [C++], get_monthname
- std::time_get [C++], get_time
- std::time_get [C++], get_weekday
- std::time_get [C++], get_year
ms.assetid: 869d5f5b-dbab-4628-8333-bdea7e272023
ms.openlocfilehash: e605423b829305bd1e7bde8be4fdbf312c8ce3c1
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685501"
---
# <a name="time_get-class"></a>time_get クラス

クラステンプレートは、`CharType` 型のシーケンスから時刻値への変換を制御するためにロケールファセットとして使用できるオブジェクトを表します。

## <a name="syntax"></a>構文

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>パラメーター

*Chartype* \
文字をエンコードするためにプログラム内で使用される型。

*InputIterator* \
時刻値の読み取り元の反復子。

## <a name="remarks"></a>Remarks

すべてのロケールのファセットと同様、静的オブジェクト ID に最初に格納されている値は 0 です。 格納されている値に初めてアクセスしようとすると、**id** に一意の正の値が格納されます。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[time_get](#time_get)|`time_get` 型のオブジェクトのコンストラクター。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[char_type](#char_type)|ロケールによって使用される文字を表すために使用される型。|
|[iter_type](#iter_type)|入力反復子を表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[date_order](#date_order)|ファセットによって使用される日付順序を返します。|
|[do_date_order](#do_date_order)|ファセットによって使用される日付順序を返すために呼び出されるプロテクト仮想メンバー関数。|
|[do_get](#do_get)|文字データを読み取り、時刻値に変換します。|
|[do_get_date](#do_get_date)|`x` の `strftime` 指定子によって生成される日付として文字列を解析するために呼び出されるプロテクト仮想メンバー関数。|
|[do_get_monthname](#do_get_monthname)|月の名前として文字列を解析するために呼び出されるプロテクト仮想メンバー関数。|
|[do_get_time](#do_get_time)|`X` の `strftime` 指定子によって生成される日付として文字列を解析するために呼び出されるプロテクト仮想メンバー関数。|
|[do_get_weekday](#do_get_weekday)|曜日の名前として文字列を解析するために呼び出されるプロテクト仮想メンバー関数。|
|[do_get_year](#do_get_year)|年の名前として文字列を解析するために呼び出されるプロテクト仮想メンバー関数。|
|[get](#get)|文字データのソースからデータを読み取り、そのデータを time 構造体に格納される時刻に変換します。|
|[get_date](#get_date)|`x` の `strftime` 指定子によって生成される日付として文字列を解析します。|
|[get_monthname](#get_monthname)|月の名前として文字列を解析します。|
|[get_time](#get_time)|`X` の `strftime` 指定子によって生成される日付として文字列を解析します。|
|[get_weekday](#get_weekday)|曜日の名前として文字列を解析します。|
|[get_year](#get_year)|年の名前として文字列を解析します。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<locale>

**名前空間:** std

## <a name="char_type"></a>  time_get::char_type

ロケールによって使用される文字を表すために使用される型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター **CharType** のシノニムです。

## <a name="date_order"></a>  time_get::date_order

ファセットによって使用される日付順序を返します。

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>戻り値

ファセットによって使用される日付順序。

### <a name="remarks"></a>Remarks

このメンバー関数は、[do_date_order](#do_date_order) を返します。

### <a name="example"></a>例

```cpp
// time_get_date_order.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
void po( char *p )
{
   locale loc( p );

   time_get <char>::dateorder order = use_facet <time_get <char> >( loc ).date_order ( );
   cout << loc.name( );
   switch (order){
      case time_base::dmy: cout << "(day, month, year)" << endl;
      break;
      case time_base::mdy: cout << "(month, day, year)" << endl;
      break;
      case time_base::ydm: cout << "(year, day, month)" << endl;
      break;
      case time_base::ymd: cout << "(year, month, day)"<< endl;
      break;
      case time_base::no_order: cout << "(no_order)"<< endl;
      break;
   }
}

int main( )
{
   po( "C" );
   po( "german" );
   po( "English_Britain" );
}
```

```Output
C(month, day, year)
German_Germany.1252(day, month, year)
English_United Kingdom.1252(day, month, year)
```

## <a name="do_date_order"></a>  time_get::do_date_order

ファセットによって使用される日付順序を返すために呼び出されるプロテクト仮想メンバー関数。

```cpp
virtual dateorder do_date_order() const;
```

### <a name="return-value"></a>戻り値

ファセットによって使用される日付順序。

### <a name="remarks"></a>Remarks

プロテクト仮想メンバー関数は、日付の部分が [do_get_date](#do_get_date) と一致する順序を示す、**time_base::dateorder** 型の値を返します。 この実装では、値は **time_base::mdy** であり、December 2, 1979 の形式の日付に対応します。

### <a name="example"></a>例

[date_order](#date_order) の例 (`do_date_order` を呼び出す) を参照してください。

## <a name="do_get"></a>  time_get::do_get

文字データを読み取り、時刻値に変換します。 1 つの変換指定子と修飾子を受け取ります。

```cpp
virtual iter_type
    do_get(
iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換されるシーケンスの開始位置を示す入力反復子。

*最後*の \
シーケンスの終了位置を示す入力反復子。

*iosbase. flags* \
ストリーム オブジェクト。

*状態*\
適切なビットマスク要素がエラーを示すように設定されている iosbase. flags のフィールド。

*ptm* \
時間を格納する時間構造体へのポインター。

*fmt* \
変換指定子の文字。

*mod* \
省略可能な修飾子文字。

### <a name="return-value"></a>戻り値

変換されない最初の要素を指定する反復子を返します。 変換エラーが発生すると `state` に `ios_base::failbit` が設定され、*最初*にが返されます。

### <a name="remarks"></a>Remarks

この仮想メンバー関数は、範囲 [`first`、`last`) 内の1つ以上の入力要素を変換およびスキップし、`*pt` の1つ以上のメンバーに格納されている値を確認します。 変換エラーが発生すると `state` に `ios_base::failbit` が設定され、*最初*にが返されます。 それ以外の場合、この関数は変換されていないの最初の要素を示す反復子を返します。

変換指定子は、次のとおりです。

`'a'` または `'A'`。動作は、[time_get::get_weekday](#get_weekday) と同じです。

`'b'`、`'B'`、または `'h'`。動作は、[time_get::get_monthname](#get_monthname) と同じです。

`'c'`。動作は `"%b %d %H : %M : %S %Y"` と同じです。

`'C'`。範囲 [0, 99] の 10 進入力フィールドを値 `val` に変換し、`val * 100 - 1900` を `pt-&tm_year` に格納します。

`'d'` または `'e'`。範囲 [1, 31] の 10 進入力フィールドを変換し、値を `pt-&tm_mday` に格納します。

`'D'`。動作は `"%m / %d / %y"` と同じです。

`'H'`。範囲 [0, 23] の 10 進入力フィールドを変換し、値を `pt-&tm_hour` に格納します。

`'I'`。範囲 [0, 11] の 10 進入力フィールドを変換し、値を `pt-&tm_hour` に格納します。

`'j'`。範囲 [1, 366] の 10 進入力フィールドを変換し、値を `pt-&tm_yday` に格納します。

`'m'`。範囲 [1, 12] の 10 進入力フィールドを値 `val` に変換し、`val - 1` とその値を `pt-&tm_mon` に格納します。

`'M'`。範囲 [0, 59] の 10 進入力フィールドを変換し、値を `pt-&tm_min` に格納します。

`'n'` または `'t'`。動作は `" "` と同じです。

`'p'`。"AM" または "am" を 0 に、"PM" または "pm" を 12 に変換し、その値を `pt-&tm_hour` に追加します。

`'r'`。動作は `"%I : %M : %S %p"` と同じです。

`'R'`。動作は `"%H %M"` と同じです。

`'S'`。範囲 [0, 59] の 10 進入力フィールドを変換し、値を `pt-&tm_sec` に格納します。

`'T'` または `'X'`。動作は `"%H : %M : S"` と同じです。

`'U'`。範囲 [0, 53] の 10 進入力フィールドを変換し、値を `pt-&tm_yday` に格納します。

`'w'`。範囲 [0, 6] の 10 進入力フィールドを変換し、値を `pt-&tm_wday` に格納します。

`'W'`。範囲 [0, 53] の 10 進入力フィールドを変換し、値を `pt-&tm_yday` に格納します。

`'x'`。動作は `"%d / %m / %y"` と同じです。

`'y'`。範囲 [0, 99] の 10 進入力フィールドを値 `val` に変換し、`val < 69  val + 100 : val` を `pt-&tm_year` に格納します。

`'Y'`。動作は、[time_get::get_year](#get_year) と同じです。

その他の変換指定子は、`state` に `ios_base::failbit` を設定して返します。 この実装では、修飾子には効果がありません。

## <a name="do_get_date"></a>  time_get::do_get_date

`strftime` の *x* 指定子によって生成される日付として文字列を解析するために呼び出されるプロテクト仮想メンバー関数。

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換されるシーケンスの開始位置を示す入力反復子。

*最後*の \
変換されるシーケンスの終了位置を示す入力反復子。

*iosbase. flags* \
書式設定フラグ。これが設定されている場合、通貨記号は省略可能です。それ以外の場合は必須です。

*状態*\
操作が成功したかどうかに基づき、ストリームの状態に適したビットマスク要素を設定します。

*ptm* \
日付の情報を格納する場所へのポインター。

### <a name="return-value"></a>戻り値

入力フィールドを超える先頭の要素を示す入力反復子。

### <a name="remarks"></a>Remarks

プロテクト仮想メンバー関数は、シーケンス [ `first`, `last`) の先頭から始め、空でない完全な日付入力フィールドを認識するまで、連続した要素との一致を試みます。 成功した場合は、このフィールドをコンポーネント**tm:: tm \_mon**、 **tm:: tm \_day**、および**tm:: tm \_year**と同等の値に変換し、それぞれの結果を `ptm->tm_mon`、`ptm->tm_day`、および `ptm->tm_year` に格納します。 これは、日付入力フィールドを超える先頭の要素を示す反復子を返します。 それ以外の場合、関数は `iosbase::failbit` を*状態*に設定します。 これは、有効な日付入力フィールドのプレフィックスを超える先頭の要素を示す反復子を返します。 どちらの場合も、戻り値が*last*と等しい場合、関数は*状態*の `ios_base::eofbit` を設定します。

日付入力フィールドの形式はロケールに依存します。 既定のロケールの場合、日付入力フィールドは MMM DD, YYYY の形式になります。各要素の説明は次のとおりです。

- MMM は、[get_monthname](#get_monthname) を呼び出すことで一致します。月を示します。

- DD は数字のシーケンスで、対応する数値が範囲 [1, 31] 内である必要があります。日にちを示します。

- YYYY は、[get_year](#get_year) を呼び出すことで一致します。年を示します。

リテラルのスペースとカンマは、入力シーケンス内の対応する要素と一致する必要があります。

### <a name="example"></a>例

[get_date](#get_date) の例 (`do_get_date` を呼び出す) を参照してください。

## <a name="do_get_monthname"></a>  time_get::do_get_monthname

月の名前として文字列を解析するために呼び出されるプロテクト仮想メンバー関数。

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換されるシーケンスの開始位置を示す入力反復子。

*最後*の \
変換されるシーケンスの終了位置を示す入力反復子。

*iosbase. flags* \
使用されません。

*状態*\
操作が成功したかどうかに基づき、ストリームの状態に適したビットマスク要素を設定する出力パラメーター。

*ptm* \
月の情報を格納する場所へのポインター。

### <a name="return-value"></a>戻り値

入力フィールドを超える先頭の要素を示す入力反復子。

### <a name="remarks"></a>Remarks

プロテクト仮想メンバー関数は、シーケンス [ `first`, `last`) の先頭から始め、空でない完全な月入力フィールドを認識するまで、連続した要素との一致を試みます。 成功した場合、このフィールドをコンポーネント**tm:: tm \_mon**と同等の値に変換し、結果を `ptm->tm_mon` に格納します。 これは、月入力フィールドを超える先頭の要素を示す反復子を返します。 それ以外の場合、関数は `ios_base::failbit` を*状態*に設定します。 これは、有効な月入力フィールドのプレフィックスを超える先頭の要素を示す反復子を返します。 どちらの場合も、戻り値が*last*と等しい場合、関数は*状態*の `ios_base::eofbit` を設定します。

月入力フィールドは、Jan、January、Feb、February などのようなロケール固有のシーケンスのセットの最長のものに一致するシーケンスです。 変換後の値は、January 以降の月を示す数値です。

### <a name="example"></a>例

[get_monthname](#get_monthname) の例 (`do_get_monthname` を呼び出す) を参照してください。

## <a name="do_get_time"></a>  time_get::do_get_time

`strftime` の *X* 指定子によって生成される日付として文字列を解析するために呼び出されるプロテクト仮想メンバー関数。

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換されるシーケンスの開始位置を示す入力反復子。

*最後*の \
変換されるシーケンスの終了位置を示す入力反復子。

*iosbase. flags* \
使用されません。

*状態*\
操作が成功したかどうかに基づき、ストリームの状態に適したビットマスク要素を設定します。

*ptm* \
日付の情報を格納する場所へのポインター。

### <a name="return-value"></a>戻り値

入力フィールドを超える先頭の要素を示す入力反復子。

### <a name="remarks"></a>Remarks

プロテクト仮想メンバー関数は、シーケンス [ `first`, `last`) の先頭から始め、空でない完全な時刻入力フィールドを認識するまで、連続した要素との一致を試みます。 成功した場合は、このフィールドをコンポーネント `tm::tm_hour`、`tm::tm_min`、および `tm::tm_sec` と同等の値に変換し、それぞれ `ptm->tm_hour`、`ptm->tm_min`、および `ptm->tm_sec` に結果を格納します。 これは、時刻入力フィールドを超える先頭の要素を示す反復子を返します。 それ以外の場合、関数は `ios_base::failbit` を*状態*に設定します。 これは、有効な時刻入力フィールドのプレフィックスを超える先頭の要素を示す反復子を返します。 どちらの場合も、戻り値が*last*と等しい場合、関数は*状態*の `ios_base::eofbit` を設定します。

この実装では、時刻入力フィールドは HH:MM:SS の形式になります。各要素の説明は次のとおりです。

- HH は数字のシーケンスで、対応する数値が範囲 [0, 24) 内である必要があります。時刻を示します。

- MM は数字のシーケンスで、対応する数値が範囲 [0, 60) 内である必要があります。正時からの経過分数を示します。

- SS は数字のシーケンスで、対応する数値が範囲 [0, 60) 内である必要があります。正分からの経過秒数を示します。

リテラルのコロンは、入力シーケンス内の対応する要素と一致する必要があります。

### <a name="example"></a>例

[get_time](#get_time) の例 (`do_get_time` を呼び出す) を参照してください。

## <a name="do_get_weekday"></a>  time_get::do_get_weekday

曜日の名前として文字列を解析するために呼び出されるプロテクト仮想メンバー関数。

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換されるシーケンスの開始位置を示す入力反復子。

*最後*の \
変換されるシーケンスの終了位置を示す入力反復子。

*iosbase. flags* \
書式設定フラグ。これが設定されている場合、通貨記号は省略可能です。それ以外の場合は必須です。

*状態*\
操作が成功したかどうかに基づき、ストリームの状態に適したビットマスク要素を設定します。

*ptm* \
曜日の情報を格納する場所へのポインター。

### <a name="return-value"></a>戻り値

入力フィールドを超える先頭の要素を示す入力反復子。

### <a name="remarks"></a>Remarks

仮想プロテクトメンバー関数は、シーケンス [`first`、`last`) の*先頭*から始まる連続した要素を、空でない完全な曜日入力フィールドを認識するまで照合しようとします。 成功した場合、このフィールドをコンポーネント**tm:: tm \_wday**と同等の値に変換し、結果を `ptm->tm_wday` に格納します。 これは、曜日入力フィールドを超える先頭の要素を示す反復子を返します。 それ以外の場合、関数は `ios_base::failbit` を*状態*に設定します。 これは、有効な曜日入力フィールドのプレフィックスを超える先頭の要素を示す反復子を返します。 どちらの場合も、戻り値が*last*と等しい場合、関数は*状態*の `ios_base::eofbit` を設定します。

曜日入力フィールドは、Sun、Sunday、Mon、Monday などのようなロケール固有のシーケンスのセットの最長のものに一致するシーケンスです。 変換後の値は、Sunday 以降の曜日を示す数値です。

### <a name="example"></a>例

[get_weekday](#get_weekday) の例 (`do_get_weekday` を呼び出す) を参照してください。

## <a name="do_get_year"></a>  time_get::do_get_year

年の名前として文字列を解析するために呼び出されるプロテクト仮想メンバー関数。

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換されるシーケンスの開始位置を示す入力反復子。

*最後*の \
変換されるシーケンスの終了位置を示す入力反復子。

*iosbase. flags* \
書式設定フラグ。これが設定されている場合、通貨記号は省略可能です。それ以外の場合は必須です。

*状態*\
操作が成功したかどうかに基づき、ストリームの状態に適したビットマスク要素を設定します。

*ptm* \
年の情報を格納する場所へのポインター。

### <a name="return-value"></a>戻り値

入力フィールドを超える先頭の要素を示す入力反復子。

### <a name="remarks"></a>Remarks

仮想プロテクトメンバー関数は、シーケンス [`first`、`last`) の*先頭*から空でない完全な年入力フィールドを認識するまで、連続した要素との照合を試みます。 成功した場合、このフィールドをコンポーネント**tm:: tm \_year**と同等の値に変換し、結果を `ptm->tm_year` に格納します。 これは、年入力フィールドを超える先頭の要素を示す反復子を返します。 それ以外の場合、関数は `ios_base::failbit` を*状態*に設定します。 これは、有効な年入力フィールドのプレフィックスを超える先頭の要素を示す反復子を返します。 どちらの場合も、戻り値が*last*と等しい場合、関数は*状態*の `ios_base::eofbit` を設定します。

年入力フィールドは、対応する数値が範囲 [1900, 2036) 内である必要があります。 格納される値は、この値から 1900 を引いた値です。 この実装では、範囲 [69, 136) の値は、[1969, 2036) の範囲の年を表します。 範囲 [0, 69) の値も許容されますが、特定の変換環境に応じて [1900, 1969) または [2000, 2069) のいずれかの範囲の年を表すことがあります。

### <a name="example"></a>例

[get_year](#get_year) の例 (`do_get_year` を呼び出す) を参照してください。

## <a name="get"></a>  time_get::get

文字データのソースからデータを読み取り、そのデータを time 構造体に格納される時刻に変換します。 最初の関数は 1 個の変換指定子と修飾子を受け取り、2 番目の関数は複数個受け取ります。

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char_type* fmt_first,
    char_type* fmt_last) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換するシーケンスの開始位置を示す入力反復子。

*最後*の \
変換するシーケンスの終了位置を示す入力反復子。

*iosbase. flags* \
ストリーム。

*状態*\
適切なビットマスク要素を設定して、ストリームの状態がエラーであることを示します。

*ptm* \
時間を格納する時間構造体へのポインター。

*fmt* \
変換指定子の文字。

*mod* \
省略可能な修飾子文字。

*fmt_first* \
形式のディレクティブの開始位置を指します。

*fmt_last* \
形式のディレクティブの終了位置を指します。

### <a name="return-value"></a>戻り値

時間構造体 `*ptm` を割り当てるために使用されたデータの後の最初の文字を指す反復子を返します。

### <a name="remarks"></a>Remarks

最初のメンバー関数は `do_get(first, last, iosbase, state, ptm, fmt, mod)` を返します。

2 番目のメンバー関数は `[fmt_first, fmt_last)` で区切られた形式の制御下で `do_get` を呼び出します。 この形式はフィールドのシーケンスとして扱われ、`[first, last)` で区切られたゼロ個以上の入力要素の変換をそれぞれのフィールドが決定します。 これは、変換されていない最初の要素を指定する反復子を返します。 フィールドには次の 3 つの種類があります。

1セント (%)形式で、次に set [EOQ #] 内の省略可能な修飾子*mod* 、その後に*変換指定子*を指定して、*最初*のを `do_get(first, last, iosbase, state, ptm, fmt, mod)` によって返される値に置き換えます。 変換に失敗すると、*状態*が `ios_base::failbit` に設定され、が返されます。

この形式の空白要素は、ゼロ個以上の入力の空白要素をスキップします。

形式内の他の要素は次の入力要素と一致する必要があり、その要素はスキップされます。 一致エラーは、*状態*の `ios_base::failbit` を設定し、を返します。

## <a name="get_date"></a>  time_get::get_date

`strftime` の *x* 指定子によって生成される日付として文字列を解析します。

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換されるシーケンスの開始位置を示す入力反復子。

*最後*の \
変換されるシーケンスの終了位置を示す入力反復子。

*iosbase. flags* \
書式設定フラグ。これが設定されている場合、通貨記号は省略可能です。それ以外の場合は必須です。

*状態*\
操作が成功したかどうかに基づき、ストリームの状態に適したビットマスク要素を設定します。

*ptm* \
日付の情報を格納する場所へのポインター。

### <a name="return-value"></a>戻り値

入力フィールドを超える先頭の要素を示す入力反復子。

### <a name="remarks"></a>Remarks

このメンバー関数は、 [do_get_date](#do_get_date)(`first`、`last`、`iosbase`、`state`、`ptm`) を返します。

月のカウントが 0 から 11 であることに注意してください。

### <a name="example"></a>例

```cpp
// time_get_get_date.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset(&t, 0, sizeof(struct tm));

   pszGetF << "July 4, 2000";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get<char> >
   (loc).get_date(basic_istream<char>::_Iter(pszGetF.rdbuf( ) ),
            basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if ( st & ios_base::failbit )
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(July 4, 2000) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 4
tm_mon: 6
tm_year: 100
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="get_monthname"></a>  time_get::get_monthname

月の名前として文字列を解析します。

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換されるシーケンスの開始位置を示す入力反復子。

*最後*の \
変換されるシーケンスの終了位置を示す入力反復子。

*iosbase. flags* \
使用されません。

*状態*\
操作が成功したかどうかに基づき、ストリームの状態に適したビットマスク要素を設定する出力パラメーター。

*ptm* \
月の情報を格納する場所へのポインター。

### <a name="return-value"></a>戻り値

入力フィールドを超える先頭の要素を示す入力反復子。

### <a name="remarks"></a>Remarks

このメンバー関数は、 [do_get_monthname](#do_get_monthname)(`first`、`last`、`iosbase`、`state`、`ptm`) を返します。

### <a name="example"></a>例

```cpp
// time_get_get_monthname.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "juillet";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get <char> >
   (loc).get_monthname(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
              basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(juillet) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 0
tm_mon: 6
tm_year: 0
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="get_time"></a>  time_get::get_time

`strftime` の *X* 指定子によって生成される日付として文字列を解析します。

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換されるシーケンスの開始位置を示す入力反復子。

*最後*の \
変換されるシーケンスの終了位置を示す入力反復子。

*iosbase. flags* \
使用されません。

*状態*\
操作が成功したかどうかに基づき、ストリームの状態に適したビットマスク要素を設定します。

*ptm* \
日付の情報を格納する場所へのポインター。

### <a name="return-value"></a>戻り値

入力フィールドを超える先頭の要素を示す入力反復子。

### <a name="remarks"></a>Remarks

このメンバー関数は、 [do_get_time](#do_get_time)(`first`、`last`、`iosbase`、`state`、`ptm`) を返します。

### <a name="example"></a>例

```cpp
// time_get_get_time.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "11:13:20";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get <char> >
      (loc).get_time(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << endl;
}
```

```Output
time_get::get_time(11:13:20) =
tm_sec: 20
tm_min: 13
tm_hour: 11
```

## <a name="get_weekday"></a>  time_get::get_weekday

曜日の名前として文字列を解析します。

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換されるシーケンスの開始位置を示す入力反復子。

*最後*の \
変換されるシーケンスの終了位置を示す入力反復子。

*iosbase. flags* \
書式設定フラグ。これが設定されている場合、通貨記号は省略可能です。それ以外の場合は必須です。

*状態*\
操作が成功したかどうかに基づき、ストリームの状態に適したビットマスク要素を設定します。

*ptm* \
曜日の情報を格納する場所へのポインター。

### <a name="return-value"></a>戻り値

入力フィールドを超える先頭の要素を示す入力反復子。

### <a name="remarks"></a>Remarks

このメンバー関数は、 [do_get_weekday](#do_get_weekday)(`first`、`last`、`iosbase`、`state`、`ptm`) を返します。

### <a name="example"></a>例

```cpp
// time_get_get_weekday.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "mercredi";
   pszGetF.imbue(loc);
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_weekday(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_wday: " << t.tm_wday
      << endl;
}
```

```Output
time_get::get_time(mercredi) =
tm_wday: 3
```

## <a name="get_year"></a>  time_get::get_year

年の名前として文字列を解析します。

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>パラメーター

*最初*の \
変換されるシーケンスの開始位置を示す入力反復子。

*最後*の \
変換されるシーケンスの終了位置を示す入力反復子。

*iosbase. flags* \
書式設定フラグ。これが設定されている場合、通貨記号は省略可能です。それ以外の場合は必須です。

*状態*\
操作が成功したかどうかに基づき、ストリームの状態に適したビットマスク要素を設定します。

*ptm* \
年の情報を格納する場所へのポインター。

### <a name="return-value"></a>戻り値

入力フィールドを超える先頭の要素を示す入力反復子。

### <a name="remarks"></a>Remarks

このメンバー関数は、 [do_get_year](#do_get_year)(`first`、`last`、`iosbase`、`state`、`ptm`) を返します。

### <a name="example"></a>例

```cpp
// time_get_get_year.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "1928";

   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_year(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_year: " << t.tm_year
      << endl;
}
```

```Output
time_get::get_year(1928) =
tm_year: 28
```

## <a name="iter_type"></a>  time_get::iter_type

入力反復子を表す型。

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター **InputIterator** のシノニムです。

## <a name="time_get"></a>  time_get::time_get

`time_get` 型のオブジェクトのコンストラクター。

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>パラメーター

*refs* \
オブジェクトのメモリ管理のタイプを指定するために使用する整数値。

### <a name="remarks"></a>Remarks

*Refs*パラメーターに指定できる値とその意味は次のとおりです。

- 0: オブジェクトの有効期間はそれが含まれるロケールによって管理されます。

- 1: オブジェクトの有効期間を手動で管理する必要があります。

- \> 1: これらの値は定義されていません。

デストラクターが保護されているため、利用できる直接的な例はありません。

コンストラクターは、 **locale::** [facet](../standard-library/locale-class.md#facet_class)(`refs`) を使用して、その基本オブジェクトを初期化します。

## <a name="see-also"></a>関連項目

[\<locale>](../standard-library/locale.md)\
[time_base クラス](../standard-library/time-base-class.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
