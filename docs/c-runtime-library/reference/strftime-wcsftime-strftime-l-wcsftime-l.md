---
title: strftime、wcsftime、_strftime_l、_wcsftime_l
ms.date: 03/22/2018
api_name:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
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
- api-ms-win-crt-time-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcsftime
- strftime
- wcsftime
- _strftime_l
- _wcsftime_l
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
ms.openlocfilehash: 0c20303973d09f48067dc331dba98a08f8f364f8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958124"
---
# <a name="strftime-wcsftime-_strftime_l-_wcsftime_l"></a>strftime、wcsftime、_strftime_l、_wcsftime_l

時刻の文字列の書式を指定します。

## <a name="syntax"></a>構文

```C
size_t strftime(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr
);
size_t _strftime_l(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr,
   _locale_t locale
);
size_t wcsftime(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr
);
size_t _wcsftime_l(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr,
   _locale_t locale
);
```

### <a name="parameters"></a>パラメーター

*strDest*<br/>
出力する文字列。

*maxsize*<br/>
文字数 (**char**または**wchar_t**) で計測された、 *strdest*バッファーのサイズ。

*format*<br/>
書式指定文字列。

*timeptr*<br/>
**tm**データ構造体。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

**strftime**は、 *strdest*に配置された文字数を返し、 **wcsftime**は対応するワイド文字数を返します。

終端の null を含む合計文字数が*maxsize*を超える場合、 **strftime**と**wcsftime**はどちらも0を返し、 *strdest*の内容は不確定になります。

*Strdest*の文字数は、書式設定されたリテラル文字の数*と、* 書式設定コードによって*書式*設定される可能性がある任意の文字と等しくなります。 文字列の終端の NULL は戻り値にはカウントされません。

## <a name="remarks"></a>Remarks

**Strftime**関数と**wcsftime**関数は、指定された*書式*引数に従って*timeptr*の**tm**時刻値を書式設定し、その結果をバッファー *strdest*に格納します。 最大*maxsize*文字は文字列に配置されます。 *Timeptr*構造体のフィールドの説明については、「 [asctime](asctime-wasctime.md)」を参照してください。 **wcsftime**は、 **strftime**に相当するワイド文字です。その文字列ポインター引数は、ワイド文字列を指します。 それ以外では、これらの関数の動作は同じです。

