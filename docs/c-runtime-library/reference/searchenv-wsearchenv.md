---
title: _searchenv、_wsearchenv
ms.date: 11/04/2016
api_name:
- _searchenv
- _wsearchenv
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
- _wsearchenv
- _tsearchenv
- wsearchenv
- _searchenv
- searchenv
helpviewer_keywords:
- _wsearchenv function
- files [C++], finding
- _searchenv function
- tsearchenv function
- environment paths, searching for files
- _tsearchenv function
- wsearchenv function
- searchenv function
- environment paths
ms.assetid: 9c944a27-d326-409b-aee6-410e8762d9d3
ms.openlocfilehash: a3139ab87335ba581ef65707602c5da1819ce4a1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948767"
---
# <a name="_searchenv-_wsearchenv"></a>_searchenv、_wsearchenv

ファイルを検索するために環境パスを使用します。 これらの関数にはセキュリティが強化されたバージョンがあります。「[_searchenv_s、_wsearchenv_s](searchenv-s-wsearchenv-s.md)」をご覧ください。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
void _searchenv(
   const char *filename,
   const char *varname,
   char *pathname
);
void _wsearchenv(
   const wchar_t *filename,
   const wchar_t *varname,
   wchar_t *pathname
);
template <size_t size>
void _searchenv(
   const char *filename,
   const char *varname,
   char (&pathname)[size]
); // C++ only
template <size_t size>
void _wsearchenv(
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

## <a name="remarks"></a>Remarks

**_Searchenv**ルーチンは、指定されたドメインでターゲットファイルを検索します。 *Varname*変数には、ディレクトリパスの一覧を指定する任意の環境またはユーザー定義変数 ( **PATH**、 **LIB**、 **INCLUDE**など) を指定できます。 **_Searchenv**では大文字と小文字が区別されるため、 *varname*は環境変数の場合と一致している必要があります。

このルーチンは最初に現在の作業ディレクトリでファイルを検索します。 ファイルが見つからなかった場合、環境変数で指定されているディレクトリを検索します。 ターゲットファイルがこれらのディレクトリのいずれかにある場合は、新しく作成されたパスが*pathname*にコピーされます。 *Filename*ファイルが見つからない場合、 *pathname*には null で終わる空の文字列が含まれます。

作成されたパス名の完全な長さを格納するには、*パス*名バッファーは、少なくとも **_max_path**文字である必要があります。 それ以外の場合、 **_searchenv**は*パス名*バッファーをオーバーランし、予期しない動作を引き起こす可能性があります。

**_wsearchenv**は **_searchenv**のワイド文字バージョンであり、 **_wsearchenv**の引数はワイド文字列です。 それ以外では、 **_wsearchenv**と **_searchenv**は同じように動作します。

*Filename*が空の文字列の場合、これらの関数は**ENOENT**を返します。

*Filename*または*pathname*が**NULL**ポインターの場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は-1 を返し、 **errno**を**EINVAL**に設定します。

**Errno**とエラーコードの詳細については、「 [errno 定数](../../c-runtime-library/errno-constants.md)」を参照してください。

C++ では、これらの関数にテンプレートのオーバーロードがあります。このオーバーロードは、これらの関数に対応するセキュリティを強化された新しい関数を呼び出します。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsearchenv**|**_searchenv**|**_searchenv**|**_wsearchenv**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_searchenv**|\<stdlib.h>|
|**_wsearchenv**|\<stdlib.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_searchenv.c
// compile with: /W3
// This program searches for a file in
// a directory that's specified by an environment variable.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char pathbuffer[_MAX_PATH];
   char searchfile[] = "CL.EXE";
   char envvar[] = "PATH";

   // Search for file in PATH environment variable:
   _searchenv( searchfile, envvar, pathbuffer ); // C4996
   // Note: _searchenv is deprecated; consider using _searchenv_s
   if( *pathbuffer != '\0' )
      printf( "Path for %s:\n%s\n", searchfile, pathbuffer );
   else
      printf( "%s not found\n", searchfile );
}
```

```Output
Path for CL.EXE:
C:\Program Files\Microsoft Visual Studio 8\VC\BIN\CL.EXE
```

## <a name="see-also"></a>関連項目

[ディレクトリ制御](../../c-runtime-library/directory-control.md)<br/>
[getenv、 _wgetenv](getenv-wgetenv.md)<br/>
[_putenv、_wputenv](putenv-wputenv.md)<br/>
[_searchenv_s、_wsearchenv_s](searchenv-s-wsearchenv-s.md)<br/>
