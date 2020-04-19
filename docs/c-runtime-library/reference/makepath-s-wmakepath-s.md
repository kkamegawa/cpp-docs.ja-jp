---
title: _makepath_s、_wmakepath_s
ms.date: 11/04/2016
api_name:
- _wmakepath_s
- _makepath_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wmakepath_s
- makepath_s
- _makepath_s
- wmakepath_s
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
ms.openlocfilehash: 7bd85734e71120a214d652048c02c176728474b2
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624353"
---
# <a name="_makepath_s-_wmakepath_s"></a>_makepath_s、_wmakepath_s

コンポーネントからパス名を作成します。 これらは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [_makepath、_wmakepath](makepath-wmakepath.md) です。

## <a name="syntax"></a>構文

```C
errno_t _makepath_s(
   char *path,
   size_t sizeInBytes,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
errno_t _wmakepath_s(
   wchar_t *path,
   size_t sizeInWords,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
template <size_t size>
errno_t _makepath_s(
   char (&path)[size],
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
); // C++ only
template <size_t size>
errno_t _wmakepath_s(
   wchar_t (&path)[size],
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
); // C++ only
```

### <a name="parameters"></a>パラメーター

*path*<br/>
完全なパスのバッファー。

*sizeInWords*<br/>
バッファーのサイズ (単語単位)。

*sizeInBytes*<br/>
バッファーのサイズ (バイト単位)。

*駆動*<br/>
必要なドライブに対応する文字 (A、B など) と、この後に続くオプションのコロンを含んでいます。 **_makepath_s**がない場合は、複合パスに自動的にコロンが挿入されます。 *ドライブ*が**NULL**であるか、空の文字列を指している場合、複合*パス*文字列にドライブ文字は表示されません。

*エイリアス*<br/>
ドライブ指定子も実際のファイル名も含まない、ディレクトリのパスを含んでいます。 末尾のスラッシュは省略可能であり、スラッシュ (/) または円記号 (\\) のいずれかまたは両方を1つの*dir*引数で使用できます。 末尾のスラッシュ (/ と \\ のいずれも) を指定していない場合は、スラッシュが自動的に挿入されます。 *Dir*が**NULL**であるか、空の文字列を指している場合、複合*パス*文字列にディレクトリパスは挿入されません。

*氏名*<br/>
ファイル名拡張子を付けないベース ファイル名が含まれています。 *Fname*が**NULL**の場合、または空の文字列を指している場合は、複合*パス*文字列にファイル名は挿入されません。

*ext*<br/>
先行するピリオド (.) の有無を問わず、実際のファイル名拡張子が含まれています。 **_makepath_s**は、 *ext*に表示されない場合、自動的に期間を挿入します。*Ext*が**NULL**の場合、または空の文字列を指している場合は、複合*パス*文字列に拡張子は挿入されません。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。

### <a name="error-conditions"></a>エラー条件

|*path*|*Sizeinwords* / *sizeinwords*|Return|*パス*の内容|
|------------|------------------------------------|------------|------------------------|
|**NULL**|任意|**EINVAL**|変更されない|
|任意|<= 0|**EINVAL**|変更されない|

上記のいずれかのエラー条件が発生すると、これらの関数は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーター ハンドラーを呼び出します。 実行の継続が許可された場合、 **errno**は**einval**に設定され、関数は**einval**を返します。 パラメーター *drive*、 *fname*、および*ext*には**NULL**を指定できます。これらのパラメーターが null ポインターまたは空の文字列である場合の動作の詳細については、「解説」を参照してください。

## <a name="remarks"></a>Remarks

**_Makepath_s**関数は、個々のコンポーネントからの複合パス文字列を作成し、結果を*パス*に格納します。 *パス*には、ドライブ文字、ディレクトリパス、ファイル名、およびファイル名拡張子を含めることができます。 **_wmakepath_s**は、 **_makepath_s**のワイド文字バージョンです。 **_wmakepath_s**の引数はワイド文字列です。 それ以外では、 **_wmakepath_s**と **_makepath_s**は同じように動作します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

*パス*引数は、完全なパスを保持するのに十分な大きさの空のバッファーを指す必要があります。 複合*パス*は、stdlib.h> で定義されている、 **_max_path**定数よりも大きくすることはできません。

Path が**NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 さらに、 **errno**は**EINVAL**に設定されています。 他のすべてのパラメーターには**NULL**値を使用できます。

C++ では、これらの関数の使用はテンプレートのオーバーロードによって簡素化されます。オーバーロードでは、バッファー長を自動的に推論できる (サイズの引数を指定する必要がなくなる) だけでなく、古くてセキュリティが万全ではない関数を新しく安全な関数に自動的に置き換えることができます。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

これらの関数のデバッグライブラリバージョンは、最初にバッファーを0xFE で埋めます。 この動作を無効にするには、[_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md) を使用します。

## <a name="requirements"></a>［要件］

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_makepath_s**|\<stdlib.h>|
|**_wmakepath_s**|\<stdlib.h> または \<wchar.h>|

互換性について詳しくは、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_makepath_s.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];
   errno_t err;

   err = _makepath_s( path_buffer, _MAX_PATH, "c", "\\sample\\crt\\",
                      "crt_makepath_s", "c" );
   if (err != 0)
   {
      printf("Error creating path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path created with _makepath_s: %s\n\n", path_buffer );
   err = _splitpath_s( path_buffer, drive, _MAX_DRIVE, dir, _MAX_DIR, fname,
                       _MAX_FNAME, ext, _MAX_EXT );
   if (err != 0)
   {
      printf("Error splitting the path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path extracted with _splitpath_s:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c

Path extracted with _splitpath_s:
   Drive: c:
   Dir: \sample\crt\
   Filename: crt_makepath_s
   Ext: .c
```

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
[_makepath、_wmakepath](makepath-wmakepath.md)<br/>
