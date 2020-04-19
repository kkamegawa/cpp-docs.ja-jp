---
title: _access_s、_waccess_s
ms.date: 11/04/2016
api_name:
- _access_s
- _waccess_s
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
- waccess_s
- access_s
- _waccess_s
- _access_s
helpviewer_keywords:
- access_s function
- taccess_s function
- _taccess_s function
- waccess_s function
- _access_s function
- _waccess_s function
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
ms.openlocfilehash: 0550b8fb42cb62d1a175960d6b0d4ed4dbecdcac
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939899"
---
# <a name="_access_s-_waccess_s"></a>_access_s、_waccess_s

ファイルの読み取り/書き込みアクセス許可を決定します。 これは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [_access, _waccess](access-waccess.md) です。

## <a name="syntax"></a>構文

```C
errno_t _access_s(
   const char *path,
   int mode
);
errno_t _waccess_s(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>パラメーター

*path*<br/>
ファイルまたはディレクトリ パス。

*モード*<br/>
アクセス許可の設定。

## <a name="return-value"></a>戻り値

ファイルに特定のモードが設定されている場合、各関数は 0 を返します。 指定したファイルが存在しないか、特定のモードでアクセスできない場合、関数はエラー コードを返します。 この場合、関数は次のようにエラー コードをセットから返し、`errno` も同じ値に設定します。

|errno の値|条件|
|-|-|
`EACCES`|アクセスが拒否されました。 ファイルのアクセス許可の設定では、指定したアクセスは許可されません。
`ENOENT`|ファイル名またはパスが見つかりません。
`EINVAL`|無効なパラメーター。

詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

ファイルと共に使用する場合、 **_access_s**関数は、指定されたファイルが存在し、*モード*の値によって指定されたとおりにアクセスできるかどうかを判断します。 ディレクトリと共に使用すると、 **_access_s**は指定されたディレクトリが存在するかどうかのみを判断します。 Windows 2000 以降のオペレーティングシステムでは、すべてのディレクトリに読み取りと書き込みのアクセス権があります。

|モード値|ファイル チェックの目的|
|----------------|---------------------|
|00|存在のみ|
|02|書き込みアクセス許可|
|04|読み取りアクセス許可|
|06|読み取りおよび書き込みアクセス許可|

ファイルの読み取りおよび書き込みアクセス許可では、ファイルを開く権限を確認するには不十分です。 たとえば、ファイルが別のプロセスによってロックされている場合、 **_access_s**から0が返されても、ファイルにアクセスできない可能性があります。

**_waccess_s**は、 **_access_s**のワイド文字バージョンです。 **_waccess_s**への*パス*引数はワイド文字列です。 それ以外の場合、 **_waccess_s**と **_access_s**は同じように動作します。

これらの関数では、パラメーターの検証が行われます。 *Path*が NULL であるか、*モード*で有効なモードが指定されていない場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は `errno` を `EINVAL` に設定し、`EINVAL` を返します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess_s`|**_access_s**|**_access_s**|**_waccess_s**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_access_s**|\<io.h>|\<errno.h>|
|**_waccess_s**|\<wchar.h> または \<io.h>|\<errno.h>|

## <a name="example"></a>例

この例では、 **_access_s**を使用して crt_access_s という名前のファイルを確認し、存在するかどうか、書き込みが許可されているかどうかを確認します。

```C
// crt_access_s.c

#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    errno_t err = 0;

    // Check for existence.
    if ((err = _access_s( "crt_access_s.c", 0 )) == 0 )
    {
        printf_s( "File crt_access_s.c exists.\n" );

        // Check for write permission.
        if ((err = _access_s( "crt_access_s.c", 2 )) == 0 )
        {
            printf_s( "File crt_access_s.c does have "
                      "write permission.\n" );
        }
        else
        {
            printf_s( "File crt_access_s.c does not have "
                      "write permission.\n" );
        }
    }
    else
    {
        printf_s( "File crt_access_s.c does not exist.\n" );
    }
}
```

```Output
File crt_access_s.c exists.
File crt_access_s.c does not have write permission.
```

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_access、_waccess](access-waccess.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_stat、_wstat 関数](stat-functions.md)