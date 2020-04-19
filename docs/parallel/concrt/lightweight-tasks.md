---
title: 軽量タスク
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
ms.openlocfilehash: be417052ffab19c1bc2d2ba6f35094f98e315812
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141850"
---
# <a name="lightweight-tasks"></a>軽量タスク

このドキュメントでは、同時実行ランタイムの軽量タスクの役割について説明します。 *軽量タスク*は、`concurrency::Scheduler` または `concurrency::ScheduleGroup` オブジェクトから直接スケジュールするタスクです。 軽量タスクは、Windows API [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)関数に提供する関数に似ています。 そのため、同時実行ランタイムのスケジュール機能を使用するように既存のコードを調整する場合は、軽量のタスクが役立ちます。 同時実行ランタイム自体は、軽量タスクを使用して非同期エージェントをスケジュールし、非同期メッセージブロック間でメッセージを送信します。

> [!TIP]
> コンカレンシー ランタイムには既定のスケジューラが用意されているため、アプリケーションにスケジューラを作成する必要はありません。 タスクスケジューラはアプリケーションのパフォーマンスを微調整するのに役立ちます。そのため、同時実行ランタイムを初めて使用する場合は、[並列パターンライブラリ (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)または[非同期エージェントライブラリ](../../parallel/concrt/asynchronous-agents-library.md)から始めることをお勧めします。

軽量タスクは、非同期エージェントやタスクグループよりもオーバーヘッドが少なくなります。 たとえば、ランタイムは、軽量タスクが終了したときに通知しません。 また、ランタイムは、軽量タスクからスローされた例外をキャッチまたは処理しません。 例外処理と軽量タスクの詳細については、「[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)」を参照してください。

ほとんどのタスクでは、複雑なタスクをより基本的なタスクに簡単に分割できるため、タスクグループや並列アルゴリズムなどのより堅牢な機能を使用することをお勧めします。 タスクグループの詳細については、「[タスクの並列](../../parallel/concrt/task-parallelism-concurrency-runtime.md)化」を参照してください。 並列アルゴリズムの詳細については、「[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)」を参照してください。

軽量タスクを作成するには、 [concurrency:: ScheduleGroup:: schedulegroup](reference/schedulegroup-class.md#scheduletask)、 [Concurrency:: currentscheduler:](reference/currentscheduler-class.md#scheduletask): schedulegroup、または[concurrency:: Scheduler:: schedulegroup](reference/scheduler-class.md#scheduletask)メソッドを呼び出します。 軽量タスクが終了するまで待機するには、親スケジューラがシャットダウンするまで待つか、 [concurrency:: event](../../parallel/concrt/reference/event-class.md)オブジェクトなどの同期機構を使用します。

## <a name="example"></a>例

軽量タスクを使用するために既存のコードを調整する方法を示す例については、「[チュートリアル: 既存のコードを適合](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)させて軽量タスクを使用する」を参照してください。

## <a name="see-also"></a>参照

[タスク スケジューラ](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[チュートリアル: 既存のコードを改変して軽量タスクを使用する](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)
