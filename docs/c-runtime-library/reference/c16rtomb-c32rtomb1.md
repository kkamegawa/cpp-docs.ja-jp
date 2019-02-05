---
title: c16rtomb、c32rtomb
ms.date: 01/22/2018
apiname:
- c16rtomb
- c32rtomb
apilocation:
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
apitype: DLLExport
f1_keywords:
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: ad58184c7bab6f95a842bda5f9eb545f09434a3e
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702779"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb、c32rtomb

UTF-16 または UTF-32 ワイド文字を現在のロケールのマルチバイト文字に変換します。

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

*mbchar*<br/>
変換されたマルチバイト文字を格納する配列へのポインター。

*wchar*<br/>
変換するワイド文字。

*state*<br/>
ポインター、 **mbstate_t**オブジェクト。

## <a name="return-value"></a>戻り値

配列オブジェクトに格納されるバイト数*mbchar*、シフト シーケンスを含むです。 場合*wchar*有効なワイド文字で、値はありません (**size_t**)(-1) が返される**errno**に設定されている**EILSEQ**の値*状態*が指定されていません。

## <a name="remarks"></a>Remarks

**C16rtomb**関数 utf-16 の文字変換*wchar*を現在のロケールで同等のマルチバイトのナロウ文字シーケンス。 場合*mbchar*によって示される配列オブジェクトに変換されたシーケンスの関数は、null ポインターではない*mbchar*します。 最大**MB_CUR_MAX**格納されるバイト*mbchar*と*状態*が結果として得られるマルチバイトのシフト状態に設定します。    場合*wchar* null ワイド文字に必要なシーケンスは、初期のシフト状態が格納されている、必要な場合、復元後に、null 文字と*状態*が初期の変換状態に設定します。 **C32rtomb**関数は同じですが、utf-32 文字に変換します。

場合*mbchar* null ポインターの場合は、動作は同等の内部バッファーを置換する関数への呼び出しに*mbchar*とのワイド null 文字*wchar*します。

*状態*変換状態オブジェクトを使用すると、この関数とマルチバイト出力のシフト状態を維持するその他の再開可能関数への後続の呼び出しを行います。 結果は、再開可能と再開不可能関数の使用を混在させることへの呼び出しの場合、または未定義**setlocale**再開可能な関数呼び出しの間で確立します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**c16rtomb**、 **c32rtomb**|C、C++: \<uchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtoc16、mbrtoc32](mbrtoc16-mbrtoc323.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
