---
title: 'A:  使用例'
ms.date: 01/18/2019
ms.assetid: c0f6192f-a205-449b-b84c-cb30dbcc8b8f
ms.openlocfilehash: 061490d34829175bfbdcd84d6208aa396bb19671
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087302"
---
# <a name="a-examples"></a>A:  使用例

このドキュメントで定義された構成要素の例を次に示します。 ディレクティブに続くステートメントは、必要な場合にのみ複合および非複合ステートメントがそれに先行するディレクティブからインデントされます。

## <a name="a1-a-simple-loop-in-parallel"></a>A.1 する単純なループを並列で

次の例を使用してループを並列化する方法を示します、[の並列](2-directives.md#251-parallel-for-construct)ディレクティブ。 ループの反復変数は既定では、プライベートなは、明示的に private 句で指定する必要はありませんが。

```cpp
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```

## <a name="a2-conditional-compilation"></a>A.2 条件付きコンパイル

次の例では、OpenMP マクロを使用して条件付きコンパイルの使用方法を示します[_OPENMP](2-directives.md#22-conditional-compilation)します。 OpenMP のコンパイルと、`_OPENMP`マクロが定義されています。

```cpp
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

定義済みプリプロセッサ演算子には、1 つのディレクティブでテストする 1 つ以上のマクロができます。

```cpp
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

## <a name="a3-parallel-regions"></a>A.3 並行領域

[並列](2-directives.md#23-parallel-construct)ディレクティブは、粒度が粗い並列プログラムで使用できます。 次の例では、並行領域内の各スレッドはグローバル配列のどの部分を決定`x`、操作スレッドの数に基づきます。

```cpp
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```

## <a name="a4-the-nowait-clause"></a>A.4 nowait 句

使用することが並行領域内で多数の独立したループがある場合、 [nowait](2-directives.md#241-for-construct)句の末尾にある暗黙のバリアを回避するために、`for`ディレクティブを次のとおりです。

```cpp
#pragma omp parallel
{
    #pragma omp for nowait
        for (i=1; i<n; i++)
             b[i] = (a[i] + a[i-1]) / 2.0;
    #pragma omp for nowait
        for (i=0; i<m; i++)
            y[i] = sqrt(z[i]);
}
```

## <a name="a5-the-critical-directive"></a>A.5 critical ディレクティブ

次の例では、いくつか含まれています[重要な](2-directives.md#262-critical-construct)ディレクティブ。 この例では、タスクがキューから削除され作業キューのモデルを使用します。 多数のスレッドが同じタスクをキューからの保護、デキュー操作がである必要があります、`critical`セクション。 によって保護されているため、この例では、2 つのキューは独立して、 `critical` 、異なる名前のディレクティブ*xaxis*と*yaxis*します。

```cpp
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```

## <a name="a6-the-lastprivate-clause"></a>A.6 lastprivate 句

適切な実行場合によっては、ループの最後の反復変数に割り当てられている値に依存します。 このようなプログラムへの引数としてこのようなすべての変数を一覧する必要があります、 [lastprivate](2-directives.md#2723-lastprivate)句の変数の値は、ループが順番に実行されるときと同じようにします。

```cpp
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

前の例の値で`i`並列領域の最後に等しい`n-1`シーケンシャル ケースのようにします。

## <a name="a7-the-reduction-clause"></a>A.7 reduction 句

次の例で、[削減](2-directives.md#2726-reduction)句。

```cpp
#pragma omp parallel for private(i) shared(x, y, n) \
                         reduction(+: a, b)
    for (i=0; i<n; i++) {
        a = a + x[i];
        b = b + y[i];
    }
```

## <a name="a8-parallel-sections"></a>A.8 並行セクション

次の例 (の[2.4.2 セクション](2-directives.md#242-sections-construct))、関数*xaxis*、 *yaxis*、および*zaxis*同時に実行することができます。 最初の`section`ディレクティブは省略可能です。  すべて`section`ディレクティブはの構文の範囲で表示する必要があります、`parallel sections`を構築します。

```cpp
#pragma omp parallel sections
{
    #pragma omp section
        xaxis();
    #pragma omp section
        yaxis();
    #pragma omp section
        zaxis();
}
```

## <a name="a9-single-directives"></a>A.9 Single ディレクティブ

次の例で、[単一](2-directives.md#243-single-construct)ディレクティブ。 例では、1 つのスレッドで (が発生した最初のスレッドは、通常、`single`ディレクティブ) 進行状況メッセージを出力します。 ユーザーでは、スレッドは実行には、どのような想定する必要があります加えないで、`single`セクション。 他のすべてのスレッドは、スキップ、`single`セクションし、バリアの最後で停止、`single`を構築します。 他のスレッドがスレッドの実行を待たずに進むことができるかどうか、 `single`  セクションで、`nowait`に句を指定できます、`single`ディレクティブ。

```cpp
#pragma omp parallel
{
    #pragma omp single
        printf_s("Beginning work1.\n");
    work1();
    #pragma omp single
        printf_s("Finishing work1.\n");
    #pragma omp single nowait
        printf_s("Finished work1 and beginning work2.\n");
    work2();
}
```

## <a name="a10-sequential-ordering"></a>A.10 順番のシーケンシャルな順序付け

[セクションでは順序付けられた](2-directives.md#266-ordered-construct)は並列で行われる処理からの出力を順番に配置するのに役立ちます。 次のプログラムは、順番にインデックスを印刷します。

```cpp
#pragma omp for ordered schedule(dynamic)
    for (i=lb; i<ub; i+=st)
        work(i);
void work(int k)
{
    #pragma omp ordered
        printf_s(" %d", k);
}
```

## <a name="a11-a-fixed-number-of-threads"></a>A.11 固定するスレッド数

一部のプログラムは正常に実行するスレッドの固定、事前の数に依存します。  スレッドの数を動的に調整の既定の設定は、実装定義であるために、このようなプログラムは、動的なスレッドの機能をオフにして、移植性を維持するには、明示的にスレッドの数を設定を選択できます。 次の例を使用してこれを行う方法を示しています[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)、および[omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function):。

```cpp
omp_set_dynamic(0);
omp_set_num_threads(16);
#pragma omp parallel shared(x, npoints) private(iam, ipoints)
{
    if (omp_get_num_threads() != 16)
      abort();
    iam = omp_get_thread_num();
    ipoints = npoints/16;
    do_by_16(x, iam, ipoints);
}
```

プログラムは、この例では 16 のスレッドによって実行される場合にのみ正しく実行します。 実装が 16 のスレッドをサポートしていない場合は、この例の動作は実装定義です。

並列領域を実行するスレッドの数は、動的なスレッドの設定に関係なく、並行領域の中に定数が維持されます。 動的なスレッド メカニズムでは、並列領域の開始時に使用するスレッドの数を決定し、リージョンの間維持します。

## <a name="a12-the-atomic-directive"></a>A.12 atomic ディレクティブ

次の例では、競合状態を回避できます (同時に更新する要素の*x*多数のスレッドによって) を使用して、[アトミック](2-directives.md#264-atomic-construct)ディレクティブ。

```cpp
#pragma omp parallel for shared(x, y, index, n)
    for (i=0; i<n; i++)
    {
        #pragma omp atomic
            x[index[i]] += work1(i);
        y[i] += work2(i);
    }
```

使用する利点、`atomic`ディレクティブがこの例では、並列的に実行する x の 2 つの異なる要素の更新できます。 場合、[重要な](2-directives.md#262-critical-construct)ディレクティブの代わりに、すべての更新の要素を使用*x*逐次的に (ただしではなく、順序を保証) に実行されます。

`atomic`ディレクティブが、C または C++ ステートメントの直後にのみ適用されます。  その結果、要素の*y*この例ではアトミックに更新されません。

## <a name="a13-a-flush-directive-with-a-list"></a>一覧で A.13 A flush ディレクティブ

次の例では、`flush`ディレクティブを特定のオブジェクトのスレッドのペア間のポイント ツー ポイントの同期。

```cpp
int   sync[NUMBER_OF_THREADS];
float work[NUMBER_OF_THREADS];
#pragma omp parallel private(iam,neighbor) shared(work,sync)
{
    iam = omp_get_thread_num();
    sync[iam] = 0;
    #pragma omp barrier

    // Do computation into my portion of work array
    work[iam] = ...;

    //  Announce that I am done with my work
    // The first flush ensures that my work is
    // made visible before sync.
    // The second flush ensures that sync is made visible.
    #pragma omp flush(work)
    sync[iam] = 1;
    #pragma omp flush(sync)

    // Wait for neighbor
    neighbor = (iam>0 ? iam : omp_get_num_threads()) - 1;
    while (sync[neighbor]==0)
    {
        #pragma omp flush(sync)
    }

    // Read neighbor's values of work array
    ... = work[neighbor];
}
```

## <a name="a14-a-flush-directive-without-a-list"></a>リストを伴わず a.14 A のない flush ディレクティブ

次の例では、(の[2.6.5 セクション](2-directives.md#265-flush-directive)) 共有に影響を受けるオブジェクトを区別する、`flush`ディレクティブは影響を受けない共有のオブジェクトの一覧がありません。

```cpp
// omp_flush_without_list.c
#include <omp.h>

int x, *p = &x;

void f1(int *q)
{
    *q = 1;
    #pragma omp flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

void f2(int *q)
{
    #pragma omp barrier
    *q = 2;

    #pragma omp barrier
    // a barrier implies a flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

int g(int n)
{
    int i = 1, j, sum = 0;
    *p = 1;

    #pragma omp parallel reduction(+: sum) num_threads(10)
    {
        f1(&j);
        // i, n and sum were not flushed
        //   because they were not accessible in f1
        // j was flushed because it was accessible
        sum += j;
        f2(&j);
        // i, n, and sum were not flushed
        //   because they were not accessible in f2
        // j was flushed because it was accessible
        sum += i + j + *p + n;
    }
    return sum;
}

int main()
{
}
```

## <a name="a15-the-number-of-threads-used"></a>A.15 使用されるスレッド数

次の正しくない例を検討してください (の[セクション 3.1.2 に従って](3-run-time-library-functions.md#312-omp_get_num_threads-function))。

```cpp
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

`omp_get_num_threads()`ためシリアル、コードのセクションでは 1 を返しますを呼び出す*np*常に前の例を 1 に等しくなります。 並列領域に配置されるスレッドの数を調べるには、並行領域内の呼び出しでなければなりません。

次の例では、スレッドの数のクエリを含めずにこのプログラムを書き換える方法を示します。

```cpp
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```

## <a name="a16-locks"></a>A.16 ロック

次の例 (の[セクション 3.2](3-run-time-library-functions.md#32-lock-functions))、ロック関数に引数は型である必要があります`omp_lock_t`、フラッシュされる前にする必要がないとします。  ロック関数では、最初の重要なセクションにエントリを待つ間アイドル状態であるが、2 番目のエントリの待機中に他の作業を行うスレッドをによりします。  `omp_set_lock`関数のブロックが、`omp_test_lock`関数で作業できるように`skip()`実行します。

```cpp
// omp_using_locks.c
// compile with: /openmp /c
#include <stdio.h>
#include <omp.h>

void work(int);
void skip(int);

int main() {
   omp_lock_t lck;
   int id;

   omp_init_lock(&lck);
   #pragma omp parallel shared(lck) private(id)
   {
      id = omp_get_thread_num();

      omp_set_lock(&lck);
      printf_s("My thread id is %d.\n", id);

      // only one thread at a time can execute this printf
      omp_unset_lock(&lck);

      while (! omp_test_lock(&lck)) {
         skip(id);   // we do not yet have the lock,
                     // so we must do something else
      }
      work(id);     // we now have the lock
                    // and can do the work
      omp_unset_lock(&lck);
   }
   omp_destroy_lock(&lck);
}
```

## <a name="a17-nestable-locks"></a>A.17 入れ子にできるロック

次の例では、(の[セクション 3.2](3-run-time-library-functions.md#32-lock-functions)) 入れ子にできるロックを使用して、そのメンバーのいずれかにおよび構造体全体に更新を同期する方法を示します。

```cpp
#include <omp.h>
typedef struct {int a,b; omp_nest_lock_t lck;} pair;

void incr_a(pair *p, int a)
{
    // Called only from incr_pair, no need to lock.
    p->a += a;
}

void incr_b(pair *p, int b)
{
    // Called both from incr_pair and elsewhere,
    // so need a nestable lock.

    omp_set_nest_lock(&p->lck);
    p->b += b;
    omp_unset_nest_lock(&p->lck);
}

void incr_pair(pair *p, int a, int b)
{
    omp_set_nest_lock(&p->lck);
    incr_a(p, a);
    incr_b(p, b);
    omp_unset_nest_lock(&p->lck);
}

void f(pair *p)
{
    extern int work1(), work2(), work3();
    #pragma omp parallel sections
    {
        #pragma omp section
            incr_pair(p, work1(), work2());
        #pragma omp section
            incr_b(p, work3());
    }
}
```

## <a name="a18-nested-for-directives"></a>ディレクティブの A.18 入れ子になった

次の例の`for`[ディレクティブの入れ子](2-directives.md#29-directive-nesting)が準拠しているため、内側と外側`for`ディレクティブは、並列の異なるリージョンにバインドします。

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
        {
            #pragma omp parallel shared(i, n)
            {
                #pragma omp for
                    for (j=0; j<n; j++)
                        work(i, j);
            }
        }
}
```

次の例のバリエーションが準拠してもです。

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
            work1(i, n);
}

void work1(int i, int n)
{
    int j;
    #pragma omp parallel default(shared)
    {
        #pragma omp for
            for (j=0; j<n; j++)
                work2(i, j);
    }
    return;
}
```

## <a name="a19-examples-showing-incorrect-nesting-of-work-sharing-directives"></a>作業の共有の正しくない入れ子 A.19 例ディレクティブ

このセクションの例を示しています、[ディレクティブの入れ子](2-directives.md#29-directive-nesting)規則。

次の例が準拠していないため、内側と外側`for`ディレクティブは入れ子になったし、同じバインド`parallel`ディレクティブ。

```cpp
void wrong1(int n)
{
  #pragma omp parallel default(shared)
  {
      int i, j;
      #pragma omp for
      for (i=0; i<n; i++) {
          #pragma omp for
              for (j=0; j<n; j++)
                 work(i, j);
     }
   }
}
```

前の例の次の動的に入れ子になったバージョンに準拠していないもです。

```cpp
void wrong2(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++)
        work1(i, n);
  }
}

void work1(int i, int n)
{
  int j;
  #pragma omp for
    for (j=0; j<n; j++)
      work2(i, j);
}
```

次の例が準拠していないため、`for`と`single`ディレクティブは入れ子になっているし、同じ並列領域にバインドします。

```cpp
void wrong3(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        #pragma omp single
          work(i);
      }
  }
}
```

次の例が準拠していないため、`barrier`ディレクティブ内で、`for`デッドロックが発生することができます。

```cpp
void wrong4(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        work1(i);
        #pragma omp barrier
        work2(i);
      }
  }
}
```

次の例が準拠していないため、`barrier`デッドロック、一度に 1 つのスレッドがクリティカル セクションに入力できるという事実が原因になります。

```cpp
void wrong5()
{
  #pragma omp parallel
  {
    #pragma omp critical
    {
       work1();
       #pragma omp barrier
       work2();
    }
  }
}
```

次の例が準拠していないため、 `barrier` 1 つのスレッドが実行されるという事実のデッドロックの結果、`single`セクション。

```cpp
void wrong6()
{
  #pragma omp parallel
  {
    setup();
    #pragma omp single
    {
      work1();
      #pragma omp barrier
      work2();
    }
    finish();
  }
}
```

## <a name="a20-bind-barrier-directives"></a>A.20 バインド barrier ディレクティブ

ディレクティブのバインディング ルールの呼び出しを`barrier`最も近い外側にバインドするディレクティブ`parallel`ディレクティブ。 ディレクティブのバインディングの詳細については、次を参照してください。[セクション 2.8](2-directives.md#28-directive-binding)します。

次の例からの呼び出しで*メイン*に*sub2*が準拠しているため、 `barrier` (で*sub3*) で並列領域にバインドします*sub2*. 呼び出しから*メイン*に*sub1*が準拠しているため、`barrier`サブルーチン内での並列領域にバインドします*sub2*。  呼び出しから*メイン*に*sub3*が準拠しているため、`barrier`並列の任意のリージョンにはバインドされません、無視されます。 また、`barrier`のみ、チームの外側の並列領域でスレッドとで作成されたすべてのスレッドを同期*sub1*します。

```cpp
int main()
{
    sub1(2);
    sub2(2);
    sub3(2);
}

void sub1(int n)
{
    int i;
    #pragma omp parallel private(i) shared(n)
    {
        #pragma omp for
        for (i=0; i<n; i++)
            sub2(i);
    }
}

void sub2(int k)
{
     #pragma omp parallel shared(k)
     sub3(k);
}

void sub3(int n)
{
    work(n);
    #pragma omp barrier
    work(n);
}
```

## <a name="a21-scope-variables-with-the-private-clause"></a>A.21 private 句のスコープ変数

値`i`と`j`次の例では、並列領域からの終了時に未定義です。

```cpp
int i, j;
i = 1;
j = 2;
#pragma omp parallel private(i) firstprivate(j)
{
  i = 3;
  j = j + 2;
}
printf_s("%d %d\n", i, j);
```

詳細については、`private`句を参照してください[セクション 2.7.2.1](2-directives.md#2721-private)します。

## <a name="a22-the-defaultnone-clause"></a>A.22 default(none) 句

次の例では、影響を受ける変数を区別する、`default(none)`句ではない変数から。

```cpp
// openmp_using_clausedefault.c
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int x, y, z[1000];
#pragma omp threadprivate(x)

void fun(int a) {
   const int c = 1;
   int i = 0;

   #pragma omp parallel default(none) private(a) shared(z)
   {
      int j = omp_get_num_thread();
             //O.K.  - j is declared within parallel region
      a = z[j];       // O.K.  - a is listed in private clause
                      //      - z is listed in shared clause
      x = c;          // O.K.  - x is threadprivate
                      //      - c has const-qualified type
      z[i] = y;       // C3052 error - cannot reference i or y here

      #pragma omp for firstprivate(y)
         for (i=0; i<10 ; i++) {
            z[i] = y;  // O.K. - i is the loop control variable
                       // - y is listed in firstprivate clause
          }
       z[i] = y;   // Error - cannot reference i or y here
   }
}
```

詳細については、`default`句を参照してください[セクション 2.7.2.5](2-directives.md#2725-default)します。

## <a name="a23-examples-of-the-ordered-directive"></a>A.23 ordered ディレクティブの例

多くの順序付けられたセクションをすることができます、`for`で指定された、`ordered`句。 最初の例は、API が次の規則を指定するために非準拠は。

"使用して、ループのイテレーションを`for`コンストラクトでは同じ実行する必要がありますされません`ordered`ディレクティブを超えると、その 1 つ以上実行する必要がありますいない`ordered`ディレクティブ"。 (を参照してください[セクション 2.6.6](2-directives.md#266-ordered-construct))。

この規則違反の例では、すべてのイテレーションは、2 つの順序付けられたセクションを実行します。

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

準拠している例を次に示します、`for`順序付けられた複数のセクション。

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```

## <a name="a24-example-of-the-private-clause"></a>A.24 private 句の例

[プライベート](2-directives.md#2721-private)並行領域の句は、リージョンの動的範囲ではなく、リージョンの構文範囲に対する効果でのみです。  変数の使用を次の例ではそのため、 *、* 内で、`for`ルーチンでループ*f*のプライベート コピーを指す *、* での使用状況の中にルーチン*g*グローバル *、* します。

```cpp
int a;

void f(int n)
{
    a = 0;

    #pragma omp parallel for private(a)
    for (int i=1; i<n; i++)
    {
        a = i;
        g(i, n);
        d(a);     // Private copy of "a"
        ...
    }
    ...

void g(int k, int n)
{
    h(k,a); // The global "a", not the private "a" in f
}
```

## <a name="a25-examples-of-the-copyprivate-data-attribute-clause"></a>A.25 copyprivate データ属性句の例

**例 1:**[Copyprivate](2-directives.md#2728-copyprivate)他のスレッド内のプライベート変数のすべてのインスタンスに直接 1 つのスレッドによって取得された値をブロードキャストする句を使用できます。

```cpp
float x, y;
#pragma omp threadprivate(x, y)

void init( )
{
    float a;
    float b;

    #pragma omp single copyprivate(a,b,x,y)
    {
        get_values(a,b,x,y);
    }

    use_values(a, b, x, y);
}
```

ルーチン*init*呼びますディレクティブの存在、serial リージョンからその動作に影響をします。 呼び出した後、 *get_values*ルーチンが 1 つのスレッドによって実行された、スレッドで指定されたプライベート オブジェクトまで、コンストラクトがない *、*、 *b*、 *x*、および*y*すべてのスレッドで読み取られた値で定義になります。

**例 2:** 前の例とは異なり、読み取りは、マスター スレッドと、特定のスレッドで実行する必要があるとします。 ここで、`copyprivate`ブロードキャストを直接実行する句を使用することはできませんが、一時的な共有オブジェクトへのアクセスを提供するために使用できます。

```cpp
float read_next( )
{
    float * tmp;
    float return_val;

    #pragma omp single copyprivate(tmp)
    {
        tmp = (float *) malloc(sizeof(float));
    }

    #pragma omp master
    {
        get_float( tmp );
    }

    #pragma omp barrier
    return_val = *tmp;
    #pragma omp barrier

    #pragma omp single
    {
       free(tmp);
    }

    return return_val;
}
```

**例 3:** 並行領域内で必要なロック オブジェクトの数はそれを入力する前に簡単に特定できないとします。 `copyprivate`その並行領域内で割り当てられている共有ロック オブジェクトへのアクセスを提供する句を使用できます。

```cpp
#include <omp.h>

omp_lock_t *new_lock()
{
    omp_lock_t *lock_ptr;

    #pragma omp single copyprivate(lock_ptr)
    {
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));
        omp_init_lock( lock_ptr );
    }

    return lock_ptr;
}
```

## <a name="a26-the-threadprivate-directive"></a>A.26 threadprivate ディレクティブの

次の例では、使用する方法、 [threadprivate](2-directives.md#271-threadprivate-directive)ディレクティブを各スレッドに別のカウンターを提供します。

### <a name="example-1"></a>例 1

```cpp
int counter = 0;
#pragma omp threadprivate(counter)

int sub()
{
    counter++;
    return(counter);
}
```

### <a name="example-2"></a>例 2

```cpp
int sub()
{
    static int counter = 0;
    #pragma omp threadprivate(counter)
    counter++;
    return(counter);
}
```

## <a name="a27-c99-variable-length-arrays"></a>A.27 C99 可変長配列

次の例では、C99 可変長配列 (Vla) を使用する方法を示しますで、 [firstprivate](2-directives.md#2722-firstprivate)ディレクティブ。

> [!NOTE]
> 現在の Visual C では、可変長配列がサポートされていません。

```cpp
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```

## <a name="a28-the-numthreads-clause"></a>A.28 num_threads 句

次の例で、 [num_threads](2-directives.md#23-parallel-construct)句。 並列領域は、最大 10 個のスレッドで実行されます。

```cpp
#include <omp.h>
main()
{
    omp_set_dynamic(1);
    ...
    #pragma omp parallel num_threads(10)
    {
        ... parallel region ...
    }
}
```

## <a name="a29-work-sharing-constructs-inside-a-critical-construct"></a>A.29 critical コンストラクト内での work-sharing コンス トラクター

次の例での work-sharing コンス トラクター内でを使用して、`critical`を構築します。 この例は、作業の共有を構築ために準拠していると、`critical`コンストラクトを同じ並列領域にバインドしていません。

```cpp
void f()
{
  int i = 1;
  #pragma omp parallel sections
  {
    #pragma omp section
    {
      #pragma omp critical (name)
      {
        #pragma omp parallel
        {
          #pragma omp single
          {
            i++;
          }
        }
      }
    }
  }
}
```

## <a name="a30-reprivatization"></a>A.30 再プライベート化

次の例では、変数の再プライベート化を示します。 プライベート変数をマークする`private`入れ子になったディレクティブにもう一度です。 外側の並列領域で、これらの変数を共有する必要はありません。

```cpp
int i, a;
...
#pragma omp parallel private(a)
{
  ...
  #pragma omp parallel for private(a)
  for (i=0; i<10; i++)
     {
       ...
     }
}
```

## <a name="a31-thread-safe-lock-functions"></a>A.31 スレッド セーフなロック関数

次の C++ の例を使用して、並列領域でロックの配列を初期化する方法を示します[omp_init_lock 関数](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions)します。

```cpp
// A_13_omp_init_lock.cpp
// compile with: /openmp
#include <omp.h>

omp_lock_t *new_locks() {
   int i;
   omp_lock_t *lock = new omp_lock_t[1000];
   #pragma omp parallel for private(i)
   for (i = 0 ; i < 1000 ; i++)
      omp_init_lock(&lock[i]);

   return lock;
}

int main () {}
```
