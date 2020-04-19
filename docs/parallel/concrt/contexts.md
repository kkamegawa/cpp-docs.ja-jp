---
title: Contexts
ms.date: 11/04/2016
helpviewer_keywords:
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
ms.openlocfilehash: 9eaf21a3d65ae891a48657de9d3e7aff78ce12b9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142191"
---
# <a name="contexts"></a>Contexts

このドキュメントでは、同時実行ランタイム内のコンテキストの役割について説明します。 スケジューラにアタッチされるスレッドは、*実行コンテキスト*または*コンテキスト*だけと呼ばれます。 [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait)関数と concurrency::[Context クラス](../../parallel/concrt/reference/context-class.md)を使用すると、コンテキストの動作を制御できます。 現在のコンテキストを指定した時間だけ中断するには、`wait` 関数を使用します。 コンテキストのブロック、ブロック解除、および生成のタイミングをより細かく制御する必要がある場合、または現在のコンテキストをオーバーサブスクライブする場合は、`Context` クラスを使用します。

> [!TIP]
> コンカレンシー ランタイムには既定のスケジューラが用意されているため、アプリケーションにスケジューラを作成する必要はありません。 タスクスケジューラはアプリケーションのパフォーマンスを微調整するのに役立ちます。そのため、同時実行ランタイムを初めて使用する場合は、[並列パターンライブラリ (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)または[非同期エージェントライブラリ](../../parallel/concrt/asynchronous-agents-library.md)から始めることをお勧めします。

## <a name="the-wait-function"></a>Wait 関数

[Concurrency:: wait](reference/concurrency-namespace-functions.md#wait)関数は、指定されたミリ秒数の間、現在のコンテキストの実行を協調的に生成します。 ランタイムは、yield time を使用して他のタスクを実行します。 指定された時間が経過すると、ランタイムはコンテキストの実行をスケジュールします。 したがって、`wait` 関数は、`milliseconds` パラメーターに指定された値よりも長い現在のコンテキストを中断する可能性があります。

`milliseconds` パラメーターに 0 (ゼロ) を渡すと、他のすべてのアクティブなコンテキストに作業を実行する機会が与えられるまで、ランタイムは現在のコンテキストを中断します。 これにより、タスクを他のすべてのアクティブなタスクに対して行うことができます。

### <a name="example"></a>例

`wait` 関数を使用して現在のコンテキストを生成し、他のコンテキストを実行できるようにする例については、「[方法: スケジュールグループを使用して実行順序に影響を与える](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)」を参照してください。

## <a name="the-context-class"></a>コンテキストクラス

Concurrency::[context クラス](../../parallel/concrt/reference/context-class.md)は、実行コンテキストのプログラミングの抽象化を提供し、2つの重要な機能を提供します。現在のコンテキストを協調的にブロック、ブロック解除、および生成する機能と、現在のコンテキストをオーバーサブスクライブする機能です。

### <a name="cooperative-blocking"></a>協調ブロッキング

`Context` クラスを使用すると、現在の実行コンテキストをブロックまたは生成できます。 ブロックまたは生成は、リソースが使用できないために現在のコンテキストを続行できない場合に便利です。

[Concurrency:: Context:: Block](reference/context-class.md#block)メソッドは、現在のコンテキストをブロックします。 ブロックされているコンテキストは、ランタイムが他のタスクを実行できるように処理リソースを生成します。 [Concurrency:: Context:: ブロック解除](reference/context-class.md#unblock)メソッドは、ブロックされたコンテキストのブロックを解除します。 `Context::Unblock` メソッドは、`Context::Block`を呼び出したコンテキストとは異なるコンテキストから呼び出す必要があります。 コンテキストが自身のブロックを解除しようとすると、ランタイムは[concurrency:: context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md)をスローします。

コンテキストを協調的にブロックおよびブロック解除するには、通常、 [concurrency:: context:: CurrentContext](reference/context-class.md#currentcontext)を呼び出して、現在のスレッドに関連付けられている `Context` オブジェクトへのポインターを取得し、結果を保存します。 次に、`Context::Block` メソッドを呼び出して、現在のコンテキストをブロックします。 後で、別のコンテキストから `Context::Unblock` を呼び出して、ブロックされたコンテキストのブロックを解除します。

呼び出しの各ペアを `Context::Block` と `Context::Unblock`に一致させる必要があります。 `Context::Block` または `Context::Unblock` メソッドが、別のメソッドに対して一致する呼び出しを行わずに連続して呼び出された場合、ランタイムは[concurrency:: context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md)をスローします。 ただし、`Context::Unblock`を呼び出す前に `Context::Block` を呼び出す必要はありません。 たとえば、あるコンテキストが同じコンテキストに対して別のコンテキストで `Context::Block` を呼び出す前に、`Context::Unblock` を呼び出すと、そのコンテキストはブロックされたままになります。

[Concurrency:: Context:: Yield](reference/context-class.md#yield)メソッドを実行すると、ランタイムは他のタスクを実行し、コンテキストの実行を再スケジュールできるようになります。 `Context::Block` メソッドを呼び出すと、ランタイムはコンテキストを再スケジュールしません。

#### <a name="example"></a>例

`Context::Block`、`Context::Unblock`、および `Context::Yield` メソッドを使用して協調セマフォクラスを実装する例については、「[方法: コンテキストクラスを使用して協調セマフォを実装](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)する」を参照してください。

##### <a name="oversubscription"></a>オーバーサブスクリプション

既定のスケジューラは、使用可能なハードウェアスレッドと同じ数のスレッドを作成します。 *オーバーサブスクリプション*を使用して、特定のハードウェアスレッドに対して追加のスレッドを作成できます。

計算を集中的に行う操作では、オーバーサブスクリプションは通常、追加のオーバーヘッドが発生するため、拡張されません。 ただし、ディスクやネットワーク接続からのデータの読み取りなど、待機時間の長いタスクの場合、オーバーサブスクリプションによって一部のアプリケーションの全体的な効率が向上します。

> [!NOTE]
> 同時実行ランタイムによって作成されたスレッドからのみオーバーサブスクリプションを有効にします。 オーバーサブスクリプションは、ランタイムによって作成されていないスレッド (メインスレッドを含む) から呼び出された場合には効果がありません。

現在のコンテキストでオーバーサブスクリプションを有効にするには、`_BeginOversubscription` パラメーターを**true**に設定して[Concurrency:: Context:: oversubscribe](reference/context-class.md#oversubscribe)メソッドを呼び出します。 同時実行ランタイムによって作成されたスレッドでオーバーサブスクリプションを有効にすると、ランタイムによって1つの追加スレッドが作成されます。 オーバーサブスクリプションを必要とするすべてのタスクが完了したら、`_BeginOversubscription` パラメーターを**false**に設定して `Context::Oversubscribe` を呼び出します。

現在のコンテキストからオーバーサブスクリプションを複数回有効にすることができますが、有効にした回数と同じ回数だけ無効にする必要があります。 オーバーサブスクリプションも入れ子にすることができます。つまり、オーバーサブスクリプションを使用する別のタスクによって作成されたタスクは、そのコンテキストをオーバーサブスクライブすることもできます。 ただし、入れ子になったタスクとその親の両方が同じコンテキストに属している場合は、`Context::Oversubscribe` の最も外側の呼び出しのみが、追加のスレッドを作成します。

> [!NOTE]
> オーバーサブスクリプションが有効になる前に無効になっている場合、ランタイムは[concurrency:: invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md)をスローします。

###### <a name="example"></a>例

オーバーサブスクリプションを使用して、ネットワーク接続からのデータの読み取りによって発生する待機時間をオフセットする例については、「[方法: オーバーサブスクリプションを使用して待機時間をオフセット](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)する」を参照してください。

## <a name="see-also"></a>参照

[タスク スケジューラ](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[方法: スケジュール グループを使用して実行順序に影響を与える](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)<br/>
[方法: Context クラスを使用して協調セマフォを実装する](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[方法: オーバーサブスクリプションを使用して待機時間を短縮する](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)
