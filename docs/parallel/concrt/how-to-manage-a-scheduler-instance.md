---
title: '方法: スケジューラ インスタンスを管理する'
ms.date: 11/04/2016
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
ms.openlocfilehash: c7ec321eaf0960dc14b61bbd8fdc76b53a31f8c5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141727"
---
# <a name="how-to-manage-a-scheduler-instance"></a>方法: スケジューラ インスタンスを管理する

スケジューラ インスタンスにより、特定のスケジューリング ポリシーと各種の作業負荷を関連付けることができます。 このトピックには、スケジューラ インスタンスを作成および管理する方法を示す 2 つの基本的な例が含まれています。

例では、既定のスケジューラ ポリシーを使用するスケジューラを作成します。 カスタムポリシーを使用するスケジューラを作成する例については、「[方法: 特定のスケジューラポリシーを指定](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)する」を参照してください。

## <a name="to-manage-a-scheduler-instance-in-your-application"></a>アプリケーションのスケジューラ インスタンスを管理するには

1. Scheduler が使用するポリシー値を含む[concurrency:: Scheduler policy](../../parallel/concrt/reference/schedulerpolicy-class.md)オブジェクトを作成します。

1. Scheduler インスタンスを作成するには、 [concurrency:: CurrentScheduler:: create](reference/currentscheduler-class.md#create)メソッドまたは[Concurrency:: Scheduler:: create](reference/scheduler-class.md#create)メソッドを呼び出します。

   `Scheduler::Create` メソッドを使用する場合は、scheduler を現在のコンテキストに関連付ける必要があるときに[concurrency:: Scheduler:: Attach](reference/scheduler-class.md#attach)メソッドを呼び出します。

1. [CreateEvent](/windows/win32/api/synchapi/nf-synchapi-createeventw)関数を呼び出して、シグナルのない自動リセットイベントオブジェクトへのハンドルを作成します。

1. 先ほど作成したイベントオブジェクトにハンドルを、 [concurrency:: CurrentScheduler:: RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)メソッドまたは[Concurrency:: Scheduler:: RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)メソッドに渡します。 これにより、スケジューラが破棄されるときに設定されるイベントが登録されます。

1. 現在のスケジューラでスケジュールするタスクを実行します。

1. [Concurrency:: CurrentScheduler::D etach](reference/currentscheduler-class.md#detach)メソッドを呼び出して、現在のスケジューラをデタッチし、以前のスケジューラを現在のスケジューラとして復元します。

   `Scheduler::Create` メソッドを使用する場合は、 [concurrency:: Scheduler:: Release](reference/scheduler-class.md#release)メソッドを呼び出して、`Scheduler` オブジェクトの参照カウントをデクリメントします。

1. イベントのハンドルを[WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject)関数に渡して、スケジューラがシャットダウンするのを待ちます。

1. [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle)関数を呼び出して、イベントオブジェクトへのハンドルを閉じます。

## <a name="example"></a>例

次のコードに、スケジューラ インスタンスを管理するための 2 つの方法を示します。 どちらの例でも、最初に既定のスケジューラを使用して、現在のスケジューラの一意の識別子を印刷するタスクを実行します。 次に、スケジューラ インスタンスを使用して同じタスクを再び実行します。 最後に、既定のスケジューラを現在のスケジューラとして復元した後、もう一度同じタスクを実行します。

最初の例では、 [concurrency:: currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md)クラスを使用してスケジューラインスタンスを作成し、それを現在のコンテキストに関連付けます。 2番目の例では、 [concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md)クラスを使用して同じタスクを実行します。 通常は、現在のスケジューラを操作するのに `CurrentScheduler` クラスを使用します。 `Scheduler` クラスを使用する 2 つ目の例は、スケジューラを現在のコンテキストに関連付けるタイミングを制御したり、特定のスケジューラを特定のタスクに関連付けたりする場合に有用です。

[!code-cpp[concrt-scheduler-instance#1](../../parallel/concrt/codesnippet/cpp/how-to-manage-a-scheduler-instance_1.cpp)]

この例を実行すると、次の出力が生成されます。

```Output
Using CurrentScheduler class...

Current scheduler id: 0
Creating and attaching scheduler...
Current scheduler id: 1
Detaching scheduler...
Current scheduler id: 0

Using Scheduler class...

Current scheduler id: 0
Creating scheduler...
Attaching scheduler...
Current scheduler id: 2
Detaching scheduler...
Current scheduler id: 0
```

## <a name="compiling-the-code"></a>コードのコンパイル

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`scheduler-instance.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

> **cl.exe/EHsc scheduler-instance**

## <a name="see-also"></a>参照

[スケジューラ インスタンス](../../parallel/concrt/scheduler-instances.md)<br/>
[方法: 特定のスケジューラ ポリシーを指定する](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)
