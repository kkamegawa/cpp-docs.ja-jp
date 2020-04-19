---
title: 並列パターン ライブラリに関するベスト プラクティス
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Patterns Library, practices to avoid
- practices to avoid, Parallel Patterns Library
- best practices, Parallel Patterns Library
- Parallel Patterns Library, best practices
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
ms.openlocfilehash: 641d85b03fca13a6592610d87563e3e701ad3e3e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854176"
---
# <a name="best-practices-in-the-parallel-patterns-library"></a>並列パターン ライブラリに関するベスト プラクティス

ここでは、並列パターン ライブラリ (PPL) を効果的に使用する方法について説明します。 PPL は、粒度の細かい並列化を実行するための汎用的なコンテナー、オブジェクト、およびアルゴリズムを提供します。

PPL の詳細については、「[並列パターンライブラリ (ppl)](../../parallel/concrt/parallel-patterns-library-ppl.md)」を参照してください。

## <a name="top"></a> セクション

このドキュメントは、次のトピックに分かれています。

- [小さいループ本体を並列化しない](#small-loops)

- [可能な限り高いレベルで並列処理を表現する](#highest)

- [Parallel_invoke を使用して、分割と統治の問題を解決する](#divide-and-conquer)

- [キャンセルまたは例外処理を使用して並列ループを中断する](#breaking-loops)

- [キャンセルと例外処理がオブジェクトの破棄に与える影響について理解する](#object-destruction)

- [並列ループで繰り返しブロックしないでください。](#repeated-blocking)

- [並列処理をキャンセルするときにブロック操作を実行しない](#blocking)

- [並列ループで共有データに書き込みません](#shared-writes)

- [可能な場合は、偽共有を避ける](#false-sharing)

- [タスクの有効期間全体にわたって変数が有効であることを確認する](#lifetime)

## <a name="small-loops"></a>小さいループ本体を並列化しない

比較的小さなループ本体を並列化すると、関連するスケジューリング オーバーヘッドが並列処理のメリットを上回る可能性があります。 次の例について考えます。この例では、2 つの配列に各要素ペアを追加しています。

[!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_1.cpp)]

並列ループの各反復の作業負荷が小さすぎるため、並列処理のオーバーヘッドに勝る利益が得られません。 ループ本体での処理量を増やすか、ループを逐次的に実行すると、ループのパフォーマンスが向上します。

[[トップ](#top)]

## <a name="highest"></a>可能な限り高いレベルで並列処理を表現する

低いレベルでのみコードを並列化する場合は、プロセッサの数が増えても拡張されない fork-join コンストラクトを導入できます。 *フォーク結合*コンストラクトは、1つのタスクが作業を小さな並列サブタスクに分割し、それらのサブタスクが終了するのを待機するコンストラクトです。 サブタスクの場合も、それぞれの処理を再帰的に別のサブタスクに分割できます。

fork-join モデルはさまざまな問題を解決するのに役立ちますが、同期のオーバーヘッドに伴ってスケーラビリティが下がるような状況もあります。 たとえば、イメージ データを逐次的に処理する次のコードについて考えます。

[!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_2.cpp)]

各ループ反復は独立しているため、次の例に示すように処理の大部分を並列化できます。 この例では、 [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)アルゴリズムを使用して、外側のループを並列化します。

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_3.cpp)]

次の例では、ループで `ProcessImage` 関数を呼び出す fork-join コンストラクトを示します。 `ProcessImage` を呼び出すたびに制御が戻されるのではなく、各サブタスクが終了してから戻されます。

[!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_4.cpp)]

並列ループの各反復でほとんど処理が実行されないか、並列ループで実行される処理が不均衡の場合 (つまり、ループ反復ごとに所要時間が異なる場合)、処理のフォークと結合を頻繁に行うことによるスケジューリング オーバーヘッドが並列実行のメリットを上回ることがあります。 プロセッサの数が増えると、このオーバーヘッドも大きくなります。

この例のスケジューリング オーバーヘッドの量を低減するには、内側のループを並列化する前に外側のループを並列化するか、パイプライン処理などの別の parallel コンストラクトを使用します。 次の例では、`ProcessImages` 関数を変更し、 [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)アルゴリズムを使用して外側のループを並列化します。

[!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_5.cpp)]

パイプラインを使用してイメージ処理を並列で実行する同様の例については、「[チュートリアル: イメージ処理ネットワークの作成](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)」を参照してください。

[[トップ](#top)]

## <a name="divide-and-conquer"></a>Parallel_invoke を使用して、分割と統治の問題を解決する

*分割と統治*の問題は、再帰を使用してタスクをサブタスクに分割するフォーク結合コンストラクトの形式です。 Concurrency: [: task_group](reference/task-group-class.md)および[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)クラスに加えて、 [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)アルゴリズムを使用して、分割と統治の問題を解決することもできます。 `parallel_invoke` アルゴリズムでは、タスク グループ オブジェクトよりも簡単な構文を使用できます。このアルゴリズムは、並列タスクの数が固定されている場合に役立ちます。

次の例では、`parallel_invoke` アルゴリズムを使用して、バイトニック ソート アルゴリズムを実装します。

[!code-cpp[concrt-parallel-bitonic-sort#12](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_6.cpp)]

`parallel_invoke` アルゴリズムでは、オーバーヘッドを低減するために、一連のタスクの最後のタスクを呼び出し元のコンテキストで実行します。

この例の完全なバージョンについては、「[方法: parallel_invoke を使用して並列並べ替えルーチンを記述](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)する」を参照してください。 `parallel_invoke` アルゴリズムの詳細については、「[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)」を参照してください。

[[トップ](#top)]

## <a name="breaking-loops"></a>キャンセルまたは例外処理を使用して並列ループを中断する

PPL では、2 とおりの方法を使用して、タスク グループまたは並列アルゴリズムによって実行される並列処理を取り消すことができます。 1つの方法は、 [concurrency:: task_group](reference/task-group-class.md)クラスおよび[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)クラスによって提供される取り消し機構を使用する方法です。 もう 1 つは、タスクの処理関数の本体で例外をスローする方法です。 並列処理ツリーを取り消す場合は、例外処理を行うよりも取り消し機構を使用する方が効率的です。 *並列作業ツリー*は、一部のタスクグループに他のタスクグループが含まれている、関連するタスクグループのグループです。 取り消し機構では、タスク グループとその子タスク グループを上位から順に取り消します。 反対に、例外処理では下位から順に処理されるため、例外が上位へ移動するたびに、子タスク グループを個別に取り消す必要があります。

タスクグループオブジェクトを直接操作する場合は、 [concurrency:: task_group:: cancel](reference/task-group-class.md#cancel)メソッドまたは[concurrency:: structured_task_group:: cancel](reference/structured-task-group-class.md#cancel)メソッドを使用して、そのタスクグループに属する作業を取り消すことができます。 たとえば、`parallel_for` では、並列アルゴリズムを取り消すために、親タスク グループを作成し、そのタスク グループを取り消します。 たとえば、次の関数 `parallel_find_any` について考えます。この関数では、配列内の値を並列に検索します。

[!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_7.cpp)]

並列アルゴリズムではタスク グループが使用されるため、並列反復処理のいずれかによって親タスク グループが取り消されると、タスク全体が取り消されます。 この例の完全なバージョンについては、「[方法: キャンセルを使用して並列ループを中断する](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)」を参照してください。

例外処理を使用して並列処理を取り消す方法は、取り消し機構を使用する方法よりも効率の面で劣りますが、例外処理の方が適している状況もあります。 たとえば、次のメソッド `for_all` では、`tree` 構造体の各ノードに対して処理関数を再帰的に実行します。 この例では、`_children` データメンバーは、`tree` オブジェクトを含む[std:: list](../../standard-library/list-class.md)です。

[!code-cpp[concrt-task-tree-search#6](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_8.cpp)]

ツリーの各要素に対して処理関数を呼び出す必要がない場合、`tree::for_all` メソッドの呼び出し元は例外をスローすることができます。 次の例は `search_for_value` 関数で、提供された `tree` オブジェクト内で値を検索します。 `search_for_value` 関数で使用される処理関数は、ツリーの現在の要素と提供された値が一致する場合に例外をスローします。 `search_for_value` 関数は、`try-catch` ブロックを使用して例外をキャプチャし、結果をコンソールに出力します。

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_9.cpp)]

この例の完全なバージョンについては、「[方法: 例外処理を使用して並列ループを中断する](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)」を参照してください。

PPL に用意されている取り消しおよび例外処理機構に関する一般的な情報については、「PPL と[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)[でのキャンセル](cancellation-in-the-ppl.md)」を参照してください。

[[トップ](#top)]

## <a name="object-destruction"></a>キャンセルと例外処理がオブジェクトの破棄に与える影響について理解する

並列処理ツリーでタスクを取り消すと、子タスクも実行されなくなります。 そのため、アプリケーションで重要となる操作 (リソースの解放など) が子タスクのいずれかで実行されるような場合に問題となります。 また、タスクを取り消すと、例外がオブジェクトのデストラクターを通じて反映され、アプリケーションで未定義の動作が発生する可能性があります。

次の例では、`Resource` クラスはリソースを表し、`Container` クラスはリソースを保持するコンテナーを表します。 そのデストラクターで、`Container` クラスは `cleanup` メンバーの 2 つに対して `Resource` メソッドを並列に呼び出し、3 つ目の `cleanup` メンバーに対して `Resource` メソッドを呼び出します。

[!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_10.h)]

このパターン自体には問題はありませんが、2 つのタスクを並列に実行する次のコードについて考えてみてください。 1 つ目のタスクでは `Container` オブジェクトを作成し、2 つ目のタスクではタスク全体を取り消します。 例では、2つの[concurrency:: event](../../parallel/concrt/reference/event-class.md)オブジェクトを使用して、`Container` オブジェクトが作成された後にキャンセルが発生し、取り消し操作が発生した後に `Container` オブジェクトが破棄されるようにします。

[!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_11.cpp)]

この例の結果は、次のようになります。

```Output
Container 1: Freeing resources...Exiting program...
```

このコード例には次の問題が含まれているため、期待どおりの動作が得られない可能性があります。

- 親タスクを取り消すと、子タスク ( [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)の呼び出しも取り消されます。 そのため、これら 2 つのリソースは解放されません。

- 親タスクを取り消すと、子タスクが内部例外をスローします。 `Container` デストラクターではこの例外は処理されないため、例外が上位に伝達され、3 つ目のリソースは解放されません。

- 子タスクによってスローされた例外が、`Container` デストラクターを通じて伝達されます。 デストラクターからスローされることにより、アプリケーションが未定義の状態になります。

タスクが取り消されないことを保証できる場合を除き、タスクでは重要な操作 (リソースの解放など) を実行しないことをお勧めします。 また、採用している型のデストラクターでスローを行うようなランタイム機能は使用しないようにしてください。

[[トップ](#top)]

## <a name="repeated-blocking"></a>並列ループで繰り返しブロックしないでください。

[同時実行::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)や[concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)などの並列ループによって操作がブロックされると、ランタイムは短時間で多数のスレッドを作成する可能性があります。

コンカレンシー ランタイムでは、タスクが終了するか、協調的にブロックまたは譲渡すると、追加の処理が実行されます。 並列ループの 1 回の反復がブロックすると、別の反復が開始されることがあります。 使用可能なアイドル スレッドが存在しない場合は、新しいスレッドが作成されます。

並列ループの本体がときどきブロックする程度であれば、この機構によりタスクの全体的なスループットが最大限に高まります。 ただし、反復処理で頻繁にブロックが発生する場合は、追加の処理を実行するために多数のスレッドが作成される可能性があります。 それに伴って、メモリ不足の状態に陥ったり、ハードウェア リソースが不適切に使用されたりする場合があります。

`parallel_for` ループの各反復処理で[concurrency:: send](reference/concurrency-namespace-functions.md#send)関数を呼び出す次の例を考えてみます。 `send` は協調的にブロックするため、`send` を呼び出すたびに、追加の処理を実行するための新しいスレッドが作成されます。

[!code-cpp[concrt-repeated-blocking#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_12.cpp)]

このパターンを回避するようにコードをリファクタリングすることをお勧めします。 この例では、逐次的な `send` ループで `for` を呼び出すことによって、追加のスレッドの作成を回避できます。

[[トップ](#top)]

## <a name="blocking"></a>並列処理をキャンセルするときにブロック操作を実行しない

並列処理を取り消すには、可能であれば、 [concurrency:: task_group:: cancel](reference/task-group-class.md#cancel)メソッドまたは[concurrency:: structured_task_group:: cancel](reference/structured-task-group-class.md#cancel)メソッドを呼び出す前に、ブロッキング操作を実行しないでください。

タスクが協調的ブロッキング操作を実行すると、ランタイムは最初のタスクがデータを待っている間に他の処理を実行できます。 待機中のタスクがブロック解除すると、ランタイムはそのタスクを再スケジュールします。 ランタイムは、通常、直近にブロック解除したタスクから順に再スケジュールします。 そのため、ブロッキング操作中に不要な処理がスケジュールされ、パフォーマンスが低下します。 したがって、並列処理を取り消す前にブロッキング操作を実行すると、そのブロッキング操作が原因で `cancel` の呼び出しが遅れる可能性があります。 それにより、他のタスクで不要な処理が実行されるようになります。

次の例について考えます。この例では、提供された述語関数を満たす指定の配列の要素を検索する `parallel_find_answer` 関数を定義します。 述語関数が**true**を返すと、parallel work 関数は `Answer` オブジェクトを作成し、タスク全体を取り消します。

[!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_13.cpp)]

`new` 演算子は、ブロッキングの対象となる可能性のあるヒープ割り当てを実行します。 ランタイムは、タスクが[concurrency:: critical_section:: lock](reference/critical-section-class.md#lock)の呼び出しなどの協調的ブロッキング呼び出しを実行する場合にのみ、他の処理を実行します。

次の例では、不要な処理を回避し、それによってパフォーマンスを向上させる方法を示します。 この例では、`Answer` オブジェクト用のストレージを割り当てる前に、タスク グループを取り消します。

[!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_14.cpp)]

[[トップ](#top)]

## <a name="shared-writes"></a>並列ループで共有データに書き込みません

同時実行ランタイムには、共有データへの同時アクセスを同期する複数のデータ構造 ( [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)など) が用意されています。 これらのデータ構造体は、複数のタスクでリソースへの共有アクセスがまれに必要になる場合など、さまざまな状況で役立ちます。

次の例では、 [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)アルゴリズムと `critical_section` オブジェクトを使用して、 [std:: array](../../standard-library/array-class-stl.md)オブジェクト内の素数の数を計算しています。 この例では、各スレッドが共有変数 `prime_sum` にアクセスするのを待つ必要があるため、効率は改善されません。

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_15.cpp)]

また、頻繁なロック操作によってループが事実上シリアル化されるため、パフォーマンスが低下する可能性もあります。 さらに、コンカレンシー ランタイム オブジェクトがブロック操作を実行すると、スケジューラによって追加のスレッドが作成され、最初のスレッドがデータを待っている間に他の処理が実行される可能性があります。 共有データを待つタスクが多数存在し、それに対処するためにランタイムで多数のスレッドが作成されると、アプリケーションのパフォーマンス低下やリソース不足状態が発生することがあります。

PPL は[concurrency:: 組み合わせ](../../parallel/concrt/reference/combinable-class.md)可能クラスを定義します。これにより、ロックのない方法で共有リソースへのアクセスを提供することで、共有状態を排除できます。 `combinable` クラスにはスレッド ローカル ストレージが用意されており、詳細な計算を実行した後、その計算を最終結果にマージできます。 `combinable` オブジェクトは減少変数と考えることができます。

次の例では、前の例を変更し、合計を計算するときに `combinable` オブジェクトの代わりに `critical_section` オブジェクトを使用するようにしています。 この例では、各スレッドが合計のローカル コピーをそれぞれ保持するため、効率が改善されます。 この例では、 [concurrency:: 組み合わせ可能::](reference/combinable-class.md#combine) merge メソッドを使用して、ローカルの計算を最終結果にマージします。

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_16.cpp)]

この例の完全なバージョンについては、「[方法: 組み合わせ可能を使用してパフォーマンスを向上](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)させる」を参照してください。 `combinable` クラスの詳細については、「[並列コンテナーとオブジェクト](../../parallel/concrt/parallel-containers-and-objects.md)」を参照してください。

[[トップ](#top)]

## <a name="false-sharing"></a>可能な場合は、偽共有を避ける

*偽共有*は、別々のプロセッサで実行されている複数の同時実行タスクが、同じキャッシュ行に配置されている変数に書き込まれる場合に発生します。 1 つのタスクが変数のいずれかに書き込みを行うと、両方の変数のキャッシュ ラインが無効化されます。 キャッシュ ラインが無効化されるたびに、各プロセッサでキャッシュ ラインの再読み込みを行う必要があります。 したがって、偽共有が発生すると、アプリケーションでパフォーマンスが低下する可能性があります。

次の基本的な例では、2 つの同時実行タスクがそれぞれ共有カウンター変数をインクリメントする場合を示します。

[!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_17.cpp)]

2 つのタスク間でデータが共有されないようにするには、2 つのカウンター変数を使用するように例を変更します。 この例では、タスクの終了後に最終的なカウンター値を計算します。 ただし、`count1` 変数と `count2` 変数が同じキャッシュ ラインに配置される可能性があるため、偽共有となります。

[!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_18.cpp)]

偽共有をなくす方法の 1 つは、カウンター変数を必ず別々のキャッシュ ラインに配置することです。 次の例では、64 バイト境界上に `count1` 変数と `count2` 変数を配置します。

[!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_19.cpp)]

この例では、メモリ キャッシュのサイズが 64 バイト以下であると仮定しています。

タスク間でデータを共有する必要がある場合は、 [concurrency:: 組み合わせ](../../parallel/concrt/reference/combinable-class.md)可能クラスを使用することをお勧めします。 `combinable` クラスは、偽共有が発生する可能性を減らすようにスレッド ローカル変数を作成します。 `combinable` クラスの詳細については、「[並列コンテナーとオブジェクト](../../parallel/concrt/parallel-containers-and-objects.md)」を参照してください。

[[トップ](#top)]

## <a name="lifetime"></a>タスクの有効期間全体にわたって変数が有効であることを確認する

タスク グループまたは並列アルゴリズムにラムダ式を渡す場合、ラムダ式の本体で外側のスコープ内の変数を値でアクセスするのか参照でアクセスするのかは、capture 句で指定します。 ラムダ式に変数を渡すときに参照渡しを使用する場合、タスクが終了するまでその変数の有効期間が続くようにする必要があります。

次の例について考えます。この例では、`object` クラスと `perform_action` 関数を定義します。 `perform_action` 関数は、`object` 変数を作成し、その変数に対していくつかのアクションを非同期的に実行します。 `perform_action` 関数から制御が戻される前にタスクが終了するとは限らないため、タスクの実行中に `object` 変数が破棄されると、プログラムのクラッシュや未定義の動作が発生します。

[!code-cpp[concrt-lambda-lifetime#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_20.cpp)]

アプリケーションの要件に応じて、次の手法のいずれかを使用して、変数が各タスクの有効期間を通じて有効のまま維持されるようにすることができます。

次の例では、タスクに対して `object` 変数の値渡しを行います。 そのため、タスクは変数の個別コピーに対して作用します。

[!code-cpp[concrt-lambda-lifetime#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_21.cpp)]

`object` 変数は値渡しで渡されるため、この変数の状態変化が発生しても、元のコピーには反映されません。

次の例では、 [concurrency:: task_group:: wait](reference/task-group-class.md#wait)メソッドを使用して、`perform_action` 関数が戻る前にタスクが終了するようにします。

[!code-cpp[concrt-lambda-lifetime#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_22.cpp)]

関数から制御が戻される前にタスクが終了するようになったため、`perform_action` 関数が非同期に動作することがなくなりました。

次の例では、`perform_action` 関数を変更して、`object` 変数の参照が使用されるようにします。 呼び出し元は、タスクが終了するまで `object` 変数の有効期間が続くようにする必要があります。

[!code-cpp[concrt-lambda-lifetime#4](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_23.cpp)]

また、タスク グループまたは並列アルゴリズムに渡すオブジェクトの有効期間をポインターで制御することもできます。

ラムダ式について詳しくは、「[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)」をご覧ください。

[[トップ](#top)]

## <a name="see-also"></a>参照

[コンカレンシー ランタイムに関するベスト プラクティス](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[並列パターン ライブラリ (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[並列コンテナーと並列オブジェクト](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL における取り消し処理](cancellation-in-the-ppl.md)<br/>
[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[チュートリアル: イメージ処理ネットワークの作成](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[方法: 並列呼び出しを使用して並列並べ替えルーチンを記述する](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br/>
[方法: キャンセル処理を使用して並列ループを中断する](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br/>
[方法: combinable を使用してパフォーマンスを向上させる](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
[非同期エージェント ライブラリに関するベスト プラクティス](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br/>
[コンカレンシー ランタイムに関する全般的なベスト プラクティス](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
