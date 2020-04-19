---
title: ferror
ms.date: 11/04/2016
api_name:
- ferror
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
- ferror
helpviewer_keywords:
- ferror function
- streams, testing for errors
- errors [C++], testing for stream
ms.assetid: 528a34bc-f2aa-4c3f-b89a-5b148e6864f7
ms.openlocfilehash: 4efb1b01ac94f1cb2d28bffb1f09b594a0e71479
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941099"
---
# <a name="ferror"></a>ferror

ストリームのエラーをテストします。

## <a name="syntax"></a>構文

```C
int ferror(
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*一連*<br/>
**FILE** 構造体へのポインター。

## <a name="return-value"></a>戻り値

*ストリーム*でエラーが発生しなかった場合、 **ferror**は0を返します。 それ以外の場合は、0 以外の値を返します。 Stream が**NULL**の場合、 **ferror**は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、この関数は**errno**を**EINVAL**に設定し、0を返します。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**Ferror**ルーチン (関数とマクロの両方として実装されます) は、*ストリーム*に関連付けられているファイルに対して読み取りまたは書き込みエラーが発生したかどうかをテストします。 エラーが発生した場合、ストリームが閉じられるか巻き戻されるか、またはそのストリームに対して**clearerr**が呼び出されるまで、ストリームのエラーインジケーターが設定されたままになります。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**ferror**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

「[feof](feof.md)」の例を参照してください。

## <a name="see-also"></a>関連項目

[エラー処理](../../c-runtime-library/error-handling-crt.md)<br/>
[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[perror、_wperror](perror-wperror.md)<br/>
