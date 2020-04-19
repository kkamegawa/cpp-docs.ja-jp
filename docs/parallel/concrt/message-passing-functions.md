---
title: メッセージ パッシング関数
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 4e1052a59f355c4ad5a7c6b57724268c24a209b4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143297"
---
# <a name="message-passing-functions"></a>メッセージ パッシング関数

非同期エージェントライブラリには、コンポーネント間でメッセージを渡すための関数がいくつか用意されています。

これらのメッセージパッシング関数は、さまざまなメッセージブロックの型と共に使用されます。 同時実行ランタイムによって定義されるメッセージブロック型の詳細については、「[非同期メッセージブロック](../../parallel/concrt/asynchronous-message-blocks.md)」を参照してください。

## <a name="top"></a> セクション

このトピックでは、次のメッセージパッシング関数について説明します。

- [send と asend](#send)

- [receive および try_receive](#receive)

- [使用例](#examples)

## <a name="send"></a>send と asend

[Concurrency:: send](reference/concurrency-namespace-functions.md#send)関数は、指定されたターゲットにメッセージを同期的に送信します。 [concurrency:: asend](reference/concurrency-namespace-functions.md#asend)関数は、指定されたターゲットにメッセージを非同期的に送信します。 `send` 関数と `asend` 関数はどちらも、最終的にメッセージが受け入れられるか拒否されることをターゲットが示すまで待機します。

`send` 関数は、が返される前に、ターゲットがメッセージを受け入れるか拒否するまで待機します。 `send` 関数は、メッセージが配信された場合は**true** 、それ以外の場合は**false**を返します。 `send` 関数は同期的に動作するため、`send` 関数は、送信先がメッセージを受信するまで待機してから制御を戻します。

逆に、`asend` 関数は、が返される前に、ターゲットがメッセージを受け入れたり拒否したりするのを待機しません。 代わりに、`asend` 関数は、ターゲットがメッセージを受け入れ、最終的にそれを受け取る場合に**true**を返します。 それ以外の場合、`asend` は**false**を返して、ターゲットがメッセージを拒否したか、メッセージを取得するかどうかの決定を延期したことを示します。

[[トップ](#top)]

## <a name="receive"></a>receive および try_receive

[Concurrency:: receive](reference/concurrency-namespace-functions.md#receive)および[concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive)関数は、指定されたソースからデータを読み取ります。 `receive` 関数は、データが使用可能になるまで待機し、`try_receive` 関数はすぐに制御を戻します。

続行するには、`receive` 関数を使用します。 現在のコンテキストをブロックしない場合、またはデータを続行する必要がない場合は、`try_receive` 関数を使用します。

[[トップ](#top)]

## <a name="examples"></a> 例

`send` と `asend`、および `receive` 関数を使用する例については、次のトピックを参照してください。

- [非同期メッセージ ブロック](../../parallel/concrt/asynchronous-message-blocks.md)

- [方法: さまざまなプロデューサー/コンシューマー パターンを実装する](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [方法: call クラスおよび transformer クラスに処理関数を提供する](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [方法: データ パイプラインでトランスフォーマーを使用する](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [方法: 完了したタスクから選択する](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [方法: メッセージを定期的に送信する](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [方法: メッセージ ブロック フィルターを使用する](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[トップ](#top)]

## <a name="see-also"></a>参照

[非同期エージェント ライブラリ](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同期メッセージ ブロック](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[send 関数](reference/concurrency-namespace-functions.md#send)<br/>
[asend 関数](reference/concurrency-namespace-functions.md#asend)<br/>
[receive 関数](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive 関数](reference/concurrency-namespace-functions.md#try_receive)
