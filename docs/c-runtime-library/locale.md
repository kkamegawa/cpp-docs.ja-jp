---
title: ロケール
ms.date: 04/11/2018
f1_keywords:
- c.international
helpviewer_keywords:
- localization, locale
- country information
- language information routines
- setlocale function
- locale routines
ms.assetid: 442f8112-9288-44d7-be3c-15d22652093a
ms.openlocfilehash: 89ff4b694137c7002ecb5f6a844c75ab403e6e2f
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744382"
---
# <a name="locale"></a>ロケール

*ロケール*とは、プログラムをカスタマイズするために使用できる国または地域と言語を表します。 ロケールに依存するカテゴリとしては、日付や通貨の値の表示形式などがあります。 詳細については、「[ロケールのカテゴリ](../c-runtime-library/locale-categories.md)」を参照してください。

現在のプログラムまたはスレッドのロケール情報の一部またはすべてを変更または照会するには、[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 関数を **_l** のサフィックスなしで使用します。 **_l** サフィックス付きの関数を指定すると、特定の関数の実行中にのみ渡されたロケール パラメーターをロケール情報として使用します。 **_l** サフィックス付きの関数を使用する場合のロケールを作成するには、[_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) を使用します。 このロケールを解放するには、[_free_locale](../c-runtime-library/reference/free-locale.md) を使用します。 現在のロケールを取得するには、[_get_current_locale](../c-runtime-library/reference/get-current-locale.md) を使用します。

各スレッドで独自のロケールを設定するか、プログラム内のすべてのスレッドで同じロケールを共有するかどうかを制御するには、[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) を使用します。 詳細については、「[ロケールとコード ページ](../text/locales-and-code-pages.md)」を参照してください。

次の表に示す関数のセキュリティを強化したバージョンは、**_s** ("secure") というサフィックスによって表されます。 詳細については、「 [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md)」を参照してください。

## <a name="locale-dependent-routines"></a>ロケールに依存するルーチン

|ルーチンによって返される値|使用|**setlocale** カテゴリの設定の依存関係|
|-------------|---------|---------------------------------------------|
|[atof、_atof_l、_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|文字を浮動小数点型の値に変換|**LC_NUMERIC**|
|[atoi、_atoi_l、_wtoi、_wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|文字を整数型の値に変換|**LC_NUMERIC**|
|[_atoi64、_atoi64_l、_wtoi64、_wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|文字を 64 ビットの整数型の値に変換|**LC_NUMERIC**|
|[atol、_atol_l、_wtol、_wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|文字を long 型の値に変換|**LC_NUMERIC**|
|[_atodbl、_atodbl_l、_atoldbl、_atoldbl_l、_atoflt、_atoflt_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|文字を double-long 型の値に変換|**LC_NUMERIC**|
|[is ルーチン](../c-runtime-library/is-isw-routines.md)|特定の状態で指定した整数をテストします。|**LC_CTYPE**|
|[isleadbyte、_isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|先行バイトのテスト|**LC_CTYPE**|
|[localeconv](../c-runtime-library/reference/localeconv.md)|数量を書式設定するために適切な値を読み取る|`LC_MONETARY, LC_NUMERIC`|
|[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)|現在のロケールのマルチバイト文字の最大長さのバイト数 (STDLIB.H で定義されているマクロ)|**LC_CTYPE**|
|[_mbccpy、_mbccpy_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md)、[_mbccpy_s、_mbccpy_s_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|マルチバイト文字の 1 文字をコピー|**LC_CTYPE**|
|[_mbclen、mblen、_mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|マルチバイト文字のバイト数を検証して返す|**LC_CTYPE**|
|[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|マルチバイト文字列の場合、文字列内の各文字を検証し、文字列の長さを返す|**LC_CTYPE**|
|[mbstowcs、_mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)、[mbstowcs_s、_mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|マルチバイト文字のシーケンスを、対応するワイド文字のシーケンスに変換|**LC_CTYPE**|
|[mbtowc、_mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|マルチバイト文字を対応するワイド文字に変換|**LC_CTYPE**|
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 関数|書式付き出力を書き出す|**LC_NUMERIC** (小数点文字の出力を決定)|
|[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 関数|書式付き入力を読み取る|**LC_NUMERIC** (基数文字が認識されます)|
|[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)|プログラムのロケールを選択する|利用不可|
|[strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|2 つの文字列の文字を比較する|**LC_COLLATE**|
|[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|大文字小文字に関係なく、2 つの文字列を比較する|**LC_CTYPE**|
|[_stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|2 つの文字列の文字を比較する (大文字小文字を区別しない)|**LC_COLLATE**|
|[_strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|2 つの文字列の先頭の **n** 文字を比較する|**LC_COLLATE**|
|[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|大文字小文字に関係なく、2 つの文字列の文字を比較する。|**LC_CTYPE**|
|[_strnicoll、_wcsnicoll、_mbsnicoll、_strnicoll_l、_wcsnicoll_l、_mbsnicoll_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|2 つの文字列の先頭の **n** 文字を比較する (大文字小文字を区別しない)|**LC_COLLATE**|
|[strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|指定された **format** 引数に従って日付と時刻の値を書式設定する|**LC_TIME**|
|[_strlwr、_wcslwr、_mbslwr、_strlwr_l、_wcslwr_l、_mbslwr_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)、[_strlwr_s、_strlwr_s_l、_mbslwr_s、_mbslwr_s_l、_wcslwr_s、_wcslwr_s_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|指定した文字列内の大文字をその位置で小文字に変換する|**LC_CTYPE**|
|[strtod、_strtod_l、wcstod、_wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|文字列を **double** 型の値に変換する|**LC_NUMERIC** (基数文字が認識されます)|
|[strtol、wcstol、_strtol_l、_wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|文字列を **long** 型の値に変換する|**LC_NUMERIC** (基数文字が認識されます)|
|[strtoul、_strtoul_l、wcstoul、_wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|文字列を unsigned long 型の値に変換する|**LC_NUMERIC** (基数文字が認識されます)|
|[_strupr、_strupr_l、_mbsupr、_mbsupr_l、_wcsupr_l、_wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)、[_strupr_s、_strupr_s_l、_mbsupr_s、_mbsupr_s_l、_wcsupr_s、_wcsupr_s_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|文字列内の小文字をその位置で大文字に変換する|**LC_CTYPE**|
|[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|ロケールに従って文字列を照合形式に変換する|**LC_COLLATE**|
|[tolower、_tolower、towlower、_tolower_l、_towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)、[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|指定した文字を対応する小文字に変換する|**LC_CTYPE**|
|[toupper、_toupper、towupper、_toupper_l、_towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)、[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|指定した文字を対応する大文字に変換する|**LC_CTYPE**|
|[wcstombs、_wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)、[wcstombs_s、_wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|ワイド文字のシーケンスを、対応するマルチバイト文字のシーケンスに変換する|**LC_CTYPE**|
|[wctomb、_wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)、[wctomb_s、_wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|ワイド文字を対応するマルチバイト文字に変換する|**LC_CTYPE**|

> [!NOTE]
> マルチバイトのルーチンの場合、マルチバイトのコード ページは [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) で設定されたロケールと同じである必要があります。 **_MB_CP_LOCALE** 引数を指定した [_setmbcp](../c-runtime-library/reference/setmbcp.md) では、マルチバイトのコード ページを **setlocale** のコード ページと同じにします。

## <a name="see-also"></a>関連項目

[国際化](../c-runtime-library/internationalization.md)<br/>
[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
