---
title: qsort
ms.date: 11/04/2016
api_name:
- qsort
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- qsort
helpviewer_keywords:
- qsort function
- quick-sort algorithm
- sorting arrays
- arrays [CRT], sorting
ms.assetid: d6cb33eb-d209-485f-8d41-229eb743c027
ms.openlocfilehash: f445158bb72c50507af913986aff2d225ee50928
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949709"
---
# <a name="qsort"></a>qsort

クイック ソートを実行します。 この関数のセキュリティが強化されたバージョンについては、「[qsort_s](qsort-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
void qsort(
   void *base,
   size_t number,
   size_t width,
   int (__cdecl *compare )(const void *, const void *)
);
```

### <a name="parameters"></a>パラメーター

*base*<br/>
対象となる配列の先頭。

*number*<br/>
配列サイズ (要素数)。

*width*<br/>
要素のサイズ (バイト単位)。

*compare*<br/>
2 つの配列要素を比較してそれらの関係を指定する値を返すユーザー指定のルーチンへのポインターです。

## <a name="remarks"></a>Remarks

**Qsort**関数は、*数値*要素の配列 (それぞれの*幅*バイト) を並べ替えるクイックソートアルゴリズムを実装します。 引数*base*は、並べ替えられる配列のベースへのポインターです。 **qsort**は、並べ替えられた要素を使用して、この配列を上書きします。

**qsort**は、並べ替え中に*比較*ルーチンを1回以上呼び出し、各呼び出しで2つの配列要素へのポインターを渡します。

```C
compare( (void *) & elem1, (void *) & elem2 );
```

ルーチンは、要素を比較し、次の値のいずれかを返します。

|関数の戻り値の比較|説明|
|-----------------------------------|-----------------|
|< 0|**elem1**未満**elem2**|
|0|**elem2**に相当する**elem1**|
|> 0|**elem1** **elem2**より大きい|

配列は、比較関数による定義に従って、昇順で並べ替えられます。 配列を降順で並べ替えるには、比較関数の "より大きい" と "より小さい" の意味を入れ替えます。

この関数は、パラメーターを検証します。 *Compare*または*number*が**null**の場合、または*base*が**null**で*数値*が0以外の場合、または*width*が0未満の場合は、「パラメーターの[検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、関数はを返し、 **errno**は**EINVAL**に設定されます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**qsort**|\<stdlib.h> および \<search.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_qsort.c
// arguments: every good boy deserves favor

/* This program reads the command-line
* parameters and uses qsort to sort them. It
* then displays the sorted arguments.
*/

#include <stdlib.h>
#include <string.h>
#include <stdio.h>

int compare( const void *arg1, const void *arg2 );

int main( int argc, char **argv )
{
   int i;
   /* Eliminate argv[0] from sort: */
   argv++;
   argc--;

   /* Sort remaining args using Quicksort algorithm: */
   qsort( (void *)argv, (size_t)argc, sizeof( char * ), compare );

   /* Output sorted list: */
   for( i = 0; i < argc; ++i )
      printf( " %s", argv[i] );
   printf( "\n" );
}

int compare( const void *arg1, const void *arg2 )
{
   /* Compare all of both strings: */
   return _stricmp( * ( char** ) arg1, * ( char** ) arg2 );
}
```

```Output
boy deserves every favor good
```

## <a name="see-also"></a>関連項目

[検索と並べ替え](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
