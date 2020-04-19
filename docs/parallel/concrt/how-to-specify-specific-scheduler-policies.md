---
title: '方法: 特定のスケジューラ ポリシーを指定する'
ms.date: 11/04/2016
helpviewer_keywords:
- specifying scheduler policies [Concurrency Runtime]
- scheduler policies, specifying [Concurrency Runtime]
ms.assetid: 9c5149f9-ac34-4ff3-9e79-0bad103e4e6b
ms.openlocfilehash: bd5edfbdf6b0fda9c7e327dab9538bbf6b5e4b12
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142449"
---
# <a name="how-to-specify-specific-scheduler-policies"></a>方法: 特定のスケジューラ ポリシーを指定する

スケジューラでタスクを管理する場合、スケジューラ ポリシーを使用することで、スケジューラが使用する方法を制御できます。 このトピックでは、スケジューラ ポリシーを使用して、プログレス インジケーターをコンソールに出力するタスクのスレッドの優先度を高くする方法について説明します。

カスタムスケジューラポリシーを非同期エージェントと共に使用する例については、「[方法: 特定のスケジューラポリシーを使用するエージェントを作成](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)する」を参照してください。

## <a name="example"></a>例

次の例では、2 つのタスクを並列で実行します。 最初のタスクは、n<sup>番目</sup>のフィボナッチ数を計算します。 2 番目のタスクは、プログレス インジケーターをコンソールに出力します。

最初のタスクは、再帰的な分解を使用してフィナボッチ数を計算します。 つまり、各タスクがサブタスクを再帰的に作成して全体的な結果を計算します。 再帰的な分解を使用するタスクは、利用可能なすべてのリソースを使用するため、他のタスクが処理を続行できなくなる可能性があります。 この例では、プログレス インジケーターを出力するタスクが、コンピューティング リソースに適切なタイミングでアクセスできない場合があります。

進行状況メッセージを出力するタスクにコンピューティングリソースへの公平なアクセスを提供するために、この例では、「[方法: スケジューラインスタンスを管理](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)してカスタムポリシーを持つスケジューラインスタンスを作成する」で説明されている手順を使用します。 このカスタム ポリシーで、スレッドの優先順位が最も高い優先順位クラスとなるように指定します。

この例では、 [concurrency:: call](../../parallel/concrt/reference/call-class.md)クラスと[concurrency:: timer](../../parallel/concrt/reference/timer-class.md)クラスを使用して進行状況インジケーターを出力します。 これらのクラスには、それらをスケジュールする[concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md)オブジェクトへの参照を受け取るコンストラクターのバージョンがあります。 この例は、フィボナッチ数を計算するタスクをスケジュールする既定のスケジューラと、プログレス インジケーターを出力するタスクをスケジュールするスケジューラ インスタンスを使用します。

カスタム ポリシーを持つスケジューラを使用する利点を示すため、この例ではタスク全体を 2 度実行しています。 まず、既定のスケジューラを使用して両方のタスクをスケジュールします。 次に、既定のスケジューラを使用して最初のタスクをスケジュールし、カスタム ポリシーを持つスケジューラを使用して 2 番目のタスクをスケジュールします。

[!code-cpp[concrt-scheduler-policy#1](../../parallel/concrt/codesnippet/cpp/how-to-specify-specific-scheduler-policies_1.cpp)]

この例を実行すると、次の出力が生成されます。

```Output
Default scheduler:
...........................................................................done
Scheduler that has a custom policy:
...........................................................................done
```

どちらのタスク セットでも結果は同じですが、カスタム ポリシーを使用するバージョンではプログレス インジケーターを出力するタスクを高い優先順位で実行できるため、応答性が向上します。

## <a name="compiling-the-code"></a>コードのコンパイル

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`scheduler-policy.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

> **cl.exe/EHsc scheduler-policy**

## <a name="see-also"></a>参照

[スケジューラ ポリシー](../../parallel/concrt/scheduler-policies.md)<br/>
[方法: スケジューラ インスタンスを管理する](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[方法: 特定のスケジューラ ポリシーを使用するエージェントを作成する](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
