---
title: _isatty
ms.date: 11/04/2016
api_name:
- _isatty
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
- _isatty
helpviewer_keywords:
- isatty function
- character device checking
- _isatty function
- checking character devices
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
ms.openlocfilehash: 2d2ba2fdfeb1c8bffe47b0953f0629746d2eb599
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954553"
---
# <a name="_isatty"></a>_isatty

ファイル記述子が文字デバイスに関連付けられているかどうかを判定します。

## <a name="syntax"></a>構文

```C
int _isatty( int fd );
```

### <a name="parameters"></a>パラメーター

*fd*<br/>
調べるデバイスを参照するファイル記述子。

## <a name="return-value"></a>戻り値

**_isatty**は、記述子が文字デバイスに関連付けられている場合、0以外の値を返します。 それ以外の場合、 **_isatty**は0を返します。

## <a name="remarks"></a>Remarks

**_Isatty**関数は、 *fd*がキャラクターデバイス (端末、コンソール、プリンター、またはシリアルポート) に関連付けられているかどうかを判断します。

この関数は、 *fd*パラメーターを検証します。 *Fd*が無効なファイルポインターの場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は0を返し、 **errno**を**EBADF**に設定します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_isatty**|\<io.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_isatty.c
/* This program checks to see whether
* stdout has been redirected to a file.
*/

#include <stdio.h>
#include <io.h>

int main( void )
{
   if( _isatty( _fileno( stdout ) ) )
      printf( "stdout has not been redirected to a file\n" );
   else
      printf( "stdout has been redirected to a file\n");
}
```

### <a name="sample-output"></a>出力例

```Output
stdout has not been redirected to a file
```

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
