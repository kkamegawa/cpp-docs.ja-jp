---
title: _ismbc 系ルーチン
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbc
helpviewer_keywords:
- ismbc routines
- _ismbc routines
ms.assetid: b8995391-7857-4ac3-9a1e-de946eb4464d
ms.openlocfilehash: 6dc14f269cafa8ccc343c5403ab0e23d319c71c3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940165"
---
# <a name="_ismbc-routines"></a>_ismbc 系ルーチン

これらの各 **_ismbc** ルーチンは、特定の条件で特定のマルチバイト文字 `c` をテストします。

|||
|-|-|
|[_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|[_ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|
|[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|[_ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|
|[_ismbchira、_ismbchira_l、_ismbckata、_ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|[_ismbclower、_ismbclower_l、_ismbcupper、 _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|

## <a name="remarks"></a>解説

各 **_ismbc** ルーチンのテスト結果は、有効なマルチバイト コード ページによって異なります。 マルチバイトのコード ページには、1 バイトの英字があります。 既定では、マルチバイト コード ページは、プログラムの開始時にオペレーティング システムから取得したシステム既定の ANSI コード ページに設定されます。 [_getmbcp](../c-runtime-library/reference/getmbcp.md)、または [_setmbcp](../c-runtime-library/reference/setmbcp.md) によって、使用中のマルチバイト コード ページをそれぞれ照会または変更できます。

出力値は、ロケールの `LC_CTYPE` カテゴリ設定に影響されます。詳細については、「[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)」を参照してください。 **_l** サフィックスが付いていないこれらの関数のバージョンでは、このロケールに依存する動作に現在のロケールを使用します。 **_l** サフィックスが付いているバージョンは、渡されたロケール パラメーターを代わりに使用する点を除いて同じです。

|ルーチンによって返される値|テスト条件|コード ページ 932 の例|
|-------------|--------------------|---------------------------|
|[_ismbcalnum、_ismbcalnum_l](../c-runtime-library/reference/ismbcalnum-functions.md)|英数字|`c` が ASCII の英字の 1 バイト表現である場合に限り、0 以外の値を返します。「`_ismbcdigit`」および「`_ismbcalpha`」の例を参照してください。|
|[_ismbcalpha, _ismbcalpha_l](../c-runtime-library/reference/ismbcalnum-functions.md)|alphabetic|`c` が ASCII の英字の 1 バイト表現である場合に限り、0 以外の値を返します。「`_ismbcupper`」および「`_ismbclower`」の例、またはカタカナ文字「0xA6<=`c`<=0xDF」の例を参照してください。|
|[_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|数字|`c` が ASCII 数字 (0x30<=`c`<=0x39) の 1 バイト表現である場合に限り、0 以外の値を返します。|
|[_ismbcgraph、_ismbcgraph_l](../c-runtime-library/reference/ismbcgraph-functions.md)|グラフィック|`c` が空白 ( ) を除く ASCII またはカタカナの印刷可能な文字の 1 バイト表現である場合に限り、0 以外の値を返します。 「`_ismbcdigit`」、「`_ismbcalpha`」、および「`_ismbcpunct`」の例を参照してください。|
|[_ismbclegal、_ismbclegal_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|有効なマルチバイト文字|`c` の最初のバイトが 0x81 - 0x9F または 0xE0 - 0xFC の範囲内にあり、2 番目のバイトが 0x40 - 0x7E または 0x80 - FC の範囲内にある場合にのみ、0 以外の値を返します。|
|[_ismbclower、_ismbclower_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|小文字の英字|`c` が ASCII 小文字の英字 (0x61<=`c`<=0x7A) の 1 バイト表現である場合に限り、0 以外の値を返します。|
|[_ismbcprint、_ismbcprint_l](../c-runtime-library/reference/ismbcgraph-functions.md)|印刷可能|`c` が空白 ( ) を含む ASCII またはカタカナの印刷可能な文字の 1 バイト表現である場合に限り、0 以外の値を返します。「`_ismbcspace`」、「`_ismbcdigit`」、「`_ismbcalpha`」、および「`_ismbcpunct`」の例を参照してください。|
|[_ismbcpunct、_ismbcpunct_l](../c-runtime-library/reference/ismbcgraph-functions.md)|区切り記号|`c` が ASCII またはカタカナの区切り記号の 1 バイト表現である場合に限り、0 以外の値を返します。|
|[_ismbcblank、_ismbcblank_l](../c-runtime-library/reference/ismbcgraph-functions.md)|空白または水平タブ|`c` が空白文字または水平タブ文字のバイト表現である場合 (`c`=0x20 または `c`=0x09) に限り、0 以外の値を返します。|
|[_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Whitespace|`c` が空白文字の場合 (`c`=0x20 または 0x09<=`c`<=0x0D)、0 以外の値を返します。|
|[_ismbcsymbol、_ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|マルチバイトの記号|0x8141<=`c`<=0x81AC の場合にのみ、0 以外の値を返します。|
|[_ismbcupper、_ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|大文字の英字|`c` が ASCII 大文字の英字 (0x41<=`c`<=0x5A) の 1 バイト表現である場合に限り、0 以外の値を返します。|

**コード ページ 932 固有情報**

次のルーチンは、コード ページ 932 に固有です。

|ルーチンによって返される値|テスト条件 (コード ページ 932 のみ)|
|-------------|-------------------------------------------|
|[_ismbchira、_ismbchira_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|2 バイトひらがな: 0x829F<=`c`<=0x82F1。|
|[_ismbckata、_ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|2 バイトカタカナ: 0x8340<=`c`<=0x8396。|
|[_ismbcl0、_ismbcl0_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS の非漢字: 0x8140<=`c`<=0x889E。|
|[_ismbcl1、_ismbcl1_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS のレベル 1: 0x889F<=`c`<=0x9872。|
|[_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|JIS のレベル 2: 0x989F<=`c`<=0xEA9E。|

`_ismbcl0`、`_ismbcl1`、および `_ismbcl2` は、指定された値 `c` が、上の表に記載のテスト条件に一致するかどうかをチェックしますが、`c` が有効なマルチバイト文字かどうかはチェックしません。 下位バイトが範囲 0x00 - 0x3F、0x7F、または 0xFD - 0xFF にある場合、これらの関数は 0 以外の値を返し、文字がテスト条件を満たすことを示します。 マルチバイト文字が定義されているかどうかをテストするために [_ismbbtrail、_ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) を使用します。

**コード ページ 932 固有情報終了**

## <a name="see-also"></a>関連項目

[文字分類](../c-runtime-library/character-classification.md)<br/>
[is、isw 系ルーチン](../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb 系ルーチン](../c-runtime-library/ismbb-routines.md)