この関数は、パラメーターを検証します。 *Strdest*、 *format*、または*timeptr*が null ポインターの場合、または*timeptr*によってアドレス指定された**tm**データ構造が無効である場合 (たとえば、時刻または日付の範囲外の値が含まれている場合)、または*書式指定*文字列の場合は、に無効な書式指定コードが含まれています。「パラメーターの[検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は0を返し、 **errno**を**EINVAL**に設定します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

*Format*引数は1つ以上のコードで構成されます。**printf**と同様に、書式設定コードの前にはパーセント記号 **%** () が付きます。 で **%** 始まらない文字は、そのまま*strdest*にコピーされます。 現在のロケールの**LC_TIME**カテゴリは、 **strftime**の出力形式に影響します。 ( **LC_TIME**の詳細については、「 [setlocale](setlocale-wsetlocale.md)」を参照してください)。**Strftime**関数と**wcsftime**関数は、現在設定されているロケールを使用します。 これらの関数の **_strftime_l**バージョンと **_wcsftime_l**バージョンは、ロケールをパラメーターとして受け取り、現在設定されているロケールの代わりにそれを使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

**Strftime**関数は、次の書式設定コードをサポートしています。

|||
|-|-|
|コード|置換文字列|
|**% a**|ロケールの曜日の省略名|
|**% A**|ロケールの完全な曜日名|
|**% b**|ロケールの省略形の月名|
|**% B**|ロケールの月の完全な名前|
|**% c**|ロケールに合った日付と時刻の表記|
|**% C**|100で除算され、10進数値として整数に切り捨てられた年 (00 − 99)|
|**% d**|10進数の月の通算日 (01-31)|
|**% D**|% **M/% d/% y**と同じです。|
|**% e**|1桁の数字の前にスペースがある場合の月の通算日 (1-31)|
|**% F**|% **Y-% m-% d**と同じです。|
|**% g**|ISO 8601 週ベースの年の最後の2桁 (10 進数) (00-99)|
|**% G**|ISO 8601 週ベースの年 (10 進数)|
|**% h**|月の省略名 ( **% b**と等価)|
|**% H**|24時間形式の時間 (00-23)|
|**% I**|12時間形式の時間 (01-12)|
|**% j**|10進数の年の通算日 (001-366)|
|**% m**|小数値としての月 (01-12)|
|**% M**|10進数としての分数 (00-59)|
|**% n**|改行文字 ( **\n**)|
|**% p**|ロケールの午前/P.M. 表示 12時間制のインジケーター|
|**% r**|ロケールの12時間制時刻|
|**% R**|**% H:%M**と同じです。|
|**% S**|10進数としての秒 (00-59)|
|**% t**|水平タブ文字 ( **\t**)|
|**% T**|**% H:%M:% S**、ISO 8601 時刻形式と同じです。|
|**% u**|ISO 8601 の曜日 (10 進数) (1-7;月曜日は 1)|
|**% U**|年の通算週の数値 (00-53) (最初の日曜日は週1の最初の日)|
|**% V**|ISO 8601 週番号 (10 進数) (00-53)|
|**% w**|小数値としての曜日 (0-6;日曜日は 0)|
|**% W**|年の通算週の数値 (00-53)。最初の月曜日が週の最初の日です1|
|**% x**|ロケールの日付表現|
|**% X**|ロケールの時刻表現|
|**% y**|世紀なし、10進数値 (00-99)|
|**% Y**|世紀を付けた 10 進数の年|
|**% z**|ISO 8601 形式の UTC からのオフセット。タイムゾーンが不明の場合は文字なし|
|**% Z**|レジストリ設定に応じて、ロケールのタイムゾーン名またはタイムゾーンの省略形。タイムゾーンが不明の場合は文字なし|
|**%%**|パーセント記号|

**Printf**関数と同様に、フラグ **#** は任意の書式指定コードにプレフィックスを付けることができます。 その場合、書式コードの説明は次のように変更します。

|[書式コード]|説明|
|-----------------|-------------|
|**% #a**、 **% #A**、 **% #b**、% **#B**、 **% #g**、 **% #G**、 **% #h**、 **% #n**、 **%** #p、 **% #t**、 **% #u**、 **% #w**、 **% #X**、 **% #z、%** **#Z、** **%#%**|**#** フラグは無視されます。|
|**%#c**|ロケールに適した長い日付と時刻の表現。 例えば:"火曜日、1995年3月14日、12:41:29"。|
|**% #x**|ロケールに適した長い日付形式。 例えば:"火曜日、1995年3月14日"。|
|**% #d**、 **% #D**、 **% #e**、% **#F**、 **% #H**、 **% #I**、 **% #j**、 **% #m**、 **%** #M、 **% #r**、 **% #R**、 **% #S**、 **% #T**、 **% #U、%** **#V**、 **% #W**、 **% #y**、 **% #Y**|先頭の0または空白を削除します (存在する場合)。|

**% V**、 **% g**、および **% g**によって生成された ISO 8601 週と週ベースの年は、月曜日に開始する週を使用します。 week 1 は1月4日の週です。この週は、少なくとも4日を含む1週間です。 年の最初の月曜日が2、3、または4の場合、前の日は前の年の最後の週の一部になります。 その日、 **% V**は53に置き換えられ、 **% g**と **% g**の両方が前の年の数字に置き換えられます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> または \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> または \<wchar.h>|

**_Strftime_l**関数と **_wcsftime_l**関数は、Microsoft 固有の関数です。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

[time](time-time32-time64.md) の例を参照してください。

## <a name="see-also"></a>関連項目

[ロケール](../../c-runtime-library/locale.md) <br/>
[時間管理](../../c-runtime-library/time-management.md) <br/>
[文字列操作](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll 系関数](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
