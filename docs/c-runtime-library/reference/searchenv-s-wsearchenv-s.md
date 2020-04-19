---
title: _searchenv_s、_wsearchenv_s
ms.date: 11/04/2016
api_name:
- _wsearchenv_s
- _searchenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _searchenv_s
- _wsearchenv_s
- wsearchenv_s
- searchenv_s
helpviewer_keywords:
- tsearchenv_s function
- files [C++], finding
- buffers [C++], buffer overruns
- environment paths, searching for files
- wsearchenv_s function
- searchenv_s function
- _tsearchenv_s function
- buffer overruns
- buffers [C++], avoiding overruns
- _wsearchenv_s function
- _searchenv_s function
- environment paths
ms.assetid: 47f9fc29-250e-4c09-b52e-9e9f0ef395ca
ms.openlocfilehash: 606215fb7a2cce7929b29e2035f8e03556ca25e0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948801"
---
# <a name="_searchenv_s-_wsearchenv_s"></a>_searchenv_s、_wsearchenv_s

環境のパスを使用してファイルを検索します。 これらの [_searchenv および _wsearchenv](searchenv-wsearchenv.md) のバージョンは、「[Security Features in the CRT](../../c-runtime-library/security-features-in-the-crt.md)」(CRT のセキュリティ機能) で説明されているように、セキュリティが強化されています。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char *pathname,
   size_t numberOfElements
);
errno_t _wsearchenv_s(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname,
   size_t numberOfElements
);
template <size_t size>
errno_t _searchenv_s(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
errno_t _wsearchenv_s(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t (&pathname)[size]
); // C++ only
```

### <a name="parameters"></a>パラメーター

*ファイル名*<br/>
検索するファイルの名前。

*varname*<br/>
検索する環境。

*pathname*<br/>
完全パスを格納するバッファー。

*numberOfElements*<br/>
*パス名*バッファーのサイズ。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。

*Filename*が空の文字列の場合、戻り値は**ENOENT**です。

### <a name="error-conditions"></a>エラー条件

|*ファイル名*|*varname*|*pathname*|*numberOfElements*|戻り値|*パス名*の内容|
|----------------|---------------|----------------|------------------------|------------------|----------------------------|
|任意|任意|**NULL**|任意|**EINVAL**|N/A|
|**NULL**|任意|任意|任意|**EINVAL**|変更されない|
|任意|任意|任意|<= 0|**EINVAL**|変更されない|

上記のいずれかのエラー条件が発生すると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように無効なパラメーター ハンドラ―が呼び出されます。 実行の継続が許可された場合、これらの関数は**errno**を**einval**に設定し、 **einval**を返します。

## <a name="remarks"></a>Remarks

**_Searchenv_s**ルーチンは、指定されたドメインでターゲットファイルを検索します。 *Varname*変数には、 **PATH**、 **LIB**、 **INCLUDE**などのディレクトリパスのリストを指定する任意の環境変数またはユーザー定義変数を指定できます。 **_Searchenv_s**では大文字と小文字が区別されるため、 *varname*は環境変数の場合と一致している必要があります。 *Varname*がプロセスの環境で定義されている環境変数の名前と一致しない場合、この関数は0を返し、 *pathname*変数は変更されません。

このルーチンは最初に現在の作業ディレクトリでファイルを検索します。 ファイルが見つからなかった場合、環境変数で指定されている次のディレクトリを検索します。 ターゲットファイルがこれらのディレクトリのいずれかにある場合は、新しく作成されたパスが*pathname*にコピーされます。 *Filename*ファイルが見つからない場合、 *pathname*には null で終わる空の文字列が含まれます。

作成されたパス名の完全な長さを格納するには、*パス*名バッファーは、少なくとも **_max_path**文字である必要があります。 そうしないと、 **_searchenv_s**が*パス名*バッファーをオーバーランし、予期しない動作が発生する可能性があります。

**_wsearchenv_s**は、 **_searchenv_s**のワイド文字バージョンです。 **_wsearchenv_s**の引数はワイド文字列です。 それ以外では、 **_wsearchenv_s**と **_searchenv_s**は同じように動作します。

C++ では、これらの関数の使用はテンプレートのオーバーロードによって簡素化されます。オーバーロードでは、バッファー長を自動的に推論できる (サイズの引数を指定する必要がなくなる) だけでなく、古くてセキュリティが万全ではない関数を新しく安全な関数に自動的に置き換えることができます。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv_s**|**_searchenv_s**|**_searchenv_s**|**_wsearchenv_s**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_searchenv_s**|\<stdlib.h>|
|**_wsearchenv_s**|\<stdlib.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_searchenv_s.c
/* This program searches for a file in
* a directory specified by an environment variable.
*/

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";
   errno_t err;

   /* Search for file in PATH environment variable: */
   err = _searchenv_s( searchfile, envvar, pathbuffer, _MAX_PATH );
   if (err != 0)
   {
      printf("Error searching the path. Error code: %d\n", err);
   }
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 2010\VC\BIN\CL.EXE
```

## <a name="see-also"></a>関連項目

[ディレクトリ制御](../../c-runtime-library/directory-control.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
[getenv、 _wgetenv](getenv-wgetenv.md)<br/>
[_putenv、_wputenv](putenv-wputenv.md)<br/>
