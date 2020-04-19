---
title: _tempnam、_wtempnam、tmpnam、_wtmpnam
ms.date: 11/04/2016
api_name:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
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
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
helpviewer_keywords:
- wtempnam function
- file names [C++], creating temporary
- _tempnam function
- ttmpnam function
- tmpnam function
- tempnam function
- wtmpnam function
- temporary files, creating
- file names [C++], temporary
- _ttmpnam function
- _wtmpnam function
- _wtempnam function
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
ms.openlocfilehash: 9fd1eb9f2f718afec5b7d5555145fcd7e5cc17cf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957517"
---
# <a name="_tempnam-_wtempnam-tmpnam-_wtmpnam"></a>_tempnam、_wtempnam、tmpnam、_wtmpnam

一時ファイルの作成に使用できる名前を生成します。 これらの関数のセキュリティを強化したバージョンを使用できます。「[tmpnam_s、_wtmpnam_s](tmpnam-s-wtmpnam-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
char *_tempnam(
   const char *dir,
   const char *prefix
);
wchar_t *_wtempnam(
   const wchar_t *dir,
   const wchar_t *prefix
);
char *tmpnam(
   char *str
);
wchar_t *_wtmpnam(
   wchar_t *str
);
```

### <a name="parameters"></a>パラメーター

*prefix*<br/>
**_Tempnam**によって返される名前の前に付加される文字列。

*エイリアス*<br/>
TMP 環境変数がない場合、または TMP が有効なディレクトリではない場合にファイル名で使用されるパス。

*str*<br/>
生成された名前を保持し、関数によって返される名前と同じになるポインター。 これは、生成された名前を保存する便利な方法です。

## <a name="return-value"></a>戻り値

これらの各関数は、生成された名前へのポインター、またはエラーが発生した場合は**NULL**を返します。 **TMP_MAX**を超える場合、エラーが発生することがあります (「STDIO」を参照してください)。H) **tmpnam**を使用してを呼び出します。また、 **_tempnam**を使用し、TMP 環境変数と*dir*パラメーターに無効なディレクトリ名が指定されている場合は、を呼び出します。

> [!NOTE]
> **Tmpnam**と **_wtmpnam**は、内部の静的バッファーを指すポインターを返します。 これらのポインターの割り当てを解除するために [free](free.md) を呼び出さないでください。 **_tempnam**および **_wtempnam**によって割り当てられたポインターに対しては、 **free**を呼び出す必要があります。

## <a name="remarks"></a>Remarks

これらの各関数は、現在存在しないファイルの名前を返します。 **tmpnam**は、 [GetTempPathW](/windows/win32/api/fileapi/nf-fileapi-gettemppathw)によって返される指定された Windows 一時ディレクトリ内で一意の名前を返します。 tempnam は、指定されたディレクトリ以外のディレクトリに一意の名前を生成します。  **\_** ファイル名の前に円記号が付いていてパス情報がない場合 (\fname21 など)、その名前は現在の作業ディレクトリに対して有効なので注意してください。

**Tmpnam**では、この生成されたファイル名を*str*に格納できます。 *Str*が**NULL**の場合、 **tmpnam**は、結果を内部の静的バッファーに残します。 したがって後続の呼び出しは、この値を破棄します。 **Tmpnam**によって生成される名前は、プログラムによって生成されるファイル名で構成され、 **tmpnam**の最初の呼び出しの後に、ベース 32 (1-) の連続する番号のファイル拡張子 (STDIO の**TMP_MAX**時) で構成されます。H は 32767)。

**_tempnam**は、次の規則で選択されたディレクトリに対して一意のファイル名を生成します。

- TMP 環境変数が定義され、有効なディレクトリ名に設定された場合は、TMP で指定したディレクトリに対して一意のファイル名が生成されます。

- TMP 環境変数が定義されていない場合、または存在しないディレクトリの名前に設定されている場合、 **_tempnam**は一意の名前を生成するパスとして*dir*パラメーターを使用します。

- TMP 環境変数が定義されていない場合、または存在しないディレクトリの名前に設定されている場合、および*dir*が**NULL**であるか、または存在しないディレクトリの名前に設定されている場合、 **_tempnam**は現在の作業ディレクトリを使用して gene します。一意の名前を評価します。 現在、TMP と*dir*の両方で、存在しないディレクトリの名前が指定されている場合、 **_tempnam**関数の呼び出しは失敗します。

**_Tempnam**によって返される名前は、*プレフィックス*と連続番号を連結したものになります。これは、指定されたディレクトリに対して一意のファイル名を作成するために使用されます。 **_tempnam**では、拡張子のないファイル名が生成されます。 **_tempnam**は[malloc](malloc.md)を使用して、ファイル名にスペースを割り当てます。プログラムは、不要になったときにこの領域を解放する役割を担います。

**_tempnam**と**tmpnam**は、オペレーティングシステムから取得した OEM コードページに従ってマルチバイト文字のシーケンスを認識し、マルチバイト文字列の引数を適切な方法で自動的に処理します。 **_wtempnam**は、 **_tempnam**のワイド文字バージョンです。 **_wtempnam**の引数と戻り値はワイド文字列です。 **_wtempnam**と **_tempnam**は、 **_wtempnam**がマルチバイト文字列を処理しない点を除いて同じように動作します。 **_wtmpnam**は、 **tmpnam**のワイド文字バージョンです。 **_wtmpnam**の引数と戻り値はワイド文字列です。 **_wtmpnam**と**tmpnam**は、 **_wtmpnam**がマルチバイト文字列を処理しない点を除いて、同じように動作します。

**_Debug**と **_CRTDBG_MAP_ALLOC**が定義されている場合、 **_tempnam**と **_wtempnam**は[_tempnam_dbg と _wtempnam_dbg](tempnam-dbg-wtempnam-dbg.md)の呼び出しに置き換えられます。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam**|**tmpnam**|**tmpnam**|**_wtmpnam**|
|**_ttempnam**|**_tempnam**|**_tempnam**|**_wtempnam**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_tempnam**|\<stdio.h>|
|**_wtempnam**、 **_wtmpnam**|\<stdio.h> または \<wchar.h>|
|**tmpnam**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_tempnam.c
// compile with: /W3
// This program uses tmpnam to create a unique filename in the
// temporary directory, and _tempname to create a unique filename
// in C:\\tmp.

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
   char * name1 = NULL;
   char * name2 = NULL;
   char * name3 = NULL;

   // Create a temporary filename for the current working directory:
   if ((name1 = tmpnam(NULL)) != NULL) { // C4996
   // Note: tmpnam is deprecated; consider using tmpnam_s instead
      printf("%s is safe to use as a temporary file.\n", name1);
   } else {
      printf("Cannot create a unique filename\n");
   }

   // Create a temporary filename in temporary directory with the
   // prefix "stq". The actual destination directory may vary
   // depending on the state of the TMP environment variable and
   // the global variable P_tmpdir.

   if ((name2 = _tempnam("c:\\tmp", "stq")) != NULL) {
      printf("%s is safe to use as a temporary file.\n", name2);
   } else {
      printf("Cannot create a unique filename\n");
   }

   // When name2 is no longer needed:
   if (name2) {
      free(name2);
   }

   // Unset TMP environment variable, then create a temporary filename in C:\tmp.
   if (_putenv("TMP=") != 0) {
      printf("Could not remove TMP environment variable.\n");
   }

   // With TMP unset, we will use C:\tmp as the temporary directory.
   // Create a temporary filename in C:\tmp with prefix "stq".
   if ((name3 = _tempnam("c:\\tmp", "stq")) != NULL) {
      printf("%s is safe to use as a temporary file.\n", name3);
   }
   else {
      printf("Cannot create a unique filename\n");
   }

   // When name3 is no longer needed:
   if (name3) {
      free(name3);
   }

   return 0;
}
```

```Output
C:\Users\LocalUser\AppData\Local\Temp\sriw.0 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\stq2 is safe to use as a temporary file.
c:\tmp\stq3 is safe to use as a temporary file.
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile](tmpfile.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
