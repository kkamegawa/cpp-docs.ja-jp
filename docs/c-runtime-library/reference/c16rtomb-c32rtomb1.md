---
title: c16rtomb、c32rtomb
ms.date: 10/22/2019
api_name:
- c16rtomb
- c32rtomb
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: 8f480d9b450b528275fea78ae878269fa6a4fa54
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811070"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb、c32rtomb

UTF-16 または UTF-32 ワイド文字を UTF-8 マルチバイト文字に変換します。

## <a name="syntax"></a>構文

```C
size_t c16rtomb(
    char *mbchar,
    char16_t wchar,
    mbstate_t *state
);
size_t c32rtomb(
    char *mbchar,
    char32_t wchar,
    mbstate_t *state
);
```

### <a name="parameters"></a>パラメーター

*mbchar*\
変換された UTF-8 マルチバイト文字を格納する配列へのポインター。

*wchar*\
変換するワイド文字。

*状態*\
**Mbstate_t**オブジェクトへのポインター。

## <a name="return-value"></a>戻り値

配列オブジェクト*mbchar*に格納されているバイト数 (シフトシーケンスを含む)。 *Wchar*が有効なワイド文字ではない場合、値 (**size_t**) (-1) が返されます。 **errno**は**EILSEQ**に設定され、 *state*の値は未指定になります。

## <a name="remarks"></a>Remarks

**C16rtomb**関数は、utf-16 LE 文字*wchar*を等価の utf-8 マルチバイトナロー文字シーケンスに変換します。 *Mbchar*が null ポインターではない場合、関数は、 *mbchar*が指す配列オブジェクトに変換されたシーケンスを格納します。 最大**MB_CUR_MAX**バイトは*mbchar*に格納され、*状態*は結果のマルチバイトシフト状態に設定されます。

*Wchar*が null ワイド文字である場合、初期シフト状態の復元に必要なシーケンスが格納され、必要に応じて null 文字が続きます。 *state*が初期変換状態に設定されます。 **C32rtomb**関数は同じですが、32文字が変換されます。

*Mbchar*が null ポインターの場合、この動作は、 *mbchar*の内部バッファーと*wchar*のワイド null 文字を置換する関数の呼び出しと同じです。

*状態*変換状態オブジェクトを使用すると、この関数およびマルチバイト出力文字のシフト状態を維持するその他の再開可能な関数への後続の呼び出しを行うことができます。 再開可能な関数と再開不可能な関数を混在させた場合、結果は未定義になります。

Utf-16 文字を非 UTF-8 マルチバイト文字に変換するには、 [wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)、 [wcstombs_s、または _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md)関数を使用します。

## <a name="requirements"></a>［要件］

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**c16rtomb**、 **c32rtomb**|C、C++: \<uchar.h>|

互換性の詳細については、「 [互換性](../compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[データ変換](../data-conversion.md)の\
[ロケール](../locale.md)\
[マルチバイト文字のシーケンスの解釈](../interpretation-of-multibyte-character-sequences.md)\
[mbrtoc16、mbrtoc32](mbrtoc16-mbrtoc323.md)\
[wcrtomb](wcrtomb.md)\
[wcrtomb_s](wcrtomb-s.md)
