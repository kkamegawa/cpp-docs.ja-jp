---
title: _mbsnbicmp、_mbsnbicmp_l
ms.date: 11/04/2016
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _strnicmp
- _wcsnicmp_l
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _tcsnicmp
- _strnicmp_l
- _tcsnicmp_l
- _wcsnicmp
- _mbsnbicmp_l
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
ms.openlocfilehash: 19ffa4c47f0144ba136607fe5cef09e9bd65374f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952187"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp、_mbsnbicmp_l

2つのマルチバイト文字列の**n**バイトを比較し、大文字と小文字を区別しません。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _mbsnbicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>パラメーター

*string1*、 *string2*<br/>
Null で終わる比較対象の文字列。

*count*<br/>
比較するバイト数。

## <a name="return-value"></a>戻り値

戻り値は、部分文字列間の関係を示しています。

|戻り値|説明|
|------------------|-----------------|
|< 0|*string1* *部分文字列より小さい*string1 部分文字列。|
|0|*string1*部分文字列は、 *string2*部分文字列と同じです。|
|> 0|*string1* *部分文字列より大きい*string1 部分文字列。|

エラーが発生すると、 **_mbsnbicmp**によって **_NLSCMPERROR**が返されます。これは、.h および mbstring.h で定義されています。

## <a name="remarks"></a>Remarks

**_Mbsnbicmp**関数は、 *string1*と*string2*の先頭の最大バイト*数の*序数比較を実行します。 比較は、各文字を小文字に変換することによって行われます。[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)は、大文字と小文字を区別する **_mbsnbicmp**のバージョンです。 *カウント*文字を比較する前に、いずれかの文字列で終端の null 文字に到達すると、比較は終了します。 文字列が等しい場合、 *count*文字が比較される前にいずれかの文字列で終端の null 文字に到達すると、短い文字列の方が小さくなります。

**_mbsnbicmp**は[_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md)に似ていますが、文字ではなく*カウント*バイトまで文字列を比較する点が異なります。

ASCII の表の 'Z' と 'a' の間にある文字 ('['、'\\'、']'、'^'、'_'、'\`') を含む 2 つの文字列は、場合に応じて異なる方法で比較します。 たとえば、2つの文字列 "ABCDE...Z" と "ABCD ^" は、比較が小文字 ("abcde...z" > "abcd ^") である場合の1つの方法と、大文字の場合は "ABCDE...Z" < "ABCD ^" のように比較されます。

**_mbsnbicmp**は、現在使用中の[マルチバイトコードページ](../../c-runtime-library/code-pages.md)に従ってマルチバイト文字のシーケンスを認識します。 これは、現在のロケール設定の影響を受けません。

*String1*または*string2*が null ポインターの場合、 **_Mbsnbicmp**は「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、関数は **_NLSCMPERROR**を返し、 **errno**を**EINVAL**に設定します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

「[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)」の例を参照してください。

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat、_mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp、_mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp、_wcsicmp、_mbsicmp、_stricmp_l、_wcsicmp_l、_mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
