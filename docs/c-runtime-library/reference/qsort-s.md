---
title: qsort_s
ms.date: 11/04/2016
api_name:
- qsort_s
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
- qsort_s
helpviewer_keywords:
- arrays [C++], sorting
- quick-sort algorithm
- qsort_s function
- sorting arrays
ms.assetid: 6ee817b0-4408-4355-a5d4-6605e419ab91
ms.openlocfilehash: aa911dbf2990bb976341a19cdb1eb88707c90e79
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949754"
---
# <a name="qsort_s"></a>qsort_s

クイック ソートを実行します。 「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [qsort](qsort.md) です。

## <a name="syntax"></a>構文

```C
void qsort_s(
   void *base,
   size_t num,
   size_t width,
   int (__cdecl *compare )(void *, const void *, const void *),
   void * context
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
比較関数。 最初の引数は*コンテキスト*ポインターです。 2番目の引数は、検索用の*キー*へのポインターです。 3番目の引数は、*キー*と比較する配列要素へのポインターです。

*context*<br/>
コンテキストへのポインター。*比較*ルーチンがアクセスする必要がある任意のオブジェクトを指定できます。

## <a name="remarks"></a>Remarks

**Qsort_s**関数は、*数値*要素の配列 (それぞれの*幅*バイト) を並べ替えるクイックソートアルゴリズムを実装します。 引数*base*は、並べ替えられる配列のベースへのポインターです。 **qsort_s**は、並べ替えられた要素でこの配列を上書きします。 引数*compare*は、2つの配列要素を比較し、それらの関係を指定する値を返すユーザー指定のルーチンへのポインターです。 **qsort_s**は、並べ替え中に*比較*ルーチンを1回または複数回呼び出し、各呼び出しで2つの配列要素へのポインターを渡します。

```C
compare( context, (void *) & elem1, (void *) & elem2 );
```

ルーチンは、要素を比較し、次の値のいずれかを返す必要があります。

|戻り値|説明|
|------------------|-----------------|
|< 0|**elem1**未満**elem2**|
|0|**elem2**に相当する**elem1**|
|> 0|**elem1** **elem2**より大きい|

配列は、比較関数による定義に従って、昇順で並べ替えられます。 配列を降順で並べ替えるには、比較関数の "より大きい" と "より小さい" の意味を入れ替えます。

この関数に無効なパラメーターが渡されると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、関数はを返し、 **errno**は**EINVAL**に設定されます。 詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

### <a name="error-conditions"></a>エラー条件

|key|base|compare|num|幅|errno|
|---------|----------|-------------|---------|-----------|-----------|
|**NULL**|任意|任意|任意|任意|**EINVAL**|
|任意|**NULL**|任意|!= 0|任意|**EINVAL**|
|任意|任意|任意|任意|<= 0|**EINVAL**|
|任意|任意|**NULL**|任意|任意|**EINVAL**|

**qsort_s**の動作は**qsort**と同じですが、*コンテキスト*パラメーターがあり、 **errno**を設定します。 比較関数は、*コンテキスト*パラメーターを渡すことにより、オブジェクトポインターを使用して、オブジェクトの機能や、要素ポインターを介してアクセスできないその他の情報にアクセスできます。 *Context パラメーターを*追加することにより、 **qsort_s**の安全性が向上します。これは、*比較*関数で共有情報を使用できるようにするために静的変数を使用することによって導入された再入バグを回避するために*コンテキスト*を使用できるためです。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**qsort_s**|\<stdlib.h> および \<search.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

**ライブラリ**すべてのバージョンの[CRT ライブラリ機能](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>例

次の例では、 **qsort_s**関数で*context*パラメーターを使用する方法を示します。 *コンテキスト*パラメーターを使用すると、スレッドセーフな並べ替えを簡単に実行できます。 スレッドセーフを確保するために同期する必要がある静的変数を使用する代わりに、並べ替えごとに異なる*コンテキスト*パラメーターを渡します。 この例では、locale オブジェクトが*コンテキスト*パラメーターとして使用されています。

```cpp
// crt_qsort_s.cpp
// compile with: /EHsc /MT
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
// so \x00e1 is the German Sharp S in that codepage and \x00a4
// is the n tilde.

char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };
char *array2[] = { "Espa\x00a4ol", "Espa\x00a4" "a", "espantado" };
char *array3[] = { "table", "tableux", "tablet" };

#define GERMAN_LOCALE "German_Germany.850"
#define SPANISH_LOCALE "Spanish_Spain.850"
#define ENGLISH_LOCALE "English_US.850"

#endif

#ifdef CODEPAGE_1252
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df
   // for the German Sharp S and \x001f for the n tilde.
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",
                   "weit" };
char *array2[] = { "Espa\x00f1ol", "Espa\x00f1" "a", "espantado" };
char *array3[] = { "table", "tableux", "tablet" };

#define GERMAN_LOCALE "German_Germany.1252"
#define SPANISH_LOCALE "Spanish_Spain.1252"
#define ENGLISH_LOCALE "English_US.1252"

#endif

// The context parameter lets you create a more generic compare.
// Without this parameter, you would have stored the locale in a
// static variable, thus making sort_array vulnerable to thread
// conflicts.

int compare( void *pvlocale, const void *str1, const void *str2)
{
    char s1[256];
    char s2[256];
    strcpy_s(s1, 256, *(char**)str1);
    strcpy_s(s2, 256, *(char**)str2);
    _strlwr_s( s1, sizeof(s1) );
    _strlwr_s( s2, sizeof(s2) );

    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));

    return use_facet< collate<char> >(loc).compare(s1,
       &s1[strlen(s1)], s2, &s2[strlen(s2)]);

}

void sort_array(char *array[], int num, locale &loc)
{
    qsort_s(array, num, sizeof(char*), compare, &loc);
}

void print_array(char *a[], int c)
{
   for (int i = 0; i < c; i++)
      printf("%s ", a[i]);
   printf("\n");

}

void sort_german(void * Dummy)
{
   sort_array(array1, 6, locale(GERMAN_LOCALE));
}

void sort_spanish(void * Dummy)
{
   sort_array(array2, 3, locale(SPANISH_LOCALE));
}

void sort_english(void * Dummy)
{
   sort_array(array3, 3, locale(ENGLISH_LOCALE));
}

int main( )
{
   int i;
   HANDLE threads[3];

   printf("Unsorted input:\n");
   print_array(array1, 6);
   print_array(array2, 3);
   print_array(array3, 3);

   // Create several threads that perform sorts in different
   // languages at the same time.

   threads[0] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_german , 0, NULL));
   threads[1] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_spanish, 0, NULL));
   threads[2] = reinterpret_cast<HANDLE>(
                 _beginthread( sort_english, 0, NULL));

   for (i = 0; i < 3; i++)
   {
      if (threads[i] == reinterpret_cast<HANDLE>(-1))
      {
         printf("Error creating threads.\n");
         exit(1);
      }
   }

   // Wait until all threads have terminated.
   WaitForMultipleObjects(3, threads, true, INFINITE);

   printf("Sorted output: \n");

   print_array(array1, 6);
   print_array(array2, 3);
   print_array(array3, 3);
}
```

### <a name="sample-output"></a>出力例

```Output
Unsorted input:
weiß weis annehmen weizen Zeit weit
Español España espantado
table tableux tablet
Sorted output:
annehmen weiß weis weit weizen Zeit
España Español espantado
table tablet tableux
```

## <a name="see-also"></a>関連項目

[検索と並べ替え](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort](qsort.md)<br/>
