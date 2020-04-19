---
title: vprintf 系関数
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- vprintf
helpviewer_keywords:
- vprintf function
- formatted text [C++]
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
ms.openlocfilehash: 3c04879c7ec90aaba1199264c0c2128b9d1ea27c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957232"
---
# <a name="vprintf-functions"></a>vprintf 系関数

`vprintf` の各関数は引数リストへのポインターを受け取り、指定されたデータを書式設定して特定の出力先に書き込みます。 各関数のパラメーターの検証内容は、ワイド文字列と 1 バイト文字列のどちらを使用するか、出力先がどこか、書式設定文字列でのパラメーターの使用順序を指定できるか、などの点が異なります。

|||
|-|-|
|[_vcprintf、_vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf、vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_vfprintf_p、_vfprintf_p_l、_vfwprintf_p、_vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf_s、_vfprintf_s_l、vfwprintf_s、_vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|
|[vprintf、vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p、_vprintf_p_l、_vwprintf_p、_vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|
|[vprintf_s、_vprintf_s_l、vwprintf_s、_vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf、vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|
|[_vsprintf_p、_vsprintf_p_l、_vswprintf_p、_vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf_s、_vsprintf_s_l、vswprintf_s、_vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|
|[_vscprintf、_vscprintf_l、_vscwprintf、_vscwprintf_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[_vsnprintf、_vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|

## <a name="remarks"></a>解説

`vprintf` の各関数は、次の表にまとめたとおり、対応する関数に似ています。 ただし、`vprintf` の各関数は引数リストへのポインターを受け取るのに対し、対応する各関数は引数リストを受け取ります。

次のように、これらの関数はデータを書式設定して出力先に書き込みます。

|関数|対応する関数|出力先|パラメーターの検証|位置指定パラメーターのサポート|
|--------------|--------------------------|------------------------|--------------------------|----------------------------------|
|`_vcprintf`|[_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|コンソール|Null を確認します。|Ｘ|
|`_vcwprintf`|[_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|コンソール|Null を確認します。|Ｘ|
|`vfprintf`|[fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*ストリーム*|Null を確認します。|Ｘ|
|**vfprintf_p**|[fprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*ストリーム*|Null と有効な書式を確認します。|可|
|`vfprintf_s`|[fprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*ストリーム*|Null と有効な書式を確認します。|Ｘ|
|`vfwprintf`|[fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*ストリーム*|Null を確認します。|Ｘ|
|**vfwprintf_p**|[fwprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*ストリーム*|Null と有効な書式を確認します。|可|
|`vfwprintf_s`|[fwprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*ストリーム*|Null と有効な書式を確認します。|Ｘ|
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Null を確認します。|Ｘ|
|**vprintf_p**|[printf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Null と有効な書式を確認します。|可|
|`vprintf_s`|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Null と有効な書式を確認します。|Ｘ|
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Null を確認します。|no|
|**vwprintf_p**|[wprintf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Null と有効な書式を確認します。|可|
|`vwprintf_s`|[wprintf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Null と有効な書式を確認します。|Ｘ|
|**vsprintf**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|*バッファー*によって指し示されるメモリ|Null を確認します。|Ｘ|
|**vsprintf_p**|[sprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|*バッファー*によって指し示されるメモリ|Null と有効な書式を確認します。|可|
|`vsprintf_s`|[sprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|*バッファー*によって指し示されるメモリ|Null と有効な書式を確認します。|Ｘ|
|`vswprintf`|[swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|*バッファー*によって指し示されるメモリ|Null を確認します。|Ｘ|
|**vswprintf_p**|[swprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|*バッファー*によって指し示されるメモリ|Null と有効な書式を確認します。|可|
|`vswprintf_s`|[swprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|*バッファー*によって指し示されるメモリ|Null と有効な書式を確認します。|Ｘ|
|`_vscprintf`|[_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|*バッファー*によって指し示されるメモリ|Null を確認します。|Ｘ|
|`_vscwprintf`|[_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|*バッファー*によって指し示されるメモリ|Null を確認します。|Ｘ|
|`_vsnprintf`|[_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|*バッファー*によって指し示されるメモリ|Null を確認します。|Ｘ|
|`_vsnwprintf`|[_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|*バッファー*によって指し示されるメモリ|Null を確認します。|Ｘ|

引数 `argptr` は、VARARGS.H と STDARG.H で定義される `va_list` 型を持ちます。 変数 `argptr` は **va_start** によって初期化される必要があり、後続の `va_arg` の呼び出しによって再初期化される必要があります。次に、`argptr` は引数 *format* の対応する仕様に従って出力用に変換および転送される引数リストの先頭を指し示します。 *format* は、[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) の引数 *format* と同じ書式と関数を持ちます。 これらの関数は、`va_end` を呼び出しません。 各 `vprintf` 関数の詳細については、上の表にある対応する関数の説明をご覧ください。

`_vsnprintf` は **vsprintf** とは異なり、vsprintf 内でわずか *count* バイトを*バッファー*に書き込むだけです。

名前に挿入辞 **w** を持つバージョンのこれらの関数は、挿入辞 **w** を持たない関数と対応関係にあるワイド文字バージョンの関数です。これらのワイド文字の各関数では、*バッファー* と *format* がワイド文字列になります。 それ以外のワイド文字の各関数は SBCS の対応する関数と全く同じ動作をします。

サフィックス **_s** と **_p** を持つこれらの関数のバージョンは、セキュリティが強化されたバージョンです。 これらのバージョンでは、書式設定文字列を検証し、書式設定文字列が整形式ではない場合 (たとえば、無効な書式設定文字が使用されている場合) に例外が発生します。

サフィックス **_p** を持つこれらの関数のバージョンによって、書式設定文字列内での指定された引数の置き換え順序を指定できます。 詳細については、「[printf_p の位置指定パラメーター](../c-runtime-library/printf-p-positional-parameters.md)」をご覧ください。

**vsprintf**、`vswprintf`、`_vsnprintf`、および `_vsnwprintf` については、重なり合う文字列間でコピーした場合の動作は未定義です。

> [!IMPORTANT]
>  *format* にユーザー定義の文字列を指定しないでください。 詳しくは、「 [バッファー オーバーランの回避](/windows/win32/SecBP/avoiding-buffer-overruns)」をご覧ください。 これらの関数 (サフィックス **_s** または **_p** のどちらか) のセキュリティが強化されたバージョンを使用する場合、ユーザー指定の書式設定文字列は、ユーザー指定文字列に無効な書式設定文字が含まれている場合に無効なパラメーター例外をトリガーします。

## <a name="see-also"></a>関連項目

[ストリーム入出力](../c-runtime-library/stream-i-o.md)<br/>
[fprintf、_fprintf_l、fwprintf、_fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg、va_copy、va_end、va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)
