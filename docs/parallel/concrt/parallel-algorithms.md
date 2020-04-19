---
title: 並列アルゴリズム
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms [Concurrency Runtime]
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
ms.openlocfilehash: 3e9cce9af01ea108e6510d42e5eedba8ef05a7a4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142919"
---
# <a name="parallel-algorithms"></a>並列アルゴリズム

並列パターンライブラリ (PPL) には、データのコレクションに対して作業を同時に実行するアルゴリズムが用意されています。 これらのアルゴリズムは、標準ライブラリC++で提供されているものと似ています。

並列アルゴリズムは、同時実行ランタイムの既存の機能を基に構成されています。 たとえば、 [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)アルゴリズムでは、 [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)オブジェクトを使用して並列ループの反復処理を実行します。 `parallel_for` アルゴリズムのパーティションは、使用可能なコンピューティングリソースの数を指定すると、最適な方法で動作します。

## <a name="top"></a> セクション

- [Parallel_for アルゴリズム](#parallel_for)

- [Parallel_for_each アルゴリズム](#parallel_for_each)

- [Parallel_invoke アルゴリズム](#parallel_invoke)

- [Parallel_transform アルゴリズムと parallel_reduce アルゴリズム](#parallel_transform_reduce)

    - [Parallel_transform アルゴリズム](#parallel_transform)

    - [Parallel_reduce アルゴリズム](#parallel_reduce)

    - [例: Map と Reduce を並列実行する](#map_reduce_example)

- [パーティション分割作業](#partitions)

- [並列並べ替え](#parallel_sorting)

    - [並べ替えアルゴリズムの選択](#choose_sort)

## <a name="parallel_for"></a>Parallel_for アルゴリズム

[同時実行::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)アルゴリズムにより、同じタスクが並列で繰り返し実行されます。 これらの各タスクは、反復値によってパラメーター化されます。 このアルゴリズムは、ループの反復処理間でリソースを共有しないループ本体がある場合に便利です。

`parallel_for` アルゴリズムでは、並列実行に最適な方法でタスクをパーティション分割します。 ワークロードが不均衡な場合に、ワークスティーリングアルゴリズムと範囲の盗難を使用して、これらのパーティションのバランスを取ることができます。 1つのループ反復が協調的にブロックされると、ランタイムは、現在のスレッドに割り当てられているイテレーションの範囲を他のスレッドまたはプロセッサに再分配します。 同様に、スレッドが一定の範囲のイテレーションを完了すると、ランタイムは他のスレッドからそのスレッドに作業を再分配します。 `parallel_for` アルゴリズムでは、*入れ子になった並列処理*もサポートされます。 1つの並列ループに別の並列ループが含まれている場合、ランタイムは、並列実行の効率的な方法でループ本体間の処理リソースを調整します。

`parallel_for` アルゴリズムには、いくつかのオーバーロードされたバージョンがあります。 最初のバージョンは、開始値、終了値、および処理関数 (ラムダ式、関数オブジェクト、または関数ポインター) を受け取ります。 2番目のバージョンは、開始値、終了値、ステップ実行する値、および作業関数を受け取ります。 この関数の最初のバージョンでは、ステップ値として1を使用します。 残りのバージョンでは、パーティショナーオブジェクトを受け取ります。これにより、`parallel_for` がスレッド間で範囲をパーティション分割する方法を指定できます。 パーティショナーの詳細については、このドキュメントの「[パーティション分割作業](#partitions)」セクションを参照してください。

多くの `for` ループを変換して `parallel_for`を使用することができます。 ただし、`parallel_for` アルゴリズムは、次の方法で `for` ステートメントとは異なります。

- `parallel_for` アルゴリズム `parallel_for` は、事前に決められた順序でタスクを実行しません。

- `parallel_for` アルゴリズムでは、任意の終了条件はサポートされていません。 `parallel_for` アルゴリズムは、反復変数の現在の値が `last`よりも1小さい場合に停止します。

- `_Index_type` 型パラメーターは整数型である必要があります。 この整数型は、符号付きまたは符号なしにすることができます。

- ループの反復処理は転送する必要があります。 `_Step` パラメーターが1より小さい場合、`parallel_for` アルゴリズムは型[std:: invalid_argument](../../standard-library/invalid-argument-class.md)の例外をスローします。

- `parallel_for` アルゴリズムの例外処理機構は、`for` ループとは異なります。 並列ループ本体で複数の例外が同時に発生した場合、ランタイムは `parallel_for`を呼び出したスレッドに1つの例外のみを反映します。 また、1つのループの反復処理で例外がスローされた場合、ランタイムは、ループ全体を即座に停止するわけではありません。 代わりに、ループは canceled 状態になり、ランタイムはまだ開始されていないタスクを破棄します。 例外処理と並列アルゴリズムの詳細については、「[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)」を参照してください。

`parallel_for` アルゴリズムでは任意の終了条件がサポートされていませんが、取り消しを使用してすべてのタスクを停止することができます。 取り消しの詳細については、「 [PPL における取り消し](cancellation-in-the-ppl.md)処理」を参照してください。

> [!NOTE]
> 負荷分散や、キャンセルなどの機能のサポートによって生じるスケジューリングコストは、特にループ本体が比較的小さい場合にループ本体を並列実行する利点を克服できない可能性があります。 並列ループでパーティショナーを使用することによって、このオーバーヘッドを最小限に抑えることができます。 詳細については、このドキュメントで後述する「[パーティション分割の機能](#partitions)」を参照してください。

### <a name="example"></a>例

次の例は、`parallel_for` アルゴリズムの基本的な構造を示しています。 この例では、範囲 [1, 5] 内の各値が並行してコンソールに出力されます。

[!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]

この例では、次のサンプル出力が生成されます。

```Output
1 2 4 3 5
```

`parallel_for` アルゴリズムは各項目に対して並列に動作するため、値がコンソールに出力される順序は異なります。

`parallel_for` アルゴリズムを使用する完全な例については、「[方法: Parallel_for ループを記述](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)する」を参照してください。

[[トップ](#top)]

## <a name="parallel_for_each"></a>Parallel_for_each アルゴリズム

[Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)アルゴリズムは、 C++標準ライブラリによって提供されるものなど、反復的なコンテナーのタスクを並行して実行します。 このアルゴリズムでは、`parallel_for` アルゴリズムで使用されるのと同じ分割ロジックが使用されます。

`parallel_for_each` アルゴリズムはC++標準ライブラリ[std:: for_each](../../standard-library/algorithm-functions.md#for_each)アルゴリズムに似ていますが、`parallel_for_each` アルゴリズムによってタスクが同時に実行される点が異なります。 他の並列アルゴリズムと同様に、`parallel_for_each` はタスクを特定の順序で実行しません。

`parallel_for_each` アルゴリズムは前方反復子とランダムアクセス反復子の両方で動作しますが、ランダムアクセス反復子によってパフォーマンスが向上します。

### <a name="example"></a>例

次の例は、`parallel_for_each` アルゴリズムの基本的な構造を示しています。 この例では、 [std:: array](../../standard-library/array-class-stl.md)オブジェクトの各値が並列にコンソールに出力されます。

[!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]

この例では、次のサンプル出力が生成されます。

```Output
4 5 1 2 3
```

`parallel_for_each` アルゴリズムは各項目に対して並列に動作するため、値がコンソールに出力される順序は異なります。

`parallel_for_each` アルゴリズムを使用する完全な例については、「[方法: Parallel_for_each ループを記述](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)する」を参照してください。

[[トップ](#top)]

## <a name="parallel_invoke"></a>Parallel_invoke アルゴリズム

[Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)アルゴリズムは、一連のタスクを並列に実行します。 各タスクが終了するまでは返されません。 このアルゴリズムは、複数の独立したタスクを同時に実行する必要がある場合に便利です。

`parallel_invoke` アルゴリズムは、一連の作業関数 (ラムダ関数、関数オブジェクト、または関数ポインター) をパラメーターとして受け取ります。 `parallel_invoke` アルゴリズムは、2つのパラメーターと10個のパラメーターの間を受け取るようにオーバーロードされます。 `parallel_invoke` に渡すすべての関数は、ゼロパラメーターを受け取る必要があります。

他の並列アルゴリズムと同様に、`parallel_invoke` はタスクを特定の順序で実行しません。 「[タスクの並列処理](../../parallel/concrt/task-parallelism-concurrency-runtime.md)」では、`parallel_invoke` アルゴリズムがタスクとタスクグループにどのように関連しているかについて説明します。

### <a name="example"></a>例

次の例は、`parallel_invoke` アルゴリズムの基本的な構造を示しています。 この例では、3つのローカル変数に対して `twice` 関数を同時に呼び出し、結果をコンソールに出力します。

[!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]

この例の結果は、次のようになります。

```Output
108 11.2 HelloHello
```

`parallel_invoke` アルゴリズムを使用する完全な例については、「[方法: parallel_invoke を使用して並列並べ替えルーチンを記述](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)する」および「[方法: parallel_invoke を使用して並列操作を実行](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)する」を参照してください。

[[トップ](#top)]

## <a name="parallel_transform_reduce"></a>Parallel_transform アルゴリズムと parallel_reduce アルゴリズム

[Concurrency::p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)と[concurrency::p arallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)アルゴリズムは、 C++それぞれ標準ライブラリアルゴリズム[std:: transform](../../standard-library/algorithm-functions.md#transform)と[std:: 蓄積](../../standard-library/numeric-functions.md#accumulate)の並列バージョンです。 同時実行ランタイムのバージョンは、標準C++ライブラリのバージョンと同様に動作します。ただし、操作の順序は並列で実行されるため、決定されません。 これらのアルゴリズムを使用して、パフォーマンスとスケーラビリティのメリットを並行して処理するのに十分な大きさのセットを操作します。

> [!IMPORTANT]
> `parallel_transform` アルゴリズムと `parallel_reduce` アルゴリズムでは、ランダムアクセス、双方向、および前方反復子のみがサポートされます。これらの反復子は、安定したメモリアドレスを生成するためです。 また、これらの反復子は、非`const` 左辺値を生成する必要があります。

### <a name="parallel_transform"></a>Parallel_transform アルゴリズム

`parallel transform` アルゴリズムを使用して、多くのデータ並列処理を実行できます。 たとえば、次のように操作できます。

- 画像の明るさを調整し、その他の画像処理操作を実行します。

- 2つのベクトル間のドット積を合計または取得し、ベクターに対して他の数値計算を実行します。

- 3d レイトレースを実行します。各イテレーションは、レンダリングする必要がある1つのピクセルを表します。

次の例は、`parallel_transform` アルゴリズムを呼び出すために使用される基本構造を示しています。 この例では、2つの方法で std::[vector](../../standard-library/vector-class.md)オブジェクトの各要素を否定します。 最初の方法では、ラムダ式を使用します。 2番目の方法では、std [:: unary_function](../../standard-library/unary-function-struct.md)から派生する[std:: 否定](../../standard-library/negate-struct.md)を使用します。

[!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]

> [!WARNING]
> この例では、`parallel_transform`の基本的な使用方法を示します。 この処理関数は大量の作業を実行しないため、この例ではパフォーマンスの大幅な増加は想定されていません。

`parallel_transform` アルゴリズムには2つのオーバーロードがあります。 最初のオーバーロードは、1つの入力範囲と単項関数を受け取ります。 単項関数は、1つの引数、関数オブジェクト、または `unary_function`から派生した型を受け取るラムダ式にすることができます。 2番目のオーバーロードは、2つの入力範囲と二項関数を受け取ります。 二項関数は、2つの引数、関数オブジェクト、または[std:: binary_function](../../standard-library/binary-function-struct.md)から派生した型を受け取るラムダ式にすることができます。 これらの違いを次の例に示します。

[!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]

> [!IMPORTANT]
> `parallel_transform` の出力に指定する反復子は、入力反復子の完全な重複または重複しないようにする必要があります。 入力反復子と出力反復子が部分的に重複している場合、このアルゴリズムの動作は指定されません。

### <a name="parallel_reduce"></a>Parallel_reduce アルゴリズム

`parallel_reduce` アルゴリズムは、結合プロパティを満たす一連の操作がある場合に便利です。 (このアルゴリズムでは、可換プロパティは必要ありません)。`parallel_reduce`で実行できる操作の一部を次に示します。

- マトリックスのシーケンスを乗算して行列を生成します。

- ベクターを一連の行列で乗算してベクターを生成します。

- 文字列のシーケンスの長さを計算します。

- 文字列などの要素のリストを1つの要素に結合します。

次の基本的な例は、`parallel_reduce` アルゴリズムを使用して文字列のシーケンスを1つの文字列に結合する方法を示しています。 `parallel_transform`の例と同様に、この基本的な例では、パフォーマンスの向上は想定されていません。

[!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]

多くの場合、`parallel_reduce` は、 [concurrency:: 組み合わせ](../../parallel/concrt/reference/combinable-class.md)可能なクラスと共に `parallel_for_each` アルゴリズムを使用するための短縮形と考えることができます。

### <a name="map_reduce_example"></a>例: Map と Reduce を並列実行する

*マップ*操作は、シーケンスの各値に関数を適用します。 *Reduce*操作は、シーケンスの要素を1つの値に結合します。 標準ライブラリC++ [std:: transform](../../standard-library/algorithm-functions.md#transform)関数と[std:: 蓄積](../../standard-library/numeric-functions.md#accumulate)関数を使用すると、マップ操作と縮小操作を実行できます。 ただし、多くの問題については、`parallel_transform` アルゴリズムを使用してマップ操作を並列に実行できます。また、`parallel_reduce` アルゴリズムでは、reduce 操作を並行して実行できます。

次の例では、素数の合計を逐次的かつ並列に計算するためにかかる時間を比較します。 マップフェーズでは、非素数値が0に変換され、reduce フェーズによって値が合計されます。

[!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]

マップと削減操作を並列で実行する別の例については、「[方法: マップ操作と縮小操作を並列実行](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)する」を参照してください。

[[トップ](#top)]

## <a name="partitions"></a>パーティション分割作業

データソースに対する操作を並列化するには、複数のスレッドが同時にアクセスできる複数のセクションにソースを*パーティション分割*することが不可欠です。 パーティショナーは、並列アルゴリズムでスレッド間の範囲をパーティション分割する方法を指定します。 このドキュメントで既に説明したように、PPL は初期ワークロードを作成する既定のパーティション分割メカニズムを使用し、ワークロードが不均衡な場合にワークスティーリングアルゴリズムと範囲の盗難を使用してこれらのパーティションのバランスを調整します。 たとえば、あるループの反復処理がイテレーションの範囲を完了すると、ランタイムは他のスレッドからそのスレッドに作業を再分配します。 ただし、シナリオによっては、問題に適した別のパーティション分割メカニズムを指定することが必要になる場合があります。

`parallel_for`、`parallel_for_each`、および `parallel_transform` アルゴリズムは、追加のパラメーター `_Partitioner`を受け取るオーバーロードされたバージョンを提供します。 このパラメーターは、作業を分割するパーティショナーの種類を定義します。 PPL が定義するパーティショナーの種類を次に示します。

[concurrency:: affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)<br/>
作業を一定の範囲に分割します (通常は、ループで動作できるワーカースレッドの数)。 このパーティショナー型は `static_partitioner`に似ていますが、範囲をワーカースレッドにマップする方法によってキャッシュ関係が向上します。 このパーティショナー型により、ループが同じデータセットに対して複数回実行される場合 (ループ内のループなど)、データがキャッシュに収まる場合にパフォーマンスを向上させることができます。 このパーティショナーはキャンセルに完全には参加しません。 また、協調ブロッキングセマンティクスを使用しないため、前方依存関係を持つ並列ループでは使用できません。

[concurrency:: auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)<br/>
作業を範囲の初期数に分割します (通常は、ループでの作業に使用できるワーカースレッドの数)。 `_Partitioner` パラメーターを受け取るオーバーロードされた並列アルゴリズムを呼び出さない場合、ランタイムは既定でこの型を使用します。 各範囲をサブ範囲に分割することにより、負荷分散を行うことができます。 一連の作業が完了すると、ランタイムは他のスレッドからそのスレッドに作業のサブ範囲を再配布します。 このパーティショナーは、ワークロードが他のカテゴリのいずれにも該当しない場合、または取り消しや協調ブロックの完全なサポートが必要な場合に使用します。

[concurrency:: simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)<br/>
各範囲に、指定されたチャンクサイズによって指定されたイテレーションの数以上が含まれるように、作業を複数の範囲に分割します。 このパーティショナーの種類は負荷分散に関与します。ただし、ランタイムは範囲をサブ範囲に分割しません。 ランタイムは、ワーカーごとにキャンセルをチェックし、`_Chunk_size` のイテレーションが完了した後に負荷分散を実行します。

[concurrency:: static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)<br/>
作業を一定の範囲に分割します (通常は、ループで動作できるワーカースレッドの数)。 このパーティショナーの種類は、ワークスティーリングを使用しないため、オーバーヘッドが少なくなるため、パフォーマンスを向上させることができます。 このパーティショナーの種類は、並列ループの各反復処理が固定された均一な量の作業を実行し、キャンセルまたは前方協調ブロックのサポートを必要としない場合に使用します。

> [!WARNING]
> `parallel_for_each` アルゴリズムと `parallel_transform` アルゴリズムでは、static、simple、および affinity パーティショナーのランダムアクセス反復子 (std::[vector](../../standard-library/vector-class.md)など) を使用するコンテナーのみがサポートされます。 双方向の反復子を使用するコンテナーを使用すると、コンパイル時エラーが発生します。 既定のパーティショナーである `auto_partitioner`は、これら3つの反復子型すべてをサポートします。

通常、これらのパーティショナーは、`affinity_partitioner`を除き、同じように使用されます。 ほとんどのパーティショナー型は状態を保持せず、ランタイムによって変更されることはありません。 そのため、次の例に示すように、これらのパーティショナーオブジェクトを呼び出しサイトで作成できます。

[!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]

ただし、`affinity_partitioner` オブジェクトを`const`ではない左辺値参照として渡す必要があります。これにより、アルゴリズムは将来のループを再利用するために状態を格納できます。 次の例は、データセットに対して同じ操作を複数回実行する基本的なアプリケーションを示しています。 配列がキャッシュに格納される可能性が高いため、`affinity_partitioner` を使用するとパフォーマンスが向上します。

[!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]

> [!CAUTION]
> `static_partitioner` または `affinity_partitioner`を使用するために、協調ブロックセマンティクスに依存する既存のコードを変更する場合は注意してください。 これらのパーティショナー型は負荷分散や範囲の盗難を使用しないため、アプリケーションの動作を変更できます。

特定のシナリオでパーティショナーを使用するかどうかを判断する最善の方法は、代表的な負荷とコンピューター構成で、操作が完了するまでの時間を実験して測定することです。 たとえば、静的パーティション分割は、少数のコアしか持たないマルチコア コンピューターでは速度が飛躍的に向上することがありますが、比較的多くのコアを持つコンピューターでは速度が低下することがあります。

[[トップ](#top)]

## <a name="parallel_sorting"></a>並列並べ替え

PPL には、[同時実行::p arallel_sort](reference/concurrency-namespace-functions.md#parallel_sort)、 [concurrency::p arallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)、および[concurrency::p arallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort)の3つの並べ替えアルゴリズムが用意されています。 これらの並べ替えアルゴリズムは、並列での並べ替えによるメリットが得られるデータセットがある場合に便利です。 特に、大規模なデータセットがある場合や、計算に負荷の高い比較操作を使用してデータを並べ替える場合は、並列での並べ替えが役立ちます。 これらの各アルゴリズムでは、要素が適切に並べ替えられます。

`parallel_sort` アルゴリズムと `parallel_buffered_sort` アルゴリズムは両方とも比較ベースのアルゴリズムです。 つまり、要素を値で比較します。 `parallel_sort` アルゴリズムには追加のメモリ要件はなく、汎用的な並べ替えに適しています。 `parallel_buffered_sort` アルゴリズムは、`parallel_sort`よりもパフォーマンスが向上しますが、O (N) 空間が必要です。

`parallel_radixsort` アルゴリズムはハッシュに基づいています。 つまり、整数キーを使用して要素を並べ替えます。 このアルゴリズムでは、キーを使用して、比較を使用する代わりに、要素の変換先を直接計算できます。 `parallel_buffered_sort`と同様に、このアルゴリズムには O (N) 空間が必要です。

次の表は、3つの並列並べ替えアルゴリズムの重要なプロパティをまとめたものです。

|アルゴリズム|説明|並べ替えメカニズム|並べ替えの安定性|メモリの要件|時間の複雑さ|反復子アクセス|
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|
|`parallel_sort`|汎用的な比較に基づく並べ替え。|比較基準 (昇順)|不安定|なし|O ((N/P) log (N/P) + 2N ((P-1)/P)|ランダム|
|`parallel_buffered_sort`|O (N) 空間を必要とする汎用的な比較ベースの並べ替えの高速化。|比較基準 (昇順)|不安定|追加の O (N) 空間が必要|O ((N/P) ログ (N))|ランダム|
|`parallel_radixsort`|O (N) 空間を必要とする整数キーベースの並べ替え。|ハッシュベース|Stable|追加の O (N) 空間が必要|O (N/P)|ランダム|

次の図は、3つの並列並べ替えアルゴリズムの重要なプロパティをグラフィカルに示しています。

![並べ替えアルゴリズムの比較](../../parallel/concrt/media/concrt_parallel_sorting.png "並べ替えアルゴリズムの比較")

これらの並列並べ替えアルゴリズムは、キャンセルと例外処理の規則に従います。 同時実行ランタイムでのキャンセルと例外処理の詳細については、「[並列アルゴリズム](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms)と[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)のキャンセル」を参照してください。

> [!TIP]
> これらの並列並べ替えアルゴリズムは、移動セマンティクスをサポートしています。 移動代入演算子を定義して、スワップ操作をより効率的に実行できるようにすることができます。 移動セマンティクスおよび移動代入演算子の詳細については、「[右辺値参照宣言子: & &](../../cpp/rvalue-reference-declarator-amp-amp.md)」、および「移動[コンストラクターC++と移動代入演算子 ()](../../cpp/move-constructors-and-move-assignment-operators-cpp.md)」を参照してください。 移動代入演算子または swap 関数を指定しない場合、並べ替えアルゴリズムではコピーコンストラクターが使用されます。

次の基本的な例は、`parallel_sort` を使用して `int` 値の `vector` を並べ替える方法を示しています。 既定では、`parallel_sort` は[std:: less](../../standard-library/less-struct.md)を使用して値を比較します。

[!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]

この例では、カスタムの compare 関数を指定する方法を示します。 Std:: [complex:: real](../../standard-library/complex-class.md#real)メソッドを使用して、 [std:: complex\<double >](../../standard-library/complex-double.md)値を昇順に並べ替えます。

[!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]

この例では、ハッシュ関数を `parallel_radixsort` アルゴリズムに提供する方法を示します。 この例では、3-d ポイントを並べ替えます。 ポイントは、参照ポイントからの距離に基づいて並べ替えられます。

[!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]

例として、この例では比較的小さなデータセットを使用しています。 ベクターの初期サイズを増やして、より大きなデータセットに対するパフォーマンスの向上を試すことができます。

この例では、ハッシュ関数としてラムダ式を使用します。 また、std::[hash クラス](../../standard-library/hash-class.md)の組み込みの実装のいずれかを使用することも、独自の特殊化を定義することもできます。 また、次の例に示すように、カスタムハッシュ関数オブジェクトを使用することもできます。

[!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]

[!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]

ハッシュ関数は整数型を返す必要があります ([std:: is_integral:: value](../../standard-library/is-integral-class.md)は**true**である必要があります)。 この整数型は `size_t`型に変換可能である必要があります。

### <a name="choose_sort"></a>並べ替えアルゴリズムの選択

多くの場合、`parallel_sort` は、速度とメモリのパフォーマンスのバランスを最大限に発揮します。 ただし、データセットのサイズを大きくすると、使用可能なプロセッサの数、または比較関数の複雑さ、`parallel_buffered_sort` または `parallel_radixsort` のパフォーマンスが向上します。 特定のシナリオでどの並べ替えアルゴリズムを使用するかを決定する最善の方法は、代表的なコンピューター構成での一般的なデータの並べ替えにかかる時間を実験して測定することです。 並べ替え方法を選択するときは、次のガイドラインに留意してください。

- データセットのサイズ。 このドキュメントでは、*小さい*データセットに含まれる要素の数が1000未満、*中規模*のデータセットに1万と10万の要素が含まれており、*大規模*なデータセットには10万の要素が含まれています。

- 比較関数またはハッシュ関数が実行する作業量。

- 使用可能なコンピューティングリソースの量。

- データセットの特性。 たとえば、既に並べ替えられていても、まったく並べ替えられていないデータに対しては、1つのアルゴリズムが適切に実行される場合があります。

- チャンクサイズ。 省略可能な `_Chunk_size` 引数は、アルゴリズムが並列からシリアル並べ替えの実装に切り替えるタイミングを指定します。これは、全体の並べ替えをより小さな作業単位に細分化ためです。 たとえば、512を指定した場合、アルゴリズムは、作業単位に512個以下の要素が含まれている場合に、直列実装に切り替わります。 直列実装では、データを並列処理するために必要なオーバーヘッドが解消されるため、全体的なパフォーマンスを向上させることができます。

使用可能なコンピューティングリソースが多数ある場合や、比較関数またはハッシュ関数が比較的大量の作業を実行する場合でも、小規模なデータセットを並列に並べ替えることができない可能性があります。 [Std:: sort](../../standard-library/algorithm-functions.md#sort)関数を使用して、小さいデータセットを並べ替えることができます。 (`parallel_sort` と `parallel_buffered_sort` は、データセットよりも大きいチャンクサイズを指定した場合に `sort` を呼び出します。ただし、`parallel_buffered_sort` では、O (N) 空間を割り当てる必要がありますが、ロックの競合やメモリの割り当てによって追加の時間がかかることがあります)。

メモリを節約する必要がある場合、またはメモリアロケーターでロックの競合が発生する場合は、`parallel_sort` を使用して、中規模のデータセットを並べ替えます。 `parallel_sort` には追加の領域は必要ありません。他のアルゴリズムでは、O (N) 空間が必要です。

`parallel_buffered_sort` は、中規模のデータセットを並べ替える場合や、アプリケーションが追加の O (N) 領域要件を満たしている場合に使用します。 `parallel_buffered_sort` は、多数のコンピューティングリソースがある場合や、負荷の大きい関数またはハッシュ関数がある場合に特に便利です。

`parallel_radixsort` を使用して、大規模なデータセットを並べ替えたり、アプリケーションが追加の O (N) 領域要件を満たしている場合に使用したりします。 `parallel_radixsort` は、同等の比較操作の負荷が高い場合や、両方の操作の負荷が高い場合に特に役立ちます。

> [!CAUTION]
> 適切なハッシュ関数を実装するには、データセットの範囲と、データセット内の各要素が対応する符号なしの値に変換される方法を把握している必要があります。 ハッシュ操作は符号なしの値に対して機能するので、符号なしのハッシュ値を生成できない場合は、別の並べ替え方法を検討してください。

次の例では、`sort`、`parallel_sort`、`parallel_buffered_sort`、および `parallel_radixsort` のパフォーマンスを、同じ大きなランダムデータセットと比較します。

[!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]

この例では、並べ替え中に O (N) 空間の割り当てが許容されることを前提としています。 `parallel_radixsort` は、このコンピューター構成でこのデータセットに対して最適なを実行します。

[[トップ](#top)]

## <a name="related-topics"></a>関連トピック

|タイトル|説明|
|-----------|-----------------|
|[方法: parallel_for ループを記述する](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|`parallel_for` アルゴリズムを使用して行列乗算を実行する方法について説明します。|
|[方法: parallel_for_each ループを記述する](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|`parallel_for_each` アルゴリズムを使用して、 [std:: array](../../standard-library/array-class-stl.md)オブジェクト内の素数の数を並列で計算する方法について説明します。|
|[方法: 並列呼び出しを使用して並列並べ替えルーチンを記述する](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|`parallel_invoke` アルゴリズムを使用して、バイトニック ソート アルゴリズムのパフォーマンスを向上させる方法について説明します。|
|[方法: Parallel.Invoke を使用して並列操作を実行する](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|`parallel_invoke` アルゴリズムを使用して、共有データ ソースに対して複数の操作を実行するプログラムのパフォーマンスを向上させる方法について説明します。|
|[方法: マップ操作と縮小操作を並列実行する](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|`parallel_transform` アルゴリズムと `parallel_reduce` アルゴリズムを使用して、ファイル内の単語の出現回数をカウントする map および reduce 操作を実行する方法について説明します。|
|[並列パターン ライブラリ (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|PPL について説明します。これは、同時実行アプリケーションを開発するためのスケーラビリティと使いやすさを促進する命令型プログラミングモデルを提供します。|
|[PPL における取り消し処理](cancellation-in-the-ppl.md)|PPL におけるキャンセルの役割、並列処理を取り消す方法、およびタスクグループがキャンセルされたことを確認する方法について説明します。|
|[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|同時実行ランタイムにおける例外処理の役割について説明します。|

## <a name="reference"></a>参照

[parallel_for 関数](reference/concurrency-namespace-functions.md#parallel_for)

[parallel_for_each 関数](reference/concurrency-namespace-functions.md#parallel_for_each)

[parallel_invoke 関数](reference/concurrency-namespace-functions.md#parallel_invoke)

[affinity_partitioner クラス](../../parallel/concrt/reference/affinity-partitioner-class.md)

[auto_partitioner クラス](../../parallel/concrt/reference/auto-partitioner-class.md)

[simple_partitioner クラス](../../parallel/concrt/reference/simple-partitioner-class.md)

[static_partitioner クラス](../../parallel/concrt/reference/static-partitioner-class.md)

[parallel_sort 関数](reference/concurrency-namespace-functions.md#parallel_sort)

[parallel_buffered_sort 関数](reference/concurrency-namespace-functions.md#parallel_buffered_sort)

[parallel_radixsort 関数](reference/concurrency-namespace-functions.md#parallel_radixsort)
