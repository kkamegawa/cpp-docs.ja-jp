---
title: bsearch
ms.date: 10/22/2019
api_name:
- bsearch
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- bsearch
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
ms.openlocfilehash: 6b476cbdd5e9c072cae03ad1091a96e2d0b7422b
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811091"
---
# <a name="bsearch"></a>bsearch

並べ替えられた配列のバイナリ検索を実行します。 この関数のセキュリティが強化されたバージョンについては、「 [bsearch_s](bsearch-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
void *bsearch(
   const void *key,
   const void *base,
   size_t num,
   size_t width,
   int ( __cdecl *compare ) (const void *key, const void *datum)
);
```

### <a name="parameters"></a>パラメーター

*キー* \
検索するキーへのポインター。

*base*\
検索データのベースへのポインター。

*数値*\
要素の数。

*幅*\
要素の幅。

\ の*比較*
2 つの要素を比較するコールバック関数。 1つ目は検索対象のキーへのポインターであり、2つ目はキーと比較する配列要素へのポインターです。

## <a name="return-value"></a>戻り値

**bsearch**は、 *base*が指す配列内の*キー*の出現箇所へのポインターを返します。 *Key*が見つからない場合、関数は**NULL**を返します。 配列が昇順でないか、同一キーで重複するレコードがある場合、結果は予測不可能になります。

## <a name="remarks"></a>Remarks

**Bsearch**関数は、*数値*要素の並べ替えられた配列のバイナリ検索を実行します。これらの要素のサイズは、それぞれ*幅*バイトです。 *ベース*値は、検索対象の配列のベースへのポインターであり、*キー*は検索対象の値です。 *Compare*パラメーターは、要求されたキーを配列要素と比較するユーザー指定のルーチンへのポインターです。 リレーションシップを指定する次のいずれかの値が返されます。

|*比較*ルーチンによって返される値|説明|
|-----------------------------------------|-----------------|
|\< 0|キーは配列要素より小さい。|
|0|キーは配列要素と等しい。|
|> 0|キーは配列要素より大きい。|

この関数は、パラメーターを検証します。 *Compare*、 *key* 、または*number*が**null**の場合、または*base*が**null**で*数値*が0以外の場合、または*width*が0の場合は、「パラメーター」で説明されているように、関数は無効なパラメーターハンドラーを呼び出します。 [検証](../../c-runtime-library/parameter-validation.md)。 実行の継続が許可された場合、 **errno**が `EINVAL` に設定され、関数は**NULL**を返します。

## <a name="requirements"></a>［要件］

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**bsearch**|\<stdlib.h> および \<search.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

このプログラムでは、qsort で文字列の配列を並べ替え、bsearch を使用して "cat" という単語を検索します。

```C
// crt_bsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( char **arg1, char **arg2 )
{
   /* Compare all of both strings: */
   return _strcmpi( *arg1, *arg2 );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};
   char **result;
   char *key = "cat";
   int i;

   /* Sort using Quicksort algorithm: */
   qsort( (void *)arr, sizeof(arr)/sizeof(arr[0]), sizeof( char * ), (int (*)(const
   void*, const void*))compare );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch( (char *) &key, (char *)arr, sizeof(arr)/sizeof(arr[0]),
                              sizeof( char * ), (int (*)(const void*, const void*))compare );
   if( result )
      printf( "\n%s found at %Fp\n", *result, result );
   else
      printf( "\nCat not found!\n" );
}
```

```Output
cat cow dog goat horse human pig rat
cat found at 002F0F04
```

## <a name="see-also"></a>関連項目

[検索と並べ替え](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
