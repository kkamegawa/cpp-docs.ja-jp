---
title: 文字分類
ms.date: 11/04/2016
f1_keywords:
- c.types.character
helpviewer_keywords:
- character classification routines
- characters, testing
ms.assetid: 3b6c8f0b-9701-407a-b384-9086698773f5
ms.openlocfilehash: 757eeac41ecd4e300b7aabef122a8dbdd7e79e11
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739771"
---
# <a name="character-classification"></a>文字分類

これらのルーチンでは、指定された 1 バイト文字、ワイド文字、またはマルチバイト文字について条件を満たすかどうかをテストします。 (定義上、0 ～ 127 の間の ASCII 文字セットは、すべてのマルチバイト文字セットのサブセットと考えることができます。 たとえば、日本語のカタカナには ASCII 文字と非 ASCII 文字が含まれています)。

テスト条件は、ロケールの **LC_CTYPE** カテゴリの設定で決まります。詳細については、「[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)」を参照してください。 **_l** サフィックスが付いていないこれらの関数のバージョンでは、このロケールに依存する動作に現在のロケールを使用します。**_l** サフィックスが付いているバージョンは、渡されたロケール パラメーターを代わりに使用する点を除いて同じです。

通常、これらのルーチンはテストを記述するより速く実行されるため、こちらを使用するようにしてください。 たとえば、次のコードを実行するより `isalpha(c)` を呼び出した方が高速に処理できます。

```C
if ((c >= 'A') && (c <= 'Z')) || ((c >= 'a') && (c <= 'z'))
    return TRUE;
```

## <a name="character-classification-routines"></a>文字分類ルーチン

|ルーチンによって返される値|文字のテスト条件|
|-------------|------------------------------|
|[isalnum、iswalnum、_isalnum_l、_iswalnum_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)、[_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|英数字|
|[_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|マルチバイトの英数字|
|[isalpha、iswalpha、_isalpha_l、_iswalpha_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md)、[_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|alphabetic|
|[isascii、__isascii、iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|ASCII|
|[isblank、iswblank、_isblank_l、_iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)、[_ismbcsblank、_ismbcsblank_l](../c-runtime-library/reference/ismbcgraph-functions.md)|空白 (スペースまたは水平タブ)|
|[iscntrl、iswcntrl、_iscntrl_l、_iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|コントロール|
|[iscsym、iscsymf、__iscsym、\__iswcsym、\__iscsymf、\__iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l](../c-runtime-library/reference/iscsym-functions.md)|文字、アンダースコア、または数字|
|[iscsym、iscsymf、__iscsym、\__iswcsym、\__iscsymf、\__iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l](../c-runtime-library/reference/iscsym-functions.md)|文字またはアンダースコア|
|[isdigit、iswdigit、_isdigit_l、_iswdigit_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)、[_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l](../c-runtime-library/reference/ismbcalnum-functions.md)|10 進数|
|[isgraph、iswgraph、_isgraph_l、_iswgraph_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)、[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|スペース以外印刷可能|
|[islower、iswlower、_islower_l、_iswlower_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)、[_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|小文字|
|[_ismbchira、_ismbchira_l、_ismbckata、_ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|ひらがな|
|[_ismbchira、_ismbchira_l、_ismbckata、_ismbckata_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|カタカナ|
|[_ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|有効なマルチバイト文字|
|[_ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本 - レベル 0 のマルチバイト文字|
|[_ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本 - レベル 1 のマルチバイト文字|
|[_ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|日本 - レベル 2 のマルチバイト文字|
|[_ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|英数字以外のマルチバイト文字|
|[isprint、iswprint、_isprint_l、_iswprint_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md)、[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|印刷可能|
|[ispunct、iswpunct、_ispunct_l、_iswpunct_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)、[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|区切り記号|
|[isspace、iswspace、_isspace_l、_iswspace_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)、[_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l](../c-runtime-library/reference/ismbcgraph-functions.md)|空白|
|[isupper, iswupper](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md), [_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|大文字|
|[_isctype、iswctype、_isctype_l、_iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|*desc* 引数で指定されたプロパティ|
|[isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|16 進数|
|[_mbclen、mblen、_mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|有効なマルチバイト文字の長さを返します。結果は、現在のロケールの **LC_CTYPE** のカテゴリの設定によって異なります|

## <a name="see-also"></a>関連項目

[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
