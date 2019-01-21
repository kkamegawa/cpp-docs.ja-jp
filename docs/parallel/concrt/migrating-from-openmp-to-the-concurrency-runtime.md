---
title: OpenMP からコンカレンシー ランタイムへの移行
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
ms.openlocfilehash: 78fa83c30bc55d82ffa5d2ba1e7d65472643f86b
ms.sourcegitcommit: ee0103752884425843556a19cf418a504dc3cd02
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2018
ms.locfileid: "53737625"
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>OpenMP からコンカレンシー ランタイムへの移行

コンカレンシー ランタイムでは、さまざまなプログラミング モデルを使用できます。 これらのモデルは、他のライブラリのモデルと重複する場合や、他のライブラリのモデルを補完する場合があります。 このドキュメントのセクション比較[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)同時実行ランタイムにし、同時実行ランタイムを使用する既存の OpenMP コードを移行する方法について例を示します。

OpenMP プログラミング モデルは、オープン標準により定義されており、Fortran および C/C++ プログラミング言語へのバインドが適切に定義されています。 OpenMP version 2.0 および 2.5 では、Visual C コンパイラでサポートされているは反復的な; の並列アルゴリズムに最適これは、データの配列を並列反復処理を実行します。 OpenMP 3.0 では、反復的なタスクに加え、非反復タスクをサポートします。

OpenMP は、並列化の度合いが事前に決定され、システムで使用可能なリソースと対応する場合に最も効果的です。 OpenMP モデルは、高パフォーマンス コンピューティングに特に適したは非常に大きい計算の問題が 1 台のコンピューターの処理リソースを分散します。 このシナリオでは、ハードウェア環境が一般に、固定し、開発者は、アルゴリズムが実行されたときに、すべてのコンピューティング リソースへの排他アクセスに予測できます。

ただし、コンピューティング環境の制約付き less 可能性がありますできません OpenMP に適しています。 たとえば、再帰の問題 (クイック ソート アルゴリズムやデータのツリーを検索) は OpenMP 2.0 および 2.5 を使用して実装することは困難です。 同時実行ランタイムでは、OpenMP の機能を補完することにより、 [Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)と[並列パターン ライブラリ](../../parallel/concrt/parallel-patterns-library-ppl.md)(PPL)。 Asynchronous Agents Library は、タスクの粒度の粗い並列処理をサポートしていますPPL には、多くの細かい並列タスクがサポートしています。 同時実行ランタイムでは、アプリケーションのロジックに専念できるように、並列操作を実行するために必要なインフラストラクチャを提供します。 ただし、同時実行ランタイムでは、さまざまなプログラミング モデルができますが、そのスケジューリング オーバーヘッドより大きくすること OpenMP などの他の同時実行ライブラリです。 そのため、同時実行ランタイムを使用する既存の OpenMP コードを変換するときに増分のパフォーマンスをテストすることをお勧めします。

## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>OpenMP から同時実行ランタイムに移行するタイミング

次の場合に、同時実行ランタイムを使用する既存の OpenMP コードを移行すると便利な場合があります。

