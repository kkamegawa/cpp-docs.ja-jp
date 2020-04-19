---
title: fwrite
ms.date: 11/04/2016
api_name:
- fwrite
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
- fwrite
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: 8149e0f2cbc84c2c28093d86fecd5ff2a9db7aba
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956192"
---
# <a name="fwrite"></a>fwrite

ストリームにデータを書き込みます。

## <a name="syntax"></a>構文

```C
size_t fwrite(
   const void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
書き込むデータへのポインター。

*size*<br/>
項目サイズ (バイト単位)。

*count*<br/>
書き込む項目の最大数。

*一連*<br/>
**FILE** 構造体へのポインター。

## <a name="return-value"></a>戻り値

**fwrite**は、実際に書き込まれたすべての項目の数を返します。エラーが発生すると、 *count*よりも小さくなる場合があります。 また、エラーが発生した場合は、ファイル位置インジケーターを決定できません。 *ストリーム*または*バッファー*が null ポインターの場合、または書き込まれる奇数バイト数が Unicode モードで指定されている場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、関数は無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、この関数は**errno**を**EINVAL**に設定し、0を返します。

## <a name="remarks"></a>Remarks

**Fwrite**関数は、*バッファー*から出力*ストリーム*に、最大*サイズ*の項目*数*を書き込みます。 *ストリーム*に関連付けられているファイルポインター (存在する場合) は、実際に書き込まれたバイト数によってインクリメントされます。 *ストリーム*がテキストモードで開かれている場合、各ラインフィードは復帰とラインフィードのペアで置き換えられます。 この置き換えは、戻り値には影響しません。

*ストリーム*が unicode 変換モードで開かれている場合 (たとえば、 **fopen**を呼び出して*ストリーム*を開き、 **ccs = Unicode**、 **ccs = 16LE**、または**ccs = utf-8**を含むモードパラメーターを使用する場合)、またはモードがの場合は、 **_setmode**と、 **_O_WTEXT**、 **_O_U16TEXT**、または **_O_U8TEXT**を含む mode パラメーターを使用して Unicode 変換モードに変更されました。*buffer*は、を含む**wchar_t**の配列へのポインターとして解釈されます。UTF-16 データ。 このモードで奇数バイトの書き込みを試みると、パラメーター検証エラーが発生します。

この関数は呼び出し元スレッドをロックするため、スレッド セーフです。 非ロックバージョンについては、「 **_fwrite_nolock**」を参照してください。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

「[fread](fread.md)」の例を参照してください。

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
