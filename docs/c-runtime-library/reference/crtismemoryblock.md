---
title: _CrtIsMemoryBlock
ms.date: 11/04/2016
api_name:
- _CrtIsMemoryBlock
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
ms.openlocfilehash: f29745acd06f6f5b3fa96367444e800bdc3e8e3a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938731"
---
# <a name="_crtismemoryblock"></a>_CrtIsMemoryBlock

指定されたメモリ ブロックがローカル ヒープ内にあり、有効なデバッグ ヒープ ブロック型識別子が設定されていることを検査します (デバッグ バージョンだけ)。

## <a name="syntax"></a>構文

```C
int _CrtIsMemoryBlock(
   const void *userData,
   unsigned int size,
   long *requestNumber,
   char **filename,
   int *linenumber
);
```

### <a name="parameters"></a>パラメーター

*userData*<br/>
検査するメモリ ブロックの先頭へのポインター。

*size*<br/>
指定されたブロックのサイズ (バイト)。

*requestNumber*<br/>
ブロックの割り当て番号へのポインターまたは**NULL**。

*ファイル名*<br/>
ブロックを要求したソースファイルの名前へのポインターまたは**NULL**。

*行番号*<br/>
ソースファイル内の行番号へのポインター、または**NULL**。

## <a name="return-value"></a>戻り値

指定されたメモリブロックがローカルヒープ内にあり、有効なデバッグヒープブロック型識別子がある場合、 **_CrtIsMemoryBlock**は**TRUE**を返します。それ以外の場合、関数は**FALSE**を返します。

## <a name="remarks"></a>Remarks

**_CrtIsMemoryBlock**関数は、指定されたメモリブロックがアプリケーションのローカルヒープ内にあり、有効なブロック型識別子があることを確認します。 また、この関数を使用すると、オブジェクト割り当て順序番号と、メモリ ブロックの割り当て要求を行ったソース ファイル名および行番号を取得できます。 *Requestnumber*、 *filename*、または*linenumber*パラメーターに**NULL**以外の値を渡すと、 **_CrtIsMemoryBlock**によって、これらのパラメーターがメモリブロックのデバッグヘッダーの値に設定され、ローカルヒープ。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_CrtIsMemoryBlock**の呼び出しはプリプロセス中に削除されます。

**_CrtIsMemoryBlock**が失敗した場合は**FALSE**を返し、出力パラメーターは既定値に初期化されます。 *requestnumber*と**lineNumber**は0に設定され、 *filename*は**NULL**に設定されます。

この関数は **TRUE** または **FALSE** を返すため、[_ASSERT](assert-asserte-assert-expr-macros.md) 系マクロに渡すことによって、デバッグ用の単純なエラー処理機構を作成できます。 指定されたアドレスがローカル ヒープ内にない場合に、アサーションの失敗を発生させるには、次のように記述します。

```C
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,
          &filename, &linenumber ) );
```

**_CrtIsMemoryBlock**を他のデバッグ関数およびマクロと共に使用する方法の詳細については、「[レポート用マクロ](/visualstudio/debugger/macros-for-reporting)」を参照してください。 デバッグ バージョンのベース ヒープに対するメモリ ブロックの割り当て、初期化、管理方法については、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_CrtIsMemoryBlock**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="example"></a>例

「[_CrtIsValidHeapPointer](crtisvalidheappointer.md)」のトピックの例を参照してください。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