|Cases|同時実行ランタイムの利点|
|-----------|-------------------------------------------|
|拡張可能な同時実行プログラミング フレームワークが必要です。|コンカレンシー ランタイムの機能の多くは拡張できます。 既存の機能を組み合わせて新しい機能を作成することもできます。 OpenMP はコンパイラ ディレクティブに依存している、ため、簡単に拡張できません。|
|アプリケーションは、協調ブロッキングをメリットとしています。|タスクがブロックはまだ使用可能なリソースを必要とするため、同時実行ランタイムは最初のタスクがリソースを待機中に、この他のタスクを実行できます。|
|アプリケーションに対しては、動的負荷分散がメリットです。|同時実行ランタイムでは、ワークロードの変化に応じて、コンピューティング リソースの割り当てを調整するスケジューリング アルゴリズムを使用します。 OpenMP、スケジューラは、並列領域では、コンピューティング リソースを割り当てるときにそれらのリソース割り当てが、計算全体で固定されます。|
|例外処理のサポートが必要です。|PPL では、両方の内部と外部並列領域またはループの例外をキャッチすることができます。 OpenMP では、並列領域またはループの内部で例外を処理する必要があります。|
|取り消し機構が必要です。|PPL には、個々 のタスクと作業の並列のツリーの両方をキャンセルするアプリケーションができます。 OpenMP には、独自のキャンセル メカニズムを実装するためにアプリケーションが必要です。|
|別の開始元のコンテキストに完了する並列コードを必要とします。|同時実行ランタイムでは、タスクを 1 つのコンテキストでは、開始を待機し、別のコンテキストでは、そのタスクをキャンセルすることができます。 OpenMP ですべての並列処理は、開始元のコンテキストで完了する必要があります。|
|強化されたデバッグ サポートが必要です。|Visual Studio では、**並列スタック**と**並列タスク**windows マルチ スレッド アプリケーションをより簡単にデバッグできるようにします。<br /><br /> 同時実行ランタイムのデバッグをサポートする詳細については、次を参照してください。[タスク ウィンドウを使用して](/visualstudio/debugger/using-the-tasks-window)、[並列スタック ウィンドウを使用して](/visualstudio/debugger/using-the-parallel-stacks-window)、および[チュートリアル。並列アプリケーションのデバッグ](/visualstudio/debugger/walkthrough-debugging-a-parallel-application)します。|

## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>OpenMP から同時実行ランタイムに移行すべきでない場合

次の場合に、同時実行ランタイムを使用する既存の OpenMP コードの移行に適したできない場合がありますがについて説明します。

|Cases|説明|
|-----------|-----------------|
|アプリケーションで既には、お客様の要件を満たしています。|アプリケーションのパフォーマンスと現在のデバッグ サポートに満足したら、移行適さない場合があります。|
|並列ループの本体は、ほとんどの作業を実行します。|同時実行ランタイムのタスク スケジューラのオーバーヘッドは、ループ本体が比較的小さい場合に特にを並列にループ本体の実行の利点を克服いない可能性があります。|
|アプリケーションが c 言語で記述されました。|同時実行ランタイムでは、多くの C++ 機能を使用するために適さない場合があります C アプリケーションを完全に使用できるようにするコードを記述することはできません。|

## <a name="related-topics"></a>関連トピック

[方法: 変換、OpenMP 並列 for ループ、同時実行ランタイムを使用するには](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)

OpenMP を使用する基本的なループを指定された[並列](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)と[の](../../parallel/openmp/reference/for-openmp.md)ディレクティブでは、同時実行ランタイムを使用するように変換する方法を示します[concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for)アルゴリズム。

[方法: 取り消しを使用して、同時実行ランタイムを使用する OpenMP ループを変換します。](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)<br/>
OpenMP を与え[並列](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[の](../../parallel/openmp/reference/for-openmp.md)ループを実行するすべての反復処理を必要としないが、同時実行ランタイムの取り消し機構を使用するように変換する方法を示します。

[方法: 同時実行ランタイムを使用する例外処理を使用する OpenMP ループを変換します。](../../parallel/concrt/convert-an-openmp-loop-that-uses-exception-handling.md)<br/>
OpenMP を与え[並列](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[の](../../parallel/openmp/reference/for-openmp.md)例外の処理を実行するループが、同時実行ランタイムの例外処理メカニズムを使用するように変換する方法を示します。

[方法: 減少変数を使用して、同時実行ランタイムを使用する OpenMP ループを変換します。](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)<br/>
OpenMP を与え[並列](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[の](../../parallel/openmp/reference/for-openmp.md)ループを使用する、[削減](../../parallel/openmp/reference/reduction.md)句は、同時実行ランタイムを使用するように変換する方法を示します。

## <a name="see-also"></a>関連項目

[コンカレンシー ランタイム](../../parallel/concrt/concurrency-runtime.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)<br/>
[並列パターン ライブラリ (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[非同期エージェント ライブラリ](../../parallel/concrt/asynchronous-agents-library.md)

