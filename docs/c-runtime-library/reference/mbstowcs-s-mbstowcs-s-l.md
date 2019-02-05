---
title: mbstowcs_s、_mbstowcs_s_l
ms.date: 11/04/2016
apiname:
- _mbstowcs_s_l
- mbstowcs_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 18af20b5722364ea306daebdcb77f5771d8ea2b5
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703065"
---
# <a name="mbstowcss-mbstowcssl"></a>mbstowcs_s、_mbstowcs_s_l

マルチバイト文字のシーケンスを、対応するワイド文字のシーケンスに変換します。 「[Security Features in the CRT](../../c-runtime-library/security-features-in-the-crt.md)」 (CRT のセキュリティ機能) で説明されているように、セキュリティが強化されたバージョンの [mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md) です。

## <a name="syntax"></a>構文

```C
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count
);
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>パラメーター

*pReturnValue*<br/>
変換された文字数。

*wcstr*<br/>
結果として変換されたワイド文字の文字列のバッファーのアドレス。

*sizeInWords*<br/>
サイズ、 *wcstr*単語内のバッファー。

*mbstr*<br/>
null で終了するマルチバイト文字のシーケンスのアドレス。

*count*<br/>
格納するワイド文字の最大数、 *wcstr*バッファー、終端の null は含まないまたは[_TRUNCATE](../../c-runtime-library/truncate.md)します。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。

|エラー条件|戻り値および**errno**|
|---------------------|------------------------------|
|*wcstr*は**NULL**と*sizeInWords* > 0|**EINVAL**|
|*mbstr*は**NULL**|**EINVAL**|
|コピー先のバッファーが小さすぎて変換後の文字列を含む (しない限り、*カウント*は **_TRUNCATE**; 以下の「解説」を参照してください)|**ERANGE**|
|*wcstr*ない**NULL**と*sizeInWords* 0 を = =|**EINVAL**|

これらのいずれかの条件が発生すると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーター例外が呼び出されます。 実行の継続が許可された場合、関数はエラー コードを返します設定と**errno**表に記載されています。

## <a name="remarks"></a>Remarks

**Mbstowcs_s**関数が指すマルチバイト文字の文字列に変換します*mbstr*が指すバッファーに格納されているワイド文字に*wcstr*します。 これらの条件のいずれかが満たされるまで、各文字に対して変換が続きます。

- マルチバイトの null 文字が検出されました。

- 無効なマルチバイト文字が検出されました。

- 格納されるワイド文字の数、 *wcstr* equals をバッファー*カウント*します。

変換後の文字列は、常に null で終わります (エラーの場合も同様)。

場合*カウント*特殊な値は、 [_TRUNCATE](../../c-runtime-library/truncate.md)、し**mbstowcs_s**コピー先のバッファーは null の空きを残して収まる限りの文字列の多くに変換されますターミネータ。

場合**mbstowcs_s** 、元の文字列を正常に変換に null の終端文字を含む変換された文字列のワイド文字のサイズが置かれる *&#42;pReturnValue* (提供*pReturnValue*ない**NULL**)。 これが発生した場合でも、 *wcstr*引数が**NULL**し、必要なバッファー サイズを決定する方法を提供します。 場合*wcstr*は**NULL**、*カウント*は無視されますと*sizeInWords* 0 にする必要があります。

場合**mbstowcs_s**検出すると、無効なマルチバイト文字に 0 を入れ *&#42;pReturnValue*、空の文字列をコピー先のバッファーを設定、設定**errno** に**EILSEQ**、し、返します**EILSEQ**します。

によって、シーケンスを指している場合*mbstr*と*wcstr*の動作が重なる**mbstowcs_s**が定義されていません。

> [!IMPORTANT]
> いることを確認*wcstr*と*mbstr*重複しないと*数*変換するマルチバイト文字の数を正確に反映します。

**mbstowcs_s**ロケールに依存する動作に現在のロケールを使用 **_mbstowcs_s_l**代わりに渡されたロケールを使用すると同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

C++ では、これらの関数の使用はテンプレートのオーバーロードによって簡素化されます。オーバーロードでは、バッファー長を自動的に推論できる (サイズの引数を指定する必要がなくなる) だけでなく、古くてセキュリティが万全ではない関数を新しく安全な関数に自動的に置き換えることができます。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**mbstowcs_s**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
