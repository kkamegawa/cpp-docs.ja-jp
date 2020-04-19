---
title: _open、_wopen
ms.date: 11/04/2016
api_name:
- _open
- _wopen
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
- _wopen
- _topen
- _open
helpviewer_keywords:
- opening files, for file I/O
- topen function
- _open function
- _topen function
- _wopen function
- files [C++], opening
- wopen function
- open function
ms.assetid: 13f6a0c3-d1aa-450d-a7aa-74abc91b163e
ms.openlocfilehash: aad98844f4d9faf57c7bc5051eebabad09b860a4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951174"
---
# <a name="_open-_wopen"></a>_open、_wopen

ファイルを開きます。 セキュリティが強化されたバージョンを使用できるようになったため、これらの関数は非推奨とされています。「[_sopen_s、_wsopen_s](sopen-s-wsopen-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _open(
   const char *filename,
   int oflag [,
   int pmode]
);
int _wopen(
   const wchar_t *filename,
   int oflag [,
   int pmode]
);
```

### <a name="parameters"></a>パラメーター

*ファイル名*<br/>
ファイル名。

*oflag*<br/>
許可される操作の種類。

*pmode*<br/>
アクセス許可モード。

## <a name="return-value"></a>戻り値

これらの各関数は、開かれたファイルのファイル記述子を返します。 戻り値-1 はエラーを示します。その場合、 **errno**は次のいずれかの値に設定されます。

|errno の値|条件|
|-|-|
| **EACCES** | 読み取り専用ファイルを書き込み用に開こうとしたか、指定された操作がファイルの共有モードで許可されていないか、指定されたパスがディレクトリです。 |
| **EEXIST** | **_O_CREAT**および **_O_EXCL**フラグが指定されていますが、 *filename*は既に存在します。 |
| **EINVAL** | *Oflag*または*pmode*引数が無効です。 |
| **EMFILE** | ファイル記述子をこれ以上使用できません (開かれているファイルが多すぎます)。 |
| **ENOENT** | ファイルまたはパスが見つかりません。 |

これらのリターン コードとその他のリターン コードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Open**関数は、 *filename*によって指定されたファイルを開き、 *oflag*で指定されているように読み取りまたは書き込み用に準備します。 **_wopen**は、 **_open**のワイド文字バージョンです。 **_wopen**の*filename*引数はワイド文字列です。 それ以外では、 **_wopen**と **_open**は同じように動作します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_topen**|**_open**|**_open**|**_wopen**|

*oflag*は、> で\<定義されている次のマニフェスト定数または定数の組み合わせの1つ以上を形成する整数式です。

|*oflag*定数|動作|
|-|-|
| **_O_APPEND** | 書き込み操作の前に、毎回、ファイル ポインターをファイルの末尾に移動します。 |
| **_O_BINARY** | ファイルをバイナリ (無変換) モードで開きます。 (バイナリ モードの詳細については、「[fopen](fopen-wfopen.md)」を参照してください)。 |
| **_O_CREAT** | ファイルを作成し、書き込み用に開きます。 *Filename*によって指定されたファイルが存在する場合は効果がありません。 **_O_CREAT**を指定する場合は、 *pmode*引数が必要です。 |
| **_O_CREAT**&#124; **_O_SHORT_LIVED** | ファイルを一時ファイルとして作成し、可能な場合は、ディスクにフラッシュしません。 **_O_CREAT**を指定する場合は、 *pmode*引数が必要です。 |
| **_O_CREAT** &#124; **_O_TEMPORARY** | ファイルを一時ファイルとして作成します。最後のファイル記述子が閉じられると、ファイルは削除されます。 **_O_CREAT**を指定する場合は、 *pmode*引数が必要です。 |
| **_O_CREAT** &#124; ` _O_EXCL` | *Filename*によって指定されたファイルが存在する場合、エラー値を返します。 **_O_CREAT**と共に使用する場合にのみ適用されます。 |
| **_O_NOINHERIT** | 共有ファイル記述子の作成を禁止します。 |
| **_O_RANDOM** | キャッシュがディスクからのランダム アクセスに最適化されるように指定します。ただし、ランダム アクセスに限定されるわけではありません。 |
| **_O_RDONLY** | 読み取り専用でファイルを開きます。 **_O_RDWR**または **_O_WRONLY**では指定できません。 |
| **_O_RDWR** | 読み取りと書き込みの両方用にファイルを開きます。 **_O_RDONLY**または **_O_WRONLY**では指定できません。 |
| **_O_SEQUENTIAL** | キャッシュがディスクからのシーケンシャル アクセスに最適化されるように指定します。ただし、シーケンシャル アクセスに限定されるわけではありません。 |
| **_O_TEXT** | ファイルをテキスト (変換) モードで開きます。 (詳細については、「[テキスト モードとバイナリ モードのファイル入出力](../../c-runtime-library/text-and-binary-mode-file-i-o.md)」および「[fopen](fopen-wfopen.md)」を参照してください。) |
| **_O_TRUNC** | ファイルを開き、長さゼロに切り詰めます。ファイルに書き込みアクセス許可が必要です。 **_O_RDONLY**と共に指定することはできません。 **_O_TRUNC** 併用 **_O_CREAT** 既存のファイルを開くか、ファイルを作成します。 **注:** **_O_TRUNC**フラグは、指定されたファイルの内容を破棄します。 |
| **_O_WRONLY** | 書き込み専用でファイルを開きます。 **_O_RDONLY**または **_O_RDWR**では指定できません。 |
| **_O_U16TEXT** | Unicode UTF-16 モードでファイルを開きます。 |
| **_O_U8TEXT** | Unicode UTF-8 モードでファイルを開きます。 |
| **_O_WTEXT** | Unicode モードでファイルを開きます。 |

ファイルアクセスモードを指定するには、 **_O_RDONLY**、 **_O_RDWR**、または **_O_WRONLY**のいずれかを指定する必要があります。 アクセス モードに既定値はありません。

**_O_WTEXT**を使用して読み取り用にファイルを開くと、 **_open**によってファイルの先頭が読み取られ、バイトオーダーマーク (BOM) がチェックされます。 BOM がある場合、ファイルは BOM に応じて UTF-8 または UTF-16LE として扱われます。 BOM がない場合、ファイルは ANSI として扱われます。 **_O_WTEXT**を使用してファイルを書き込み用に開くと、utf-16 が使用されます。 以前の設定またはバイトオーダーマークに関係なく、 **_O_U8TEXT**を使用すると、ファイルは常に utf-8 として開かれます。 **_O_U16TEXT**が使用されている場合、ファイルは常に utf-16 として開かれます。

**_O_WTEXT**、 **_O_U8TEXT**、または **_O_U16TEXT**を使用してファイルが Unicode モードで開かれると、入力関数は、ファイルから読み取られたデータを、 **wchar_t**型として格納された utf-16 データに変換します。 Unicode モードで開かれたファイルに書き込む関数は、 **wchar_t**型として格納された utf-16 データを含むバッファーを想定します。 ファイルが UTF-8 としてエンコードされている場合、UTF-16 データは書き込まれるときに UTF-8 に変換され、ファイルの UTF-8 でエンコードされた内容は読み取られるときに UTF-16 に変換されます。 Unicode モードで奇数バイトの読み取りまたは書き込みを試みると、パラメーター検証エラーが発生します。 UTF-8 としてプログラムに格納されたデータを読み取るか書き込む場合は、Unicode モードではなくテキストまたはバイナリ ファイル モードを使用します。 必要なエンコード変換は各自が行う必要があります。

**_O_WRONLY** _O_APPEND | (APPEND mode) と _O_WTEXT、_O_U16TEXT、または **_O_U8TEXT**を使用して _open が呼び出された場合、まず読み取りと書き込みのためにファイルを開き、BOM を読み取り、次に再オープンしようとします。書き込みのみ。 読み取りおよび書き込み用にファイルを開くのに失敗した場合、書き込み専用でファイルを開き、Unicode モード設定の既定値を使用します。

フォームに 2 つ以上のマニフェスト定数を使用する場合、 *oflag*引数、定数はビットごとの OR 演算子で組み合わされます ( **&#124;** )。 バイナリ モードとテキスト モードの詳細については、「[テキスト モードとバイナリ モードのファイル入出力](../../c-runtime-library/text-and-binary-mode-file-i-o.md)」を参照してください。

**_O_CREAT**が指定されている場合にのみ、 *pmode*引数が必要です。 ファイルが既に存在する場合、 *pmode*は無視されます。 それ以外の場合、 *pmode*では、ファイルのアクセス許可の設定を指定します。この設定は、新しいファイルが最初に閉じられたときに設定されます。 **_open**アクセス許可が設定される前に、現在のファイルアクセス許可マスクを*pmode*に適用します。 (詳細については、「 [_umask](umask.md)」を参照してください)。*pmode*は、次のマニフェスト定数のいずれかまたは両方を含む整数式です。 > \<で定義されています。

|*pmode*|説明|
|-|-|
| **_S_IREAD** | 読み取りのみが許可されます。 |
| **_S_IWRITE** | 書き込みが許可されます。 (実際には、読み取りと書き込みが許可されます)。 |
| **_S_IREAD**&#124; **_S_IWRITE** | 読み取りと書き込みが許可されます。 |

ビットごとの OR 演算子で参加している両方の定数を指定する場合 ( **&#124;** )。 Windows では、すべてのファイルは読み取り可能です。書き込み専用のアクセス許可は使用できません。 そのため、モード **_S_IWRITE**と **_S_IREAD** |  **_S_IWRITE**は同等です。

**_S_IREAD**と **_S_IWRITE**の一部の組み合わせ以外の値が、別のオペレーティングシステムで有効な*pmode*を指定する場合でも、または、許可された*oflag*値以外の値*がの場合*は、指定した場合、関数はデバッグモードでアサーションを生成し、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、この関数は-1 を返し、 **errno**を**EINVAL**に設定します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_open**|\<io.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>|
|**_wopen**|\<io.h> または \<wchar.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>|

**_open**と **_wopen**は Microsoft の拡張機能です。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_open.c
// compile with: /W3
/* This program uses _open to open a file
* named CRT_OPEN.C for input and a file named CRT_OPEN.OUT
* for output. The files are then closed.
*/
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int fh1, fh2;

   fh1 = _open( "CRT_OPEN.C", _O_RDONLY ); // C4996
   // Note: _open is deprecated; consider using _sopen_s instead
   if( fh1 == -1 )
      perror( "Open failed on input file" );
   else
   {
      printf( "Open succeeded on input file\n" );
      _close( fh1 );
   }

   fh2 = _open( "CRT_OPEN.OUT", _O_WRONLY | _O_CREAT, _S_IREAD |
                            _S_IWRITE ); // C4996
   if( fh2 == -1 )
      perror( "Open failed on output file" );
   else
   {
      printf( "Open succeeded on output file\n" );
      _close( fh2 );
   }
}
```

### <a name="output"></a>Output

```Output
Open succeeded on input file
Open succeeded on output file
```

## <a name="see-also"></a>関連項目

[下位入出力](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_dup、_dup2](dup-dup2.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
