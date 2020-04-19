---
title: '方法: さまざまなプロデューサー/コンシューマー パターンを実装します。'
ms.date: 11/04/2016
helpviewer_keywords:
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
ms.openlocfilehash: 113518e97b6715384b5e7b84b0d0eab63dfcfcc7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411358"
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>方法: さまざまなプロデューサー/コンシューマー パターンを実装します。

ここでは、アプリケーションにプロデューサー/コンシューマー パターンを実装する方法について説明します。 このパターンでは、"*プロデューサー*" がメッセージをメッセージ ブロックに送信し、"*コンシューマー*" がそのブロックからメッセージを読み取ります。

このトピックでは、2 つのシナリオに従って説明します。 最初のシナリオでは、コンシューマーはプロデューサーが送信した各メッセージを受信する必要があります。 2 番目のシナリオでは、コンシューマーは定期的にデータをポーリングします。そのため、各メッセージを受信する必要はありません。

このトピックのどちらの例も、エージェント、メッセージ ブロック、およびメッセージ パッシング関数を使用して、メッセージをプロデューサーからコンシューマーに転送します。 プロデューサー エージェントを使用して、 [concurrency::send](reference/concurrency-namespace-functions.md#send)関数にメッセージを書き込みます、 [concurrency::itarget](../../parallel/concrt/reference/itarget-class.md)オブジェクト。 コンシューマー エージェントを使用して、 [concurrency::receive](reference/concurrency-namespace-functions.md#receive)からメッセージを読み取る関数を[concurrency::isource](../../parallel/concrt/reference/isource-class.md)オブジェクト。 どちらのエージェントにも、処理の終了を調整するための sentinel 値が保持されます。

非同期エージェントの詳細については、次を参照してください。[非同期エージェント](../../parallel/concrt/asynchronous-agents.md)します。 メッセージ ブロックとメッセージ パッシング関数の詳細については、次を参照してください。[非同期メッセージ ブロック](../../parallel/concrt/asynchronous-message-blocks.md)と[メッセージを渡す関数](../../parallel/concrt/message-passing-functions.md)します。

## <a name="example"></a>例

この例では、プロデューサー エージェントは一連の数字をコンシューマー エージェントに送信します。 コンシューマーはこれらの各数字を受け取り、その平均を計算します。 アプリケーションはその平均をコンソールに出力します。

この例では、 [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md)メッセージをキューにプロデューサーを有効にするオブジェクト。 `unbounded_buffer` クラスに、`ITarget` および `ISource` を実装して、プロデューサーおよびコンシューマーと共有バッファーとの間でメッセージを送受信できるようにします。 `send` 関数および `receive` 関数で、プロデューサーからコンシューマーにデータを伝達するタスクを調整します。

[!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]

この例を実行すると、次の出力が生成されます。

```Output
The average is 50.
```

## <a name="example"></a>例

この例では、プロデューサー エージェントは一連の株式相場をコンシューマー エージェントに送信します。 コンシューマー エージェントは定期的に現在の相場を読み取り、それをコンソールに出力します。

使用するこの例には、前に似ています、 [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)プロデューサー、コンシューマーと 1 つのメッセージを共有するを有効にするオブジェクト。 前の例と同様に、`overwrite_buffer` クラスに、`ITarget` および `ISource` を実装して、プロデューサーおよびコンシューマーが共有メッセージ バッファーを操作できるようにします。

[!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_2.cpp)]

この例では、次のサンプル出力が生成されます。

```Output
Current quote is 24.44.
Current quote is 24.44.
Current quote is 24.65.
Current quote is 24.99.
Current quote is 23.76.
Current quote is 22.30.
Current quote is 25.89.
```

`unbounded_buffer` オブジェクトとは異なり、`receive` 関数によって、`overwrite_buffer` オブジェクトからメッセージが削除されることはありません。 プロデューサーがメッセージを上書きする前に、コンシューマーがメッセージ バッファーから 2 回以上読み取りを行った場合、コンシューマーは毎回同じメッセージを取得します。

## <a name="compiling-the-code"></a>コードのコンパイル

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、という名前のファイルに貼り付ける`producer-consumer.cpp`Visual Studio コマンド プロンプト ウィンドウで、次のコマンドを実行します。

**cl.exe/EHsc producer-consumer.cpp**

## <a name="see-also"></a>関連項目

[非同期エージェント ライブラリ](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同期エージェント](../../parallel/concrt/asynchronous-agents.md)<br/>
[非同期メッセージ ブロック](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[メッセージ パッシング関数](../../parallel/concrt/message-passing-functions.md)
