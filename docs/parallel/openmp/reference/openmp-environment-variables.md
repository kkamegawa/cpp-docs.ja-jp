---
title: OpenMP の環境変数
ms.date: 03/20/2019
f1_keywords:
- OpenMP environment variables
- OMP_DYNAMIC
- OMP_NESTED
- OMP_NUM_THREADS
- OMP_SCHEDULE
helpviewer_keywords:
- OpenMP environment variables
- OMP_DYNAMIC OpenMP environment variable
- OMP_NESTED OpenMP environment variable
- OMP_NUM_THREADS OpenMP environment variable
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
ms.openlocfilehash: 838427320fcb68cedb97b36156fc18002ed962d8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143281"
---
# <a name="openmp-environment-variables"></a>OpenMP の環境変数

OpenMP API で使用される環境変数へのリンクを示します。

OpenMP 標準C++のビジュアル実装には、次の環境変数が含まれています。 これらの環境変数はプログラムの起動時に読み込まれ、その値に対する変更は実行時には無視されます (たとえば、 [_putenv、_wputenv](../../../c-runtime-library/reference/putenv-wputenv.md))。

|環境変数|説明|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|`for` または `parallel for` ディレクティブで `schedule(runtime)` が指定されている場合に、 [schedule](openmp-clauses.md#schedule)句の動作を変更します。|
|[OMP_NUM_THREADS](#omp-num-threads)|[Omp_set_num_threads](openmp-functions.md#omp-set-num-threads)または[num_threads](openmp-clauses.md#num-threads)でオーバーライドされない限り、並列領域内のスレッドの最大数を設定します。|
|[OMP_DYNAMIC](#omp-dynamic)|OpenMP ランタイムが並列領域のスレッド数を調整できるかどうかを指定します。|
|[OMP_NESTED](#omp-nested)|入れ子になった並列化が有効になっているか、`omp_set_nested`で無効になっていない限り、入れ子になった並列化を有効にするか|

## <a name="omp-dynamic"></a>OMP_DYNAMIC

OpenMP ランタイムが並列領域のスレッド数を調整できるかどうかを指定します。

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>解説

`OMP_DYNAMIC` 環境変数は、 [omp_set_dynamic](openmp-functions.md#omp-set-dynamic)関数によってオーバーライドできます。

OpenMP 標準のビジュアルC++実装の既定値は `OMP_DYNAMIC=FALSE`です。

詳細については、「 [4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md)」を参照してください。

### <a name="example"></a>例

次のコマンドは、`OMP_DYNAMIC` 環境変数を TRUE に設定します。

```cmd
set OMP_DYNAMIC=TRUE
```

次のコマンドは、`OMP_DYNAMIC` 環境変数の現在の設定を表示します。

```cmd
set OMP_DYNAMIC
```

## <a name="omp-nested"></a>OMP_NESTED

入れ子になった並列化が有効になっているか、`omp_set_nested`で無効になっていない限り、入れ子になった並列化を有効にするか

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>解説

`OMP_NESTED` 環境変数は、 [omp_set_nested](openmp-functions.md#omp-set-nested)関数によってオーバーライドできます。

OpenMP 標準のビジュアルC++実装の既定値は `OMP_DYNAMIC=FALSE`です。

詳細については、「 [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md)」を参照してください。

### <a name="example"></a>例

次のコマンドは、`OMP_NESTED` 環境変数を TRUE に設定します。

```cmd
set OMP_NESTED=TRUE
```

次のコマンドは、`OMP_NESTED` 環境変数の現在の設定を表示します。

```cmd
set OMP_NESTED
```

## <a name="omp-num-threads"></a>OMP_NUM_THREADS

[Omp_set_num_threads](openmp-functions.md#omp-set-num-threads)または[num_threads](openmp-clauses.md#num-threads)でオーバーライドされない限り、並列領域内のスレッドの最大数を設定します。

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>パラメーター

*num*<br/>
並列領域に必要なスレッドの最大数。ビジュアルC++実装では最大64です。

### <a name="remarks"></a>解説

`OMP_NUM_THREADS` 環境変数は、 [omp_set_num_threads](openmp-functions.md#omp-set-num-threads)関数または[num_threads](openmp-clauses.md#num-threads)によってオーバーライドできます。

OpenMP 標準のビジュアルC++実装での `num` の既定値は、ハイパースレッディング cpu を含む仮想プロセッサの数です。

詳細については、「 [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md)」を参照してください。

### <a name="example"></a>例

次のコマンドは、`OMP_NUM_THREADS` 環境変数を `16`に設定します。

```cmd
set OMP_NUM_THREADS=16
```

次のコマンドは、`OMP_NUM_THREADS` 環境変数の現在の設定を表示します。

```cmd
set OMP_NUM_THREADS
```

## <a name="omp-schedule"></a>OMP_SCHEDULE

`for` または `parallel for` ディレクティブで `schedule(runtime)` が指定されている場合に、 [schedule](openmp-clauses.md#schedule)句の動作を変更します。

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>パラメーター

*size*<br/>
Optionalイテレーションのサイズを指定します。 *サイズ*は正の整数である必要があります。 既定値は `1`です (*型*が static の場合を除く)。 *型*が `runtime`の場合は無効です。

*type*<br/>
スケジュールの種類 (`dynamic`、`guided`、`runtime`、または `static`)。

### <a name="remarks"></a>解説

OpenMP 標準のビジュアルC++実装の既定値は `OMP_SCHEDULE=static,0`です。

詳細については、「 [4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md)」を参照してください。

### <a name="example"></a>例

次のコマンドは、`OMP_SCHEDULE` 環境変数を設定します。

```cmd
set OMP_SCHEDULE="guided,2"
```

次のコマンドは、`OMP_SCHEDULE` 環境変数の現在の設定を表示します。

```cmd
set OMP_SCHEDULE
```
