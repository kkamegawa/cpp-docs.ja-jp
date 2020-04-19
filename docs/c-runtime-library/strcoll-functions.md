---
title: strcoll 系関数
ms.date: 11/04/2016
api_location:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strcoll
helpviewer_keywords:
- code pages, using for string comparisons
- string comparison [C++], culture-specific
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: c09eeff3-8aba-4cfb-a524-752436d85573
ms.openlocfilehash: c63a130cee6913006fff2ed5568c41cc4fdeac3c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944900"
---
# <a name="strcoll-functions"></a>strcoll 系関数

各 `strcoll` 関数と各 `wcscoll` 関数は、現在使用されているロケールのコード ページの `LC_COLLATE` カテゴリ設定に基づいて 2 つの文字列を比較します。 各 `_mbscoll` 関数は、現在使用されているマルチバイトのコード ページに基づいて、2 つの文字列を比較します。 文字列を比較する `coll` 関数は、現在のコード ページの文字セット順序と辞書式文字順序との間に相違点あり、この違いが比較に関係がある場合にのみ使用します。 対応する `cmp` 関数は、文字列が等しいかをテストする目的でのみ使用します。

### <a name="strcoll-functions"></a>strcoll 系関数

|SBCS|Unicode|MBCS|説明|
|----------|-------------|----------|-----------------|
|[strcoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[wcscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[_mbscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|2 つの文字列を照合する|
|[_stricoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_wcsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_mbsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|2 つの文字列を照合する (大文字と小文字を区別しない)|
|[_strncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_wcsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_mbsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|2 つの文字列の先頭の `count` 文字を照合する|
|[_strnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_wcsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_mbsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|2 つの文字列の先頭の `count` 文字を照合する (大文字と小文字を区別しない)|

## <a name="remarks"></a>解説

これらの関数の 1 バイト文字 (SBCS) バージョン (`strcoll`、`stricoll`、`_strncoll`、`_strnicoll`) は、現在のロケールの `LC_COLLATE` カテゴリ設定に基づいて `string1` と `string2` を比較します。 これらの関数は、対応する `strcmp` 関数 (その中の `strcoll` 関数が照合順序を提供するロケール コード ページ情報を使用する) とは異なります。 文字セット順序と辞書式文字順序が異なるロケールでの文字列比較では、対応する `strcmp` 関数ではなく `strcoll` 関数を使用する必要があります。 `LC_COLLATE` の詳細については、[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) に関する記事をご覧ください。

一部のコード ページとそれに対応する文字セットでは、文字セットの文字の順序が辞書式の文字の順序と異なる場合があります。 "C" ロケールでは、前述とは異なり、ASCII 文字セットの文字の順序が辞書式の文字の順序と同じです。 しかし、たとえば、ヨーロッパの一部のコード ページでは、文字 a (値 0x61) は文字セットで文字 'ä' (値 0xE4) の前にありますが、辞書式の順序では文字 'ä' が文字 'a' の前にあります。 このようなインスタンスで、辞書式比較を実行するには、`strcmp` ではなく `strcoll` を使用します。 あるいは、元の文字列に対して `strxfrm` を使用してから、結果の文字列に対して `strcmp` を使用できます。

`strcoll`、`stricoll`、`_strncoll`、`_strnicoll` では、ワイド文字 (Unicode) の対応関数と同様に、現在使用中のロケールのコード ページに従ってマルチバイト文字の文字列を自動的に処理します。 ただし、これらの関数のマルチバイト (MBCS) バージョンでは、現在使用中のマルチバイトのコード ページに基づいて文字ごとに文字列を照合します。

`coll` 関数が単に文字列の等価性をテストするのに対して、`cmp` 関数は比較のために文字列を辞書式に照合するため、`coll` 関数は `cmp` の対応するバージョンよりもかなり低速です。 したがって、`coll` 関数は、現在のコード ページの文字セット順序と辞書式文字順序との間に相違点あり、この違いが文字列比較に関係がある場合にのみ使用します。

## <a name="see-also"></a>関連項目

[ロケール](../c-runtime-library/locale.md)<br/>
[文字列操作](../c-runtime-library/string-manipulation-crt.md)<br/>
[localeconv](../c-runtime-library/reference/localeconv.md)<br/>
[_mbsnbcoll、_mbsnbcoll_l、_mbsnbicoll、_mbsnbicoll_l](../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[strcmp、wcscmp、_mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)<br/>
[strncmp、wcsncmp、_mbsncmp、_mbsncmp_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp、_wcsnicmp、_mbsnicmp、_strnicmp_l、_wcsnicmp_l、_mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)
