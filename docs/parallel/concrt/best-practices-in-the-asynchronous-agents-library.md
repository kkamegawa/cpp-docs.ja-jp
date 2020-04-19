---
title: 非同期エージェント ライブラリに関するベスト プラクティス
ms.date: 11/04/2016
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
ms.openlocfilehash: 1cd6b54a014d35d17c732ed52f8529b05274585b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142093"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>非同期エージェント ライブラリに関するベスト プラクティス

ここでは、非同期エージェント ライブラリを効果的に使用する方法について説明します。 エージェント ライブラリは、アクター ベースのプログラミング モデルと、粒度の粗いデータ フローおよびパイプライン処理タスクのためのインプロセス メッセージ パッシングを推進します。

エージェントライブラリの詳細については、「[非同期エージェントライブラリ](../../parallel/concrt/asynchronous-agents-library.md)」を参照してください。

## <a name="top"></a> セクション

このドキュメントは、次のトピックに分かれています。

- [エージェントを使用して状態を分離する](#isolation)

- [スロットルメカニズムを使用して、データパイプライン内のメッセージの数を制限する](#throttling)

- [データパイプラインで粒度の細かい作業を実行しない](#fine-grained)

- [サイズの大きいメッセージペイロードを値で渡さない](#large-payloads)

- [所有権が定義されていない場合にデータネットワークで shared_ptr を使用する](#ownership)

## <a name="isolation"></a>エージェントを使用して状態を分離する

エージェント ライブラリは、非同期メッセージ引き渡し方法を使用して分離コンポーネントを接続できるようにすることで、共有状態に代わる手段を提供します。 非同期エージェントは、他のコンポーネントから内部状態を分離する場合に最も効果的です。 状態を分離することによって、通常、複数のコンポーネントが共有データに作用することがなくなります。 状態分離により共有メモリの競合が軽減されるため、アプリケーションのスケーラビリティが高まります。 また、コンポーネントが共有データへのアクセスを同期する必要がなくなるため、デッドロックや競合状態が発生しにくくなります。

通常、エージェントで状態を分離するには、エージェント クラスの `private` セクションまたは `protected` セクションにデータ メンバーを保持し、メッセージ バッファーを使用して状態の変化を通知します。 次の例は、 [concurrency:: agent](../../parallel/concrt/reference/agent-class.md)から派生した `basic_agent` クラスを示しています。 `basic_agent` クラスは、2 つのメッセージ バッファーを使用して外部コンポーネントと通信します。 2 つのメッセージ バッファーにはそれぞれ受信メッセージと送信メッセージが保持されます。

[!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]

エージェントを定義して使用する方法の完全な例については、「[チュートリアル: エージェントベースのアプリケーションの作成](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)」および「[チュートリアル: データフローエージェントの作成](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)」を参照してください。

[[トップ](#top)]

## <a name="throttling"></a>スロットルメカニズムを使用して、データパイプライン内のメッセージの数を制限する

[Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)など、多くのメッセージバッファーの種類では、無制限の数のメッセージを保持できます。 メッセージ プロデューサーがメッセージをデータ パイプラインに送信する速度が、コンシューマーがそれらのメッセージを処理する速度よりも速い場合、アプリケーションはメモリ不足の状態になることがあります。 セマフォなどのスロットリング機構を使用すると、データ パイプラインで同時にアクティブになるメッセージの数を制限できます。

次の基本的な例では、セマフォを使用してデータ パイプラインのメッセージの数を制限する方法を示します。 データパイプラインでは、 [concurrency:: wait](reference/concurrency-namespace-functions.md#wait)関数を使用して、100ミリ秒以上かかる操作をシミュレートします。 コンシューマーがメッセージを処理するよりも速く送信側でメッセージが生成されるため、この例では `semaphore` クラスを定義し、アプリケーションがアクティブ メッセージの数を制限できるようにしています。

[!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]

`semaphore` オブジェクトでは、パイプラインで同時に処理するメッセージ数を 2 までに制限しています。

この例では、プロデューサーからコンシューマーに送信されるメッセージは比較的少量です。 そのため、メモリ不足の状態は発生しません。 ただし、データ パイプラインに含まれるメッセージの数が比較的多い場合、この機構は便利です。

この例で使用するセマフォクラスを作成する方法の詳細については、「[方法: コンテキストクラスを使用して協調セマフォを実装](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)する」を参照してください。

[[トップ](#top)]

## <a name="fine-grained"></a>データパイプラインで粒度の細かい作業を実行しない

エージェント ライブラリが最も役立つのは、データ パイプラインで実行される処理の粒度が非常に粗い場合です。 たとえば、1 つのアプリケーション コンポーネントがファイルまたはネットワーク接続からデータを読み取り、状況に応じてそのデータを別のコンポーネントに送信する場合があります。 エージェントライブラリがメッセージの伝達に使用するプロトコルによって、メッセージパッシング機構は、[並列パターンライブラリ](../../parallel/concrt/parallel-patterns-library-ppl.md)(PPL) によって提供されるタスク並列構造よりもオーバーヘッドが大きくなります。 したがって、データ パイプラインで実行される処理の時間が十分長く、このオーバーヘッドを相殺できることを確認してください。

データ パイプラインはそのタスクの粒度が粗い場合に最も有効ですが、データ パイプラインの各ステージでは PPL コンストラクト (タスク グループや並列アルゴリズムなど) を使用してより粒度の細かい処理を実行できます。 各処理ステージで粒度の細かい並列処理を使用する粒度の粗いデータネットワークの例については、「[チュートリアル: イメージ処理ネットワークの作成](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)」を参照してください。

[[トップ](#top)]

## <a name="large-payloads"></a>サイズの大きいメッセージペイロードを値で渡さない

ランタイムでは、各メッセージのコピーを作成してそれをメッセージ バッファー間での引き渡しに使用する場合があります。 たとえば、 [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)クラスは、各メッセージのコピーを各ターゲットに提供します。 また、 [concurrency:: send](reference/concurrency-namespace-functions.md#send)や[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)などのメッセージパッシング関数を使用してメッセージバッファーにメッセージを書き込み、メッセージを読み取るときに、ランタイムはメッセージデータのコピーを作成します。 この機構を使用すると、共有データに対する同時書き込みのリスクはなくなりますが、メッセージ ペイロードが比較的大きい場合、メモリのパフォーマンスが低下する可能性があります。

ペイロードの大きいメッセージを渡す場合は、ポインターまたは参照を使用してメモリのパフォーマンスを向上させることができます。 次の例では、大きなメッセージの値渡しを行う場合と同じメッセージ型にポインターを渡す場合を比較します。 この例では、`producer` オブジェクトに対して作用する 2 種類のエージェント `consumer` および `message_data` を定義します。 また、プロデューサーが複数の `message_data` オブジェクトをコンシューマーに送信するのに必要な時間と、プロデューサー エージェントが複数のポインターを `message_data` オブジェクト、コンシューマーへと順番に送信するのに必要な時間を比較します。

[!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]

この例では、次のサンプル出力が生成されます。

```Output
Using message_data...
took 437ms.
Using message_data*...
took 47ms.
```

ポインターを使用したバージョンの方がパフォーマンスは高くなります。これは、ランタイムがプロデューサーからコンシューマーに渡す各 `message_data` オブジェクトの完全なコピーを作成する必要がなくなるためです。

[[トップ](#top)]

## <a name="ownership"></a>所有権が定義されていない場合にデータネットワークで shared_ptr を使用する

メッセージ パッシング パイプラインまたはネットワークを通じてメッセージをポインターで送信する場合、通常、ネットワークの始端で各メッセージ用のメモリを割り当て、ネットワークの終端でそのメモリを解放します。 この機構も通常は有効に働きますが、使用するのが困難な場合や、使用できない場合もあります。 たとえば、データ ネットワークに複数の終了ノードが存在する場合を考えます。 この場合、メッセージ用のメモリを解放する場所が明確ではありません。

この問題を解決するには、たとえば[std:: shared_ptr](../../standard-library/shared-ptr-class.md)というメカニズムを使用して、複数のコンポーネントがポインターを所有できるようにします。 リソースを所有する最後の `shared_ptr` オブジェクトが破棄されると、そのリソースも解放されます。

次の例では、`shared_ptr` を使用して複数のメッセージ バッファー間でポインター値を共有する方法を示します。 この例では、 [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)オブジェクトを3つの[concurrency:: call](../../parallel/concrt/reference/call-class.md)オブジェクトに接続します。 `overwrite_buffer` クラスは、メッセージを各ターゲットに提供します。 データ ネットワークの終端にはデータの所有者が複数存在するため、この例では `shared_ptr` を使用して各 `call` オブジェクトでメッセージの所有権を共有できるようにしています。

[!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]

この例では、次のサンプル出力が生成されます。

```Output
Creating resource 42...
receiver1: received resource 42
Creating resource 64...
receiver2: received resource 42
receiver1: received resource 64
Destroying resource 42...
receiver2: received resource 64
Destroying resource 64...
```

## <a name="see-also"></a>参照

[コンカレンシー ランタイムに関するベスト プラクティス](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[非同期エージェント ライブラリ](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[チュートリアル: エージェント ベースのアプリケーションの作成](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
[チュートリアル: データフロー エージェントの作成](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[チュートリアル: イメージ処理ネットワークの作成](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[並列パターン ライブラリに関するベスト プラクティス](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[コンカレンシー ランタイムに関する全般的なベスト プラクティス](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
