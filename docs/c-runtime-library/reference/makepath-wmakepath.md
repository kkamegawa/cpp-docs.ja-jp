---
title: _makepath、_wmakepath
ms.date: 11/04/2016
api_name:
- _makepath
- _wmakepath
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
ms.openlocfilehash: aafde0aeeebb7b773d3f96ca66ae65762dcdebdf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952924"
---
# <a name="_makepath-_wmakepath"></a>_makepath、_wmakepath

コンポーネントからパス名を作成します。 これらの関数のセキュリティを強化したバージョンについては、「[_makepath_s、_wmakepath_s (_makepath_s、_wmakepath_s)](makepath-s-wmakepath-s.md)」をご覧ください。

## <a name="syntax"></a>構文

```C
void _makepath(
   char *path,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
void _wmakepath(
   wchar_t *path,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
```

### <a name="parameters"></a>パラメーター

*path*<br/>
完全なパスのバッファー。

*駆動*<br/>
必要なドライブに対応する文字 (A、B など) と、省略可能である後続のコロンを含んでいます。 **_makepath**がない場合は、複合パスに自動的にコロンが挿入されます。 *ドライブ*が**NULL**であるか、空の文字列を指している場合、複合*パス*文字列にドライブ文字は表示されません。

*エイリアス*<br/>
ドライブ指定子も実際のファイル名も含まない、ディレクトリのパスを含んでいます。 末尾のスラッシュは省略可能であり、スラッシュ (/) または円記号 (\\) のいずれかまたは両方を1つの*dir*引数で使用できます。 末尾のスラッシュ (/ と \\ のいずれも) を指定していない場合は、スラッシュが自動的に挿入されます。 *Dir*が**NULL**であるか、空の文字列を指している場合、複合*パス*文字列にディレクトリパスは挿入されません。

*fname*<br/>
ファイル名拡張子がないベース ファイル名が含まれています。 *Fname*が**NULL**の場合、または空の文字列を指している場合は、複合*パス*文字列にファイル名は挿入されません。

*ext*<br/>
先行するピリオド (.) の有無を問わず、実際のファイル名拡張子が含まれています。 **_makepath**は、 *ext*に表示されない場合、自動的に期間を挿入します。*Ext*が**NULL**の場合、または空の文字列を指している場合は、複合*パス*文字列に拡張子は挿入されません。

## <a name="remarks"></a>Remarks

**_Makepath**関数は、個々のコンポーネントからの複合パス文字列を作成し、結果を*パス*に格納します。 *パス*には、ドライブ文字、ディレクトリパス、ファイル名、およびファイル名拡張子を含めることができます。 **_wmakepath**は、 **_makepath**のワイド文字バージョンです。 **_wmakepath**の引数はワイド文字列です。 それ以外では、 **_wmakepath**と **_makepath**は同じように動作します。

**セキュリティに関するメモ** null で終わる文字列をご使用ください。 バッファーオーバーランを回避するには、null で終わる文字列が*パス*バッファーのサイズを超えないようにする必要があります。 **_makepath**では、複合パス文字列の長さが **_max_path**を超えないことは保証されません。 詳しくは、「 [バッファー オーバーランの回避](/windows/win32/SecBP/avoiding-buffer-overruns)」をご覧ください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath**|**_makepath**|**_makepath**|**_wmakepath**|

*パス*引数は、完全なパスを保持するのに十分な大きさの空のバッファーを指す必要があります。 複合*パス*は、stdlib.h> で定義されている、 **_max_path**定数よりも大きくすることはできません。

Path が**NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 さらに、 **errno**は**EINVAL**に設定されています。 他のすべてのパラメーターには**NULL**値を使用できます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_makepath**|\<stdlib.h>|
|**_wmakepath**|\<stdlib.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_makepath.c
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];

   _makepath( path_buffer, "c", "\\sample\\crt\\", "makepath", "c" ); // C4996
   // Note: _makepath is deprecated; consider using _makepath_s instead
   printf( "Path created with _makepath: %s\n\n", path_buffer );
   _splitpath( path_buffer, drive, dir, fname, ext ); // C4996
   // Note: _splitpath is deprecated; consider using _splitpath_s instead
   printf( "Path extracted with _splitpath:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath: c:\sample\crt\makepath.c

Path extracted with _splitpath:
   Drive: c:
   Dir: \sample\crt\
   Filename: makepath
   Ext: .c
```

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath、_wsplitpath](splitpath-wsplitpath.md)<br/>
[_makepath_s、_wmakepath_s](makepath-s-wmakepath-s.md)<br/>
