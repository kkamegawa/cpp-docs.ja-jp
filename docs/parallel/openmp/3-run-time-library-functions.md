---
title: 3. ランタイム ライブラリの関数
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 6155eb87bd7a1a0533caf99afb3db8417854df30
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142957"
---
# <a name="3-run-time-library-functions"></a>3. ランタイムライブラリ関数

このセクションでは、OpenMP C C++およびランタイムライブラリ関数について説明します。 ヘッダー\<omp > では、並列実行環境の制御とクエリに使用できる複数の関数と、データへのアクセスを同期するために使用できるロック関数の2つの型が宣言されて**います。**

`omp_lock_t` 型は、ロックが使用可能であること、またはスレッドがロックを所有していることを表すことができるオブジェクト型です。 これらのロックは、*単純なロック*と呼ばれます。

`omp_nest_lock_t` 型は、ロックが使用可能であること、またはロックを所有しているスレッドの id と*入れ子の数*の両方を表すことができるオブジェクト型です (以下で説明します)。 これらのロックは、 *a.17 locks*と呼ばれます。

ライブラリ関数は、"C" リンケージを持つ外部関数です。

この章で説明する内容は、次のトピックに分かれています。

- [実行環境関数](#31-execution-environment-functions)
- [ロック関数](#32-lock-functions)
- [タイミングルーチン](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 実行環境関数

このセクションで説明する関数は、スレッド、プロセッサ、および並列環境に影響を与え、監視します。

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

### <a name="311-omp_set_num_threads-function"></a>3.1.1 omp_set_num_threads 関数

`omp_set_num_threads` 関数は、`num_threads` 句を指定しない後の並列領域に使用する既定のスレッド数を設定します。 形式は次のとおりです。

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

パラメーター *num_threads*の値は正の整数である必要があります。 その効果は、スレッド数の動的調整が有効になっているかどうかによって異なります。 `omp_set_num_threads` 関数とスレッドの動的調整の間の相互作用に関するルールの包括的なセットについては、[セクション 2.3](2-directives.md#23-parallel-construct)を参照してください。

この関数は、`omp_in_parallel` 関数が0を返すプログラムの一部から呼び出された場合に、上記で説明した効果を持ちます。 `omp_in_parallel` 関数が0以外の値を返すプログラムの一部から呼び出された場合、この関数の動作は未定義になります。

この呼び出しは、`OMP_NUM_THREADS` 環境変数よりも優先されます。 `omp_set_num_threads` を呼び出すか、`OMP_NUM_THREADS` 環境変数を設定することによって確立されるスレッドの数の既定値は、`num_threads` 句を指定することによって、1つの `parallel` ディレクティブで明示的にオーバーライドできます。

詳細については、「 [omp_set_dynamic](#317-omp_set_dynamic-function)」を参照してください。

#### <a name="cross-references"></a>相互参照

- [omp_set_dynamic](#317-omp_set_dynamic-function)関数
- [omp_get_dynamic](#318-omp_get_dynamic-function)関数
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)環境変数
- [num_threads](2-directives.md#23-parallel-construct)句

### <a name="312-omp_get_num_threads-function"></a>3.1.2 omp_get_num_threads 関数

`omp_get_num_threads` 関数は、現在チーム内で呼び出されている並列領域を実行しているスレッドの数を返します。 形式は次のとおりです。

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

`num_threads` 句、`omp_set_num_threads` 関数、および `OMP_NUM_THREADS` 環境変数は、チーム内のスレッドの数を制御します。

ユーザーによってスレッドの数が明示的に設定されていない場合、既定値は実装によって定義されます。 この関数は、最も近い外側の `parallel` ディレクティブにバインドします。 プログラムのシリアル部分、またはシリアル化された入れ子になった並列領域から呼び出された場合、この関数は1を返します。

詳細については、「 [omp_set_dynamic](#317-omp_set_dynamic-function)」を参照してください。

#### <a name="cross-references"></a>相互参照

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a>3.1.3 omp_get_max_threads 関数

`omp_get_max_threads` 関数は、コード内のその時点で `num_threads` 句のない並列領域が見られる場合に、チームを形成するために使用されるスレッドの数と少なくとも同じであることが保証される整数を返します。 形式は次のとおりです。

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

次のは `omp_get_max_threads`の値の下限を表します。

> *使用中のスレッド-次のチーム* <= `omp_get_max_threads`

別の並列領域で `num_threads` 句を使用して特定の数のスレッドを要求した場合、`omp_get_max_threads` の結果の下限に対する保証はなくなります。

`omp_get_max_threads` 関数の戻り値を使用して、次の並列領域で形成されるチーム内のすべてのスレッドに対して十分なストレージを動的に割り当てることができます。

#### <a name="cross-references"></a>相互参照

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a>3.1.4 omp_get_thread_num 関数

`omp_get_thread_num` 関数は、そのチーム内で、関数を実行しているスレッドのスレッド番号を返します。 スレッド番号は、0から `omp_get_num_threads()`-1 までの範囲です。 チームのマスタスレッドはスレッド0です。

形式は次のとおりです。

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

シリアル領域から呼び出された場合、`omp_get_thread_num` は0を返します。 シリアル化された入れ子になった並列領域内から呼び出された場合、この関数は0を返します。

#### <a name="cross-references"></a>相互参照

- [omp_get_num_threads](#312-omp_get_num_threads-function)関数

### <a name="315-omp_get_num_procs-function"></a>3.1.5 omp_get_num_procs 関数

`omp_get_num_procs` 関数は、関数が呼び出されたときにプログラムで使用可能なプロセッサの数を返します。 形式は次のとおりです。

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a>3.1.6 omp_in_parallel 関数

`omp_in_parallel` 関数は、並列で実行される並列領域の動的な範囲内で呼び出される場合、0以外の値を返します。それ以外の場合は0を返します。 形式は次のとおりです。

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

この関数は、並列で実行されている領域内から、シリアル化された入れ子になった領域を含めて、0以外の値を返します。

### <a name="317-omp_set_dynamic-function"></a>3.1.7 omp_set_dynamic 関数

`omp_set_dynamic` 関数は、並列領域の実行に使用できるスレッド数の動的な調整を有効または無効にします。 形式は次のとおりです。

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

*Dynamic_threads*が0以外の値に評価される場合、システムリソースを最適に使用するために、実行時の環境によって、今後の並列領域の実行に使用されるスレッドの数が自動的に調整されることがあります。 その結果、ユーザーによって指定されたスレッドの数がスレッドの最大数になります。 並列領域を実行しているチーム内のスレッドの数は、その並列領域の期間中は固定され、`omp_get_num_threads` 関数によって報告されます。

*Dynamic_threads*が0に評価される場合、動的調整は無効になります。

この関数は、`omp_in_parallel` 関数が0を返すプログラムの一部から呼び出された場合に、上記で説明した効果を持ちます。 `omp_in_parallel` 関数が0以外の値を返すプログラムの一部から呼び出された場合、この関数の動作は未定義になります。

`omp_set_dynamic` の呼び出しは、`OMP_DYNAMIC` 環境変数よりも優先されます。

スレッドの動的調整の既定値は、実装によって定義されます。 結果として、特定のスレッド数に依存するユーザーコードを正しく実行するには、動的スレッドを明示的に無効にする必要があります。 実装では、スレッドの数を動的に調整する機能を提供する必要はありませんが、すべてのプラットフォーム間での移植性をサポートするインターフェイスを提供する必要があります。

#### <a name="microsoft-specific"></a>Microsoft 固有の仕様

`omp_get_dynamic` と `omp_set_dynamic` の現在のサポートは次のとおりです。

`omp_set_dynamic` の入力パラメーターは、スレッド処理ポリシーに影響を与えず、スレッドの数を変更しません。 が設定されている場合、`omp_get_num_threads` は常にユーザー定義の番号を返すか、既定のスレッド番号を返します。 現在の Microsoft 実装では、`omp_set_dynamic(0)` は動的スレッド処理をオフにして、次の並列領域に対して既存のスレッドセットを再利用できるようにします。 `omp_set_dynamic(1)` は、既存のスレッドのセットを破棄し、今後の並列領域に対して新しいセットを作成することによって、動的スレッド処理をオンにします。 新しいセット内のスレッドの数は、古いセットと同じであり、`omp_get_num_threads`の戻り値に基づいています。 したがって、最適なパフォーマンスを得るには、`omp_set_dynamic(0)` を使用して、既存のスレッドを再利用します。

#### <a name="cross-references"></a>相互参照

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a>3.1.8 omp_get_dynamic 関数

`omp_get_dynamic` 関数は、スレッドの動的調整が有効になっている場合は0以外の値を返し、それ以外の場合は0を返します。 形式は次のとおりです。

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

実装がスレッド数の動的調整を実装していない場合、この関数は常に0を返します。 詳細については、「 [omp_set_dynamic](#317-omp_set_dynamic-function)」を参照してください。

#### <a name="cross-references"></a>相互参照

- 動的なスレッド調整の詳細については、「 [omp_set_dynamic](#317-omp_set_dynamic-function)」を参照してください。

### <a name="319-omp_set_nested-function"></a>3.1.9 omp_set_nested 関数

`omp_set_nested` 関数は、入れ子になった並列処理を有効または無効にします。 形式は次のとおりです。

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

*Nested*が0に評価される場合は、入れ子になった並列処理が無効になります。これは既定の設定で、入れ子になった並列領域は現在のスレッドによってシリアル化され、実行されます。 それ以外の場合、入れ子になった並列処理が有効になり、入れ子になった並列領域では、入れ子になったチームを形成するために追加のスレッドを配置できます。

この関数は、`omp_in_parallel` 関数が0を返すプログラムの一部から呼び出された場合に、上記で説明した効果を持ちます。 `omp_in_parallel` 関数が0以外の値を返すプログラムの一部から呼び出された場合、この関数の動作は未定義になります。

この呼び出しは、`OMP_NESTED` 環境変数よりも優先されます。

入れ子になった並列処理が有効になっている場合、入れ子になった並列領域の実行に使用されるスレッドの数は実装によって定義されます。 その結果、入れ子になった並列処理が有効になっている場合でも、OpenMP 準拠の実装では、入れ子になった並列領域をシリアル化できます。

#### <a name="cross-references"></a>相互参照

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a>3.1.10 omp_get_nested 関数

入れ子になった並列処理が有効になっている場合、`omp_get_nested` 関数は0以外の値を返し、無効になっている場合は0を返します。 入れ子になった並列処理の詳細については、「 [omp_set_nested](#319-omp_set_nested-function)」を参照してください。 形式は次のとおりです。

```cpp
#include <omp.h>
int omp_get_nested(void);
```

実装が入れ子になった並列処理を実装していない場合、この関数は常に0を返します。

## <a name="32-lock-functions"></a>3.2 ロック関数

このセクションで説明する関数は、同期に使用されるロックを操作します。

次の関数では、ロック変数の型 `omp_lock_t`である必要があります。 この変数にアクセスするには、これらの関数を使用する必要があります。 すべてのロック関数には `omp_lock_t` 型へのポインターを持つ引数が必要です。

- [Omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)関数は、単純なロックを初期化します。
- [Omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)関数は、単純なロックを解除します。
- [Omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)関数は、単純なロックが使用可能になるまで待機します。
- [Omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)関数は、単純なロックを解除します。
- [Omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)関数は、単純なロックをテストします。

次の関数では、ロック変数の型 `omp_nest_lock_t`である必要があります。  この変数にアクセスするには、これらの関数を使用する必要があります。 すべての a.17 lock 関数には `omp_nest_lock_t` 型へのポインターを持つ引数が必要です。

- [Omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)関数は、a.17 ロックを初期化します。
- [Omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)関数は、a.17 ロックを解除します。
- [Omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)関数は、a.17 ロックが使用可能になるまで待機します。
- [Omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)関数は、a.17 ロックを解放します。
- [Omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)関数は、a.17 ロックをテストします。

OpenMP ロック関数は、ロック変数の最新の値を常に読み取って更新するようにロック変数にアクセスします。 したがって、OpenMP プログラムに明示的な `flush` ディレクティブを含めて、ロック変数の値が異なるスレッド間で一貫していることを確認する必要はありません。 (他の変数の値の一貫性を確保するために `flush` ディレクティブが必要になる場合があります)。

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 omp_init_lock と omp_init_nest_lock 関数

これらの関数は、ロックを初期化する唯一の手段を提供します。 各関数は、今後の呼び出しで使用するために、パラメーター*ロック*に関連付けられているロックを初期化します。 形式は次のとおりです。

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

初期状態がロック解除されています (つまり、スレッドがロックを所有していません)。 A.17 ロックの場合、最初の入れ子数は0です。 既に初期化されているロック変数を使用してこれらのルーチンを呼び出すことは非準拠です。

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>3.2.2 omp_destroy_lock と omp_destroy_nest_lock 関数

これらの関数は、ポインター変数ロックが初期化され*ていない*ことを確認します。 形式は次のとおりです。

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

初期化されていない、またはロック解除されているロック変数を使用してこれらのルーチンを呼び出すことは非準拠です。

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3 omp_set_lock と omp_set_nest_lock 関数

これらの各関数は、指定されたロックが使用可能になるまで関数を実行しているスレッドをブロックし、ロックを設定します。 ロックが解除されている場合は、単純なロックを使用できます。 ロックが解除されている場合、または関数を実行しているスレッドによって既に所有されている場合は、a.17 ロックを使用できます。 形式は次のとおりです。

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

単純なロックの場合、`omp_set_lock` 関数の引数は、初期化されたロック変数を指す必要があります。 ロックの所有権は、関数を実行しているスレッドに付与されます。

A.17 ロックの場合、`omp_set_nest_lock` 関数の引数は、初期化されたロック変数を指す必要があります。 入れ子の数がインクリメントされ、スレッドにはロックの所有権が付与されるか、保持されます。

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>3.2.4 omp_unset_lock と omp_unset_nest_lock 関数

これらの関数は、ロックの所有権を解放する手段を提供します。 形式は次のとおりです。

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

これらの関数の引数は、関数を実行するスレッドによって所有されている初期化済みのロック変数を指す必要があります。 スレッドがそのロックを所有していない場合、動作は未定義です。

単純なロックの場合、`omp_unset_lock` 関数は、関数を実行しているスレッドをロックの所有権から解放します。

A.17 ロックの場合、`omp_unset_nest_lock` 関数は入れ子の数をデクリメントし、その結果のカウントが0の場合は、関数を実行しているスレッドをロックの所有権から解放します。

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5 omp_test_lock と omp_test_nest_lock 関数

これらの関数は、ロックを設定しようとしますが、スレッドの実行をブロックしません。 形式は次のとおりです。

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

引数は、初期化されたロック変数を指す必要があります。 これらの関数は、スレッドの実行をブロックしない点を除いて、`omp_set_lock` と `omp_set_nest_lock`と同じ方法でロックを設定しようとします。

単純なロックの場合、`omp_test_lock` 関数は、ロックが正常に設定された場合に0以外の値を返します。それ以外の場合は0を返します。

A.17 ロックの場合、`omp_test_nest_lock` 関数は、ロックが正常に設定された場合に新しい入れ子数を返します。それ以外の場合は0を返します。

## <a name="33-timing-routines"></a>3.3 タイミングルーチン

このセクションで説明する関数は、移植可能な壁面クロックタイマーをサポートしています。

- [Omp_get_wtime](#331-omp_get_wtime-function)関数は、経過したウォールクロック時間を返します。
- [Omp_get_wtick](#332-omp_get_wtick-function)関数は、連続するクロックティック間の秒数を返します。

### <a name="331-omp_get_wtime-function"></a>3.3.1 omp_get_wtime 関数

`omp_get_wtime` 関数は、ある程度の "過去の時間" から経過したウォールクロック時間 (秒) に等しい倍精度浮動小数点値を返します。  実際の "過去の時間" は任意ですが、アプリケーションプログラムの実行中に変更されることは保証されていません。 形式は次のとおりです。

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

関数は、次の例に示すように、経過時間を計測するために使用されることが予想されます。

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

返される時刻は "スレッドごとの時間" です。これは、アプリケーションに参加しているすべてのスレッド間でグローバルに一貫性を維持する必要がないことを意味します。

### <a name="332-omp_get_wtick-function"></a>3.3.2 omp_get_wtick 関数

`omp_get_wtick` 関数は、連続するクロックティック間の秒数と等しい倍精度浮動小数点値を返します。 形式は次のとおりです。

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
