---
title: bsearch_s
ms.date: 10/22/2019
api_name:
- bsearch_s
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
- bsearch_s
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
ms.openlocfilehash: fc86576dbbe73f63da6bf0e28e7166ef7c552e55
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811143"
---
# <a name="bsearch_s"></a>bsearch_s

並べ替えられた配列のバイナリ検索を実行します。 この関数は、「 [CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの[bsearch](bsearch.md)です。

## <a name="syntax"></a>構文

```C
void *bsearch_s(
   const void *key,
   const void *base,
   size_t number,
   size_t width,
   int ( __cdecl *compare ) ( void *, const void *key, const void *datum),
   void * context
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
2 つの要素を比較するコールバック関数。 最初の引数は*コンテキスト*ポインターです。 2番目の引数は、検索用の*キー*へのポインターです。 3番目の引数は、*キー*と比較する配列要素へのポインターです。

*コンテキスト*\
比較関数内でアクセスできるオブジェクトへのポインター。

## <a name="return-value"></a>戻り値

**bsearch_s**は、 *base*が指す配列内の*キー*の出現箇所へのポインターを返します。 *Key*が見つからない場合、関数は**NULL**を返します。 配列が昇順でないか、同一キーで重複するレコードがある場合、結果は予測不可能になります。

無効なパラメーターが関数に渡されると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、 **errno**は**EINVAL**に設定され、関数は**NULL**を返します。 詳細については、「[errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

### <a name="error-conditions"></a>エラー条件

|||||||
|-|-|-|-|-|-|
|*key*|*base*|*compare*|*少数*|*width*|**番号**|
|**NULL**|任意|任意|任意|任意|**EINVAL**|
|任意|**NULL**|任意|!= 0|任意|**EINVAL**|
|任意|任意|任意|任意|= 0|**EINVAL**|
|任意|任意|**NULL**|1 つ|任意|**EINVAL**|

## <a name="remarks"></a>Remarks

**Bsearch_s**関数は、*数値*要素の並べ替えられた配列のバイナリ検索を実行します。これらの要素のサイズは、それぞれ*幅*バイトです。 *ベース*値は、検索対象の配列のベースへのポインターであり、*キー*は検索対象の値です。 *Compare*パラメーターは、ユーザーが指定したルーチンへのポインターであり、要求されたキーを配列要素と比較し、次のいずれかの値を返します。

|*比較*ルーチンによって返される値|説明|
|-----------------------------------------|-----------------|
|\< 0|キーは配列要素より小さい。|
|0|キーは配列要素と等しい。|
|> 0|キーは配列要素より大きい。|

*コンテキスト*ポインターは、検索対象のデータ構造体がオブジェクトの一部であり、compare 関数がオブジェクトのメンバーにアクセスする必要がある場合に便利です。 *Compare*関数は、void ポインターを適切なオブジェクト型にキャストし、そのオブジェクトのメンバーにアクセスすることができます。 *Context*パラメーターを追加することにより、 **bsearch_s**のセキュリティが強化されます。これは、*比較*関数でデータを使用できるようにするために静的変数を使用する場合に関連する再入バグを回避するために、コンテキストを追加するためです。

## <a name="requirements"></a>［要件］

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**bsearch_s**|\<stdlib.h> および \<search.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

このプログラムでは、 [qsort_s](qsort-s.md)で文字列の配列を並べ替え、bsearch_s を使用して "cat" という単語を検索します。

```cpp
// crt_bsearch_s.cpp
// This program uses bsearch_s to search a string array,
// passing a locale as the context.
// compile with: /EHsc
#include <stdlib.h>
#include <stdio.h>
#include <search.h>
#include <process.h>
#include <locale.h>
#include <locale>
#include <windows.h>
using namespace std;

// The sort order is dependent on the code page.  Use 'chcp' at the
// command line to change the codepage.  When executing this application,
// the command prompt codepage must match the codepage used here:

#define CODEPAGE_850

#ifdef CODEPAGE_850
#define ENGLISH_LOCALE "English_US.850"
#endif

#ifdef CODEPAGE_1252
#define ENGLISH_LOCALE "English_US.1252"
#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making it vulnerable to thread conflicts
// (if this were a multithreaded program).

int compare( void *pvlocale, char **str1, char **str2)
{
    char *s1 = *str1;
    char *s2 = *str2;

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(
       s1, s1+strlen(s1),
       s2, s2+strlen(s2) );
}

int main( void )
{
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};

   char *key = "cat";
   char **result;
   int i;

   /* Sort using Quicksort algorithm: */
   qsort_s( arr,
            sizeof(arr)/sizeof(arr[0]),
            sizeof( char * ),
            (int (*)(void*, const void*, const void*))compare,
            &locale(ENGLISH_LOCALE) );

   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */
      printf( "%s ", arr[i] );

   /* Find the word "cat" using a binary search algorithm: */
   result = (char **)bsearch_s( &key,
                                arr,
                                sizeof(arr)/sizeof(arr[0]),
                                sizeof( char * ),
                                (int (*)(void*, const void*, const void*))compare,
                                &locale(ENGLISH_LOCALE) );
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
