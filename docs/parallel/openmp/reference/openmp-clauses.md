---
title: OpenMP 句
ms.date: 03/20/2019
f1_keywords:
- OpenMP clauses
- copyin
- copyprivate
- default
- firstprivate
- if
- lastprivate
- nowait
- num_threads
- ordered
- private
- reduction
- schedule
- shared
helpviewer_keywords:
- OpenMP clauses
- copyin OpenMP clause
- copyprivate OpenMP clause
- default OpenMP clause
- defaults, OpenMP clause
- firstprivate OpenMP clause
- if OpenMP clause
- lastprivate OpenMP clause
- nowait OpenMP clause
- num_threads OpenMP clause
- ordered OpenMP clause
- private OpenMP clause
- reduction OpenMP clause
- schedule OpenMP clause
- shared OpenMP clause
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
ms.openlocfilehash: 92bd73fda5891b0bbf7393d1a7fda573d0f00263
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142510"
---
# <a name="openmp-clauses"></a>OpenMP 句

OpenMP API で使用される句へのリンクを提供します。

Visual C++では、次の OpenMP 句がサポートされています。

一般的な属性の場合:

|句|説明|
|------|-----------|
|[if](#if-openmp)|ループを並列で実行するか、直列で実行するかを指定します。|
|[num_threads](#num-threads)|スレッドチーム内のスレッドの数を設定します。|
|[番号](#ordered-openmp-clauses)|[順次](openmp-directives.md#ordered-openmp-directives)ディレクティブをループで使用する場合は、parallel [for](openmp-directives.md#for-openmp)ステートメントで必要です。|
|[schedule](#schedule)|[For](openmp-directives.md#for-openmp)ディレクティブに適用されます。|
|[nowait](#nowait)|ディレクティブで暗黙的にバリアをオーバーライドします。|

データ共有属性の場合:

|句|説明|
|------|-----------|
|[private](#private-openmp)|各スレッドが変数の独自のインスタンスを持つ必要があることを指定します。|
|[firstprivate](#firstprivate)|各スレッドが変数の独自のインスタンスを持つ必要があり、変数の値を使用して変数を初期化する必要があることを指定します。これは、parallel コンストラクトの前に存在するためです。|
|[lastprivate](#lastprivate)|外側のコンテキストの変数のバージョンが、最後の反復処理 (for ループコンストラクト) または最後のセクション (#pragma セクション) を実行するいずれかのスレッドのプライベートバージョンと等しいように設定されていることを指定します。|
|[共用](#shared-openmp)|1つ以上の変数をすべてのスレッド間で共有することを指定します。|
|[既定値](#default-openmp)|並行領域内の対象範囲外の変数の動作を指定します。|
|[reduction](#reduction)|各スレッドに対してプライベートである1つ以上の変数が、並列領域の最後のリダクション操作の対象であることを指定します。|
|[copyin](#copyin)|スレッドが[threadprivate](openmp-directives.md#threadprivate)変数のマスタースレッドの値にアクセスできるようにします。|
|[copyprivate](#copyprivate)|1つ以上の変数をすべてのスレッド間で共有することを指定します。|

## <a name="copyin"></a>copyin

スレッドが[threadprivate](openmp-directives.md#threadprivate)変数のマスタースレッドの値にアクセスできるようにします。

```cpp
copyin(var)
```

### <a name="parameters"></a>パラメーター

*var*<br/>
Parallel コンストラクトの前に存在するため、マスタースレッドで変数の値を使用して初期化される `threadprivate` 変数。

### <a name="remarks"></a>コメント

`copyin` は、次のディレクティブに適用されます。

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

詳細については、「 [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md)」を参照してください。

### <a name="example"></a>例

`copyin`の使用例については、「 [threadprivate](openmp-directives.md#threadprivate) 」を参照してください。

## <a name="copyprivate"></a>copyprivate

1つ以上の変数をすべてのスレッド間で共有することを指定します。

```cpp
copyprivate(var)
```

### <a name="parameters"></a>パラメーター

*var*<br/>
共有する1つ以上の変数。 複数の変数を指定する場合は、変数名をコンマで区切ります。

### <a name="remarks"></a>コメント

`copyprivate` は、[単一](openmp-directives.md#single)のディレクティブに適用されます。

詳細については、「 [2.7.2.8 copyprivate](../../../parallel/openmp/2-7-2-8-copyprivate.md)」を参照してください。

### <a name="example"></a>例

```cpp
// omp_copyprivate.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

float x, y, fGlobal = 1.0;
#pragma omp threadprivate(x, y)

float get_float() {
   fGlobal += 0.001;
   return fGlobal;
}

void use_float(float f, int t) {
   printf_s("Value = %f, thread = %d\n", f, t);
}

void CopyPrivate(float a, float b) {
   #pragma omp single copyprivate(a, b, x, y)
   {
      a = get_float();
      b = get_float();
      x = get_float();
      y = get_float();
    }

   use_float(a, omp_get_thread_num());
   use_float(b, omp_get_thread_num());
   use_float(x, omp_get_thread_num());
   use_float(y, omp_get_thread_num());
}

int main() {
   float a = 9.99, b = 123.456;

   printf_s("call CopyPrivate from a single thread\n");
   CopyPrivate(9.99, 123.456);

   printf_s("call CopyPrivate from a parallel region\n");
   #pragma omp parallel
   {
      CopyPrivate(a, b);
   }
}
```

```Output
call CopyPrivate from a single thread
Value = 1.001000, thread = 0
Value = 1.002000, thread = 0
Value = 1.003000, thread = 0
Value = 1.004000, thread = 0
call CopyPrivate from a parallel region
Value = 1.005000, thread = 0
Value = 1.005000, thread = 1
Value = 1.006000, thread = 0
Value = 1.006000, thread = 1
Value = 1.007000, thread = 0
Value = 1.007000, thread = 1
Value = 1.008000, thread = 0
Value = 1.008000, thread = 1
```

## <a name="default-openmp"></a>標準

並行領域内の対象範囲外の変数の動作を指定します。

```cpp
default(shared | none)
```

### <a name="remarks"></a>コメント

`shared`は、`default` 句が指定されていない場合に有効です。これは、並列領域内の任意の変数が、 [shared](#shared-openmp)句で指定されているかのように処理されることを意味します。 `none` は、 [private](#private-openmp)、 [shared](#shared-openmp)、 [reduction](#reduction)、 [firstprivate](#firstprivate)、または[a.6 lastprivate](#lastprivate)句でスコープされていない並行領域で使用される変数があると、コンパイラエラーが発生することを意味します。

`default` は、次のディレクティブに適用されます。

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

詳細については、「 [2.7.2.5 default](../../../parallel/openmp/2-7-2-5-default.md)」を参照してください。

### <a name="example"></a>例

`default`の使用例については、「 [private](#private-openmp) 」を参照してください。

## <a name="firstprivate"></a>firstprivate

各スレッドが変数の独自のインスタンスを持つ必要があり、変数の値を使用して変数を初期化する必要があることを指定します。これは、parallel コンストラクトの前に存在するためです。

```cpp
firstprivate(var)
```

### <a name="parameters"></a>パラメーター

*var*<br/>
変数は、各スレッド内にインスタンスを持ち、変数の値を使用して初期化されます。これは、parallel コンストラクトの前に存在するためです。 複数の変数を指定する場合は、変数名をコンマで区切ります。

### <a name="remarks"></a>コメント

`firstprivate` は、次のディレクティブに適用されます。

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [sections](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

詳細については、「 [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md)」を参照してください。

### <a name="example"></a>例

`firstprivate`の使用例については、「 [private](#private-openmp)」の例を参照してください。

## <a name="if-openmp"></a>if (OpenMP)

ループを並列で実行するか、直列で実行するかを指定します。

```cpp
if(expression)
```

### <a name="parameters"></a>パラメーター

*式 (expression)*<br/>
True (0 以外) に評価された場合に並列領域内のコードが並列実行される整数式。 式が false (ゼロ) に評価されると、並列領域は (1 つのスレッドによって) シリアルで実行されます。

### <a name="remarks"></a>コメント

`if` は、次のディレクティブに適用されます。

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

詳細については、「 [2.3 parallel コンストラクト](../../../parallel/openmp/2-3-parallel-construct.md)」を参照してください。

### <a name="example"></a>例

```cpp
// omp_if.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void test(int val)
{
    #pragma omp parallel if (val)
    if (omp_in_parallel())
    {
        #pragma omp single
        printf_s("val = %d, parallelized with %d threads\n",
                 val, omp_get_num_threads());
    }
    else
    {
        printf_s("val = %d, serialized\n", val);
    }
}

int main( )
{
    omp_set_num_threads(2);
    test(0);
    test(2);
}
```

```Output
val = 0, serialized
val = 2, parallelized with 2 threads
```

## <a name="lastprivate"></a>a.6 lastprivate

外側のコンテキストの変数のバージョンが、最後の反復処理 (for ループコンストラクト) または最後のセクション (#pragma セクション) を実行するいずれかのスレッドのプライベートバージョンと等しいように設定されていることを指定します。

```cpp
lastprivate(var)
```

### <a name="parameters"></a>パラメーター

*var*<br/>
いずれかのスレッドのプライベートバージョンと同じように設定されている変数は、最後の反復処理 (for ループコンストラクト) または最後のセクション (#pragma セクション) を実行します。

### <a name="remarks"></a>コメント

`lastprivate` は、次のディレクティブに適用されます。

- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

詳細については、「 [2.7.2.3 a.6 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md)」を参照してください。

### <a name="example"></a>例

`lastprivate` 句の使用例については、「[スケジュール](#schedule)」を参照してください。

## <a name="nowait"></a>nowait

ディレクティブで暗黙的にバリアをオーバーライドします。

```cpp
nowait
```

### <a name="remarks"></a>コメント

`nowait` は、次のディレクティブに適用されます。

- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

詳細については、「 [2.4.1 for construct](../../../parallel/openmp/2-4-1-for-construct.md)、 [2.4.2 sections コンストラクト](../../../parallel/openmp/2-4-2-sections-construct.md)、および[2.4.3 single construct](../../../parallel/openmp/2-4-3-single-construct.md)」を参照してください。

### <a name="example"></a>例

```cpp
// omp_nowait.cpp
// compile with: /openmp /c
#include <stdio.h>

#define SIZE 5

void test(int *a, int *b, int *c, int size)
{
    int i;
    #pragma omp parallel
    {
        #pragma omp for nowait
        for (i = 0; i < size; i++)
            b[i] = a[i] * a[i];

        #pragma omp for nowait
        for (i = 0; i < size; i++)
            c[i] = a[i]/2;
    }
}

int main( )
{
    int a[SIZE], b[SIZE], c[SIZE];
    int i;

    for (i=0; i<SIZE; i++)
        a[i] = i;

    test(a,b,c, SIZE);

    for (i=0; i<SIZE; i++)
        printf_s("%d, %d, %d\n", a[i], b[i], c[i]);
}
```

```Output
0, 0, 0
1, 1, 0
2, 4, 1
3, 9, 1
4, 16, 2
```

## <a name="num-threads"></a>num_threads

スレッドチーム内のスレッドの数を設定します。

```cpp
num_threads(num)
```

### <a name="parameters"></a>パラメーター

*num*<br/>
スレッド数

### <a name="remarks"></a>コメント

`num_threads` 句には、 [omp_set_num_threads](openmp-functions.md#omp-set-num-threads)関数と同じ機能があります。

`num_threads` は、次のディレクティブに適用されます。

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

詳細については、「 [2.3 parallel コンストラクト](../../../parallel/openmp/2-3-parallel-construct.md)」を参照してください。

### <a name="example"></a>例

`num_threads` 句の使用例については、「 [parallel](openmp-directives.md#parallel) 」を参照してください。

## <a name="ordered-openmp-clauses"></a>番号

[順次](openmp-directives.md#ordered-openmp-directives)ディレクティブをループで使用する場合は、parallel [for](openmp-directives.md#for-openmp)ステートメントで必要です。

```cpp
ordered
```

### <a name="remarks"></a>コメント

`ordered` は[for](openmp-directives.md#for-openmp)ディレクティブに適用されます。

詳細については、「 [2.4.1 for コンストラクト](../../../parallel/openmp/2-4-1-for-construct.md)」を参照してください。

### <a name="example"></a>例

`ordered` 句の使用例については、「 [ordered](openmp-directives.md#ordered-openmp-directives) 」を参照してください。

## <a name="private-openmp"></a>プライバシー

各スレッドが変数の独自のインスタンスを持つ必要があることを指定します。

```cpp
private(var)
```

### <a name="parameters"></a>パラメーター

*var*<br/>
各スレッドにインスタンスを持つ変数。

### <a name="remarks"></a>コメント

`private` は、次のディレクティブに適用されます。

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [sections](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

詳細については、「 [2.7.2.1 private](../../../parallel/openmp/2-7-2-1-private.md)」を参照してください。

### <a name="example"></a>例

```c
// openmp_private.c
// compile with: /openmp
#include <windows.h>
#include <assert.h>
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define SLEEP_THREAD 1
#define NUM_LOOPS 2

enum Types {
   ThreadPrivate,
   Private,
   FirstPrivate,
   LastPrivate,
   Shared,
   MAX_TYPES
};

int nSave[NUM_THREADS][MAX_TYPES][NUM_LOOPS] = {{0}};
int nThreadPrivate;

#pragma omp threadprivate(nThreadPrivate)
#pragma warning(disable:4700)

int main() {
   int nPrivate = NUM_THREADS;
   int nFirstPrivate = NUM_THREADS;
   int nLastPrivate = NUM_THREADS;
   int nShared = NUM_THREADS;
   int nRet = 0;
   int i;
   int j;
   int nLoop = 0;

   nThreadPrivate = NUM_THREADS;
   printf_s("These are the variables before entry "
           "into the parallel region.\n");
   printf_s("nThreadPrivate = %d\n", nThreadPrivate);
   printf_s("      nPrivate = %d\n", nPrivate);
   printf_s(" nFirstPrivate = %d\n", nFirstPrivate);
   printf_s("  nLastPrivate = %d\n", nLastPrivate);
   printf_s("       nShared = %d\n\n", nShared);
   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel copyin(nThreadPrivate) private(nPrivate) shared(nShared) firstprivate(nFirstPrivate)
   {
      #pragma omp for schedule(static) lastprivate(nLastPrivate)
      for (i = 0 ; i < NUM_THREADS ; ++i) {
         for (j = 0 ; j < NUM_LOOPS ; ++j) {
            int nThread = omp_get_thread_num();
            assert(nThread < NUM_THREADS);

            if (nThread == SLEEP_THREAD)
               Sleep(100);
            nSave[nThread][ThreadPrivate][j] = nThreadPrivate;
            nSave[nThread][Private][j] = nPrivate;
            nSave[nThread][Shared][j] = nShared;
            nSave[nThread][FirstPrivate][j] = nFirstPrivate;
            nSave[nThread][LastPrivate][j] = nLastPrivate;
            nThreadPrivate = nThread;
            nPrivate = nThread;
            nShared = nThread;
            nLastPrivate = nThread;
            --nFirstPrivate;
         }
      }
   }

   for (i = 0 ; i < NUM_LOOPS ; ++i) {
      for (j = 0 ; j < NUM_THREADS ; ++j) {
         printf_s("These are the variables at entry of "
                  "loop %d of thread %d.\n", i + 1, j);
         printf_s("nThreadPrivate = %d\n",
                  nSave[j][ThreadPrivate][i]);
         printf_s("      nPrivate = %d\n",
                  nSave[j][Private][i]);
         printf_s(" nFirstPrivate = %d\n",
                  nSave[j][FirstPrivate][i]);
         printf_s("  nLastPrivate = %d\n",
                  nSave[j][LastPrivate][i]);
         printf_s("       nShared = %d\n\n",
                  nSave[j][Shared][i]);
      }
   }

   printf_s("These are the variables after exit from "
            "the parallel region.\n");
   printf_s("nThreadPrivate = %d (The last value in the "
            "master thread)\n", nThreadPrivate);
   printf_s("      nPrivate = %d (The value prior to "
            "entering parallel region)\n", nPrivate);
   printf_s(" nFirstPrivate = %d (The value prior to "
            "entering parallel region)\n", nFirstPrivate);
   printf_s("  nLastPrivate = %d (The value from the "
            "last iteration of the loop)\n", nLastPrivate);
   printf_s("       nShared = %d (The value assigned, "
            "from the delayed thread, %d)\n\n",
            nShared, SLEEP_THREAD);
}
```

```Output
These are the variables before entry into the parallel region.
nThreadPrivate = 4
      nPrivate = 4
nFirstPrivate = 4
  nLastPrivate = 4
       nShared = 4

These are the variables at entry of loop 1 of thread 0.
nThreadPrivate = 4
      nPrivate = 1310720
nFirstPrivate = 4
  nLastPrivate = 1245104
       nShared = 3

These are the variables at entry of loop 1 of thread 1.
nThreadPrivate = 4
      nPrivate = 4488
nFirstPrivate = 4
  nLastPrivate = 19748
       nShared = 0

These are the variables at entry of loop 1 of thread 2.
nThreadPrivate = 4
      nPrivate = -132514848
nFirstPrivate = 4
  nLastPrivate = -513199792
       nShared = 4

These are the variables at entry of loop 1 of thread 3.
nThreadPrivate = 4
      nPrivate = 1206
nFirstPrivate = 4
  nLastPrivate = 1204
       nShared = 2

These are the variables at entry of loop 2 of thread 0.
nThreadPrivate = 0
      nPrivate = 0
nFirstPrivate = 3
  nLastPrivate = 0
       nShared = 0

These are the variables at entry of loop 2 of thread 1.
nThreadPrivate = 1
      nPrivate = 1
nFirstPrivate = 3
  nLastPrivate = 1
       nShared = 1

These are the variables at entry of loop 2 of thread 2.
nThreadPrivate = 2
      nPrivate = 2
nFirstPrivate = 3
  nLastPrivate = 2
       nShared = 2

These are the variables at entry of loop 2 of thread 3.
nThreadPrivate = 3
      nPrivate = 3
nFirstPrivate = 3
  nLastPrivate = 3
       nShared = 3

These are the variables after exit from the parallel region.
nThreadPrivate = 0 (The last value in the master thread)
      nPrivate = 4 (The value prior to entering parallel region)
nFirstPrivate = 4 (The value prior to entering parallel region)
  nLastPrivate = 3 (The value from the last iteration of the loop)
       nShared = 1 (The value assigned, from the delayed thread, 1)
```

## <a name="reduction"></a>reduction

各スレッドに対してプライベートである1つ以上の変数が、並列領域の最後のリダクション操作の対象であることを指定します。

```cpp
reduction(operation:var)
```

### <a name="parameters"></a>パラメーター

*operation*<br/>
並列領域の最後にある変数*var*に対して操作を実行する演算子。

*var*<br/>
スカラーを減らすために使用する1つ以上の変数。 複数の変数を指定する場合は、変数名をコンマで区切ります。

### <a name="remarks"></a>コメント

`reduction` は、次のディレクティブに適用されます。

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

詳細については、「 [2.7.2.6 reduction](../../../parallel/openmp/2-7-2-6-reduction.md)」を参照してください。

### <a name="example"></a>例

```cpp
// omp_reduction.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define SUM_START   1
#define SUM_END     10
#define FUNC_RETS   {1, 1, 1, 1, 1}

int bRets[5] = FUNC_RETS;
int nSumCalc = ((SUM_START + SUM_END) * (SUM_END - SUM_START + 1)) / 2;

int func1( ) {return bRets[0];}
int func2( ) {return bRets[1];}
int func3( ) {return bRets[2];}
int func4( ) {return bRets[3];}
int func5( ) {return bRets[4];}

int main( )
{
    int nRet = 0,
        nCount = 0,
        nSum = 0,
        i,
        bSucceed = 1;

    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel reduction(+ : nCount)
    {
        nCount += 1;

        #pragma omp for reduction(+ : nSum)
        for (i = SUM_START ; i <= SUM_END ; ++i)
            nSum += i;

        #pragma omp sections reduction(&& : bSucceed)
        {
            #pragma omp section
            {
                bSucceed = bSucceed && func1( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func2( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func3( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func4( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func5( );
            }
        }
    }

    printf_s("The parallel section was executed %d times "
             "in parallel.\n", nCount);
    printf_s("The sum of the consecutive integers from "
             "%d to %d, is %d\n", 1, 10, nSum);

    if (bSucceed)
        printf_s("All of the functions, func1 through "
                 "func5 succeeded!\n");
    else
        printf_s("One or more of the functions, func1 "
                 "through func5 failed!\n");

    if (nCount != NUM_THREADS)
    {
        printf_s("ERROR: For %d threads, %d were counted!\n",
                 NUM_THREADS, nCount);
        nRet |= 0x1;
   }

    if (nSum != nSumCalc)
    {
        printf_s("ERROR: The sum of %d through %d should be %d, "
                "but %d was reported!\n",
                SUM_START, SUM_END, nSumCalc, nSum);
        nRet |= 0x10;
    }

    if (bSucceed != (bRets[0] && bRets[1] &&
                     bRets[2] && bRets[3] && bRets[4]))
    {
        printf_s("ERROR: The sum of %d through %d should be %d, "
                 "but %d was reported!\n",
                 SUM_START, SUM_END, nSumCalc, nSum);
        nRet |= 0x100;
    }
}
```

```Output
The parallel section was executed 4 times in parallel.
The sum of the consecutive integers from 1 to 10, is 55
All of the functions, func1 through func5 succeeded!
```

## <a name="schedule"></a>予定

[For](openmp-directives.md#for-openmp)ディレクティブに適用されます。

```cpp
schedule(type[,size])
```

### <a name="parameters"></a>パラメーター

*type*<br/>
スケジュールの種類 (`dynamic`、`guided`、`runtime`、または `static`)。

*size*<br/>
Optionalイテレーションのサイズを指定します。 *サイズ*は整数でなければなりません。 *型*が `runtime`の場合は無効です。

### <a name="remarks"></a>コメント

詳細については、「 [2.4.1 for コンストラクト](../../../parallel/openmp/2-4-1-for-construct.md)」を参照してください。

### <a name="example"></a>例

```cpp
// omp_schedule.cpp
// compile with: /openmp
#include <windows.h>
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define STATIC_CHUNK 5
#define DYNAMIC_CHUNK 5
#define NUM_LOOPS 20
#define SLEEP_EVERY_N 3

int main( )
{
    int nStatic1[NUM_LOOPS],
        nStaticN[NUM_LOOPS];
    int nDynamic1[NUM_LOOPS],
        nDynamicN[NUM_LOOPS];
    int nGuided[NUM_LOOPS];

    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel
    {
        #pragma omp for schedule(static, 1)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nStatic1[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(static, STATIC_CHUNK)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nStaticN[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(dynamic, 1)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nDynamic1[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(dynamic, DYNAMIC_CHUNK)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nDynamicN[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(guided)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nGuided[i] = omp_get_thread_num( );
        }
    }

    printf_s("------------------------------------------------\n");
    printf_s("| static | static | dynamic | dynamic | guided |\n");
    printf_s("|    1   |    %d   |    1    |    %d    |        |\n",
             STATIC_CHUNK, DYNAMIC_CHUNK);
    printf_s("------------------------------------------------\n");

    for (int i=0; i<NUM_LOOPS; ++i)
    {
        printf_s("|    %d   |    %d   |    %d    |    %d    |"
                 "    %d   |\n",
                 nStatic1[i], nStaticN[i],
                 nDynamic1[i], nDynamicN[i], nGuided[i]);
    }

    printf_s("------------------------------------------------\n");
}
```

```Output
------------------------------------------------
| static | static | dynamic | dynamic | guided |
|    1   |    5   |    1    |    5    |        |
------------------------------------------------
|    0   |    0   |    0    |    2    |    1   |
|    1   |    0   |    3    |    2    |    1   |
|    2   |    0   |    3    |    2    |    1   |
|    3   |    0   |    3    |    2    |    1   |
|    0   |    0   |    2    |    2    |    1   |
|    1   |    1   |    2    |    3    |    3   |
|    2   |    1   |    2    |    3    |    3   |
|    3   |    1   |    0    |    3    |    3   |
|    0   |    1   |    0    |    3    |    3   |
|    1   |    1   |    0    |    3    |    2   |
|    2   |    2   |    1    |    0    |    2   |
|    3   |    2   |    1    |    0    |    2   |
|    0   |    2   |    1    |    0    |    3   |
|    1   |    2   |    2    |    0    |    3   |
|    2   |    2   |    2    |    0    |    0   |
|    3   |    3   |    2    |    1    |    0   |
|    0   |    3   |    3    |    1    |    1   |
|    1   |    3   |    3    |    1    |    1   |
|    2   |    3   |    3    |    1    |    1   |
|    3   |    3   |    0    |    1    |    3   |
------------------------------------------------
```

## <a name="shared-openmp"></a>共用

1つ以上の変数をすべてのスレッド間で共有することを指定します。

```cpp
shared(var)
```

### <a name="parameters"></a>パラメーター

*var*<br/>
共有する1つ以上の変数。 複数の変数を指定する場合は、変数名をコンマで区切ります。

### <a name="remarks"></a>コメント

スレッド間で変数を共有するもう1つの方法は、 [copyprivate](#copyprivate)句を使用することです。

`shared` は、次のディレクティブに適用されます。

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [sections](openmp-directives.md#sections-openmp)

詳細については、「 [2.7.2.4 shared](../../../parallel/openmp/2-7-2-4-shared.md)」を参照してください。

### <a name="example"></a>例

`shared`の使用例については、「 [private](#private-openmp) 」を参照してください。
