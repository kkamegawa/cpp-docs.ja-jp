---
title: _creat、_wcreat
ms.date: 11/04/2016
api_name:
- _creat
- _wcreat
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
ms.openlocfilehash: d278bffbfdf856956a20b01da4dad2ba00952359
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938886"
---
# <a name="_creat-_wcreat"></a>_creat、_wcreat

新しいファイルを作成します。 **_creat**と **_wcreat**は非推奨とされました。代わりに[、_sopen_s、_wsopen_s](sopen-s-wsopen-s.md)を使用してください。

## <a name="syntax"></a>構文

```C
int _creat(
   const char *filename,
   int pmode
);
int _wcreat(
   const wchar_t *filename,
   int pmode
);
```

### <a name="parameters"></a>パラメーター

*ファイル名*<br/>
新しいファイルの名前。

*pmode*<br/>
アクセス許可の設定。

## <a name="return-value"></a>戻り値

これらの関数は正常に実行された場合、作成されたファイルにファイル記述子を返します。 それ以外の場合、次の表に示すように、関数は-1 を返し、 **errno**を設定します。

|**errno**の設定|説明|
|---------------------|-----------------|
|**EACCES**|*filename*には、既存の読み取り専用ファイルを指定するか、ファイルの代わりにディレクトリを指定します。|
|**EMFILE**|ファイル記述子をこれ以上使用できません。|
|**ENOENT**|指定されたファイルが見つかりませんでした。|

*Filename*が**NULL**の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は**errno**を**EINVAL**に設定し、-1 を返します。

リターン コードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Creat**関数は、新しいファイルを作成するか、既存のファイルを開き、切り捨てます。 **_wcreat**は、 **_creat**のワイド文字バージョンです。 **_wcreat**の*filename*引数はワイド文字列です。 それ以外では、 **_wcreat**と **_creat**は同じように動作します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

*Filename*によって指定されたファイルが存在しない場合は、指定されたアクセス許可の設定で新しいファイルが作成され、書き込み用に開かれます。 ファイルが既に存在し、そのアクセス許可の設定で書き込みが許可されている場合、 **_creat**はファイルを長さ0に切り詰め、前の内容を破棄して、書き込み用に開きます。 アクセス許可の設定である*pmode*は、新しく作成されたファイルにのみ適用されます。 新しいファイルは、最初に閉じた後に、指定されたアクセス許可設定を受け取ります。 整数式*pmode*には、 **_S_IWRITE**および **_S_IREAD**で定義されているマニフェスト定数の1つまたは両方が含まれています。 両方の定数が指定されている場合は、ビットごとの **&#124;** or 演算子 () と結合されます。 *Pmode*パラメーターは、次のいずれかの値に設定されます。

|値|定義|
|-----------|----------------|
|**_S_IWRITE**|書き込みが許可されます。|
|**_S_IREAD**|読み取りが許可されます。|
|**_S_IREAD**&#124; **_S_IWRITE**|読み取りと書き込みが許可されます。|

書き込みアクセス許可が与えられない場合、ファイルは読み取り専用になります。 ファイルはすべて常に読み取り可能です。書き込みのみのアクセス許可を与えることはできません。 これらのモード **_S_IWRITE**と **_S_IREAD** |  **_S_IWRITE**は同等です。 **_Creat**を使用して開いたファイルは常に互換モード ( [_sopen](sopen-wsopen.md)を参照) で**開かれます**。

**_creat**は、アクセス許可を設定する前に、現在のファイルアクセス許可マスクを*pmode*に適用します ( [_umask](umask.md)を参照)。 **_creat**は、主に以前のライブラリとの互換性のために用意されています。 *Oflag*パラメーターで **_O_CREAT**と **_O_TRUNC**を指定して **_open**を呼び出すと、 **_creat**に相当し、新しいコードに適しています。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|
|**_wcreat**|\<io.h> または \<wchar.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_creat.c
// compile with: /W3
// This program uses _creat to create
// the file (or truncate the existing file)
// named data and open it for writing.

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int fh;

   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996
   // Note: _creat is deprecated; use _sopen_s instead
   if( fh == -1 )
      perror( "Couldn't create data file" );
   else
   {
      printf( "Created data file.\n" );
      _close( fh );
   }
}
```

```Output
Created data file.
```

## <a name="see-also"></a>関連項目

[下位入出力](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup、_dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
