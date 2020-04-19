---
title: mbstowcs_s、_mbstowcs_s_l
ms.date: 11/04/2016
api_name:
- _mbstowcs_s_l
- mbstowcs_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 0812c3f667f28c5c43d7932d4746052dbaff3a60
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952026"
---
# <a name="mbstowcs_s-_mbstowcs_s_l"></a>mbstowcs_s、_mbstowcs_s_l

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
*Wcstr*バッファーのサイズ (単語単位)。

*mbstr*<br/>
null で終了するマルチバイト文字のシーケンスのアドレス。

*count*<br/>
*Wcstr*バッファーに格納するワイド文字の最大数。終端の Null や[TRUNCATE](../../c-runtime-library/truncate.md)は含まれません。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。

|エラー状況|戻り値と**errno**|
|---------------------|------------------------------|
|*wcstr*が**NULL**で、 *sizeinwords* > 0|**EINVAL**|
|*mbstr*が**NULL**です|**EINVAL**|
|コピー先のバッファーが小さすぎて、変換された文字列を含めることができません ( *count*が**TRUNCATE**の場合を除きます。次の「解説」を参照してください)。|**ERANGE**|
|*wcstr*が**NULL**ではなく、 *sizeinwords* = = 0|**EINVAL**|

これらのいずれかの条件が発生すると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーター例外が呼び出されます。 実行の継続が許可された場合、関数はエラーコードを返し、表に示されているように**errno**を設定します。

## <a name="remarks"></a>Remarks

**Mbstowcs_s**関数は、 *mbstr*が指すマルチバイト文字の文字列を、 *wcstr*が指すバッファーに格納されているワイド文字に変換します。 これらの条件のいずれかが満たされるまで、各文字に対して変換が続きます。

- マルチバイトの null 文字が検出されました。

- 無効なマルチバイト文字が検出されました。

- *Wcstr* buffer に格納されているワイド文字の数は*count*と等しくなります。

変換後の文字列は、常に null で終わります (エラーの場合も同様)。

*Count*が特別な値の[切り捨て](../../c-runtime-library/truncate.md)である場合、 **mbstowcs_s**は、null 終端文字用の空きを残したまま、コピー先のバッファーに収まる限りの文字列を変換します。

**Mbstowcs_s**がソース文字列を正常に変換した場合は、null 終端文字を含む、変換された文字列のサイズが、  *&#42;preturnvalue* (指定された*preturnvalue* **値が null**ではない) に格納されます。 これは、 *wcstr*引数が**NULL**の場合にも発生し、必要なバッファーサイズを決定する手段を提供します。 *Wcstr*が**NULL**の場合、 *count*は無視され、 *sizeinwords*は0である必要があることに注意してください。

**Mbstowcs_s**で無効なマルチバイト文字が検出された場合は、  *&#42;preturnvalue*値に0を格納し、コピー先のバッファーを空の文字列に設定し、 **errno**を**EILSEQ**に設定して、 **EILSEQ**を返します。

*Mbstr*と*wcstr*が指すシーケンスが重なり合う場合、 **mbstowcs_s**の動作は未定義になります。

> [!IMPORTANT]
> *Wcstr*と*mbstr*が重複しないようにし、その*カウント*に変換するマルチバイト文字数が正しく反映されていることを確認します。

**mbstowcs_s**は、ロケールに依存する動作に現在のロケールを使用します。 **_mbstowcs_s_l**は、渡されたロケールを代わりに使用する点を除いて同じです。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

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
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen、mblen、_mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs、_wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb、_wctomb_l](wctomb-wctomb-l.md)<br/>
