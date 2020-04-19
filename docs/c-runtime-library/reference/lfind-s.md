---
title: _lfind_s
ms.date: 11/04/2016
api_name:
- _lfind_s
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
- lfind_s
- _lfind_s
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
ms.openlocfilehash: 69db97dc24b567714bda3e02f5f53ff381ae4911
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953449"
---
# <a name="_lfind_s"></a>_lfind_s

指定されたキーの線形探索を実行します。 「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [_lfind](lfind.md) です。

## <a name="syntax"></a>構文

```C
void *_lfind_s(
   const void *key,
   const void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>パラメーター

*key*<br/>
検索するオブジェクト。

*base*<br/>
検索データのベースへのポインター。

*number*<br/>
配列要素の数。

*size*<br/>
バイト単位での配列要素のサイズ。

*compare*<br/>
比較ルーチンへのポインター。 最初のパラメーターは*コンテキスト*ポインターです。 2 番目のパラメーターは、検索用のキーへのポインターです。 3 番目のパラメーターは、キーと比較する配列要素へのポインターです。

*context*<br/>
比較関数内でアクセスされることのあるオブジェクトへのポインター。

## <a name="return-value"></a>戻り値

キーが見つかった場合、 **_lfind_s**は、*キー*に一致する*ベース*の配列の要素へのポインターを返します。 キーが見つからない場合、 **_lfind_s**は**NULL**を返します。

この関数に無効なパラメーターが渡されると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、 **errno**は**EINVAL**に設定され、関数は**NULL**を返します。

### <a name="error-conditions"></a>エラー条件

|key|base|compare|num|size|errno|
|---------|----------|-------------|---------|----------|-----------|
|**NULL**|任意|任意|任意|任意|**EINVAL**|
|任意|**NULL**|任意|!= 0|任意|**EINVAL**|
|任意|任意|任意|任意|ゼロ|**EINVAL**|
|任意|任意|**NULL**|1 つ|任意|**EINVAL**|

## <a name="remarks"></a>Remarks

**_Lfind_s**関数は、*数値*要素の配列内の値*キー*の線形検索を実行します (各*幅*バイト)。 **Bsearch_s**とは異なり、 **_lfind_s**では配列を並べ替える必要はありません。 *基本*引数は、検索する配列のベースへのポインターです。 *Compare*引数は、2つの配列要素を比較し、それらの関係を指定する値を返すユーザー指定のルーチンへのポインターです。 **_lfind_s**は、検索中に*比較*ルーチンを1回以上呼び出し、*コンテキスト*ポインターとポインターを呼び出しごとに2つの配列要素に渡します。 *比較*ルーチンは、要素を比較し、0以外の値 (要素が異なることを意味します) または 0 (要素が同じであることを意味します) を返す必要があります。

**_lfind_s**は **_lfind**に似ていますが、比較関数の引数への*コンテキスト*ポインターと関数のパラメーターリストが追加されている点が異なります。 *コンテキスト*ポインターは、検索対象のデータ構造体がオブジェクトの一部であり、 *compare*関数がオブジェクトのメンバーにアクセスする必要がある場合に役立ちます。 *Compare*関数は、void ポインターを適切なオブジェクト型にキャストし、そのオブジェクトのメンバーにアクセスできます。 *Context*パラメーターを追加することにより、 **_lfind_s**の安全性が向上します。これは、*比較*関数でデータを使用できるようにするために静的変数を使用する場合に関連する再入バグを回避するために、コンテキストを追加できるためです。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_lfind_s**|\<search.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```cpp
// crt_lfind_s.cpp
// This program uses _lfind_s to search a string array,
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
// Codepage 850 is the OEM codepage used by the command line,
// so \x00e1 is the German Sharp S

char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };

#define GERMAN_LOCALE "German_Germany.850"

#endif

#ifdef CODEPAGE_1252
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df
   // for the German Sharp S
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };

#define GERMAN_LOCALE "German_Germany.1252"

#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making it vulnerable to thread conflicts
// (if this were a multithreaded program).

int compare( void *pvlocale, const void *str1, const void *str2)
{
    char *s1 = *(char**)str1;
    char *s2 = *(char**)str2;

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(
       s1, s1+strlen(s1),
       s2, s2+strlen(s2) );
}

void find_it( char *key, char *array[], unsigned int num, locale &loc )
{
   char **result = (char **)_lfind_s( &key, array,
                      &num, sizeof(char *), compare, &loc );
   if( result )
      printf( "%s found\n", *result );
   else
      printf( "%s not found\n", key );
}

int main( )
{
   find_it( "weit", array1, sizeof(array1)/sizeof(char*), locale(GERMAN_LOCALE) );
}
```

```Output
weit found
```

## <a name="see-also"></a>関連項目

[検索と並べ替え](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
