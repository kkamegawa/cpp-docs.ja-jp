---
title: _fullpath、_wfullpath
ms.date: 11/04/2016
api_name:
- _fullpath
- _wfullpath
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
- wfullpath
- fullpath
- _wfullpath
- _fullpath
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
ms.openlocfilehash: 30e62716c496ebb1a39b53a420f372a6e743c2c0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956265"
---
# <a name="_fullpath-_wfullpath"></a>_fullpath、_wfullpath

指定された相対パス名の絶対または完全パス名を作成します。

## <a name="syntax"></a>構文

```C
char *_fullpath(
   char *absPath,
   const char *relPath,
   size_t maxLength
);
wchar_t *_wfullpath(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength
);
```

### <a name="parameters"></a>パラメーター

*absPath*<br/>
絶対パス名または完全パス名を格納しているバッファーへのポインター、または**NULL**。

*relPath*<br/>
相対パス名。

*maxLength*<br/>
絶対パス名バッファー (*Abspath*) の最大長。 この長さは、 **_wfullpath**の場合はバイト単位**ですが、** の場合はワイド文字 (**wchar_t**) になります。

## <a name="return-value"></a>戻り値

これらの各関数は、絶対パス名 (*Abspath*) を格納しているバッファーへのポインターを返します。 エラーが発生した場合 (たとえば、 *relPath*で渡された値に有効でないドライブ文字が含まれている場合や見つからない場合、または作成された絶対パス名 (*abspath*) の長さが*maxLength*を超える場合)、関数はを返します。**NULL**。

## <a name="remarks"></a>Remarks

**Fullpath**関数は、 *relPath*の相対パス名を完全修飾パスまたは絶対パスに拡張し、この名前を*abspath*に格納します。 *Abspath*が**NULL**の場合、 **malloc**は、パス名を保持するのに十分な長さのバッファーを割り当てるために使用されます。 このバッファーを解放するのは、呼び出し元の役目です。 相対パス名は、現在の場所から別の場所 (現在の作業ディレクトリ "." など) にパスを指定します。 絶対パス名は、ファイル システムのルートから目的の位置に到達するために必要なパス全体を示す相対パス名の拡張です。 **_Makepath**とは異なり、"./" または "." が含まれている相対パス (*relPath*) の絶対パス名を取得するために、 **[fullpath]** を使用できます。/"という名前です。

たとえば、C ランタイム ルーチンを使用するには、アプリケーションに、ルーチンの宣言を含むヘッダー ファイルを含める必要があります。 各ヘッダー ファイルは、(アプリケーションの作業ディレクトリから) 相対的な方法でファイルの場所を参照するステートメントを含んでいます。

```C
#include <stdlib.h>
```

ファイルの絶対パス (実際のファイル システムの場所) は次のようになります。

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

現在使用中のマルチバイトコードページに従ってマルチバイト文字シーケンスを認識し、マルチバイト文字列の引数を適切に自動的に処理します **(_s)** 。 **_wfullpath**のワイド文字バージョン**です。** **_wfullpath**への文字列引数はワイド文字列です。 **_wfullpath**と**fullpath**は、 **_wfullpath**がマルチバイト文字列を処理しない点を除いて、同じように動作します。

**_Debug**と **_CRTDBG_MAP_ALLOC**の両方が定義されている場合、 **_wfullpath** **への**呼び出しは **_fullpath_dbg**および **_wfullpath_dbg**の呼び出しに置き換えられ、メモリ割り当てをデバッグできるようになります。 詳細については、「[_fullpath_dbg、_wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md)」を参照してください。

この関数は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、" *maxlen* " が0以下の場合に、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、この関数は**errno**を**EINVAL**に設定し、 **NULL**を返します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

*Abspath*バッファーが**NULL**の場合、 **(_s)** は[malloc](malloc.md)を呼び出してバッファーを割り当て、 *maxLength*引数を無視します。 このバッファーを ([free](free.md) を使用して) 適切に解放するのは、呼び出し元の責任です。 *RelPath*引数にディスクドライブが指定されている場合、このドライブの現在のディレクトリがパスと結合されます。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**_fullpath**|\<stdlib.h>|
|**_wfullpath**|\<stdlib.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_fullpath.c
// This program demonstrates how _fullpath
// creates a full path from a partial path.

#include <stdio.h>
#include <conio.h>
#include <stdlib.h>
#include <direct.h>

void PrintFullPath( char * partialPath )
{
   char full[_MAX_PATH];
   if( _fullpath( full, partialPath, _MAX_PATH ) != NULL )
      printf( "Full path is: %s\n", full );
   else
      printf( "Invalid path\n" );
}

int main( void )
{
   PrintFullPath( "test" );
   PrintFullPath( "\\test" );
   PrintFullPath( "..\\test" );
}
```

```Output
Full path is: C:\Documents and Settings\user\My Documents\test
Full path is: C:\test
Full path is: C:\Documents and Settings\user\test
```

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd、_wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[_makepath、_wmakepath](makepath-wmakepath.md)<br/>
[_splitpath、_wsplitpath](splitpath-wsplitpath.md)<br/>
