---
title: コンカレンシー ランタイムに関する全般的なベスト プラクティス
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
ms.openlocfilehash: 15bae5ba25da4987b076cf3de67cd8484fe47df8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141770"
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>コンカレンシー ランタイムに関する全般的なベスト プラクティス

ここでは、コンカレンシー ランタイムの複数の領域に適用されるベスト プラクティスについて説明します。

## <a name="top"></a> セクション

このドキュメントは、次のトピックに分かれています。

- [可能な場合は協調同期コンストラクトを使用する](#synchronization)

- [時間のかかるタスクを避けてください。](#yield)

- [オーバーサブスクリプションを使用して、ブロックまたは待機時間が長い操作をオフセットする](#oversubscription)

- [可能な場合は、同時実行メモリ管理関数を使用します。](#memory)

- [RAII を使用して同時実行オブジェクトの有効期間を管理する](#raii)

- [グローバルスコープで同時実行オブジェクトを作成しない](#global-scope)

- [共有データセグメントで同時実行オブジェクトを使用しない](#shared-data)

## <a name="synchronization"></a>可能な場合は協調同期コンストラクトを使用する

コンカレンシー ランタイムには、外部同期オブジェクトを必要としないコンカレンシー セーフのコンストラクトが多数用意されています。 たとえば、 [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)クラスは、同時実行セーフな追加操作と要素アクセス操作を提供します。 ここでは、同時実行セーフとは、ポインターまたは反復子が常に有効であることを意味します。 これは、要素の初期化、または特定のトラバーサルの順序の保証ではありません。 ただし、リソースへの排他アクセスが必要な場合、ランタイムは[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)、 [concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)、および[concurrency:: event](../../parallel/concrt/reference/event-class.md)クラスを提供します。 これらの型は協調的に動作するため、タスク スケジューラは、最初のタスクがデータを待っている間、処理リソースを別のコンテキストに再割り当てすることができます。 可能であれば、協調的に動作しない他の同期機構 (Windows API に用意されている同期機構など) の代わりに、これらの同期型を使用してください。 これらの同期の種類とコード例の詳細については、「同期[データ構造](../../parallel/concrt/synchronization-data-structures.md)」と「[同期データ構造と Windows API の比較](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)」を参照してください。

[[トップ](#top)]

## <a name="yield"></a>時間のかかるタスクを避けてください。

タスク スケジューラは協調的に動作するため、タスク間で公平性は保たれません。 したがって、1 つのタスクが原因で他のタスクを開始できなくなることがあります。 このような状況は許容される場合もありますが、デッドロックやスタベーションを引き起こす場合もあります。

次の例では、割り当てられている処理リソースの数を超えるタスクを実行します。 1 つ目のタスクはタスク スケジューラに譲渡しないため、そのタスクが終了するまで 2 つ目のタスクは開始されません。

[!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]

この例の結果は、次のようになります。

1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000

いくつかの方法を使用して、2 つのタスク間の協調を有効にすることができます。 1 つは、長時間実行されるタスクの中でタスク スケジューラに譲渡する時間を不定期に設けることです。 次の例では、`task` 関数を変更して、 [concurrency:: Context:: Yield](reference/context-class.md#yield)メソッドを呼び出して、別のタスクが実行できるようにタスクスケジューラに実行を生成します。

[!code-cpp[concrt-cooperative-tasks#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_2.cpp)]

この例の結果は、次のようになります。

```Output
1: 250000000
2: 250000000
1: 500000000
2: 500000000
1: 750000000
2: 750000000
1: 1000000000
2: 1000000000
```

`Context::Yield` メソッドが譲渡するのは、現在のスレッドが属しているスケジューラ上の別のアクティブ スレッド、軽量タスク、または別のオペレーティング システム スレッドのみです。 このメソッドは、 [concurrency:: task_group](reference/task-group-class.md)または[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)オブジェクトで実行するようにスケジュールされているが、まだ開始されていない作業にはなりません。

他の方法を使用して、長時間実行されるタスク間の協調を有効にすることもできます。 大きなタスクを小さなサブタスクに分割できます。 また、時間のかかるタスクの中でオーバーサブスクリプションを有効にすることもできます。 オーバーサブスクリプションを使用すると、使用可能なハードウェア スレッドよりも多くのスレッドを作成できます。 オーバーサブスクリプションは、長時間実行されるタスクの中で非常に長い待機時間 (ディスクやネットワーク接続からのデータの読み取りなど) が発生するような場合に特に役立ちます。 軽量タスクとオーバーサブスクリプションの詳細については、「[タスクスケジューラ](../../parallel/concrt/task-scheduler-concurrency-runtime.md)」を参照してください。

[[トップ](#top)]

## <a name="oversubscription"></a>オーバーサブスクリプションを使用して、ブロックまたは待機時間が長い操作をオフセットする

同時実行ランタイムには、タスクを協調的にブロックおよび生成できるようにする[Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)などの同期プリミティブが用意されています。 最初のタスクが協調的なブロッキングや譲渡を行った場合、タスク スケジューラは、そのタスクがデータを待っている間、処理リソースを別のコンテキストに再割り当てすることができます。

コンカレンシー ランタイムに用意されている協調的ブロッキング機構を使用できない場合もあります。 たとえば、使用する外部ライブラリによっては、別の同期機構が使用されることがあります。 別の例としては、Windows API `ReadFile` 関数を使用してネットワーク接続からデータを読み取る場合など、非常に長い待機時間が発生するような操作を実行する場合です。 このような場合、オーバーサブスクリプションを使用して、該当するタスクがアイドル状態のときに他のタスクが実行されるようにすることができます。 オーバーサブスクリプションを使用すると、使用可能なハードウェア スレッドよりも多くのスレッドを作成できます。

次の関数 `download` について考えます。この関数では、特定の URL にあるファイルをダウンロードします。 この例では、 [concurrency:: Context:: Oversubscribe](reference/context-class.md#oversubscribe)メソッドを使用して、アクティブなスレッドの数を一時的に増やしています。

[!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]

`GetHttpFile` 関数は潜在的な操作を実行するため、オーバーサブスクリプションを使用することで、現在のタスクがデータを待っている間、他のタスクを実行できるようになります。 この例の完全なバージョンについては、「[方法: オーバーサブスクリプションを使用して待機時間をオフセットする](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)」を参照してください。

[[トップ](#top)]

## <a name="memory"></a>可能な場合は、同時実行メモリ管理関数を使用します。

有効期間が比較的短い小さいオブジェクトを頻繁に割り当てるタスクがある場合は、メモリ管理関数 ( [concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc)と[Concurrency:: Free](reference/concurrency-namespace-functions.md#free)) を使用します。 コンカレンシー ランタイムでは、実行中のスレッドごとに別個のメモリ キャッシュが保持されます。 `Alloc` 関数と `Free` 関数は、ロックやメモリ バリアを使用することなく、これらのキャッシュからメモリの割り当てと解放を行います。

これらのメモリ管理機能の詳細については、「[タスクスケジューラ](../../parallel/concrt/task-scheduler-concurrency-runtime.md)」を参照してください。 これらの関数を使用する例については、「[方法: Alloc と Free を使用してメモリパフォーマンスを向上させる](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)」を参照してください。

[[トップ](#top)]

## <a name="raii"></a>RAII を使用して同時実行オブジェクトの有効期間を管理する

コンカレンシー ランタイムでは、例外処理を使用して、取り消し処理などの機能を実装します。 したがって、ランタイムを呼び出す場合や、ランタイムを呼び出す別のライブラリを呼び出す場合は、例外セーフなコードを記述してください。

*リソース取得 Is 初期化*(RAII) パターンは、特定のスコープで同時実行オブジェクトの有効期間を安全に管理するための1つの方法です。 RAII パターンでは、データ構造はスタック上に割り当てられます。 データ構造は、作成されたときにリソースを初期化または取得し、破棄されたときにそのリソースを破棄または解放します。 RAII パターンでは、外側のスコープが終了する前に、常にデストラクターが呼び出されます。 このパターンは、関数に複数の `return` ステートメントが含まれる場合に便利です。 また、このパターンは、例外セーフなコードを記述するのにも役立ちます。 `throw` ステートメントによってスタックがアンワインドされると、RAII オブジェクトのデストラクターが呼び出されます。そのため、リソースが常に正しく削除または解放されます。

ランタイムは、RAII パターンを使用する複数のクラス ( [concurrency:: critical_section:: scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class) 、 [concurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)など) を定義します。 これらのヘルパークラスは、*スコープロック*と呼ばれます。 これらのクラスは、 [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)オブジェクトまたは[concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)オブジェクトを操作するときに、いくつかの利点を提供します。 これらのクラスのコンストラクターは、提供された `critical_section` オブジェクトまたは `reader_writer_lock` オブジェクトへのアクセスを取得し、デストラクターはそのオブジェクトへのアクセスを解放します。 相互排他オブジェクトが破棄されると、スコープ ロックはそのオブジェクトへのアクセスを自動的に解放するため、基になるオブジェクトのロックを手動で解除する必要はありません。

次のクラス `account` について考えます。このクラスは、外部ライブラリで定義されているため、変更できません。

[!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]

次の例では、`account` オブジェクトに対して複数のトランザクションを並列に実行します。 この例では、`critical_section` オブジェクトを使用して、`account` オブジェクトへのアクセスを同期します。`account` クラスはコンカレンシー セーフではないためです。 各並列操作では、`critical_section::scoped_lock` オブジェクトを使用して、操作が成功または失敗したときに `critical_section` オブジェクトのロックが確実に解除されるようにします。 口座残高が負の場合、`withdraw` 操作は例外をスローして失敗します。

[!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]

この例では、次のサンプル出力が生成されます。

```Output
Balance before deposit: 1924
Balance after deposit: 2924
Balance before withdrawal: 2924
Balance after withdrawal: -76
Balance before withdrawal: -76
Error details:
    negative balance: -76
```

RAII パターンを使用して同時実行オブジェクトの有効期間を管理するその他の例については、「[チュートリアル: ユーザーインターフェイススレッドからの作業の削除](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)」、「[方法: コンテキストクラスを使用して協調セマフォを実装する](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)」、および「[方法: オーバーサブスクリプションを使用して待機時間をオフセットする](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)」を参照してください。

[[トップ](#top)]

## <a name="global-scope"></a>グローバルスコープで同時実行オブジェクトを作成しない

グローバル スコープでコンカレンシー オブジェクトを作成すると、アプリケーションでデッドロックやメモリ アクセス違反などの問題が発生する可能性があります。

たとえば、コンカレンシー ランタイム オブジェクトの作成時にスケジューラがまだ作成されていない場合、既定のスケジューラが作成されます。 グローバル オブジェクトの構築時に作成されるランタイム オブジェクトにより、ランタイムがこの既定のスケジューラを作成します。 ただし、このプロセスでは内部ロックが使用され、コンカレンシー ランタイムのインフラストラクチャをサポートする他のオブジェクトの初期化を妨げる可能性があります。 まだ初期化されていない別のインフラストラクチャ オブジェクトでこの内部ロックが必要になる場合があるため、アプリケーションでデッドロックが発生する可能性があります。

グローバル[concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md)オブジェクトを作成する例を次に示します。 このパターンは、`Scheduler` クラスだけでなく、コンカレンシー ランタイムに用意されている他のすべての型にも適用されます。 このパターンはアプリケーションの予期しない動作を引き起こす可能性があるため、使用しないことをお勧めします。

[!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]

`Scheduler` オブジェクトを作成する正しい方法の例については、「[タスクスケジューラ](../../parallel/concrt/task-scheduler-concurrency-runtime.md)」を参照してください。

[[トップ](#top)]

## <a name="shared-data"></a>共有データセグメントで同時実行オブジェクトを使用しない

同時実行ランタイムでは、 [data_seg](../../preprocessor/data-seg.md)`#pragma` ディレクティブによって作成されるデータセクションなど、共有データセクションでの同時実行オブジェクトの使用はサポートされていません。 コンカレンシー オブジェクトがプロセス境界をまたいで共有される場合、ランタイムが不整合な状態または無効な状態になる可能性があります。

[[トップ](#top)]

## <a name="see-also"></a>参照

[コンカレンシー ランタイムに関するベスト プラクティス](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[並列パターン ライブラリ (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[非同期エージェント ライブラリ](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[タスク スケジューラ](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[同期データ構造](../../parallel/concrt/synchronization-data-structures.md)<br/>
[同期データ構造と Windows API の比較](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
[方法: Alloc および Free を使用してメモリ パフォーマンスを改善する](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)<br/>
[方法: オーバーサブスクリプションを使用して待機時間を短縮する](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)<br/>
[方法: Context クラスを使用して協調セマフォを実装する](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[チュートリアル: ユーザー インターフェイス スレッドからの処理の除去](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
[並列パターン ライブラリに関するベスト プラクティス](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[非同期エージェント ライブラリに関するベスト プラクティス](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
