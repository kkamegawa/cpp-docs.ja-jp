---
title: コンカレンシー ランタイム
ms.date: 07/20/2018
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
ms.openlocfilehash: a17b4439baaec9caacfeca08983d0255b5a145de
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141616"
---
# <a name="concurrency-runtime"></a>コンカレンシー ランタイム

C++ のコンカレンシー ランタイムにより、信頼性が高く、スケーラブルで、応答性の高い並行アプリケーションを作成できます。 このフレームワークでは抽象のレベルが引き上げられるので、コンカレンシーに関連するインフラストラクチャの詳細を管理する必要はありません。 また、アプリケーションのサービスの品質への要求を満たすスケジューリング ポリシーを指定するためにも使用できます。 コンカレンシー ランタイムを初めて使用する場合に役立つ情報が記載されている次の各ドキュメントを活用してください。

リファレンスドキュメントについては、「[リファレンス](../../parallel/concrt/reference/reference-concurrency-runtime.md)」を参照してください。

> [!TIP]
> コンカレンシー ランタイムは C++11 機能に大きく依存しており、最新の C++ のスタイルが採用されています。 詳細については、「」[をC++](../../cpp/welcome-back-to-cpp-modern-cpp.md)参照してください。

## <a name="choosing-concurrency-runtime-features"></a>コンカレンシー ランタイムの機能を選択する

