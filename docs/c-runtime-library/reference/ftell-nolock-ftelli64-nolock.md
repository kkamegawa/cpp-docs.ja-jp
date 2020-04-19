---
title: _ftell_nolock、_ftelli64_nolock
ms.date: 11/04/2016
api_name:
- _ftelli64_nolock
- _ftell_nolock
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
- _ftelli64_nolock
- ftelli64_nolock
- ftell_nolock
- _ftell_nolock
helpviewer_keywords:
- ftelli64_nolock function
- _ftelli64_nolock function
- _ftell_nolock function
- ftell_nolock function
- file pointers [C++], getting current position
ms.assetid: 84e68b0a-32f8-4c4a-90ad-3f2387685ede
ms.openlocfilehash: 9e72687077cc5401bb411fca81a3ccec48a6258f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956362"
---
# <a name="_ftell_nolock-_ftelli64_nolock"></a>_ftell_nolock、_ftelli64_nolock

スレッドをロックせずに、ファイル ポインターの現在の位置を取得します。

## <a name="syntax"></a>構文

```C
long _ftell_nolock(
   FILE *stream
);
__int64 _ftelli64_nolock(
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*一連*<br/>
**ファイル**構造をターゲットにします。

## <a name="return-value"></a>戻り値

**Ftell**と **_ftelli64**と同じです。 詳細については、「 [ftell、_ftelli64](ftell-ftelli64.md)」を参照してください。

## <a name="remarks"></a>Remarks

これらの関数は、それぞれ**ftell**と **_ftelli64**の非ロックバージョンです。 これらは、他のスレッドによる干渉から保護されないことを除いて、 **ftell**と **_ftelli64**と同じです。 これらの関数では他のスレッドをロックアウトするオーバーヘッドが発生しないため、処理が速くなる場合があります。 これらの関数は、シングルスレッド アプリケーション、呼び出し元のスコープで既にスレッド分離を処理している場合などのスレッドセーフなコンテキストでのみ使用してください。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|オプション ヘッダー|
|--------------|---------------------|---------------------|
|**ftell_nolock**|\<stdio.h>|\<errno.h>|
|**_ftelli64_nolock**|\<stdio.h>|\<errno.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek、_fseeki64](fseek-fseeki64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
[ftell、_ftelli64](ftell-ftelli64.md)<br/>
