---
title: _sopen、_wsopen
ms.date: 11/04/2016
api_name:
- _sopen
- _wsopen
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
- _wsopen
- wsopen
- _sopen
- _tsopen
helpviewer_keywords:
- sopen function
- sharing files
- opening files, for sharing
- _sopen function
- wsopen function
- files [C++], opening
- files [C++], sharing
- _wsopen function
ms.assetid: a9d4cccf-06e9-414d-96fa-453fca88cc1f
ms.openlocfilehash: d337b2353ad15eade15235b4b5217a3b881bab1d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948058"
---
# <a name="_sopen-_wsopen"></a>_sopen、_wsopen

共有用にファイルを開きます。 これらの関数のセキュリティを強化したバージョンについては[、「_sopen_s、_wsopen_s」を](sopen-s-wsopen-s.md)参照してください。

## <a name="syntax"></a>構文

```C
int _sopen(
   const char *filename,
   int oflag,
   int shflag [,
   int pmode ]
);
int _wsopen(
   const wchar_t *filename,
   int oflag,
   int shflag [,
   int pmode ]
);
```

### <a name="parameters"></a>パラメーター

*ファイル名*<br/>
ファイル名。

*oflag*<br/>
許可される操作の種類。

*shflag*<br/>
許可される共有の種類。

*pmode*<br/>
アクセス許可の設定。

## <a name="return-value"></a>戻り値

これらの各関数は、開かれたファイルのファイル記述子を返します。

*Filename*または*oflag*が**NULL**ポインターの場合、または*oflag*または*shflag*が有効な値の範囲内にない場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は-1 を返し、 **errno**を次のいずれかの値に設定します。

|errno の値|条件|
|-|-|
| **EACCES** | 指定されたパスがディレクトリであるか、またはファイルが読み取り専用ですが、書き込み用に開く操作が試行されました。 |
| **EEXIST** | **_O_CREAT**および **_O_EXCL**フラグが指定されましたが、 *filename*は既に存在します。 |
| **EINVAL** | *Oflag*または*shflag*引数が無効です。 |
| **EMFILE** | ファイル記述子をこれ以上使用できません。 |
| **ENOENT** | ファイルまたはパスが見つかりません。 |

リターン コードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Sopen**関数は、 *filename*で指定されたファイルを開き、 *oflag*および*shflag*で定義されている共有の読み取りまたは書き込み用にファイルを準備します。 **_sopen**のワイド文字バージョンを**開く (_c)** *ファイル名*に対する filename 引数は、ワイド**文字列です。** それ**以外の場合、** **_sopen**は同じように動作します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen**|**_sopen**|**_sopen**|**_wsopen**|

*Oflag* > で\<定義されている次のマニフェスト定数の1つ以上を組み合わせることによって、整数式が形成されます。 2つ以上の定数が引数*oflag*を形成する場合、それらはビットごとの or 演算子 **&#124;** () と組み合わされます。

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

**_O_WTEXT**、 **_O_U8TEXT**、または **_O_U16TEXT**を使用してファイルが Unicode モードで開かれると、入力関数は、ファイルから読み取られたデータを、 **wchar_t**型として格納された utf-16 データに変換します。 Unicode モードで開かれたファイルに書き込む関数は、 **wchar_t**型として格納された utf-16 データを含むバッファーを想定します。 ファイルが UTF-8 としてエンコードされている場合、UTF-16 データは書き込まれるときに UTF-8 に変換され、ファイルの UTF-8 でエンコードされた内容は読み取られるときに UTF-16 に変換されます。 Unicode モードで奇数バイトの読み取りまたは書き込みを試みると、パラメーター検証エラーが発生します。 UTF-8 としてプログラムに格納されたデータを読み取るか書き込む場合は、Unicode モードではなくテキストまたはバイナリ ファイル モードを使用します。 必要なエンコード変換は各自が行う必要があります。

**_Sopen**が **_O_WRONLY** |  **_O_APPEND** (追加モード) と **_O_WTEXT**、 **_O_U16TEXT**、または **_O_U8TEXT**で呼び出された場合、まず読み取りと書き込みのためにファイルを開き、BOM を読み取り、次に再オープンしようとします。書き込みのみ。 読み取りおよび書き込み用にファイルを開くのに失敗した場合、書き込み専用でファイルを開き、Unicode モード設定の既定値を使用します。

引数*shflag*は、次のマニフェスト定数のいずれかで構成される定数式です。これ\<は、resource.h > で定義されています。

|*shflag*定数|動作|
|-|-|
| **(_L)** | ファイルへの読み取りおよび書き込みアクセスを拒否します。 |
| **_SH_DENYWR** | ファイルへの書き込みアクセスを拒否します。 |
| **検索 (_D)** | ファイルへの読み取りアクセスを拒否します。 |
| **(_L)** | 読み取りおよび書き込みアクセスを許可します。 |

**_O_CREAT**が指定されている場合にのみ、 *pmode*引数が必要です。 ファイルが存在しない場合は、ファイルのアクセス許可の設定*を指定し*ます。これは、新しいファイルが最初に閉じられたときに設定されます。 それ以外の場合、 *pmode*は無視されます。 *pmode*は、_S_IWRITE > \<で定義されているマニフェスト定数と **_S_IREAD**の一方または両方を含む整数式です。 両方の定数が指定されると、これらはビットごとの OR 演算子を使用して組み合わされます。 *Pmode*の意味は次のとおりです。

|*pmode*|説明|
|-|-|
| **_S_IREAD** | 読み取りのみが許可されます。 |
| **_S_IWRITE** | 書き込みが許可されます。 (実際には、読み取りと書き込みが許可されます)。 |
| **_S_IREAD**&#124; **_S_IWRITE** | 読み取りと書き込みが許可されます。 |

書き込みアクセス許可が与えられない場合、ファイルは読み取り専用になります。 Windows オペレーティング システムでは、すべてのファイルは読み取り可能です。書き込み専用のアクセス許可を与えることはできません。 そのため、モード **_S_IWRITE**と **_S_IREAD** |  **_S_IWRITE**は同等です。

**_sopen**は、アクセス許可が設定される前に、現在のファイルアクセス許可マスクを*pmode*に適用します。 (「[_umask](umask.md)」を参照。)

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_sopen**|\<io.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>、\<share.h>|
|**_wsopen**|\<io.h> または \<wchar.h>|\<fcntl.h>、\<sys\types.h>、\<sys\stat.h>、\<share.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

「[_locking](locking.md)」の例をご覧ください。

## <a name="see-also"></a>関連項目

[下位入出力](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_fsopen、_wfsopen](fsopen-wfsopen.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
