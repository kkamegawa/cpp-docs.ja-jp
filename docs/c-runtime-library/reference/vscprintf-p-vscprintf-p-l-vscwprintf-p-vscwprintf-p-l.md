---
title: _vscprintf_p、_vscprintf_p_l、_vscwprintf_p、_vscwprintf_p_l
ms.date: 11/04/2016
api_name:
- _vscprintf_p_l
- _vscprintf_p
- _vscwprintf_p_l
- _vscwprintf_p
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vscprintf_p
- _vscprintf_p_l
- vscwprintf_p
- vscprintf_p
- vscwprintf_p_l
- _vscwprintf_p_l
- vscprintf_p_l
- _vscwprintf_p
helpviewer_keywords:
- vscprintf_p function
- _vsctprintf_p_l function
- vscwprintf_p_l function
- _vscwprintf_p_l function
- _vscprintf_p function
- vsctprintf_p function
- _vscprintf_p_l function
- _vscwprintf_p function
- vscwprintf_p function
- vsctprintf_p_l function
- _vsctprintf_p function
- vscprintf_p_l function
ms.assetid: 5da920b3-8652-4ee9-b19e-5aac3ace9d03
ms.openlocfilehash: 102ec617e42061e673cd14aea9c96916c907cf58
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945424"
---
# <a name="_vscprintf_p-_vscprintf_p_l-_vscwprintf_p-_vscwprintf_p_l"></a>_vscprintf_p、_vscprintf_p_l、_vscwprintf_p、_vscwprintf_p_l

引数リストへのポインターを使用して、書式設定された文字列内の文字数を返します。その際、引数を使用する順序を指定できます。

## <a name="syntax"></a>構文

```C
int _vscprintf_p(
   const char *format,
   va_list argptr
);
int _vscprintf_p _l(
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vscwprintf_p (
   const wchar_t *format,
   va_list argptr
);
int _vscwprintf_p _l(
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>パラメーター

*format*<br/>
書式指定文字列。

*argptr*<br/>
引数リストへのポインター。

*locale*<br/>
使用するロケール。

詳細については、「 [printf 関数と wprintf 関数の書式指定フィールド](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)」を参照してください。

## <a name="return-value"></a>戻り値

**_vscprintf_p**は、指定された書式設定コードを使用して、引数リストが指す文字列が出力されたか、ファイルまたはバッファーに送信された場合に生成される文字数を返します。 戻り値には、終端の NULL 文字は含まれません。 **_vscwprintf_p**は、ワイド文字に対して同じ関数を実行します。

## <a name="remarks"></a>Remarks

これらの関数は、引数を使用する順序を指定する機能をサポートしている点でのみ、 **_vscprintf**および **_vscwprintf**と異なります。 詳細については、「[printf_p の位置指定パラメーター](../../c-runtime-library/printf-p-positional-parameters.md)」をご覧ください。

**_L**サフィックスを持つこれらの関数のバージョンは、現在のスレッドロケールの代わりに渡されたロケールパラメーターを使用する点を除いて同じです。

*Format*が null ポインターの場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は-1 を返し、 **errno**を**EINVAL**に設定します。

> [!IMPORTANT]
> *Format*がユーザー定義の文字列である場合は、null で終了し、正しい数と種類のパラメーターを持つことを確認します。 詳しくは、「 [バッファー オーバーランの回避](/windows/win32/SecBP/avoiding-buffer-overruns)」をご覧ください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsctprintf_p**|**_vscprintf_p**|**_vscprintf_p**|**_vscwprintf_p**|
|**_vsctprintf_p_l**|**_vscprintf_p_l**|**_vscprintf_p_l**|**_vscwprintf_p_l**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_vscprintf_p**、 **_vscprintf_p_l**|\<stdio.h>|
|**_vscwprintf_p**、 **_vscwprintf_p_l**|\<stdio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

「[vsprintf](vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)」の例をご覧ください。

## <a name="see-also"></a>関連項目

[vprintf 系関数](../../c-runtime-library/vprintf-functions.md)<br/>
[_scprintf_p、_scprintf_p_l、_scwprintf_p、_scwprintf_p_l](scprintf-p-scprintf-p-l-scwprintf-p-scwprintf-p-l.md)<br/>
[_vscprintf、_vscprintf_l、_vscwprintf、_vscwprintf_l](vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)<br/>
