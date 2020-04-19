---
title: 非同期エージェント
ms.date: 11/19/2018
helpviewer_keywords:
- asynchronous agents
- agents [Concurrency Runtime]
ms.assetid: 6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a
ms.openlocfilehash: ff6fa851519066c3c399a28557fd8f103d0e94be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412819"
---
# <a name="asynchronous-agents"></a>非同期エージェント

*非同期エージェント*(または単*エージェント*) は大規模なコンピューティング タスクを解決するには、他のエージェントで非同期的に動作するアプリケーション コンポーネントです。 エージェントの設定のライフ サイクルを持つタスクとして考えます。 たとえば、1 つエージェントは、入力/出力デバイス (キーボード、ディスク上のファイル、ネットワーク接続など) と別のエージェントからのデータは、使用可能になったように、そのデータの操作を実行可能性がありますを読み取る可能性があります。 最初のエージェントより多くのデータが使用可能なであることを 2 つ目のエージェントに通知するのにメッセージ パッシングを使用します。 同時実行ランタイムのタスク スケジューラは、ブロッキングや譲渡を協調的にエージェントを有効にする効率的なメカニズムを提供せず、それほど効率的で優先。

エージェント ライブラリの定義、 [concurrency::agent](../../parallel/concrt/reference/agent-class.md)非同期エージェントを表すクラス。 `agent` 仮想メソッドを宣言する抽象クラスは、 [concurrency::agent::run](reference/agent-class.md#run)します。 `run`メソッドは、エージェントによって実行されるタスクを実行します。 `run`は抽象クラスである必要がありますメソッドを実装するこのから派生したすべてのクラスで`agent`します。

## <a name="agent-life-cycle"></a>エージェントのライフ サイクル

エージェントでは、一定のライフ サイクルがあります。 [Concurrency::agent_status](reference/concurrency-namespace-enums.md#agent_status)列挙体は、エージェントのさまざまな状態を定義します。 次の図は、1 つの状態から別のエージェントの進捗を示す状態図を示します。 この図では、実線は、アプリケーションから呼び出すメソッドを表します。点線は、ランタイムから呼び出されるメソッドを表します。

![エージェントの状態ダイアグラム](../../parallel/concrt/media/agentstate.png "エージェントの状態ダイアグラム")

次の表に、各状態で、`agent_status`列挙体。

|エージェントの状態|説明|
|-----------------|-----------------|
|`agent_created`|実行するため、エージェントがスケジュールされていません。|
|`agent_runnable`|ランタイムのエージェントの実行スケジュールを設定します。|
|`agent_started`|エージェントが開始されが実行されています。|
|`agent_done`|エージェントが完了しました。|
|`agent_canceled`|これに入る前に、エージェントが取り消されました、`started`状態。|

`agent_created` エージェントの初期状態です`agent_runnable`と`agent_started`はアクティブの状態と`agent_done`と`agent_canceled`ターミナル状態です。

使用して、 [concurrency::agent::status](reference/agent-class.md#status)の現在の状態を取得するメソッドを`agent`オブジェクト。 ですが、`status`メソッドは同時実行セーフ、時間によってエージェントの状態を変更することができます、`status`メソッドを返します。 エージェント可能性がありますなど、`agent_started`を呼び出すときの状態、`status`メソッドに移動、`agent_done`直後の状態、`status`メソッドを返します。

## <a name="methods-and-features"></a>メソッドと機能

次の表にはいくつかの重要なメソッドに属している、`agent`クラス。 すべての詳細については、`agent`クラス メソッドを参照してください[エージェント クラス](../../parallel/concrt/reference/agent-class.md)します。

|メソッド|説明|
|------------|-----------------|
|[start](reference/agent-class.md#start)|スケジュール、`agent`実行のオブジェクトに設定し、`agent_runnable`状態。|
|[run](reference/agent-class.md#run)|によって実行されるタスクを実行、`agent`オブジェクト。|
|[done](reference/agent-class.md#done)|エージェントでの移動、`agent_done`状態。|
|[cancel](../../parallel/concrt/cancellation-in-the-ppl.md#cancel)|このメソッドは、エージェントの実行をキャンセルし、設定して、エージェントが開始されていない場合、`agent_canceled`状態。|
|[status](reference/agent-class.md#status)|現在の状態を取得、`agent`オブジェクト。|
|[wait](reference/agent-class.md#wait)|待機、`agent`を入力するオブジェクト、`agent_done`または`agent_canceled`状態。|
|[wait_for_all](reference/agent-class.md#wait_for_all)|提供されるすべての待機`agent`を入力するオブジェクト、`agent_done`または`agent_canceled`状態。|
|[wait_for_one](reference/agent-class.md#wait_for_one)|少なくとも 1 つ提供されているを待ちます`agent`を入力するオブジェクト、`agent_done`または`agent_canceled`状態。|

エージェント オブジェクトを作成した後に呼び出し、 [:start](reference/agent-class.md#start)メソッドの実行をスケジュールします。 ランタイム呼び出し、`run`メソッドに設定し、エージェントのスケジュールを設定した後、`agent_runnable`状態。

ランタイムは、非同期エージェントによってスローされる例外を管理しません。 例外処理とエージェントの詳細については、次を参照してください。[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)します。

## <a name="example"></a>例

基本的なエージェント ベースのアプリケーションを作成する方法の例を参照してください[チュートリアル。エージェント ベースのアプリケーションを作成する](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)します。

## <a name="see-also"></a>関連項目

[非同期エージェント ライブラリ](../../parallel/concrt/asynchronous-agents-library.md)
