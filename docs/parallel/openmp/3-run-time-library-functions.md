---
title: 3. ランタイム ライブラリ関数
ms.date: 01/17/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 4e72d2d74bb26f8eeeb422881cabf92630cced43
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087315"
---
# <a name="3-run-time-library-functions"></a>3.ランタイム ライブラリ関数

このセクションでは、OpenMP C および C++ ランタイム ライブラリ関数について説明します。 ヘッダー  **\<omp.h >** 2 つの型は、制御およびクエリの並列実行環境とロック データへのアクセスを同期するために使用する関数を使用できるいくつかの関数を宣言します。

型`omp_lock_t`オブジェクトの種類は、ロックが使用可能なことを表すことができる、またはスレッドがロックを所有しています。 これらのロックと呼びます*単純ロック*します。

型`omp_nest_lock_t`するかを表すことができるオブジェクトの種類のロックが使用可能なまたはスレッド id、ロックを所有しているが、*入れ子カウント*(下記参照)。 これらのロックと呼びます*入れ子にできるロック*します。

ライブラリ関数は、"C"リンケージを持つ外部関数です。

この章の説明は、次のトピックに分かれています。

- [実行環境関数](#31-execution-environment-functions)
- [ロック関数](#32-lock-functions)
- [タイミング ルーチン](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 実行環境関数

このセクションで説明した関数に影響を与えるし、スレッド、プロセッサ、および並列環境を監視します。

- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_get_max_threads](#313-omp_get_max_threads-function)
- [omp_get_thread_num](#314-omp_get_thread_num-function)
- [omp_get_num_procs](#315-omp_get_num_procs-function)
- [omp_in_parallel](#316-omp_in_parallel-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [omp_get_dynamic](#318-omp_get_dynamic-function)
- [omp_set_nested](#319-omp_set_nested-function)
- [omp_get_nested](#3110-omp_get_nested-function)

### <a name="311-ompsetnumthreads-function"></a>3.1.1 omp_set_num_threads 関数

`omp_set_num_threads`関数に指定しないと、並行領域後で使用するスレッド数の既定の設定、`num_threads`句。 形式は次のとおりです。

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

パラメーターの値*num_threads*正の整数を指定する必要があります。 その効果は、スレッドの数を動的に調整が有効になっているかどうかによって異なります。 包括的な一連のルール間の相互作用についての`omp_set_num_threads`関数とスレッド、動的に調整を参照してください[2.3 セクション](2-directives.md#23-parallel-construct)します。

この関数は、プログラムの部分から呼び出されたときに上記で説明した効果を`omp_in_parallel`関数は 0 を返します。 プログラムの部分から呼び出された場合、`omp_in_parallel`関数は 0 以外の値を返します、この関数の動作は未定義です。

この呼び出しに優先、`OMP_NUM_THREADS`環境変数。 スレッドである可能性がありますが呼び出すことで確立されている数の既定値`omp_set_num_threads`かを設定して、`OMP_NUM_THREADS`環境変数は、1 つで明示的にオーバーライド`parallel`ディレクティブを指定して、`num_threads`句。

#### <a name="cross-references"></a>相互参照

- [omp_set_dynamic](#317-omp_set_dynamic-function)関数
- [omp_get_dynamic](#318-omp_get_dynamic-function)関数
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)環境変数
- [num_threads](2-directives.md#23-parallel-construct)句

### <a name="312-ompgetnumthreads-function"></a>3.1.2 omp_get_num_threads 関数

`omp_get_num_threads`関数の数を返しますスレッド現在、チームが並列に呼び出し元のリージョンを実行します。 形式は次のとおりです。

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

`num_threads`句、`omp_set_num_threads`関数、および`OMP_NUM_THREADS`環境変数は、チーム内のスレッドの数を制御します。

スレッドの数は、ユーザーが明示的に設定されていない場合、既定値は実装定義には。 この関数に最も近い外側バインド`parallel`ディレクティブ。 シリアル、プログラムの一部から、またはシリアル化される入れ子になった並列領域から呼び出されると、この関数は 1 を返します。

#### <a name="cross-references"></a>相互参照

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-ompgetmaxthreads-function"></a>3.1.3 omp_get_max_threads 関数

`omp_get_max_threads`関数は、チームを作ることがなく、並行領域の場合に使用されるスレッドの数とサイズ以上であることが保証が整数を返します、`num_threads`句がその時点で、コードで確認します。 形式は次のとおりです。

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

次の値の下限の境界を表現する`omp_get_max_threads`:

```

threads-used-for-next-team
<= omp_get_max_threads
```

場合、並列の別のリージョンで使用、`num_threads`句の結果の下限の境界上の保証、スレッドの特定の番号を要求する`omp_get_max_threads`ありません時間保持されます。

`omp_get_max_threads`関数の戻り値は次の並列領域で形成されるチームのすべてのスレッドに十分な記憶域を動的に割り当てるには使用できます。

#### <a name="cross-references"></a>相互参照

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num 関数

`omp_get_thread_num`関数のスレッドの数を返します、のチーム内で関数を実行するスレッド。 スレッドの番号は 0 との間および`omp_get_num_threads()`-1、包括的です。 チームのマスター スレッドはスレッド 0 です。

形式は次のとおりです。

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

シリアル領域から呼び出された場合`omp_get_thread_num`0 を返します。 シリアル化される入れ子になった並列領域内から呼び出されると、この関数は 0 を返します。

#### <a name="cross-references"></a>相互参照

- [omp_get_num_threads](#312-omp_get_num_threads-function)関数

### <a name="315-ompgetnumprocs-function"></a>3.1.5 omp_get_num_procs 関数

`omp_get_num_procs`関数は、関数が呼び出された時点で、プログラムに使用できるプロセッサの数を返します。 形式は次のとおりです。

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel 関数

`omp_in_parallel`関数は、並列で実行される並列領域の動的範囲内で呼び出された場合に 0 以外の値を返します。 それ以外の場合、0 を返します。 形式は次のとおりです。

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

この関数は、シリアル化される入れ子になったリージョンを含む、並列で実行される領域内から呼び出された場合は 0 以外の値を返します。

### <a name="317-ompsetdynamic-function"></a>3.1.7 omp_set_dynamic 関数

`omp_set_dynamic`関数が有効にまたは並行領域の実行に使用できるスレッドの数を動的に調整を無効にします。 形式は次のとおりです。

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

場合*dynamic_threads*評価 0 以外の値を今後の並列領域の実行に使用されるスレッドの数可能性がありますがによって自動的に調整システム リソースを活用するランタイム環境。 その結果、ユーザーによって指定されたスレッドの数は、最大スレッド数。 並列領域を実行する、チーム内のスレッドの数のまま、並列領域の期間、固定とによって報告された、`omp_get_num_threads`関数。

場合*dynamic_threads*評価を 0 に動的に調整が無効になっています。

この関数は、プログラムの部分から呼び出されたときに上記で説明した効果を`omp_in_parallel`関数は 0 を返します。 プログラムの部分から呼び出された場合、`omp_in_parallel`関数は 0 以外の値を返します、この関数の動作は未定義です。

呼び出し`omp_set_dynamic`経由での優先順位を持つ、`OMP_DYNAMIC`環境変数。

動的に調整するスレッドの既定値は、実装定義です。 結果として、適切な実行のスレッドの特定の数に依存しているユーザー コードは、明示的に動的スレッドを無効にする必要があります。 実装がスレッドの数を動的に調整する機能を提供する必要はありませんが、すべてのプラットフォーム間で移植性をサポートするインターフェイスを提供する必要があります。

#### <a name="cross-references"></a>相互参照

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic 関数

`omp_get_dynamic`関数は、スレッドの動的な調整が有効であり、それ以外の場合は 0 を返す場合に 0 以外の値を返します。 形式は次のとおりです。

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

実装がスレッドの数を動的に調整を実装していない場合、この関数は常に 0 を返します。

#### <a name="cross-references"></a>相互参照

- 動的なスレッドの調整については、次を参照してください。 [omp_set_dynamic](#317-omp_set_dynamic-function)します。

### <a name="319-ompsetnested-function"></a>3.1.9 omp_set_nested 関数

`omp_set_nested`関数を有効または入れ子になった並列処理を無効にします。 形式は次のとおりです。

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

場合*入れ子になった*入れ子になった 0 に評価される、これは、既定では、並列処理が無効と入れ子になった並列領域はシリアル化され、現在のスレッドによって実行します。 それ以外の場合、入れ子になった並列処理が有効になっているし、入れ子になっている並列領域は入れ子になったチームを形成する追加のスレッドをデプロイできます。

この関数は、プログラムの部分から呼び出されたときに上記で説明した効果を`omp_in_parallel`関数は 0 を返します。 プログラムの部分から呼び出された場合、`omp_in_parallel`関数は 0 以外の値を返します、この関数の動作は未定義です。

この呼び出しに優先、`OMP_NESTED`環境変数。

入れ子になった並列処理が有効にすると入れ子になった並列領域の実行に使用されるスレッドの数は実装定義です。 その結果、OpenMP に準拠した実装では、入れ子になった並列処理が有効な場合でも、入れ子になった並列領域をシリアル化許可されます。

#### <a name="cross-references"></a>相互参照

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested 関数

`omp_get_nested`関数 0 を返します 0 以外の値を使用している場合、入れ子になった並列処理が有効になっている場合は無効になります。 入れ子になった並列処理の詳細については、次を参照してください。 [omp_set_nested](#319-omp_set_nested-function)します。 形式は次のとおりです。

```cpp
#include <omp.h>
int omp_get_nested(void);
```

実装が入れ子になった並列処理を実装していない場合、この関数は常に 0 を返します。

## <a name="32-lock-functions"></a>3.2 ロック関数

このセクションで説明した関数では、同期に使用されるロックを操作します。

ロックの変数、次の関数の型である必要があります`omp_lock_t`します。 この変数は、これらの関数からのみアクセスする必要があります。 ポインターを持つ引数を必要とするすべてのロック関数`omp_lock_t`型。

- [Omp_init_lock 関数](#321-omp_init_lock-and-omp_init_nest_lock-functions)関数は、単純なロックを初期化します。
- [Omp_destroy_lock 関数](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)関数は、単純なロックを削除します。
- [Omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)関数は、単純なロックが使用できるまで待機します。
- [Omp_unset_lock 関数](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)関数は、単純なロックを解放します。
- [Omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)関数は、単純なロックをテストします。

ロックの変数、次の関数の型である必要があります`omp_nest_lock_t`します。  この変数は、これらの関数からのみアクセスする必要があります。 ポインターを持つ引数を必要とするすべての入れ子にできるロック関数`omp_nest_lock_t`型。

- [Omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)関数を入れ子にできるロックを初期化します。
- [Omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)関数が入れ子にできるロックを削除します。
- [Omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)関数が入れ子にできるロックが使用できるまでに待機します。
- [Omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)関数が入れ子にできるロックを解放します。
- [Omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)関数は入れ子にできるロックをテストします。

OpenMP のロック関数が常に読み取りをロック変数の最新の値を更新方法でロック変数にアクセスします。 そのため、OpenMP プログラムの明示的なを含める必要はありません`flush`ロック変数の値が別のスレッド間で一貫性のあることを確認するためのディレクティブ。 (必要である可能性があります`flush`ディレクティブを一貫性のあるその他の変数の値を作成します)。

### <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock 関数と omp_init_nest_lock 関数

これらの関数は、ロックの初期化の唯一の手段を提供します。 各関数の初期化パラメーターに関連付けられているロック*ロック*今後の呼び出しで使用します。 形式は次のとおりです。

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

初期状態がロックされている (つまり、スレッド ロックを所有していません)。 入れ子にできるロックでは、入れ子の最初の数は 0 です。 これらのルーチンには、既に初期化されているロック変数のいずれかを呼び出さない非準拠になります。

### <a name="322-ompdestroylock-and-ompdestroynestlock-functions"></a>3.2.2 omp_destroy_lock 関数と omp_destroy_nest_lock 関数

これらの関数を確認する変数をロックするには、指す*ロック*が初期化されていません。 形式は次のとおりです。

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

呼び出しが初期化されていないロック変数でこれらのルーチンのいずれかに準拠していないか、ロックされていません。

### <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 omp_set_lock 関数と omp_set_nest_lock 関数

これらの各関数は、指定されたロックがあるし、ロックを設定するまで、関数の実行スレッドをブロックします。 単純なロックがである場合に使用可能なロックを解除します。 入れ子にできるロックがである場合に使用可能なロックされていない、または関数を実行するスレッドによって既に所有している場合。 形式は次のとおりです。

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

単純なロックを引数、`omp_set_lock`関数は、初期化されたロックの変数を指す必要があります。 ロックの所有権は、関数を実行しているスレッドに付与されます。

入れ子にできるロックでの引数、`omp_set_nest_lock`関数は、初期化されたロックの変数を指す必要があります。 入れ子のカウントがインクリメントされ、スレッドが付与される、またはロックの所有権を保持します。

### <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 omp_unset_lock 関数と omp_unset_nest_lock 関数

これらの関数では、ロックの所有権を解放する手段を提供します。 形式は次のとおりです。

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

これらの各関数の引数は、関数を実行するスレッドによって所有されているロックが初期化された変数をポイントする必要があります。 スレッドは、そのロックを所有しない場合、動作は未定義です。

単純なロックを`omp_unset_lock`関数は、ロックの所有権から関数を実行するスレッドを解放します。

入れ子にできるロックで、`omp_unset_nest_lock`関数デクリメント、入れ子のカウントとリリース、結果のカウントが 0 の場合、ロックの所有権から関数を実行するスレッド。

### <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 omp_test_lock 関数と omp_test_nest_lock 関数

これらの関数は、ロックを設定しようとしていますが、スレッドの実行をブロックしません。 形式は次のとおりです。

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

引数は、ロックが初期化された変数をポイントする必要があります。 これらの関数と同様に、ロックを設定しようとしました。`omp_set_lock`と`omp_set_nest_lock`スレッドの実行をブロックしないことを除いて、します。

単純なロックを`omp_test_lock`関数が正常にロックが設定されている場合、0 以外の値を返します。 それ以外の場合、0 を返します。

入れ子にできるロックで、`omp_test_nest_lock`関数が正常にロックが設定されている場合、新しい入れ子数を返します。 それ以外の場合、0 を返します。

## <a name="33-timing-routines"></a>3.3 タイミング ルーチン

このセクションで説明されている関数は、ポータブルのウォール クロックのタイマーをサポートします。

- [Omp_get_wtime](#331-omp_get_wtime-function)経過したウォール クロック時間を返します。
- [Omp_get_wtick](#332-omp_get_wtick-function)関数は、連続したクロックのティック間 (秒) を返します。

### <a name="331-ompgetwtime-function"></a>3.3.1 omp_get_wtime 関数

`omp_get_wtime` 「過去の時間」からの秒数で関数が経過したウォール クロック時間に等しいにある倍精度浮動小数点値を返します。  実際「の時間、過去に」は任意ですが、アプリケーション プログラムの実行中に変わらないことを保証しています。 形式は次のとおりです。

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

次の例に示すように、経過時間を測定する関数が使用されることが予想されます。

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

返される時間は、「スレッドごとの時間」を使用してアプリケーションに参加しているすべてのスレッド間でグローバルに一貫性がある必要はありませんがありました。

### <a name="332-ompgetwtick-function"></a>3.3.2 omp_get_wtick 関数

`omp_get_wtick`連続クロックのティック間関数が秒数に等しいにある倍精度浮動小数点値を返します。 形式は次のとおりです。

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
