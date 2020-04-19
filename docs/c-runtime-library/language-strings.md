---
title: Language Strings
ms.date: 11/04/2016
f1_keywords:
- c.strings
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
ms.openlocfilehash: a9e6eaa65516b5b49022526f24e220dec83b2c26
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500074"
---
# <a name="language-strings"></a>Language Strings

[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 関数と [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) 関数は、Unicode コード ページを使用しないオペレーティング システム上では、Windows NLS API をサポートする言語を使用できます。 オペレーティング システムのバージョンによってサポートされている言語の一覧については、「[付録 A:Product Behavior](https://msdn.microsoft.com/library/cc233982.aspx)」(付録 A: 製品の動作) にある表内) をご覧ください。これは、[MS-LCID]:Windows Language Code Identifier (LCID) Reference ([MS-LCID]: Windows 言語コード識別子 (LCID) リファレンス) にあります。 言語識別文字列には、サポートされる言語の一覧の **[Language]** 列と **[Language tag]** 列の任意の値を指定できます。 利用できるロケール名と関連する値を列挙するコードの例については、次をご覧ください: 「[NLS:名前ベースの API のサンプル](/windows/win32/intl/nls--name-based-apis-sample)」。

## <a name="additional-supported-language-strings"></a>サポートされるその他の言語識別文字列

Microsoft の C ランタイム ライブラリの実装では、次の言語識別文字列もサポートされます。

|言語識別文字列|同等のロケール名|
|---------------------|----------------------------|
|american|en-US|
|american english|en-US|
|american-english|en-US|
|australian|en-AU|
|belgian|nl-BE|
|canadian|en-CA|
|chh|zh-HK|
|chi|zh-SG|
|chinese|zh|
|chinese-hongkong|zh-HK|
|chinese-simplified|zh-CN|
|chinese-singapore|zh-SG|
|chinese-traditional|zh-TW|
|dutch-belgian|nl-BE|
|english-american|en-US|
|english-aus|en-AU|
|english-belize|en-BZ|
|english-can|en-CA|
|english-caribbean|en-029|
|english-ire|en-IE|
|english-jamaica|en-JM|
|english-nz|en-NZ|
|english-south africa|en-ZA|
|english-trinidad y tobago|en-TT|
|english-uk|en-GB|
|english-us|en-US|
|english-usa|en-US|
|french-belgian|fr-BE|
|french-canadian|fr-CA|
|french-luxembourg|fr-LU|
|french-swiss|fr-CH|
|german-austrian|de-AT|
|german-lichtenstein|de-LI|
|german-luxembourg|de-LU|
|german-swiss|de-CH|
|irish-english|en-IE|
|italian-swiss|it-CH|
|norwegian|Ｘ|
|norwegian-bokmal|nb-NO|
|norwegian-nynorsk|nn-NO|
|portuguese-brazilian|pt-BR|
|spanish-argentina|es-AR|
|spanish-bolivia|es-BO|
|spanish-chile|es-CL|
|spanish-colombia|es-CO|
|spanish-costa rica|es-CR|
|spanish-dominican republic|es-DO|
|spanish-ecuador|es-EC|
|spanish-el salvador|es-SV|
|spanish-guatemala|es-GT|
|spanish-honduras|es-HN|
|spanish-mexican|es-MX|
|spanish-modern|es-ES|
|spanish-nicaragua|es-NI|
|spanish-panama|es-PA|
|spanish-paraguay|es-PY|
|spanish-peru|es-PE|
|spanish-puerto rico|es-PR|
|spanish-uruguay|es-UY|
|spanish-venezuela|es-VE|
|swedish-finland|sv-FI|
|swiss|de-CH|
|uk|en-GB|
|us|en-US|
|usa|en-US|

## <a name="see-also"></a>関連項目

[ロケール名、言語、および国/地域識別文字列](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Country/Region Strings](../c-runtime-library/country-region-strings.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
