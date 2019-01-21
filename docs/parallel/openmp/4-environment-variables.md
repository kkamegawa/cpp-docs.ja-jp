---
title: 4. 環境変数
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: 5d08031c252d1f3c45fc45c021d24476b393fe33
ms.sourcegitcommit: 2ebbf8093fadb9a1b78a4381439bcd5c01a89267
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397330"
---
# <a name="4-environment-variables"></a>4.環境変数

この章は、OpenMP C および C++ API 環境変数 (または類似のプラットフォーム固有のメカニズム) について説明します。 並列コードの実行を制御します。  環境変数の名前を大文字にする必要があります。 割り当てられている値は、大文字と小文字を区別しない先頭および末尾の空白文字があります。  プログラムが開始した後の値の変更は無視されます。

環境変数は次のとおりです。

- [OMP_SCHEDULE](#41-omp_schedule)実行時のスケジュールの種類とチャンクのサイズを設定します。
- [OMP_NUM_THREADS](#42-omp_num_threads)実行中に使用するスレッドの数を設定します。
- [OMP_DYNAMIC](#43-omp_dynamic)有効またはスレッドの数を動的に調整を無効にします。
- [OMP_NESTED](#44-omp_nested)有効または入れ子になった並列処理を無効にします。

この章の例では、Unix C シェル (csh) 環境でこれらの変数を設定する方法のみを示します。 Korn シェルと DOS の環境では、アクションは似ています。

csh:  
`setenv OMP_SCHEDULE "dynamic"`

ksh:  
`export OMP_SCHEDULE="dynamic"`

DOS:  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE` のみ適用されます`for`と`parallel for`をスケジュールの種類を持つディレクティブ`runtime`します。 このようなすべてのループのスケジュールの種類とチャンクのサイズは、実行時に設定できます。 この環境変数を設定どの種類の認識されているスケジュールし、省略可能な設定*chunk_size*します。

`for`と`parallel for`ディレクティブを他にも、スケジュールの種類を持つ`runtime`、`OMP_SCHEDULE`は無視されます。 この環境変数の既定値は、実装で定義されます。 場合、省略可能な*chunk_size*設定すると、値は正である必要があります。 場合*chunk_size*が設定された場合、スケジュールがの場合を除き、値 1 が想定されていない`static`します。 `static`スケジュール、既定のチャンク サイズは、ループの反復領域をループに適用されるスレッドの数で割った値に設定されています。

例:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>相互参照

- [ディ](2-4-1-for-construct.md)レクティブ
- [並列](2-5-1-parallel-for-construct.md)ディレクティブ

## <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS

`OMP_NUM_THREADS`環境変数は、実行中に使用するスレッドの既定の数を設定します。 `OMP_NUM_THREADS` その数は、明示的に呼び出すことによって変更する場合は無視されます、`omp_set_num_threads`ライブラリ ルーチン。 明示的ながある場合も無視されます`num_threads`句、`parallel`ディレクティブ。

値、`OMP_NUM_THREADS`環境変数は、正の整数である必要があります。 その効果は、スレッドの数を動的に調整が有効になっているかどうかによって異なります。 包括的な一連のルール間の相互作用についての`OMP_NUM_THREADS`環境、スレッドの変数および動的な調整は、2.3 のセクションを参照してください。

使用するスレッドの数は実装に定義されている場合。

- `OMP_NUM_THREADS`環境変数が指定されていません。
- 指定された値は正の整数はありませんか
- 値は、システムがサポートできるスレッドの最大数を超えています。

例:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>相互参照

- [num_threads](2-3-parallel-construct.md)句
- [omp_set_num_threads](3-1-1-omp-set-num-threads-function.md)関数
- [omp_set_dynamic](3-1-7-omp-set-dynamic-function.md)関数

## <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC

`OMP_DYNAMIC`環境変数が有効にまたは並行領域の実行に使用できるスレッドの数を動的に調整を無効にします。 `OMP_DYNAMIC` 動的に調整が明示的に有効になっているまたは呼び出すことによって無効になっている場合は無視されます、`omp_set_dynamic`ライブラリ ルーチン。 その値である必要があります`TRUE`または`FALSE`します。

場合`OMP_DYNAMIC`に設定されている`TRUE`、最適なシステム リソースを使用するランタイム環境によって並列領域の実行に使用されるスレッドの数を調整することがあります。  場合`OMP_DYNAMIC`に設定されている`FALSE`、動的に調整が無効になっています。 既定の条件では、実装定義されます。

例:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>相互参照

- [並列領域](2-3-parallel-construct.md)
- [omp_set_dynamic](3-1-7-omp-set-dynamic-function.md)関数

## <a name="44-ompnested"></a>4.4 OMP_NESTED

`OMP_NESTED`環境変数を有効または入れ子になった並列処理が有効になっているか、呼び出すことによって無効になっている場合を除き、入れ子になった並列処理を無効になります、`omp_set_nested`ライブラリ ルーチン。 場合`OMP_NESTED`に設定されている`TRUE`、入れ子になった並列処理を有効にします。 場合`OMP_NESTED`に設定されている`FALSE`、入れ子になった並列処理が無効になっています。 既定値は `FALSE` です。

例:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>相互参照

- [omp_set_nested](3-1-9-omp-set-nested-function.md)関数
