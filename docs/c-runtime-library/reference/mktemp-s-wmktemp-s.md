---
title: _mktemp_s、_wmktemp_s
ms.date: 11/04/2016
api_name:
- _mktemp_s
- _wmktemp_s
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
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
helpviewer_keywords:
- _tmktemp_s function
- mktemp_s function
- _wmktemp_s function
- _mktemp_s function
- files [C++], temporary
- tmktemp_s function
- wmktemp_s function
- temporary files [C++]
ms.assetid: 92a7e269-7f3d-4c71-bad6-14bc827a451d
ms.openlocfilehash: 464f0dfbdb0b84e1fd29ec650e53f5c2543c4403
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624212"
---
# <a name="_mktemp_s-_wmktemp_s"></a>_mktemp_s、_wmktemp_s

一意のファイル名を作成します。 これらは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [_mktemp、_wmktemp](mktemp-wmktemp.md) です。

## <a name="syntax"></a>構文

```C
errno_t _mktemp_s(
   char *nameTemplate,
   size_t sizeInChars
);
errno_t _wmktemp_s(
   wchar_t *nameTemplate,
   size_t sizeInChars
);
template <size_t size>
errno_t _mktemp_s(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
errno_t _wmktemp_s(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>パラメーター

*nameTemplate*<br/>
ファイル名のパターン。

*sizeInChars*<br/>
**_Mktemp_s**の1バイト文字のバッファーサイズnull ターミネータを含む、 **_wmktemp_s**のワイド文字。

## <a name="return-value"></a>戻り値

これらの関数のどちらも、成功した場合は 0 を返し、エラーの場合はエラー コードを返します。

### <a name="error-conditions"></a>エラー条件

|*nameTemplate*|*sizeInChars*|戻り値|*Nametemplate*の新しい値|
|----------------|-------------------|----------------------|-------------------------------|
|**NULL**|任意|**EINVAL**|**NULL**|
|形式が正しくありません (正しい形式については、「解説」を参照してください)|任意|**EINVAL**|空の文字列|
|任意|X の数以下|**EINVAL**|空の文字列|

上記のいずれかのエラー条件が発生すると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているように、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、 **errno**は**einval**に設定され、関数は**einval**を返します。

## <a name="remarks"></a>Remarks

**_Mktemp_s**関数は、 *nametemplate*引数を変更することで一意のファイル名を作成します。これにより、呼び出しの後に、 *nametemplate*ポインターは、新しいファイル名を含む文字列を指します。 **_mktemp_s**は、現在ランタイムシステムによって使用されているマルチバイトコードページに従ってマルチバイト文字シーケンスを認識し、マルチバイト文字列の引数を適切な方法で自動的に処理します。 **_wmktemp_s**は、 **_mktemp_s**のワイド文字バージョンです。 **_wmktemp_s**の引数はワイド文字列です。 **_wmktemp_s**と **_mktemp_s**は、 **_wmktemp_s**がマルチバイト文字列を処理しない点を除いて、同じように動作します。

これらの関数のデバッグライブラリバージョンは、最初にバッファーを0xFE で埋めます。 この動作を無効にするには、[_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md) を使用します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

*Nametemplate*引数の形式は**basexxxxxx**です。ここで、 *base*は指定する新しいファイル名の一部で、各 X は **_mktemp_s**によって提供される文字のプレースホルダーです。 *Nametemplate*内の各プレースホルダー文字は、 **_mktemp_s** *を保持し、先頭*の x を英字で置き換える必要があります。 **_mktemp_s**は、次の末尾の X を5桁の値に置き換えます。この値は、呼び出し元のプロセスを識別する一意の番号、またはマルチスレッドプログラムでの呼び出し元のスレッドを示します。

**_Mktemp_s**への呼び出しが成功するたびに、 *nametemplate*が変更されます。 同じ*Nametemplate*引数を持つ同じプロセスまたはスレッドからの後続の呼び出しでは、 **_mktemp_s**は、前の呼び出しで **_mktemp_s**によって返された名前と一致するファイル名を確認します。 指定された名前のファイルが存在しない場合、 **_mktemp_s**はその名前を返します。 以前に返されたすべての名前のファイルが存在する場合、 **_mktemp_s**は、以前に返された名前で使用されていた英字を ' a ' ~ ' z ' の順に使用可能な次の小文字で置き換えることによって、新しい名前を作成します。 たとえば、 *base*がの場合は次のようになります。

> **1億**

**_mktemp_s**によって指定された5桁の値は12345で、最初に返される名前は次のようになります。

> **fna12345**

この名前を使用してファイル FNA12345 を作成しても、このファイルがまだ存在する場合、 *Nametemplate*の同じ*ベース*を持つ同じプロセスまたはスレッドから次の名前が返されます。

> **fnb12345**

FNA12345 が存在しない場合、次に返される名前はもう一度次のようになります。

> **fna12345**

**_mktemp_s**では、 *Base*と*nametemplate*の値の任意の組み合わせに対して一意のファイル名を最大26個作成できます。 したがって、FNZ12345 は、この例で使用される*base*および*nametemplate*の値に対して **_mktemp_s**が作成できる最後の一意のファイル名です。

C++ では、これらの関数の使用はテンプレートのオーバーロードによって簡素化されます。オーバーロードでは、バッファー長を自動的に推論できる (サイズの引数を指定する必要がなくなる) だけでなく、古くてセキュリティが万全ではない関数を新しく安全な関数に自動的に置き換えることができます。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

## <a name="requirements"></a>［要件］

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_mktemp_s**|\<io.h>|
|**_wmktemp_s**|\<io.h> または \<wchar.h>|

互換性について詳しくは、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```cpp
// crt_mktemp_s.cpp
/* The program uses _mktemp to create
* five unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>

char *fnTemplate = "fnXXXXXX";
char names[5][9];

int main()
{
   int i, err, sizeInChars;
   FILE *fp;

   for( i = 0; i < 5; i++ )
   {
      strcpy_s( names[i], sizeof(names[i]), fnTemplate );
      /* Get the size of the string and add one for the null terminator.*/
      sizeInChars = strnlen(names[i], 9) + 1;
      /* Attempt to find a unique filename: */
      err = _mktemp_s( names[i], sizeInChars );
      if( err != 0 )
         printf( "Problem creating the template" );
      else
      {
         if( fopen_s( &fp, names[i], "w" ) == 0 )
            printf( "Unique filename is %s\n", names[i] );
         else
            printf( "Cannot open %s\n", names[i] );
         fclose( fp );
      }
   }

   return 0;
}
```

### <a name="sample-output"></a>出力例

```Output
Unique filename is fna03188
Unique filename is fnb03188
Unique filename is fnc03188
Unique filename is fnd03188
Unique filename is fne03188
```

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
