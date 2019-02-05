---
title: '方法: スケジューラ インスタンスを管理します。'
ms.date: 11/04/2016
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
ms.openlocfilehash: d8e79f7c132abd8e43f661f4dc7c7bb758cb2a6d
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893991"
---
# <a name="how-to-manage-a-scheduler-instance"></a>方法: スケジューラ インスタンスを管理します。

スケジューラ インスタンスにより、特定のスケジューリング ポリシーと各種の作業負荷を関連付けることができます。 このトピックには、スケジューラ インスタンスを作成および管理する方法を示す 2 つの基本的な例が含まれています。

例では、既定のスケジューラ ポリシーを使用するスケジューラを作成します。 カスタム ポリシーを使用すると、スケジューラを作成する例を参照してください。[方法。特定のスケジューラ ポリシーを指定](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)します。

### <a name="to-manage-a-scheduler-instance-in-your-application"></a>アプリケーションのスケジューラ インスタンスを管理するには

1. 作成、 [concurrency::schedulerpolicy](../../parallel/concrt/reference/schedulerpolicy-class.md)のスケジューラが使用するポリシーを含んでいるオブジェクトの値します。

1. 呼び出す、 [::create](reference/currentscheduler-class.md#create)メソッドまたは[:create](reference/scheduler-class.md#create)スケジューラ インスタンスを作成します。

   使用する場合、`Scheduler::Create`メソッドを呼び出し、 [concurrency::Scheduler::Attach](reference/scheduler-class.md#attach)メソッドに、現在のコンテキストにスケジューラを関連付ける必要がある場合。

1. 呼び出す、 [CreateEvent](/windows/desktop/api/synchapi/nf-synchapi-createeventa)非シグナル状態の自動リセット イベント オブジェクトへのハンドルを作成する関数。

1. 先ほど作成したイベント オブジェクトへのハンドルを渡す、 [concurrency::CurrentScheduler::RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)メソッドまたは[concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)メソッド。 これにより、スケジューラが破棄されるときに設定されるイベントが登録されます。

1. 現在のスケジューラでスケジュールするタスクを実行します。

1. 呼び出す、 [:currentscheduler](reference/currentscheduler-class.md#detach)現在のスケジューラをデタッチおよび以前のスケジューラを現在の 1 つとして復元する方法。

   使用する場合、`Scheduler::Create`メソッドを呼び出し、 [concurrency::Scheduler::Release](reference/scheduler-class.md#release)の参照カウントをデクリメントするメソッド、`Scheduler`オブジェクト。

1. イベントにハンドルを渡す、 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject)スケジューラをシャット ダウンするを待機する関数。

1. 呼び出す、 [CloseHandle](/windows/desktop/api/handleapi/nf-handleapi-closehandle)イベント オブジェクトへのハンドルを閉じます。

## <a name="example"></a>例

次のコードに、スケジューラ インスタンスを管理するための 2 つの方法を示します。 どちらの例でも、最初に既定のスケジューラを使用して、現在のスケジューラの一意の識別子を印刷するタスクを実行します。 次に、スケジューラ インスタンスを使用して同じタスクを再び実行します。 最後に、既定のスケジューラを現在のスケジューラとして復元した後、もう一度同じタスクを実行します。

最初の例では、 [:currentscheduler](../../parallel/concrt/reference/currentscheduler-class.md)スケジューラ インスタンスを作成し、現在のコンテキストに関連付けるクラス。 2 番目の例では、 [concurrency::scheduler](../../parallel/concrt/reference/scheduler-class.md)クラスを同じタスクを実行します。 通常は、現在のスケジューラを操作するのに `CurrentScheduler` クラスを使用します。 `Scheduler` クラスを使用する 2 つ目の例は、スケジューラを現在のコンテキストに関連付けるタイミングを制御したり、特定のスケジューラを特定のタスクに関連付けたりする場合に有用です。

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

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、という名前のファイルに貼り付ける`scheduler-instance.cpp`Visual Studio コマンド プロンプト ウィンドウで、次のコマンドを実行します。

**cl.exe/EHsc scheduler-instance.cpp**

## <a name="see-also"></a>関連項目

[スケジューラ インスタンス](../../parallel/concrt/scheduler-instances.md)<br/>
[方法: 特定のスケジューラ ポリシーを指定する](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)

