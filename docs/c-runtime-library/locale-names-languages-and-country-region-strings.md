---
title: ロケール名、言語、および国/地域識別文字列
ms.date: 12/10/2018
f1_keywords:
- c.strings
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
ms.openlocfilehash: 512eb589d964da9ef8e87f4193362c739b39b4b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500061"
---
# <a name="ucrt-locale-names-languages-and-countryregion-strings"></a>UCRT ロケール名、言語、および国/地域識別文字列

[setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)、[\_create\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)、および [\_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) 関数の "*ロケール*" 引数は、Windows NLS API でサポートされているロケール名、言語、国/地域コード、コード ページを使用して設定できます。 *ロケール*引数は次の形式になります。

> *locale* :: "*locale-name*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "*language*\[ **\_** _country-region_\[ __.__ *code-page*]]"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| " __.__ *code-page*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "C"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| ""<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| NULL

*locale-name* の形式は、IETF 標準化された短い文字列 (例: 英語 (米国) の `en-US`、ボスニア語 (キリル、ボスニア ヘルツェゴビナ) の `bs-Cyrl-BA` など) になります。 これらの形式は優先されます。 Windows オペレーティング システムのバージョンによってサポートされているロケール名の一覧については、**Language tag** の列 (「[Appendix A: Product Behavior](https://msdn.microsoft.com/library/cc233982.aspx)」(付録 A: 製品の動作) にある表内) をご覧ください。これは、[MS-LCID]:Windows Language Code Identifier (LCID) Reference ([MS-LCID]: Windows 言語コード識別子 (LCID) リファレンス) にあります。 このリソースは、ロケール名のサポートされている言語、スクリプト、および地域の部分を示しています。 既定以外の並べ替え順序を持つ、サポートされているロケール名については、「 **並べ替え順序の識別子** 」の [Locale name](/windows/win32/Intl/sort-order-identifiers)の列を参照してください。 Windows 10 以降では、有効な [BCP-47](https://tools.ietf.org/html/bcp47) の言語タグに対応するロケール名が許可されています。 たとえば、`jp-US` は有効な BCP-47 タグですが、ロケール機能としては `US` にのみ有効です。

ロケールを作成するために、言語識別文字列、または言語識別文字列と国/地域識別文字列が使用される場合、*language*\[ **\_** _country-region_\[ __.__ *code-page*]] 形式がカテゴリのロケール設定に格納されます。 サポートされる言語識別文字列のセットは「[Language Strings](../c-runtime-library/language-strings.md)」、サポートされるすべての国および地域識別文字列のリストは「[国/地域別文字列](../c-runtime-library/country-region-strings.md)」に記述されています。 指定した言語が指定した国または地域に関連付けられてない場合、その指定した国または地域に対する既定の言語がロケール設定に格納されます。 この形式は、コードに埋め込まれた、またはストレージに対してシリアル化されたロケール文字列にはお勧めしません。これらの文字列は、ロケール名形式よりも、オペレーティング システムの更新によって変更される可能性が高いからです。

*code-page* は、ロケールに関連付けられた ANSI/OEM コード ページです。 コード ページは、言語または言語と国/地域のみによってロケールを指定すると決定されます。 特殊な値 `.ACP` は国/地域の ANSI コード ページを指定します。 特殊な値 `.OCP` は国/地域の OEM コード ページを指定します。 たとえば、ロケールとして `"Greek_Greece.ACP"` を指定すると、ロケールは `Greek_Greece.1253` (ギリシャ語の ANSI コード ページ) として格納されます。また、ロケールとして `"Greek_Greece.OCP"` を指定すると、 `Greek_Greece.737` (ギリシャ語の OEM のコード ページ) として格納されます。 コード ページの詳細については、「 [Code Pages](../c-runtime-library/code-pages.md)」を参照してください。 Windows でサポートされているコード ページの一覧については、「 [コード ページの識別子](/windows/win32/Intl/code-page-identifiers)」を参照してください。

ロケールを指定するためにコード ページだけを使用する場合、ユーザーの既定の言語と国または地域 ([GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename) で報告される) が使用されます。 たとえば、英語 (米国) に構成されたユーザーのロケールとして `".1254"` (ANSI トルコ語) を指定した場合は、格納されているロケールは `English_United States.1254` です。 この形式はお勧めしません。これにより一貫性のない動作が実行される可能性があるためです。

`C` の*ロケール*引数値は、C 翻訳のための ANSI に準拠した最小環境を指定します。 `C` ロケールは、任意の **char** データ型が 1 バイトであり、値は常に 256 未満であると推定します。 *ロケール*が空の文字列をポイントしている場合は、実装定義のネイティブ環境になります。

`setlocale` 関数と `_wsetlocale` 関数に `LC_ALL` カテゴリを使用して、ロケールのカテゴリのすべてを同時に指定できます。 カテゴリはすべて同じロケールに設定できますが、次の形式を持つロケール引数を使用して各カテゴリを個別に設定できます。

> *LC-ALL-specifier* :: *locale*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| \[**LC_COLLATE=** _locale_]\[ **;LC_CTYPE=** _locale_]\[ **;LC_MONETARY=** _locale_]\[ **;LC_NUMERIC=** _locale_]\[ **;LC_TIME=** _locale_]

セミコロンで区切って複数のカテゴリの種類を指定できます。 指定されていないカテゴリの種類は、現在のロケール設定を使用します。 たとえば、このコード スニペットは、すべてのカテゴリの現在のロケールを `de-DE` に設定し、カテゴリ `LC_MONETARY` を `en-GB` に、カテゴリ `LC_TIME` を `es-ES` に設定します。

```C
_wsetlocale(LC_ALL, L"de-DE");
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");
```

## <a name="see-also"></a>関連項目

[C ランタイム ライブラリ リファレンス](../c-runtime-library/c-run-time-library-reference.md)<br/>
[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[言語識別文字列](../c-runtime-library/language-strings.md)<br/>
[Country/Region Strings](../c-runtime-library/country-region-strings.md)
