---
title: _access、_waccess
ms.date: 11/04/2016
api_name:
- _access
- _waccess
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
- _waccess
- _access
- taccess
- waccess
- _taccess
helpviewer_keywords:
- access function
- _taccess function
- waccess function
- _access function
- _waccess function
- taccess function
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
ms.openlocfilehash: 90092b5d1c250fd79be107b0c36ee5641f70b30c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943940"
---
# <a name="_access-_waccess"></a>_access、_waccess

ファイルが読み取り専用かどうかを判断します。 セキュリティを強化したバージョンを使用できます。「[_access_s、_waccess_s](access-s-waccess-s.md)」をご覧ください。

## <a name="syntax"></a>構文

```C
int _access(
   const char *path,
   int mode
);
int _waccess(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>パラメーター

*path*<br/>
ファイルまたはディレクトリ パス。

*モード*<br/>
読み取り/書き込み属性。

## <a name="return-value"></a>戻り値

ファイルに特定のモードが設定されている場合、各関数は 0 を返します。 指定されたファイルが存在しない場合、または指定されたモードがない場合、この関数は-1 を返します。この場合、 `errno`は次の表に示すように設定されます。

|||
|-|-|
`EACCES`|アクセス拒否: ファイルのアクセス許可の設定では、指定したアクセスは許可されません。
`ENOENT`|ファイル名またはパスが見つかりません。
`EINVAL`|無効なパラメーター。

リターン コードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

ファイルと共に使用する場合、 **_access**関数は、指定したファイルまたはディレクトリが存在するかどうかを判断し、*モード*の値によって指定された属性を持ちます。 ディレクトリと共に使用すると、 **_access**は、指定されたディレクトリが存在するかどうかのみを判断します。Windows 2000 以降のオペレーティングシステムでは、すべてのディレクトリに読み取りと書き込みのアクセス権があります。

|*モード*値|ファイル チェックの目的|
|------------------|---------------------|
|00|存在のみ|
|02|書き込み専用|
|04|読み取り専用です。|
|06|読み取りおよび書き込み|

この関数は、ファイルとディレクトリが読み取り専用かどうかだけを確認し、ファイルシステムのセキュリティ設定は確認しません。 そのためには、アクセス トークンが必要です。 ファイルシステムのセキュリティの詳細については、「[アクセス トークン](/windows/win32/SecAuthZ/access-tokens)」を参照してください。 ATL クラスはこの機能を提供するために存在します。「[CAccessToken クラス](../../atl/reference/caccesstoken-class.md)」を参照してください。

**_waccess**は、 **_access**のワイド文字バージョンです。 **_waccess**への*パス*引数は、ワイド文字列です。 それ以外では、 **_waccess**と **_access**は同じように動作します。

この関数は、パラメーターを検証します。 *Path*が NULL であるか、*モード*で有効なモードが指定されていない場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は `errno` を `EINVAL` に設定し、-1 を返します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess`|**_access**|**_access**|**_waccess**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|省略可能なヘッダー|
|-------------|---------------------|----------------------|
|**_access**|\<io.h>|\<errno.h>|
|**_waccess**|\<wchar.h> または \<io.h>|\<errno.h>|

## <a name="example"></a>例

次の例では、 **_access**を使用して、crt_ACCESS という名前のファイルを確認します。C は、存在するかどうか、書き込みが許可されているかどうかを確認します。

```C
// crt_access.c
// compile with: /W1
// This example uses _access to check the file named
// crt_ACCESS.C to see if it exists and if writing is allowed.

#include  <io.h>
#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    // Check for existence.
    if( (_access( "crt_ACCESS.C", 0 )) != -1 )
    {
        printf_s( "File crt_ACCESS.C exists.\n" );

        // Check for write permission.
        // Assume file is read-only.
        if( (_access( "crt_ACCESS.C", 2 )) == -1 )
            printf_s( "File crt_ACCESS.C does not have write permission.\n" );
    }
}
```

```Output
File crt_ACCESS.C exists.
File crt_ACCESS.C does not have write permission.
```

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_stat、_wstat 関数](stat-functions.md)