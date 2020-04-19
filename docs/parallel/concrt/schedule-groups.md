---
title: スケジュール グループ
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
ms.openlocfilehash: 1765c10f4cf8fe499aed1a140d2bba1ecaaf2300
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142309"
---
# <a name="schedule-groups"></a>スケジュール グループ

このドキュメントでは、同時実行ランタイムのスケジュールグループの役割について説明します。 *スケジュールグループ*は、関連するタスクをまとめてアフィニティ化する、またはグループ化します。 すべてのスケジューラには、1つまたは複数のスケジュールグループがあります。 スケジュール グループは、タスク間で高いレベルの局所性が求められる場合 (たとえば、関連するタスクのグループが同一プロセッサ ノードでの実行によって恩恵を受ける場合) に使用します。 逆に、タスクのセットに割り当てられる処理リソースの量を制限する必要がある場合など、アプリケーションに特定の品質要件がある場合は、scheduler インスタンスを使用します。 Scheduler インスタンスの詳細については、「 [Scheduler instances](../../parallel/concrt/scheduler-instances.md)」を参照してください。

> [!TIP]
> コンカレンシー ランタイムには既定のスケジューラが用意されているため、アプリケーションにスケジューラを作成する必要はありません。 タスクスケジューラはアプリケーションのパフォーマンスを微調整するのに役立ちます。そのため、同時実行ランタイムを初めて使用する場合は、[並列パターンライブラリ (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)または[非同期エージェントライブラリ](../../parallel/concrt/asynchronous-agents-library.md)から始めることをお勧めします。

すべての `Scheduler` オブジェクトには、すべてのスケジュールノードに既定のスケジュールグループがあります。 *スケジュールノード*は、基になるシステムトポロジにマップされます。 ランタイムは、プロセッサパッケージまたは Non-uniform Memory Architecture (NUMA) ノードごとに1つのスケジュールノードを作成します。 タスクをスケジュールグループに明示的に関連付けない場合は、タスクを追加するグループがスケジューラによって選択されます。

`SchedulingProtocol` scheduler ポリシーは、スケジューラが各スケジュールグループ内のタスクを実行する順序に影響します。 `SchedulingProtocol` が `EnhanceScheduleGroupLocality` (既定) に設定されている場合、現在のタスクが終了または協調的になったときに、タスクスケジューラによってスケジュールグループから次のタスクが選択されます。 タスクスケジューラは、現在のスケジュールグループの作業を検索してから、次に使用可能なグループに移動します。 逆に、`SchedulingProtocol` が `EnhanceForwardProgress`に設定されている場合、スケジューラは、各タスクが終了または生成された後、次のスケジュールグループに移動します。 これらのポリシーを比較する例については、「[方法: スケジュールグループを使用して実行順序に影響を与える](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)」を参照してください。

ランタイムは、 [concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)クラスを使用して、スケジュールグループを表します。 `ScheduleGroup` オブジェクトを作成するには、 [concurrency:: CurrentScheduler:: CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)メソッドまたは[Concurrency:: Scheduler:: CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)メソッドを呼び出します。 ランタイムは、参照カウント機構を使用して、`Scheduler` オブジェクトと同様に `ScheduleGroup` オブジェクトの有効期間を制御します。 `ScheduleGroup` オブジェクトを作成すると、ランタイムによって参照カウンターが1に設定されます。 [Concurrency:: ScheduleGroup:: reference](reference/schedulegroup-class.md#reference)メソッドは、参照カウンターを1だけインクリメントします。 [Concurrency:: ScheduleGroup:: Release](reference/schedulegroup-class.md#release)メソッドは、参照カウンターを1だけデクリメントします。

同時実行ランタイムの多くの型を使用して、オブジェクトをスケジュールグループと関連付けることができます。 たとえば、concurrency [:: agent](../../parallel/concrt/reference/agent-class.md)クラスとメッセージブロッククラス ( [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)、 [concurrency:: join](../../parallel/concrt/reference/join-class.md)、concurrency::[timer](reference/timer-class.md)など) は、`ScheduleGroup` オブジェクトを受け取るコンストラクターのオーバーロードされたバージョンを提供します。 ランタイムは、この `ScheduleGroup` オブジェクトに関連付けられている `Scheduler` オブジェクトを使用して、タスクをスケジュールします。

また、 [concurrency:: ScheduleGroup:: schedulegroup](reference/schedulegroup-class.md#scheduletask)メソッドを使用して、軽量タスクをスケジュールすることもできます。 軽量タスクの詳細については、「[軽量タスク](../../parallel/concrt/lightweight-tasks.md)」を参照してください。

## <a name="example"></a>例

スケジュールグループを使用してタスクの実行順序を制御する例については、「[方法: スケジュールグループを使用して実行順序に影響を与える](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)」を参照してください。

## <a name="see-also"></a>参照

[タスク スケジューラ](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[スケジューラ インスタンス](../../parallel/concrt/scheduler-instances.md)<br/>
[方法: スケジュール グループを使用して実行順序に影響を与える](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)
