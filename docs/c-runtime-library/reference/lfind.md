---
title: _lfind
ms.date: 11/04/2016
api_name:
- _lfind
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lfind
- _lfind
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
ms.openlocfilehash: 8fd2141caf8311844a90a6d12226bb7797ac4734
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953386"
---
# <a name="_lfind"></a>_lfind

指定されたキーの線形探索を実行します。 この関数のセキュリティが強化されたバージョンについては、「[_lfind_s](lfind-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
void *_lfind(
   const void *key,
   const void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
検索するオブジェクト。

*base*<br/>
検索データのベースへのポインター。

*number*<br/>
配列要素の数。

*width*<br/>
配列要素の幅。

*compare*<br/>
比較ルーチンへのポインター。 最初のパラメーターは、検索用のキーへのポインターです。 2 番目の引数は、キーと比較する配列要素へのポインターです。

## <a name="return-value"></a>戻り値

キーが見つかった場合、 **_lfind**は、*キー*に一致する*ベース*の配列の要素へのポインターを返します。 キーが見つからない場合、 **_lfind**は**NULL**を返します。

## <a name="remarks"></a>Remarks

**_Lfind**関数は、*数値*要素の配列内の値*キー*の線形検索を実行します (各*幅*バイト)。 **Bsearch**とは異なり、 **_lfind**では配列を並べ替える必要はありません。 *基本*引数は、検索する配列のベースへのポインターです。 *Compare*引数は、2つの配列要素を比較し、それらの関係を指定する値を返すユーザー指定のルーチンへのポインターです。 **_lfind**は、検索中に*比較*ルーチンを1回以上呼び出し、各呼び出しで2つの配列要素へのポインターを渡します。 *比較*ルーチンは、要素を比較し、0以外の値 (要素が異なる場合) または 0 (要素が同一であることを意味します) を返す必要があります。

この関数は、パラメーターを検証します。 *Compare*、 *key* 、または*number*が**null**の場合、または*base*が**null**で、 *number*が0以外の場合、または*width*が0未満の場合は、「パラメーター」に説明されているように、無効なパラメーターハンドラーが呼び出されます。 [検証](../../c-runtime-library/parameter-validation.md)。 実行の継続が許可された場合、 **errno**は**EINVAL**に設定され、関数は**NULL**を返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_lfind**|\<search.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_lfind.c
// This program uses _lfind to search a string array
// for an occurrence of "hello".

#include <search.h>
#include <string.h>
#include <stdio.h>

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}

int main( )
{
   char *arr[] = {"Hi", "Hello", "Bye"};
   int n = sizeof(arr) / sizeof(char*);
   char **result;
   char *key = "hello";

   result = (char **)_lfind( &key, arr,
                      &n, sizeof(char *), compare );

   if( result )
      printf( "%s found\n", *result );
   else
      printf( "hello not found!\n" );
}
```

```Output
Hello found
```

## <a name="see-also"></a>関連項目

[検索と並べ替え](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
