---
title: _get_osfhandle
ms.date: 05/29/2018
api_name:
- _get_osfhandle
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
- get_osfhandle
- _get_osfhandle
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
ms.openlocfilehash: 65060689e0a7fc72b67da8fc3bf7ce0af75fd645
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955781"
---
# <a name="_get_osfhandle"></a>_get_osfhandle

指定されたファイル記述子に関連付けられている、オペレーティング システム ファイル ハンドルを取得します。

## <a name="syntax"></a>構文

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>パラメーター

*fd*<br/>
既存のファイル記述子。

## <a name="return-value"></a>戻り値

*Fd*が有効な場合は、オペレーティングシステムのファイルハンドルを返します。 それ以外の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているように、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、 **INVALID_HANDLE_VALUE** (-1) が返されます。 また、 **errno**を**EBADF**に設定し、無効なファイルハンドルを示します。 結果が Win32 ファイルハンドルとして使用されたときに警告が発生しないようにするには、それを**ハンドル**型にキャストします。

> [!NOTE]
> **Stdin**、 **stdout**、および**stderr**がストリームに関連付けられていない場合 (たとえば、コンソールウィンドウがない Windows アプリケーションで)、これらのストリームのファイル記述子の値は[_fileno](fileno.md)から特別な値-2 として返されます。 同様に、 **_fileno**の呼び出しの結果ではなく、ファイル記述子のパラメーターとして0、1、または2を使用した場合、 **_get_osfhandle**は、ファイル記述子がストリームに関連付けられていない場合にも特殊な値2を返し、 **errno**を設定しません。 ただし、これは有効なファイルハンドル値ではなく、それを使用しようとする呼び出しが失敗する可能性があります。

**EBADF**とその他のエラーコードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Get_osfhandle**によってオペレーティングシステム (os) ファイルハンドルが取得されたファイルを閉じるには、ファイル記述子*fd*で[_close](close.md)を呼び出します。 この関数の戻り値には**CloseHandle**を呼び出さないでください。 基になる OS ファイルハンドルは*fd*ファイル記述子によって所有され、 *fd*で[_close](close.md)が呼び出されると閉じられます。 ファイル記述子が`FILE *`ストリームによって所有されている場合、その`FILE *`ストリームで [fclose](fclose-fcloseall.md) を呼び出すと、ファイル記述子と基になる OS ファイルハンドルの両方が閉じられます。 この場合は、ファイル記述子で[_close](close.md)を呼び出さないでください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_dup、_dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
