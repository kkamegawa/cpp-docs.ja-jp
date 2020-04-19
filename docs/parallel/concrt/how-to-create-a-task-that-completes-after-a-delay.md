---
title: '方法: 遅延後に完了するタスクを作成する'
ms.date: 11/04/2016
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
ms.openlocfilehash: 76189f45eb486e06b040155f6697bf003659b474
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141741"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>方法: 遅延後に完了するタスクを作成する

この例では、 [concurrency:: task](../../parallel/concrt/reference/task-class.md)、 [concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)、 [concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)、concurrency [:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)、 [concurrency:: timer](../../parallel/concrt/reference/timer-class.md)、および[concurrency:: call](../../parallel/concrt/reference/call-class.md)クラスを使用して、遅延後に完了するタスクを作成する方法を示します。 このメソッドを使用すると、定期的にデータをポーリングするループを作成したり、タイムアウトを導入したり、事前に定義された時間にユーザー入力の処理を遅延させることができます。

## <a name="example"></a>例

`complete_after` 関数および `cancel_after_timeout` 関数の例を次に示します。 `complete_after` 関数は、指定された遅延の後に完了する `task` オブジェクトを作成します。 `timer` オブジェクトと `call` オブジェクトを使用して、指定された遅延の後に `task_completion_event` オブジェクトを設定します。 `task_completion_event` クラスを使用すると、スレッドまたは別のタスクによって値が使用可能であることが通知された後に完了するタスクを定義できます。 イベントが設定されると、リスナータスクが完了し、その継続が実行されるようにスケジュールされます。

> [!TIP]
> 非同期エージェントライブラリの一部である `timer` および `call` クラスの詳細については、「[非同期メッセージブロック](../../parallel/concrt/asynchronous-message-blocks.md)」を参照してください。

`cancel_after_timeout` 関数は、指定されたタイムアウトの前にタスクが完了しない場合にタスクを取り消すために、`complete_after` 関数を基にしています。 `cancel_after_timeout` 関数は、2つのタスクを作成します。 最初のタスクは成功を示し、指定されたタスクが完了した後に完了します。2番目のタスクは失敗を示し、指定されたタイムアウトの後に完了します。 `cancel_after_timeout` 関数は、成功または失敗のタスクが完了したときに実行される継続タスクを作成します。 エラータスクが最初に完了した場合、継続はトークンソースをキャンセルしてタスク全体を取り消します。

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example"></a>例

次の例では、範囲 [0, 10万] の素数の数を複数回計算しています。 指定された制限時間内に完了しなかった場合、操作は失敗します。 `count_primes` 関数は、`cancel_after_timeout` 関数の使用方法を示しています。 指定された範囲の primes の数をカウントし、指定された時間内にタスクが完了しない場合は失敗します。 `wmain` 関数は、`count_primes` 関数を複数回呼び出します。 そのたびに、時間制限が半分になります。 現在の制限時間内に操作が完了しないと、プログラムは終了します。

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

この手法を使用して遅延後にタスクを取り消すと、タスク全体が取り消された後に、未開始のタスクが開始されません。 ただし、長時間実行されるタスクは、キャンセルに迅速に応答することが重要です。 タスクのキャンセルの詳細については、「 [PPL における取り消し](cancellation-in-the-ppl.md)処理」を参照してください。

## <a name="example"></a>例

この例の完全なコードを次に示します。

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>コードのコンパイル

コードをコンパイルするには、コードをコピーし、Visual Studio プロジェクトに貼り付けるか、`task-delay.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

**cl.exe/EHsc task-delay**

## <a name="see-also"></a>参照

[タスクの並列化](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[task クラス (コンカレンシー ランタイム)](../../parallel/concrt/reference/task-class.md)<br/>
[cancellation_token_source クラス](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[cancellation_token クラス](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[task_completion_event クラス](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[timer クラス](../../parallel/concrt/reference/timer-class.md)<br/>
[call クラス](../../parallel/concrt/reference/call-class.md)<br/>
[非同期メッセージ ブロック](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[PPL における取り消し処理](cancellation-in-the-ppl.md)
