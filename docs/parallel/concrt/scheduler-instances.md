---
title: スケジューラ インスタンス
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
ms.openlocfilehash: e9e9b8124254084ac30191d37d49f2ef72bd677e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142293"
---
# <a name="scheduler-instances"></a>スケジューラ インスタンス

このドキュメントでは、同時実行ランタイムにおける scheduler インスタンスの役割と、 [concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)クラスおよび[Concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md)クラスを使用して scheduler インスタンスを作成および管理する方法について説明します。 Scheduler インスタンスは、明示的なスケジュールポリシーを特定の種類のワークロードに関連付ける場合に便利です。 たとえば、昇格したスレッド優先順位で一部のタスクを実行するようにスケジューラ インスタンスを 1 つ作成し、他のタスクについては既定のスケジューラを使用して通常のスレッド優先順位で実行することができます。

> [!TIP]
> コンカレンシー ランタイムには既定のスケジューラが用意されているため、アプリケーションにスケジューラを作成する必要はありません。 タスクスケジューラはアプリケーションのパフォーマンスを微調整するのに役立ちます。そのため、同時実行ランタイムを初めて使用する場合は、[並列パターンライブラリ (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)または[非同期エージェントライブラリ](../../parallel/concrt/asynchronous-agents-library.md)から始めることをお勧めします。

## <a name="top"></a> セクション

- [Scheduler および CurrentScheduler クラス](#classes)

- [Scheduler インスタンスの作成](#creating)

- [スケジューラインスタンスの有効期間の管理](#managing)

- [メソッドと機能](#features)

- [例](#example)

## <a name="classes"></a>Scheduler および CurrentScheduler クラス

タスクスケジューラを使用すると、アプリケーションで1つ以上の*スケジューラインスタンス*を使用して作業をスケジュールできます。 [Concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)クラスはスケジューラインスタンスを表し、タスクのスケジュール設定に関連する機能をカプセル化します。

スケジューラにアタッチされるスレッドは、*実行コンテキスト*または*コンテキスト*だけと呼ばれます。 現在のコンテキストでは、いつでも1つのスケジューラをアクティブにすることができます。 アクティブなスケジューラは、*現在のスケジューラ*とも呼ばれます。 同時実行ランタイムは、 [Concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md)クラスを使用して、現在のスケジューラへのアクセスを提供します。 あるコンテキストの現在のスケジューラは、別のコンテキストの現在のスケジューラとは異なる場合があります。 ランタイムは、現在のスケジューラのプロセスレベル表現を提供しません。

通常、現在のスケジューラにアクセスするには、`CurrentScheduler` クラスを使用します。 `Scheduler` クラスは、現在のものではないスケジューラを管理する必要がある場合に便利です。

次のセクションでは、scheduler インスタンスを作成および管理する方法について説明します。 これらのタスクを示す完全な例については、「[方法: スケジューラインスタンスを管理](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)する」を参照してください。

[[トップ](#top)]

## <a name="creating"></a>Scheduler インスタンスの作成

`Scheduler` オブジェクトを作成するには、次の3つの方法があります。

- スケジューラが存在しない場合は、ランタイム機能 (並列アルゴリズムなど) を使用して作業を実行するときに、ランタイムによって既定のスケジューラが作成されます。 既定のスケジューラは、並列処理を開始するコンテキストの現在のスケジューラになります。

- [Concurrency:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create)メソッドは、特定のポリシーを使用する `Scheduler` オブジェクトを作成し、そのスケジューラを現在のコンテキストに関連付けます。

- [Concurrency:: Scheduler:: Create](reference/scheduler-class.md#create)メソッドは、特定のポリシーを使用する `Scheduler` オブジェクトを作成しますが、現在のコンテキストには関連付けません。

ランタイムが既定のスケジューラを作成できるようにすると、すべての同時実行タスクで同じスケジューラを共有できるようになります。 通常は、並列[パターンライブラリ](../../parallel/concrt/parallel-patterns-library-ppl.md)(PPL) または[非同期エージェントライブラリ](../../parallel/concrt/asynchronous-agents-library.md)によって提供される機能を使用して、並列処理を実行します。 そのため、スケジューラを直接操作してポリシーまたは有効期間を制御する必要はありません。 PPL またはエージェントライブラリを使用する場合、ランタイムは、既定のスケジューラが存在しない場合は既定のスケジューラを作成し、各コンテキストの現在のスケジューラにします。 スケジューラを作成し、それを現在のスケジューラとして設定すると、ランタイムはそのスケジューラを使用してタスクをスケジュールします。 特定のスケジューリングポリシーが必要な場合にのみ、追加の scheduler インスタンスを作成します。 スケジューラに関連付けられているポリシーの詳細については、「 [Scheduler policies (スケジューラポリシー](../../parallel/concrt/scheduler-policies.md))」を参照してください。

[[トップ](#top)]

## <a name="managing"></a>スケジューラインスタンスの有効期間の管理

ランタイムは、参照カウント機構を使用して、`Scheduler` オブジェクトの有効期間を制御します。

`CurrentScheduler::Create` メソッドまたは `Scheduler::Create` メソッドを使用して `Scheduler` オブジェクトを作成すると、ランタイムはそのスケジューラの最初の参照カウントを1に設定します。 ランタイムは、 [concurrency:: Scheduler:: Attach](reference/scheduler-class.md#attach)メソッドを呼び出すと、参照カウントをインクリメントします。 `Scheduler::Attach` メソッドは、`Scheduler` オブジェクトを現在のコンテキストと関連付けます。 これにより、現在のスケジューラが作成されます。 `CurrentScheduler::Create` メソッドを呼び出すと、ランタイムは、`Scheduler` オブジェクトを作成し、それを現在のコンテキストにアタッチします (参照カウントを1に設定します)。 また、 [concurrency:: Scheduler:: reference](reference/scheduler-class.md#reference)メソッドを使用して、`Scheduler` オブジェクトの参照カウントをインクリメントすることもできます。

[Concurrency:: CurrentScheduler::D etach](reference/currentscheduler-class.md#detach)メソッドを呼び出して現在のスケジューラをデタッチするか、 [Concurrency:: Scheduler:: Release](reference/scheduler-class.md#release)メソッドを呼び出すと、ランタイムは参照カウントをデクリメントします。 参照カウントが0になると、すべてのスケジュールされたタスクが完了した後に、ランタイムによって `Scheduler` オブジェクトが破棄されます。 実行中のタスクは、現在のスケジューラの参照カウントをインクリメントできます。 したがって、参照カウントがゼロに達し、タスクが参照カウントをインクリメントした場合、参照カウントが再び0になり、すべてのタスクが終了するまで、ランタイムは `Scheduler` オブジェクトを破棄しません。

ランタイムは、各コンテキストの `Scheduler` オブジェクトの内部スタックを保持します。 `Scheduler::Attach` または `CurrentScheduler::Create` メソッドを呼び出すと、ランタイムはその `Scheduler` オブジェクトを現在のコンテキストのスタックにプッシュします。 これにより、現在のスケジューラが作成されます。 `CurrentScheduler::Detach`を呼び出すと、ランタイムは現在のコンテキストのスタックから現在のスケジューラをポップし、前のスケジューラを現在のスケジューラとして設定します。

ランタイムには、スケジューラインスタンスの有効期間を管理するためのいくつかの方法が用意されています。 次の表は、現在のコンテキストに対してスケジューラを作成またはアタッチする各メソッドの現在のコンテキストから、スケジューラを解放またはデタッチするための適切なメソッドを示しています。

|Create または attach メソッド|Release または detach メソッド|
|-----------------------------|------------------------------|
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|
|`Scheduler::Create`|`Scheduler::Release`|
|`Scheduler::Attach`|`CurrentScheduler::Detach`|
|`Scheduler::Reference`|`Scheduler::Release`|

不適切な release メソッドまたは detach メソッドを呼び出すと、ランタイムで特定できない動作が発生します。

ランタイムが既定のスケジューラを作成するなどの機能を使用する場合は、このスケジューラを解放したり、デタッチしたりしないでください。 ランタイムは、作成するスケジューラの有効期間を管理します。

すべてのタスクが完了する前にランタイムが `Scheduler` オブジェクトを破棄しないので、 [concurrency:: Scheduler:: RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)メソッドまたは[Concurrency:: Currentscheduler:: RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)メソッドを使用して、`Scheduler` オブジェクトが破棄されたときに通知を受け取ることができます。 これは、`Scheduler` オブジェクトによってスケジュールされたすべてのタスクが終了するまで待機する必要がある場合に便利です。

[[トップ](#top)]

## <a name="features"></a>メソッドと機能

このセクションでは、`CurrentScheduler` クラスと `Scheduler` クラスの重要なメソッドについて説明します。

`CurrentScheduler` クラスは、現在のコンテキストで使用するためのスケジューラを作成するためのヘルパーと考えてください。 `Scheduler` クラスを使用すると、別のコンテキストに属するスケジューラを制御できます。

次の表は、`CurrentScheduler` クラスによって定義される重要なメソッドを示しています。

|方法|説明|
|------------|-----------------|
|[作成](reference/currentscheduler-class.md#create)|指定したポリシーを使用し、現在のコンテキストに関連付けられている `Scheduler` オブジェクトを作成します。|
|[Get](reference/currentscheduler-class.md#get)|現在のコンテキストに関連付けられている `Scheduler` オブジェクトへのポインターを取得します。 このメソッドは、`Scheduler` オブジェクトの参照カウントをインクリメントしません。|
|[デタッチ](reference/currentscheduler-class.md#detach)|現在のコンテキストから現在のスケジューラをデタッチし、前のスケジューラを現在のスケジューラとして設定します。|
|[RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)|現在のスケジューラが破棄されたときにランタイムによって設定されるイベントを登録します。|
|[CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)|現在のスケジューラに[concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md)オブジェクトを作成します。|
|[ScheduleTask](reference/currentscheduler-class.md#scheduletask)|現在のスケジューラのスケジュールキューに軽量タスクを追加します。|
|[GetPolicy](reference/currentscheduler-class.md#getpolicy)|現在のスケジューラに関連付けられているポリシーのコピーを取得します。|

次の表は、`Scheduler` クラスによって定義される重要なメソッドを示しています。

|方法|説明|
|------------|-----------------|
|[作成](reference/scheduler-class.md#create)|指定されたポリシーを使用する `Scheduler` オブジェクトを作成します。|
|[Attach](reference/scheduler-class.md#attach)|現在のコンテキストと共に `Scheduler` オブジェクトを関連付けます。|
|[リファレンス](reference/scheduler-class.md#reference)|`Scheduler` オブジェクトの参照カウンターをインクリメントします。|
|[Release](reference/scheduler-class.md#release)|`Scheduler` オブジェクトの参照カウンターをデクリメントします。|
|[RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)|`Scheduler` オブジェクトが破棄されるときにランタイムによって設定されるイベントを登録します。|
|[CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)|`Scheduler` オブジェクトに[concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md)オブジェクトを作成します。|
|[ScheduleTask](reference/scheduler-class.md#scheduletask)|`Scheduler` オブジェクトから軽量タスクをスケジュールします。|
|[GetPolicy](reference/scheduler-class.md#getpolicy)|`Scheduler` オブジェクトに関連付けられているポリシーのコピーを取得します。|
|[SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)|ランタイムが既定のスケジューラを作成するときに使用するポリシーを設定します。|
|[ResetDefaultSchedulerPolicy](reference/scheduler-class.md#resetdefaultschedulerpolicy)|既定のポリシーを、`SetDefaultSchedulerPolicy`の呼び出しの前にアクティブだったものに復元します。 この呼び出しの後に既定のスケジューラが作成された場合、ランタイムは既定のポリシー設定を使用してスケジューラを作成します。|

[[トップ](#top)]

## <a name="example"></a> 例

スケジューラインスタンスを作成および管理する方法の基本的な例については、「[方法: スケジューラインスタンスを管理](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)する」を参照してください。

## <a name="see-also"></a>参照

[タスク スケジューラ](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[方法: スケジューラ インスタンスを管理する](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[スケジューラ ポリシー](../../parallel/concrt/scheduler-policies.md)<br/>
[スケジュール グループ](../../parallel/concrt/schedule-groups.md)
