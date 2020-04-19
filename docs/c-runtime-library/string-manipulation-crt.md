---
title: 文字列操作 (CRT)
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- strings [C++], manipulating
- string manipulation
- manipulating strings
ms.assetid: 6545861a-59e7-408d-9d29-2ec9134fc91a
ms.openlocfilehash: 7ea66c38f73e32a99981f331249362e8e0a789c1
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742835"
---
# <a name="string-manipulation-crt"></a>文字列操作 (CRT)

これらのルーチンは、null で終わる 1 バイト文字、ワイド文字、およびマルチバイト文字の文字列に対して動作します。 null 文字で終わらない文字配列を使用するには、「[バッファー操作](../c-runtime-library/buffer-manipulation.md)」で説明されているバッファー操作ルーチンを使用します。

## <a name="string-manipulation-routines"></a>文字列操作ルーチン

|ルーチンによって返される値|使用|
|-------------|---------|
|[strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)、[_stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)、[_strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)、[_strnicoll、_wcsnicoll、_mbsnicoll、_strnicoll_l、_wcsnicoll_l、_mbsnicoll_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|コード ページの情報を使用して、2 つの文字列を比較します (**_mbsicoll** および **_mbsnicoll** では、大文字と小文字が区別されます)。|
|[_strdec、_wcsdec、_mbsdec、_mbsdec_l](../c-runtime-library/reference/strdec-wcsdec-mbsdec-mbsdec-l.md)|文字列ポインターを 1 文字前に移動します。|
|[_strinc、_wcsinc、_mbsinc、_mbsinc_l](../c-runtime-library/reference/strinc-wcsinc-mbsinc-mbsinc-l.md)|文字列ポインターを 1 文字進めます。|
|[_mbsnbcat、_mbsnbcat_l](../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)、[_mbsnbcat_s、_mbsnbcat_s_l](../c-runtime-library/reference/mbsnbcat-s-mbsnbcat-s-l.md)|1 つの文字列の先頭の最大 *n* バイトを別の文字列に追加します。|
|[_mbsnbcmp、_mbsnbcmp_l](../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)|2 つの文字列の先頭の *n* バイトを比較します。|
|[_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l](../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)|指定した文字数内の文字のバイト数を返します。|
|[_mbsnbcpy、_mbsnbcpy_l](../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)、[_mbsnbcpy_s、_mbsnbcpy_s_l](../c-runtime-library/reference/mbsnbcpy-s-mbsnbcpy-s-l.md)|文字列の *n* バイトをコピーします。|
|[_mbsnbicmp、_mbsnbicmp_l](../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)|2 つの文字列の先頭の *n* バイトを比較します (大文字と小文字の区別は無視されます)。|
|[_mbsnbset、_mbsnbset_l](../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)|指定した文字に文字列の先頭の *n* バイトを設定します。|
|[_strncnt、_wcsncnt、_mbsnbcnt、_mbsnbcnt_l、_mbsnccnt、_mbsnccnt_l](../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)|指定したバイト数内の文字数を返します。|
|[_strnextc、_wcsnextc、_mbsnextc、_mbsnextc_l](../c-runtime-library/reference/strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)|文字列の次の文字を検索します。|
|[_strninc、_wcsninc、_mbsninc、_mbsninc_l](../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)|文字列ポインターを *n* 文字進めます。|
|[_strspnp、_wcsspnp、_mbsspnp、_mbsspnp_l](../c-runtime-library/reference/strspnp-wcsspnp-mbsspnp-mbsspnp-l.md)|指定した一方の文字列の文字のうち、もう一方の指定した文字列にはない最初の文字へのポインターを返します。|
|[_scprintf、_scprintf_l、_scwprintf、_scwprintf_l](../c-runtime-library/reference/scprintf-scprintf-l-scwprintf-scwprintf-l.md)|書式設定された文字列内の文字数を返します。|
|[_snscanf、_snscanf_l、_snwscanf、_snwscanf_l](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md)、[_snscanf_s、_snscanf_s_l、_snwscanf_s、_snwscanf_s_l](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|指定した長さの書式付きデータを標準入力ストリームから読み取ります。|
|[sscanf、_sscanf_l、swscanf、_swscanf_l](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)、[sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|指定した長さの書式付きデータを標準入力ストリームから読み取ります。|
|[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)、[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)、[_sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|文字列に書式付きデータを書き込みます。|
|[strcat、wcscat、_mbscat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)、[strcat_s、wcscat_s、_mbscat_s](../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md)|1 つの文字列を別の文字列に追加します。|
|[strchr、wcschr、_mbschr、_mbschr_l](../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)|指定した文字が最初に出現する位置を、文字列内で検索します。|
|[strcmp、wcscmp、_mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|2 つの文字列を比較します。|
|[strcoll、wcscoll、_mbscoll、_strcoll_l、_wcscoll_l、_mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)、[_stricoll、_wcsicoll、_mbsicoll、_stricoll_l、_wcsicoll_l、_mbsicoll_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)、[_strncoll、_wcsncoll、_mbsncoll、_strncoll_l、_wcsncoll_l、_mbsncoll_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)、[_strnicoll、_wcsnicoll、_mbsnicoll、_strnicoll_l、_wcsnicoll_l、_mbsnicoll_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|現在のロケールのコード ページの情報を使用して、2 つの文字列を比較します (**_stricoll**、**_wcsicoll**、**_strnicoll**、および **_wcsnicoll** では、大文字と小文字が区別されます)。|
|[strcpy、wcscpy、_mbscpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)、[strcpy_s、wcscpy_s、_mbscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)|1 つの文字列を別の文字列にコピーします。|
|[strcspn、wcscspn、_mbscspn、_mbscspn_l](../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)|指定した文字セットからの文字が最初に出現する位置を、文字列内で検索します。|
|[_strdup、_wcsdup、_mbsdup](../c-runtime-library/reference/strdup-wcsdup-mbsdup.md)、[_strdup_dbg、_wcsdup_dbg](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)|文字列を複製します。|
|[strerror、_strerror、_wcserror、\__wcserror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)、[strerror_s、_strerror_s、_wcserror_s、\__wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|エラー番号をメッセージ文字列にマップします。|
|[strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|日付と時刻の文字列の書式を設定します。|
|[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|大文字小文字に関係なく、2 つの文字列を比較する|
|[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)、[strnlen、strnlen_s、wcsnlen、wcsnlen_s、_mbsnlen、_mbsnlen_l、_mbstrnlen、_mbstrnlen_l](../c-runtime-library/reference/strnlen-strnlen-s.md)|文字列の長さを検索します。|
|[_strlwr、_wcslwr、_mbslwr、_strlwr_l、_wcslwr_l、_mbslwr_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)、[_strlwr_s、_strlwr_s_l、_mbslwr_s、_mbslwr_s_l、_wcslwr_s、_wcslwr_s_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|文字列を小文字に変換します。|
|[strncat、_strncat_l、wcsncat、_wcsncat_l、_mbsncat、_mbsncat_l](../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)、[strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)|文字列の文字を追加します。|
|[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|2 つの文字列の文字を比較する|
|[strncpy、_strncpy_l、wcsncpy、_wcsncpy_l、_mbsncpy、_mbsncpy_l](../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)、[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)|1 つの文字列の文字を別の文字列にコピーします。|
|[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|大文字小文字に関係なく、2 つの文字列の文字を比較します。|
|[_strnset、_strnset_l、_wcsnset、_wcsnset_l、_mbsnset、_mbsnset_l](../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)|指定した文字に文字列の先頭の *n* 文字を設定します。|
|[strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l](../c-runtime-library/reference/strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)|1 つの文字列からの文字が最初に出現する位置を、別の文字列内で検索します。|
|[strrchr、wcsrchr、_mbsrchr、_mbsrchr_l](../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)|指定した文字が最後に出現する位置を、文字列内で検索します。|
|[_strrev、_wcsrev、_mbsrev、_mbsrev_l](../c-runtime-library/reference/strrev-wcsrev-mbsrev-mbsrev-l.md)|文字列の順序を逆にします。|
|[_strset、_strset_l、_wcsset、_wcsset_l、_mbsset、_mbsset_l](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|指定した文字に文字列のすべての文字を設定します。|
|[strspn、wcsspn、_mbsspn、_mbsspn_l](../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)|別の文字列内では見つからない文字の文字列が最初に出現する位置を、文字列内で検索します。|
|[strstr、wcsstr、_mbsstr、_mbsstr_l](../c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l.md)|指定した文字列が最初に出現する位置を、別の文字列内で検索します。|
|[strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md)、[strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l](../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)|文字列の次のトークンを検索します。|
|[_strupr、_strupr_l、_mbsupr、_mbsupr_l、_wcsupr_l、_wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)、[_strupr_s、_strupr_s_l、_mbsupr_s、_mbsupr_s_l、_wcsupr_s、_wcsupr_s_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|文字列を大文字に変換します。|
|[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|ロケール固有の情報に基づいて、文字列を照合形式に変換します。|
|[vsprintf、_vsprintf_l、vswprintf、_vswprintf_l、\__vswprintf_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)、[vsprintf_s、_vsprintf_s_l、vswprintf_s、_vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)、[_vsprintf_p、_vsprintf_p_l、_vswprintf_p、_vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|引数リストへのポインターを使用して、書式付き出力を書き込みます。|
|[vsnprintf、_vsnprintf、_vsnprintf_l、_vsnwprintf、_vsnwprintf_l](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)、[vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|引数リストへのポインターを使用して、書式付き出力を書き込みます。|

## <a name="see-also"></a>関連項目

[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
