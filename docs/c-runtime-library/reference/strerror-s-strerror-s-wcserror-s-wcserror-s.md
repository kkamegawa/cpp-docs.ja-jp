---
title: strerror_s、_strerror_s、_wcserror_s、__wcserror_s
ms.date: 11/04/2016
api_name:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcserror_s
- __wcserror_s
- _tcserror_s
- _wcserror_s
- tcserror_s
- strerror_s
- _strerror_s
helpviewer_keywords:
- __wcserror_s function
- error messages, printing
- tcserror_s function
- printing error messages
- strerror_s function
- _wcserror_s function
- _tcserror_s function
- _strerror_s function
- wcserror_s function
- error messages, getting
ms.assetid: 9e5b15a0-efe1-4586-b7e3-e1d7c31a03d6
ms.openlocfilehash: 74caba0398fdb5cdd0f9c80270a42d2903200a5d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625809"
---
# <a name="strerror_s-_strerror_s-_wcserror_s-__wcserror_s"></a>strerror_s、_strerror_s、_wcserror_s、__wcserror_s

システムエラーメッセージ (**strerror_s**、 **_wcserror_s**) を取得するか、ユーザーが指定したエラーメッセージ ( **_strerror_s**、 **__wcserror_s**) を出力します。 これらは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [strerror、_strerror、_wcserror、\__wcserror](strerror-strerror-wcserror-wcserror.md) です。

## <a name="syntax"></a>構文

```C
errno_t strerror_s(
   char *buffer,
   size_t numberOfElements,
   int errnum
);
errno_t _strerror_s(
   char *buffer,
   size_t numberOfElements,
   const char *strErrMsg
);
errno_t _wcserror_s(
   wchar_t *buffer,
   size_t numberOfElements,
   int errnum
);
errno_t __wcserror_s(
   wchar_t *buffer,
   size_t numberOfElements,
   const wchar_t *strErrMsg
);
template <size_t size>
errno_t strerror_s(
   char (&buffer)[size],
   int errnum
); // C++ only
template <size_t size>
errno_t _strerror_s(
   char (&buffer)[size],
   const char *strErrMsg
); // C++ only
template <size_t size>
errno_t _wcserror_s(
   wchar_t (&buffer)[size],
   int errnum
); // C++ only
template <size_t size>
errno_t __wcserror_s(
   wchar_t (&buffer)[size],
   const wchar_t *strErrMsg
); // C++ only
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
エラー文字列を格納するバッファー。

*numberOfElements*<br/>
バッファーのサイズ。

*errnum*<br/>
エラー番号。

*strErrMsg*<br/>
ユーザーが指定したメッセージ。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。

### <a name="error-condtions"></a>エラー条件

|*バッファー*|*numberOfElements*|*strErrMsg*|*バッファー*の内容|
|--------------|------------------------|-----------------|--------------------------|
|**NULL**|任意|任意|N/A|
|任意|0|任意|変更されない|

## <a name="remarks"></a>Remarks

**Strerror_s**関数は、 *errnum*をエラーメッセージ文字列にマップし、*バッファー*内の文字列を返します。 **_strerror_s**はエラー番号を受け取りません。**errno**の現在の値を使用して、適切なメッセージを決定します。 **Strerror_s**も **_strerror_s**も実際にはメッセージを出力しません。そのため、 [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)のような出力関数を呼び出す必要があります。

```C
if (( _access( "datafile",2 )) == -1 )
{
   _strerror_s(buffer, 80);
   fprintf( stderr, buffer );
}
```

*StrErrMsg*が**NULL**の場合、 **_strerror_s**は、エラーを生成した最後のライブラリの呼び出しのシステムエラーメッセージを含む文字列を*buffer*に返します。 エラー メッセージ文字列は、改行文字 (「\n」) で終了します。 *StrErrMsg*が**NULL**でない場合、 **_strerror_s**は、文字列メッセージ、コロン、空白、エラーを生成した最後のライブラリの呼び出しのシステムエラーメッセージ、および改行を含む*バッファー*内の文字列を返します。記号. 文字列のメッセージの長さは、最大で 94 文字です。

これらの関数は、長さが*Numberofelements* -1 を超えた場合にエラーメッセージを切り捨てます。 *バッファー*内の結果の文字列は、常に null で終わります。

**_Strerror_s**の実際のエラー番号は、変数[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)に格納されます。 システム エラー メッセージは、エラー番号順のメッセージの配列である変数 [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) を使用してアクセスできます。 **_strerror_s**は、変数 **_sys_errlist**のインデックスとして**errno**値を使用して、適切なエラーメッセージにアクセスします。 変数[_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)の値は、 **_sys_errlist**配列内の要素の最大数として定義されます。 正確な結果を生成するには、ライブラリルーチンからエラーが返された直後に **_strerror_s**を呼び出します。 それ以外の場合、 **strerror_s**または **_strerror_s**を呼び出すと、 **errno**値が上書きされる可能性があります。

**_wcserror_s**と **__wcserror_s**は、それぞれ**strerror_s**と **_strerror_s**のワイド文字バージョンです。

これらの関数では、パラメーターの検証が行われます。 Buffer が**NULL**の場合、または size パラメーターが0の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、関数は**einval**を返し、 **errno**を**einval**に設定します。

**_strerror_s**、 **_wcserror_s**、および **__wcserror_s**は、ANSI 定義の一部ではなく、Microsoft による拡張機能です。 移植性が必要な場合は使用しないでください。ANSI 互換の場合は、代わりに**strerror_s**を使用してください。

C++ では、テンプレートのオーバーロードによってこれらの関数を簡単に使用できます。オーバーロードでは、バッファー長を自動的に推論できるため、サイズ引数を指定する必要がなくなります。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

これらの関数のデバッグライブラリバージョンは、最初にバッファーを0xFE で埋めます。 この動作を無効にするには、[_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md) を使用します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror_s**|**strerror_s**|**strerror_s**|**_wcserror_s**|

## <a name="requirements"></a>［要件］

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**strerror_s**、 **_strerror_s**|\<string.h>|
|**_wcserror_s**、 **__wcserror_s**|\<string.h> または \<wchar.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

「[perror](perror-wperror.md)」の例をご覧ください。

## <a name="see-also"></a>関連項目

[文字列操作](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
