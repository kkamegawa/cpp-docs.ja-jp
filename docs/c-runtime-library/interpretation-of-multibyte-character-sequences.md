---
title: マルチバイト文字のシーケンスの解釈
ms.date: 10/22/2019
f1_keywords:
- c.character.multibyte
helpviewer_keywords:
- MBCS [C++], locale code page
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
ms.openlocfilehash: 7431f0c63df60414af192ea38103318c775c430d
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811075"
---
# <a name="interpretation-of-multibyte-character-sequences"></a>マルチバイト文字のシーケンスの解釈

Microsoft ランタイム ライブラリにあるほとんどのマルチバイト文字ルーチンは、マルチバイト コード ページに関連するマルチバイト文字のシーケンスを認識します。 出力値は、ロケールの**LC_CTYPE**カテゴリの設定に影響されます。 詳細については、「[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)」を参照してください。 **_L**サフィックスが付いていないこれらの関数のバージョンは、このロケールに依存する動作に現在のロケールを使用します。 **_L**サフィックスが付いているバージョンは、現在のロケールの代わりに locale パラメーターを使用する点を除いて同じです。

## <a name="locale-dependent-multibyte-routines"></a>ロケールに依存するマルチバイトルーチン

|ルーチンによって返される値|上限のファイル数を変更するには、|
|-------------|---------|
|[_mbclen、mblen、_mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|マルチバイト文字のバイト数を検証して返す|
|[strlen、wcslen、_mbslen、_mbslen_l、_mbstrlen、_mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|マルチバイト文字列の場合は、文字列内の各文字を検証し、文字列の長さを返す ワイド文字列の場合は、文字列の長さを返す|
|[mbstowcs、_mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)、[mbstowcs_s、_mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|マルチバイト文字のシーケンスを、対応するワイド文字のシーケンスに変換|
|[mbtowc、_mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|マルチバイト文字を対応するワイド文字に変換|
|[wcstombs、_wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)、[wcstombs_s、_wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|ワイド文字のシーケンスを、対応するマルチバイト文字のシーケンスに変換する|
|[wctomb、_wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md)、[wctomb_s、_wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|ワイド文字を対応するマルチバイト文字に変換する|

## <a name="locale-independent-multibyte-routines"></a>ロケールに依存しないマルチバイトルーチン

|ルーチンによって返される値|上限のファイル数を変更するには、|
|-------------|---------|
|[mbrtoc16、mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|マルチバイト UTF-8 文字を等価の UTF-16 または UTF-32 文字に変換します。|
|[c16rtomb、c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|UTF-16 または UTF-32 文字を等価の UTF-8 マルチバイト文字に変換します。|

## <a name="see-also"></a>関連項目

[国際化](../c-runtime-library/internationalization.md)\
[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)
