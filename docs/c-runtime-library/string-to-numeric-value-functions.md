---
title: 文字列を数値に変換する関数
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstoui64
- _tcstoi64
helpviewer_keywords:
- parsing, numeric strings
- string conversion, to numeric values
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
ms.openlocfilehash: b9d8218bd5a3151e17b7ac380bb86c85dac3e6a3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944724"
---
# <a name="string-to-numeric-value-functions"></a>文字列を数値に変換する関数

- [strtod、_strtod_l、wcstod、_wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)

- [strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)

- [strtoul、_strtoul_l、wcstoul、_wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)

- [_strtoi64、_wcstoi64、_strtoi64_l、_wcstoi64_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)

- [_strtoui64、_wcstoui64、_strtoui64_l、_wcstoui64_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)

## <a name="remarks"></a>解説

**strtod** ファミリの各関数は、NULL 終了文字列を数値に変換します。 利用できる関数を次の表に示します。

|関数|説明|
|--------------|-----------------|
|`strtod`|文字列を倍精度浮動小数点値に変換する|
|`strtol`|文字列を長整数型に変換する|
|`strtoul`|文字列を符号なし長整数型に変換する|
|`_strtoi64`|文字列を 64 ビット `__int64` 整数に変換する|
|`_strtoui64`|文字列を符号なし 64 ビット `__int64` 整数に変換する|

`wcstod`、`wcstol`、`wcstoul`、`_wcstoi64` は、それぞれ、`strtod`、`strtol`、`strtoul`、`_strtoi64` のワイド文字バージョンです。 これらのワイド文字関数の文字列引数はワイド文字です。各関数は、それが 1 バイト文字列の場合と同様に動作します。

`strtod` 関数は 2 つの引数を取ります。1 つは入力文字列です。もう 1 つは文字のポインターであり、変換プロセスを終わらせます。 `strtol`、`strtoul`、 **_strtoi64**、 **_strtoui64** は変換プロセスで利用する基数として 3 つ目の引数を取ります。

入力文字列は、指定された型の数値として解釈できる文字シーケンスです。 各関数は、数値の一部として認識できない文字を最初に見つけた時点で、文字列の読み取りを終了します。 数値として認識できない最初の文字が、終端の NULL 文字の場合もあります。 `strtol`、`strtoul`、`_strtoi64`、`_strtoui64` の場合、この終端文字は、ユーザーが指定した基数と等しいか、それより大きい最初の数字になることもあります。

変換終了文字へのユーザー指定ポインターが呼び出し時に **NULL** に設定されない場合、スキャンを停止した文字のポインターがそこに代わりに保存されます。 変換できなかった場合 (有効な数字が見つからなかったか、無効な基数を指定した場合) は、文字列ポインターの値がそのアドレスに保存されます。

`strtod` は、次の形式の文字列を要求します。

[*whitespace*] [*sign*] [`digits`] [ **.** `digits`] [ {**d** &#124; **D** &#124; **e** &#124; **E**}[*sign*]`digits`]

*空白文字*はスペースやタブで構成され、無視されます。*符号*はプラス ( **+** ) またはマイナス ( **-** ) のいずれかで、`digits` は 1 つまたは複数の 10 進数字です。 小数点文字の前に数字がない場合は、少なくとも 1 つの数字が小数点文字の後に必要です。 10 進数の後には指数部を指定できます。指数部は、指数部の開始文字 (**d**、**D**、**e**、**E**) および必要に応じて符号付き整数で構成されます。 指数部と小数点文字のいずれも指定されない場合は、文字列の最後の数字の後に小数点文字が続くと想定されます。 この形式に一致しない文字を見つけるとスキャンを停止します。

`strtol`、`strtoul`、`_strtoi64`、`_strtoui64` 関数は、次の形式の文字列を要求します。

[*whitespace*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **X** }]] [`digits`]

基数引数が 2 から 36 の間の場合、数値の基数として使用されます。 0 の場合、変換終了ポインターが参照する最初の文字で基数を決定します。 最初の文字が 0 で、2 番目の文字が 'x' または 'X' 以外の場合、文字列は 8 進数と解釈されます。それ以外の場合、10 進数と解釈されます。 最初の文字が '0' で、2 番目の文字が 'x' または 'X' である場合、文字列は 16 進数と解釈されます。 最初の文字が '1' ～ '9' の間の数値の場合、文字列は 10 進数と解釈されます。 'a' ～ 'z' (または 'A' ～ 'Z') の文字には、10 ～ 35 の値が割り当てられています。*基数*よりも小さい値が割り当てられている文字のみ許可されます。 `strtoul` と `_strtoui64` では正符号 ( **+** ) または負符号 ( **-** ) のプレフィックスを使用できます。先頭の負符号は戻り値の符号が反転されることを表します。

出力値は、ロケールの `LC_NUMERIC` カテゴリの設定に影響されます。詳細については、「[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)」を参照してください。 **_l** サフィックスが付いていないこれらの関数のバージョンでは、このロケールに依存する動作に現在のロケールを使用します。 **_l** サフィックスが付いているバージョンは、渡されたロケール パラメーターを代わりに使用する点を除いて同じです。

これらの関数により返される値がオーバーフローやアンダーフローを引き起こすようなとき、あるいは変換できないとき、次のように特殊ケースの値が返されます。

|関数|条件|返される値|
|--------------|---------------|--------------------|
|`strtod`|オーバーフロー|+/- `HUGE_VAL`|
|`strtod`|アンダーフローまたは変換なし|0|
|`strtol`|+ オーバーフロー|**LONG_MAX**|
|`strtol`|- オーバーフロー|**LONG_MIN**|
|`strtol`|アンダーフローまたは変換なし|0|
|`_strtoi64`|+ オーバーフロー|**_I64_MAX**|
|`_strtoi64`|- オーバーフロー|**_I64_MIN**|
|`_strtoi64`|変換なし|0|
|`_strtoui64`|オーバーフロー|**_UI64_MAX**|
|`_strtoui64`|変換なし|0|

**_I64_MAX**、_**I64_MIN**、 **_UI64_MAX** は LIMITS.H で定義されます。

`wcstod`、`wcstol`、`wcstoul`、`_wcstoi64`、`_wcstoui64` はそれぞれ、`strtod`、`strtol`、`strtoul`、`_strtoi64`、`_strtoui64` のワイド文字バージョンです。これらのワイド文字関数の変換終了引数へのポインターはワイド文字です。 ワイド文字関数は、それが 1 バイト文字の場合と同様に動作します。

## <a name="see-also"></a>関連項目

[データ変換](../c-runtime-library/data-conversion.md)<br/>
[ロケール](../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[浮動小数点サポート](../c-runtime-library/floating-point-support.md)<br/>
[atof、_atof_l、_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)
