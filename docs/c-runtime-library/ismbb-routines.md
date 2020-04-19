---
title: _ismbb 系ルーチン
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbb
- ismbb
helpviewer_keywords:
- ismbb routines
- _ismbb routines
ms.assetid: d63c232e-3fe4-4844-aafd-2133846ece4b
ms.openlocfilehash: 374c78ca222f9c63f6b37f26d4cf3a00f48f845e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944528"
---
# <a name="_ismbb-routines"></a>_ismbb 系ルーチン

現在のロケールまたは指定された LC_CTYPE 変換状態カテゴリを使用して、特定の条件に対して整数値 `c` をテストします。

|||
|-|-|
|[_ismbbalnum、_ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|[_ismbbkprint、_ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|
|[_ismbbalpha、_ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|[_ismbbkpunct、_ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|
|[_ismbbblank、_ismbbblank_l](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|[_ismbblead、_ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|
|[_ismbbgraph、_ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|[_ismbbprint、_ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|
|[_ismbbkalnum、_ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|[_ismbbpunct、_ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|
|[_ismbbkana、_ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|[_ismbbtrail、_ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|

## <a name="remarks"></a>解説

`_ismbb` ファミリのすべてのルーチンは、特定の条件に対して整数値 `c` をテストします。 テスト結果は、有効なマルチバイト コード ページによって異なります。 既定では、マルチバイト コード ページは、プログラムの開始時にオペレーティング システムから取得した ANSI コード ページに設定されます。 [_getmbcp](../c-runtime-library/reference/getmbcp.md) を使って使用中のマルチバイト コード ページを照会し、または [_setmbcp](../c-runtime-library/reference/setmbcp.md) を使って変更できます。

出力値は、ロケールの `LC_CTYPE` カテゴリの設定で決まります。詳しくは、「[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)」をご覧ください。 **_l** サフィックスが付いていないこれらの関数のバージョンでは、このロケールに依存する動作に現在のロケールを使用します。 **_l** サフィックスが付いているバージョンは、渡されたロケール パラメーターを代わりに使用する点を除いて同じです。

`_ismbb` ファミリのルーチンは、特定の整数 `c` を次のようにテストします。

|ルーチンによって返される値|バイト テスト条件|
|-------------|-------------------------|
|[_ismbbalnum](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum` &#124;&#124; `_ismbbkalnum`.|
|[_ismbbalpha](reference/ismbbalpha-ismbbalpha-l.md)|`isalpha` &#124;&#124; `_ismbbkalnum`.|
|[_ismbbblank](../c-runtime-library/reference/ismbbblank-ismbbblank-l.md)|`isblank`|
|[_ismbbgraph](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|`_ismbbprint`は、 `_ismbbgraph` と同じですが、空白文字 (0x20) は含みません。|
|[_ismbbkalnum](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|区切り記号以外の非 ASCII テキストの記号。 たとえば、コード ページ 932 でのみ `_ismbbkalnum` は、カタカナ英数字をテストします。|
|[_ismbbkana](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|カタカナ (0xA1 - 0xDF)。 コード ページ 932 固有。|
|[_ismbbkprint](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|非 ASCII テキストまたは ASCII 以外の区切り記号。 たとえば、コード ページ 932 でのみ、`_ismbbkprint` はカタカナの英数字、またはカタカナの句読点 (範囲: 0xA1 - 0xDF) をテストします。|
|[_ismbbkpunct](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|ASCII 以外の区切り記号。 たとえば、コード ページ 932 でのみ `_ismbbkpunct` は、カタカナ区切り文字をテストします。|
|[_ismbblead](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|マルチバイト文字の最初のバイト。 たとえば、コード ページ 932 でのみ、有効な範囲は 0x81 - 0x9F、0xE0 - 0xFC です。|
|[_ismbbprint](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint` &#124;&#124; `_ismbbkprint`. **ismbbprint** には、空白文字 (0x20) が含まれます。|
|[_ismbbpunct](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct` &#124;&#124; `_ismbbkpunct`.|
|[_ismbbtrail](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|マルチバイト文字の 2 番目のバイト。 たとえば、コード ページ 932 でのみ、有効な範囲は 0x40 - 0x7E、0x80 - 0xEC です。|

次の表は、これらのルーチンのテスト条件を構成する値の論理和を示します。 マニフェスト定数 `_BLANK`、 `_DIGIT`、 `_LOWER`、 `_PUNCT`、および `_UPPER` は Ctype.h で定義されます。

|ルーチンによって返される値|_BLANK|_DIGIT|LOWER|_PUNCT|UPPER|非<br /><br /> ASCII<br /><br /> テキスト|非<br /><br /> ASCII<br /><br /> 区切り文字|
|-------------|-------------|-------------|-----------|-------------|-----------|------------------------------|-------------------------------|
|`_ismbbalnum`|—|x|x|—|x|x|—|
|`_ismbbalpha`|—|—|x|—|x|x|—|
|`_ismbbblank`|x|—|—|—|—|—|—|
|`_ismbbgraph`|—|x|x|x|x|x|x|
|`_ismbbkalnum`|—|—|—|—|—|x|—|
|`_ismbbkprint`|—|—|—|—|—|x|x|
|`_ismbbkpunct`|—|—|—|—|—|—|x|
|`_ismbbprint`|x|x|x|x|x|x|x|
|`_ismbbpunct`|—|—|—|x|—|—|x|

`_ismbb` ルーチンは、関数とマクロの両方として実装されます。 実装の選び方については、「[関数またはマクロの選択に関する推奨事項](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[バイト分類](../c-runtime-library/byte-classification.md)<br/>
[is、isw 系ルーチン](../c-runtime-library/is-isw-routines.md)<br/>
[_mbbtombc、_mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)<br/>
[_mbctombb、_mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)
