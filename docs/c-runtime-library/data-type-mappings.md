---
title: データ型のマップ
ms.date: 11/04/2016
f1_keywords:
- _TXCHAR
- _TUCHAR
- _TINT
- _TSCHAR
- _TCHAR
- TCHAR::H
- TCHAR
- _T
- _TEXT
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- TXCHAR type
- _TSCHAR type
- T type
- _TUCHAR type
- _TEXT type
- _T type
ms.assetid: 4e573c05-8800-468b-ae5f-76ff7409835e
ms.openlocfilehash: 60dc4329ae4c908b9bd168584c71c42c12634bb2
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749101"
---
# <a name="data-type-mappings"></a>データ型のマップ

ここで説明するデータ型のマッピングは TCHAR.H で定義されており、定数 `_UNICODE` または `_MBCS` がプログラムで定義されているかどうかに依存します。

関連情報については、次を参照してください。 [TCHAR を使用します。_MBCS コードでデータ型を H](../text/using-tchar-h-data-types-with-mbcs-code.md)します。

### <a name="generic-text-data-type-mappings"></a>汎用テキストのデータ型のマップ

|汎用テキスト<br /><br /> データ型名|SBCS (_UNICODE、<br /><br /> _MBCS が<br /><br /> 定義されていない)|_MBCS<br /><br /> 定義|_UNICODE<br /><br /> 定義|
|--------------------------------------|----------------------------------------------------|------------------------|---------------------------|
|`_TCHAR`|`char`|`char`|`wchar_t`|
|`_tfinddata_t`|`_finddata_t`|`_finddata_t`|`_wfinddata_t`|
|`_tfinddata64_t`|`__finddata64_t`|`__finddata64_t`|`__wfinddata64_t`|
|`_tfinddatai64_t`|`_finddatai64_t`|`_finddatai64_t`|`_wfinddatai64_t`|
|`_TINT`|`int`|`int`|`wint_t`|
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|
|`_T` または `_TEXT`|影響なし (プリプロセッサによって削除される)|影響なし (プリプロセッサによって削除される)|`L` (後続の文字または文字列を対応する Unicode の文字または文字列に変換する)|

## <a name="see-also"></a>関連項目

[汎用テキスト マップ](../c-runtime-library/generic-text-mappings.md)<br/>
[定数とグローバル変数のマップ](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[ルーチンのマップ](../c-runtime-library/routine-mappings.md)<br/>
[汎用テキストのプログラム例](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[汎用テキスト マップの使用](../c-runtime-library/using-generic-text-mappings.md)
