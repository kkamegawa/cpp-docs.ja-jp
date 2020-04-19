---
title: localeconv
ms.date: 11/04/2016
api_name:
- localeconv
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- localeconv
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
ms.openlocfilehash: ca7113903e1ed6e9ffb94bef79beba41e09bfb71
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953359"
---
# <a name="localeconv"></a>localeconv

ロケールの設定に関する詳細情報を取得します。

## <a name="syntax"></a>構文

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>戻り値

**localeconv**型の埋め込まれたオブジェクトへのポインターを返します、 [struct lconv](../../c-runtime-library/standard-types.md)です。 オブジェクトに含まれる値は、スレッドローカルストレージのロケール設定からコピーされ、その後**localeconv**への呼び出しによって上書きされる可能性があります。 このオブジェクトの値を変更しても、ロケールの設定は変更されません。 *Category*値が**LC_ALL**、 **LC_MONETARY**、または**LC_NUMERIC**の[setlocale](setlocale-wsetlocale.md)を呼び出すと、構造体の内容が上書きされます。

## <a name="remarks"></a>Remarks

**Localeconv**関数は、現在のロケールの数値書式設定に関する詳細情報を取得します。 この情報は、**lconv** 型の構造体で格納されます。 **lconv** 構造体は、LOCALE.H で定義され、次のメンバーが含まれます。

|フィールド|説明|
|-|-|
decimal_point,<br/>_W_decimal_point|通貨数量の数量の小数点文字へのポインター。
thousands_sep,<br/>_W_thousands_sep|通貨数量の数量の小数点の左にある数字のグループを区切る文字へのポインター。
グループ化 (grouping)|通貨数量数量の各桁のグループのサイズを格納する**char**サイズの整数へのポインター。
int_curr_symbol,<br/>_W_int_curr_symbol|現在のロケールの国際通貨記号へのポインター。 最初の 3 文字は、*ISO 4217 Codes for the Representation of Currency and Funds* 規格で定義されている英字の国際通貨記号を指定します。 4 文字目 (null 文字の直前) は、国際通貨記号と通貨の数量を区切ります。
符号<br/>_W_currency_symbol|現在のロケールの現地通貨記号へのポインター。
mon_decimal_point,<br/>_W_mon_decimal_point|通貨数量の小数点文字へのポインター。
mon_thousands_sep,<br/>_W_mon_thousands_sep|通貨数量の小数点以下の桁のグループの区切り記号へのポインター。
mon_grouping|通貨数量の各桁のグループのサイズを格納する**char**サイズの整数へのポインター。
positive_sign,<br/>_W_positive_sign|負でない通貨数量の符号を示す文字列。
negative_sign,<br/>_W_negative_sign|負の通貨数量の符号を示す文字列。
int_frac_digits|国際方式で書式化された通貨数量の小数点より右側の桁数。
frac_digits|書式化された通貨数量の小数点より右側の桁数。
p_cs_precedes|書式化された負でない通貨数量の値の前に通貨記号が付く場合は、1 に設定します。 値の後に記号が続く場合は、0 に設定します。
p_sep_by_space|書式化された負でない通貨数量の値と通貨記号をスペースで区切る場合は、1 に設定します。 スペースで区切らない場合は、0 に設定します。
n_cs_precedes|書式化された負の通貨数量の値の前に通貨記号が付く場合は、1 に設定します。 値の後に記号が続く場合は、0 に設定します。
n_sep_by_space|書式化された負の通貨数量の値と通貨記号をスペースで区切る場合は、1 に設定します。 スペースで区切らない場合は、0 に設定します。
p_sign_posn|書式化された負でない通貨数量での正符号の位置。
n_sign_posn|書式化された負の通貨数量での正符号の位置。

指定されている場合を除き、と`wchar_t *`のバージョン`char *`を持つ**lconv**構造体のメンバーは、文字列へのポインターです。 これらのいずれかが **""** ( **wchar_t** <strong>\*</strong>の場合は**L "** ) に等しいか、現在のロケールではサポートされていません。 **Decimal_point**と **_W_decimal_point**は常にサポートされ、長さは0以外であることに注意してください。

構造体の**char**メンバーは、文字ではなく、小さい負以外の数値です。 そのいずれかが **CHAR_MAX** に相当する場合は、現在のロケールではサポートされていません。

**Grouping**と**mon_grouping**の値は、次の規則に従って解釈されます。

- **CHAR_MAX** -それ以上のグループ化を実行しません。

- 0: 残りの数字のそれぞれに対して previous 要素を使用します。

- *n* -現在のグループを構成する数字の数。 次の要素が調べられて、現在のグループの前にある次のグループのサイズが決定されます。

**int_curr_symbol** の値は、次の規則に従って解釈されます。

- 最初の 3 文字は、*ISO 4217 Codes for the Representation of Currency and Funds* 規格で定義されている英字の国際通貨記号を指定します。

- 4 文字目 (null 文字の直前) は、国際通貨記号と通貨の数量を区切ります。

**p_cs_precedes** と **n_cs_precedes** の値は、次の規則に従って解釈されます (かっこ内は **n_cs_precedes** 規則です)。

- 0-通貨記号は、負でない (負の) 書式設定された通貨値の値に従います。

- 1-通貨記号は、負でない (負の) 書式設定された通貨値の値よりも前になります。

**p_sep_by_space** と **n_sep_by_space** の値は、次の規則に従って解釈されます (かっこ内は **n_sep_by_space** 規則です)。

- 0-通貨記号は、負でない (負の) 書式設定された通貨値の値からスペースで区切られます。

- 1-通貨記号と負でない (負の) 書式設定された通貨値の間には空白を区別しません。

**p_sign_posn** と **n_sign_posn** の値は、次の規則に従って解釈されます。

- 0: [数量] と [通貨記号] をかっこで囲みます。

- 1-署名文字列は、数量と通貨記号の前に付けます。

- 2-署名文字列は、数量と通貨記号の後に続きます。

- 3-符号付き文字列は、通貨記号の直前にあります。

- 4-符号文字列は、通貨記号の直後に続きます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="see-also"></a>関連項目

[ロケール](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll 系関数](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
