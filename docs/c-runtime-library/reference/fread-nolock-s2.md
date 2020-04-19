---
title: _fread_nolock_s2
ms.date: 11/04/2016
api_name:
- _fread_nolock_s
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
- _fread_nolock_s
- stdio/_fread_nolock_s
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
ms.openlocfilehash: e7fded9860b7a1364841d5f9b8a7e3aa478a8420
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956889"
---
# <a name="_fread_nolock_s"></a>_fread_nolock_s

他のスレッドをロックしないで、ストリームからデータを読み取ります。 これは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [fread_nolock](fread-nolock.md) です。

## <a name="syntax"></a>構文

```C
size_t _fread_nolock_s(
   void *buffer,
   size_t bufferSize,
   size_t elementSize,
   size_t elementCount,
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
データの格納場所。

*bufferSize*<br/>
ターゲット バッファーのサイズ (バイト単位)。

*elementSize*<br/>
読み取る項目のサイズ (バイト単位)。

*elementCount*<br/>
読み取る項目の最大数。

*一連*<br/>
**FILE** 構造体へのポインター。

## <a name="return-value"></a>戻り値

「[fread_s](fread-s.md)」を参照してください。

## <a name="remarks"></a>Remarks

この関数は、 **fread_s**のロックされていないバージョンです。 他のスレッドによる干渉から保護されない点を除いて、 **fread_s**と同じです。 他のスレッドをロックするオーバーヘッドが発生しないため、処理が速くなる場合があります。 この関数は、シングルスレッド アプリケーション、呼び出し元のスコープで既にスレッド分離を処理している場合などのスレッドセーフなコンテキストでのみご使用ください。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**_fread_nolock_s**|C: \<stdio.h>、C++: \<cstdio>、または \<stdio.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
