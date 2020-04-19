---
title: _setmaxstdio
ms.date: 05/21/2019
api_name:
- _setmaxstdio
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
- setmaxstdio
- _setmaxstdio
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: 620213b4df9ea555189a1403b3c9e83b55cad6c6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948218"
---
# <a name="_setmaxstdio"></a>_setmaxstdio

ストリーム入出力のレベルで同時に開かれるファイルの数の最大値を設定します。

## <a name="syntax"></a>構文

```C
int _setmaxstdio(
   int new_max
);
```

### <a name="parameters"></a>パラメーター

*new_max*<br/>
ストリーム入出力のレベルで同時に開かれるファイルの数の最大値。

## <a name="return-value"></a>戻り値

正常に終了した場合は *new_max* を返し、それ以外の場合は –1 を返します。

*new_max* が **_IOB_ENTRIES** より小さいか、オペレーティング システムで使用できるハンドルの最大数より大きい場合には、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているとおり、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は -1 を返し、**errno** を **EINVAL** に設定します。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**_setmaxstdio** 関数は、ストリーム入出力のレベルで同時に開かれるファイル数の最大値を変更します。

C ランタイム入出力では現在、[低入出力レベル](../../c-runtime-library/low-level-i-o.md)で最大 8,192 のファイルを同時に開くことができます。 このレベルには、入出力の **_open**、 **_read**、 **_write** の関数ファミリを使用して開いたり、アクセスしたりできるファイルが含まれます。 既定では、この[ストリーム入出力レベル](../../c-runtime-library/stream-i-o.md)では最大 512 のファイルを同時に開くことができます。 このレベルには、**fopen**、**fgetc**、**fputc** の関数ファミリを使用して開いたり、アクセスしたりできるファイルが含まれます。 このストリーム入出力レベルで開くことができる最大ファイル数 512 は、 **_setmaxstdio** 関数を使うことで、8,192 の最大値へ引き上げることができます。

**fopen** などのストリーム入出力レベルの関数は低入出力レベルの関数の上に構築されているため、8,192 という最大値は、C ランタイム ライブラリによってアクセスされる同時に開いているファイルの数の固定された上限です。

> [!NOTE]
> この上限は、特定の Win32 プラットフォームと構成でサポートされる上限を超える可能性があります。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

**_setmaxstdio** の使用例については、「[_getmaxstdio](getmaxstdio.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