|||
|-|-|
|[概要](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|コンカレンシー ランタイムが重要である理由とその主要機能について説明しています。|
|[他の同時実行モデルとの比較](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|各自のアプリケーション要件に最も合ったコンカレンシー モデルを使用できるように、コンカレンシー ランタイムと他のコンカレンシー モデル (Windows スレッド プールや OpenMP など) の違いについて説明しています。|
|[OpenMP からコンカレンシー ランタイムへの移行](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|OpenMP とコンカレンシー ランタイムの違いについて説明し、既存の OpenMP コードからコンカレンシー ランタイムの使用に移行する方法の例を示します。|
|[並列パターン ライブラリ (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|並列ループ、タスク、および並列コンテナーを提供する PPL について説明します。|
|[非同期エージェント ライブラリ](../../parallel/concrt/asynchronous-agents-library.md)|非同期エージェントとメッセージ パッシングを使用して、アプリケーションにデータ フローおよびパイプライン処理タスクを簡単に組み込む方法について説明しています。|
|[タスク スケジューラ](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|コンカレンシー ランタイムを使用するデスクトップ アプリケーションのパフォーマンスを細かく調整できるタスク スケジューラについて説明します。|

## <a name="task-parallelism-in-the-ppl"></a>PPL でのタスクの並列処理

|||
|-|-|
|[タスクの並列化](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [方法: 並列呼び出しを使用して並列並べ替えルーチンを記述する](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [方法: Parallel.Invoke を使用して並列操作を実行する](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [方法: 遅延後に完了するタスクを作成する](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|非同期コードを記述し、並列処理を分解するために役立つ、タスク グループとタスクについて説明します。|
|[チュートリアル: フューチャの実装](../../parallel/concrt/walkthrough-implementing-futures.md)|コンカレンシー ランタイムの機能をまとめて、より多くの処理を行う方法を示します。|
|[チュートリアル: ユーザー インターフェイス スレッドからの処理の除去](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|MFC アプリケーションの UI スレッドによって実行される処理をワーカー スレッドへ移動する方法を示します。|
|[並列パターン ライブラリに関するベスト プラクティス](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [コンカレンシー ランタイムに関する全般的なベスト プラクティス](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|PPL の使用上のヒントとベスト プラクティスを提供します。|

## <a name="data-parallelism-in-the-ppl"></a>PPL でのデータの並列処理

|||
|-|-|
|[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [方法: parallel_for ループを記述する](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [方法: parallel_for_each ループを記述する](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [方法: マップ操作と縮小操作を並列実行する](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|`parallel_for`、 `parallel_for_each`、 `parallel_invoke`および他の並列アルゴリズムについて説明します。 データの収集を含む *データの並列化* の問題を解決するには、並列アルゴリズムを使用します。|
|[並列コンテナーと並列オブジェクト](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [方法: 並列コンテナーを使用して効率を向上させる](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [方法: combinable を使用してパフォーマンスを向上させる](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [方法: combinable を使用して集合を結合する](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|`combinable` クラス、および `concurrent_vector`、 `concurrent_queue`、 `concurrent_unordered_map`および他の並列コンテナーについて説明します。 要素へのスレッドセーフなアクセスを提供するコンテナーを必要とする場合には、並列コンテナーと並列オブジェクトを使用します。|
|[並列パターン ライブラリに関するベスト プラクティス](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [コンカレンシー ランタイムに関する全般的なベスト プラクティス](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|PPL の使用上のヒントとベスト プラクティスを提供します。|

## <a name="canceling-tasks-and-parallel-algorithms"></a>タスクと並列アルゴリズムの取り消し

|||
|-|-|
|[PPL における取り消し処理](cancellation-in-the-ppl.md)|開始の方法やキャンセル要求への応答の方法など、PPL でのキャンセル処理の役割について説明します。|
|[方法: キャンセル処理を使用して並列ループを中断する](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [方法: 例外処理を使用して並列ループを中断する](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|データ並列処理を取り消すための 2 とおりの方法を示します。|

## <a name="universal-windows-platform-apps"></a>ユニバーサル Windows プラットフォーム アプリ

|||
|-|-|
|[C++ における UWP アプリ用の非同期操作の作成](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|同時実行ランタイムを使用して UWP アプリで非同期操作を作成する際に留意すべき重要な点について説明します。|
|[チュートリアル: タスクおよび XML HTTP 要求を使用した接続](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|PPL タスクを `IXMLHTTPRequest2` および `IXMLHTTPRequest2Callback` インターフェイスと組み合わせて、UWP アプリで HTTP GET 要求と POST 要求を web サービスに送信する方法について説明します。|
|[Windows ランタイムアプリのサンプル](https://code.msdn.microsoft.com/windowsapps)|Windows 8.x 用のダウンロード可能なコードサンプルとデモアプリが含まれています。 C++ のサンプルでは、UX の応答性を保つためにバックグラウンドでデータを処理する PPL のタスクなど、コンカレンシー ランタイムの機能を使用します。|

## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>非同期エージェント ライブラリでのデータ フロー プログラミング

|||
|-|-|
|[非同期エージェント](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [非同期メッセージ ブロック](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [メッセージ パッシング関数](../../parallel/concrt/message-passing-functions.md)<br /><br /> [方法: さまざまなプロデューサー/コンシューマー パターンを実装する](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [方法: call クラスおよび transformer クラスに処理関数を提供する](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [方法: データ パイプラインでトランスフォーマーを使用する](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [方法: 完了したタスクから選択する](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [方法: メッセージを定期的に送信する](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [方法: メッセージ ブロック フィルターを使用する](../../parallel/concrt/how-to-use-a-message-block-filter.md)|非同期エージェント、メッセージ ブロック、およびコンカレンシー ランタイムでデータ フローの操作を実行するためのビルド ブロックであるメッセージ パッシング関数について説明します。|
|[チュートリアル: エージェント ベースのアプリケーションの作成](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [チュートリアル: データフロー エージェントの作成](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|基本的なエージェント ベースのアプリケーションの作成方法を示します。|
|[チュートリアル: イメージ処理ネットワークの作成](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|イメージ処理を実行する非同期メッセージ ブロックのネットワークを作成する方法を示します。|
|[チュートリアル: join を使用したデッドロックの防止](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|コンカレンシー ランタイムを使用してアプリケーションでデッドロックを防止する方法について、"食事する哲学者の問題" を使用して説明します。|
|[チュートリアル: カスタム メッセージ ブロックの作成](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|受信メッセージを優先順位に従って並べるカスタム メッセージ ブロックの型を作成する方法について説明します。|
|[非同期エージェント ライブラリに関するベスト プラクティス](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [コンカレンシー ランタイムに関する全般的なベスト プラクティス](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|エージェントの使用上のヒントとベスト プラクティスを提供します。|

## <a name="exception-handling-and-debugging"></a>例外処理とデバッグ

|||
|-|-|
|[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|コンカレンシー ランタイムで例外を使用する方法について説明します。|
|[並列診断ツール](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|アプリケーションを微調整し、コンカレンシー ランタイムを最も効果的に使用できるようにする方法について説明しています。|

## <a name="tuning-performance"></a>パフォーマンスの調整

|||
|-|-|
|[並列診断ツール](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|アプリケーションを微調整し、コンカレンシー ランタイムを最も効果的に使用できるようにする方法について説明しています。|
|[スケジューラ インスタンス](../../parallel/concrt/scheduler-instances.md)<br /><br /> [方法: スケジューラ インスタンスを管理する](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [スケジューラ ポリシー](../../parallel/concrt/scheduler-policies.md)<br /><br /> [方法: 特定のスケジューラ ポリシーを指定する](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [方法: 特定のスケジューラ ポリシーを使用するエージェントを作成する](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|スケジューラ インスタンスを使用してスケジューラ ポリシーを管理する方法を示します。 デスクトップ アプリケーションの場合、スケジューラ ポリシーを使って、特定の種類の作業負荷と特定の規則を関連付けることができます。 たとえば、昇格したスレッド優先順位で一部のタスクを実行するようにスケジューラ インスタンスを 1 つ作成し、他のタスクについては既定のスケジューラを使用して通常のスレッド優先順位で実行することができます。|
|[スケジュール グループ](../../parallel/concrt/schedule-groups.md)<br /><br /> [方法: スケジュール グループを使用して実行順序に影響を与える](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|スケジュール グループを使用して、関連するタスクの関係付け (グループ化) を行う方法を説明します。 たとえば、関連するタスクが同一プロセッサ ノードでの実行によって恩恵を受ける場合などには、タスク間で高いレベルの局所性が求められます。|
|[軽量タスク](../../parallel/concrt/lightweight-tasks.md)|負荷分散や取り消しを必要としない作業を作成する場合に、軽量タスクがどのように役立つかを説明します。また既存のコードを改変してコンカレンシー ランタイムと使用する場合にも、軽量タスクが有用であることを説明します。|
|[コンテキスト](../../parallel/concrt/contexts.md)<br /><br /> [方法: Context クラスを使用して協調セマフォを実装する](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [方法: オーバーサブスクリプションを使用して待機時間を短縮する](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|コンカレンシー ランタイムによって管理されるスレッドの動作を制御する方法について説明します。|
|[メモリ管理関数](../../parallel/concrt/memory-management-functions.md)<br /><br /> [方法: Alloc および Free を使用してメモリ パフォーマンスを改善する](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|ここでは、コンカレンシー ランタイムに用意されているメモリ管理関数について説明します。これらの関数を使用すると、コンカレンシー方式でメモリの割り当てと解放を行うことができます。|

## <a name="additional-resources"></a>その他のリソース

|||
|-|-|
|[Hilo での非同期プログラミング パターンとヒント (C++ と XAML を使った Windows ストア アプリ)](/previous-versions/windows/apps/jj160321(v=win.10))|同時実行ランタイムを使用して、および XAML を使用する Windows ランタイムアプリである Hilo でC++非同期操作を実装する方法について説明します。|
|[Parallel Programming in Native Code blog (ネイティブ コードでの並行プログラミング ブログ)](https://go.microsoft.com/fwlink/p/?linkid=183873)|コンカレンシー ランタイムでの並列プログラミングに関する詳細なブログ記事を別途紹介しています。|
|[Parallel Computing in C++ and Native Code forum (C++ とネイティブ コードでの並列コンピューティング フォーラム)](https://go.microsoft.com/fwlink/p/?linkid=183874)|コンカレンシー ランタイムに関するコミュニティ ディスカッションに参加できます。|
|[並列プログラミング](/dotnet/standard/parallel-programming/index)|.NET Framework で使用できる並列プログラミングモデルについて説明します。|

## <a name="see-also"></a>参照

[リファレンス](../../parallel/concrt/reference/reference-concurrency-runtime.md)
