---
title: fclose、_fcloseall
ms.date: 11/04/2016
api_name:
- fclose
- _fcloseall
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
- fclose
- _fcloseall
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
ms.openlocfilehash: 215925fb16f5d51e481ae92cbb45b0270bd5ebd4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941505"
---
# <a name="fclose-_fcloseall"></a>fclose、_fcloseall

ストリーム (**fclose**) を閉じるか、すべての開いているストリーム ( **_fcloseall**) を閉じます。

## <a name="syntax"></a>構文

```C
int fclose(
   FILE *stream
);
int _fcloseall( void );
```

### <a name="parameters"></a>パラメーター

*一連*<br/>
**FILE** 構造体へのポインター。

## <a name="return-value"></a>戻り値

ストリームが正常に閉じられた場合、 **fclose**は0を返します。 **_fcloseall**は、閉じられたストリームの合計数を返します。 どちらの関数も、エラーを示す**EOF**を返します。

## <a name="remarks"></a>Remarks

**Fclose**関数は、*ストリーム*を閉じます。 *Stream*が**NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、 **fclose**は**errno**を**EINVAL**に設定し、 **EOF**を返します。 この関数を呼び出す前に、*ストリーム*ポインターを常に確認することをお勧めします。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

**_Fcloseall**関数は、 **stdin**、 **stdout**、 **stderr** (および、MS-DOS、 **_stdaux** 、および **_stdprn**) を除くすべての開いているストリームを閉じます。 また、 **tmpfile**によって作成された一時ファイルを閉じて削除します。 両方の関数では、終了する前に、ストリームに関連付けられているすべてのバッファーがフラッシュされます。 システムによって割り当てられたバッファーについては、ストリームを閉じる際に解放します。 **Setbuf**と**setvbuf**を使用してユーザーによって割り当てられたバッファーは、自動的には解放されません。

**注:** これらの関数を使用してストリームを閉じると、基になるファイル記述子と OS ファイルハンドル (またはソケット) とストリームが閉じられます。 このため、ファイルが最初にファイルハンドルまたはファイル記述子として開かれていて、 **fclose**で閉じられている場合は、 **_close**を呼び出してファイル記述子を閉じることはできません。ファイルハンドルを閉じるには、Win32 関数**CloseHandle**を呼び出さないでください。

**fclose**と **_fcloseall**には、他のスレッドからの干渉を防ぐためのコードが含まれています。 **Fclose**の非ロックバージョンについては、「 **_fclose_nolock**」を参照してください。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**fclose**|\<stdio.h>|
|**_fcloseall**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

「[fopen](fopen-wfopen.md)」の例を参照してください。

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[_close](close.md)<br/>
[_fdopen、_wfdopen](fdopen-wfdopen.md)<br/>
[fflush](fflush.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[freopen、_wfreopen](freopen-wfreopen.md)<br/>
