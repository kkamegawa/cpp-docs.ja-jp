---
title: '方法: 特定のスケジューラ ポリシーを使用するエージェントを作成する'
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
ms.openlocfilehash: ece6b113e3fe10c2c3179517f73137df281acf87
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141731"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>方法: 特定のスケジューラ ポリシーを使用するエージェントを作成する

エージェントは、他のコンポーネントと非同期的にやり取りしてより大きなコンピューティング タスクを解決するアプリケーション コンポーネントです。 通常、エージェントは一定のライフ サイクルを持ち、状態を保持します。

どのエージェントにも、固有のアプリケーションの要件があります。 たとえば、ユーザーとのやり取り (入力の取得または出力の表示) を可能にするエージェントは、コンピューティング リソースに優先的にアクセスできなければならない場合があります。 スケジューラでタスクを管理する場合、スケジューラ ポリシーを使用することで、スケジューラが使用する方法を制御できます。 このトピックでは、特定のスケジューラ ポリシーを使用するエージェントの作成方法を示します。

カスタムスケジューラポリシーを非同期メッセージブロックと共に使用する基本的な例については、「[方法: 特定のスケジューラポリシーを指定](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)する」を参照してください。

このトピックでは、エージェント、メッセージ ブロック、メッセージ パッシング関数などの非同期エージェント ライブラリの機能を使用して、処理を行います。 非同期エージェントライブラリの詳細については、「[非同期エージェントライブラリ](../../parallel/concrt/asynchronous-agents-library.md)」を参照してください。

## <a name="example"></a>例

次の例では、 [concurrency:: agent](../../parallel/concrt/reference/agent-class.md): `permutor` と `printer`から派生する2つのクラスを定義します。 `permutor` クラスは、指定された入力文字列のすべての順列を計算します。 `printer` クラスは、進行状況メッセージをコンソールに出力します。 `permutor` クラスは計算量が非常に多い演算を行うため、使用できるコンピューティング リソースが使い果たされる可能性があります。 `printer` クラスを活かすためには、各進行状況メッセージが適時に出力されなければなりません。

この例では、コンピューティングリソースへの `printer` クラスのフェアアクセスを提供するために、「[方法: スケジューラインスタンスを管理](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)してカスタムポリシーを持つスケジューラインスタンスを作成する」で説明されている手順を使用します。 このカスタム ポリシーで、スレッドの優先順位が最も高い優先順位クラスとなるように指定します。

カスタム ポリシーを持つスケジューラを使用する利点を示すため、この例ではタスク全体を 2 度実行しています。 まず、既定のスケジューラを使用して両方のタスクをスケジュールします。 次の例では、既定のスケジューラを使用して `permutor` オブジェクトをスケジュールし、カスタム ポリシーを持つスケジューラを使用して `printer` オブジェクトをスケジュールします。

[!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/cpp/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]

この例を実行すると、次の出力が生成されます。

```Output
With default scheduler:
Computing all permutations of 'Grapefruit'...
100% complete...

With higher context priority:
Computing all permutations of 'Grapefruit'...
100% complete...
```

どちらのタスク セットでも結果は同じですが、カスタム ポリシーを使用するバージョンでは `printer` オブジェクトを高い優先順位で実行できるため、応答性が高まります。

## <a name="compiling-the-code"></a>コードのコンパイル

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`permute-strings.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

> **cl.exe/EHsc permute-strings**

## <a name="see-also"></a>参照

[スケジューラ ポリシー](../../parallel/concrt/scheduler-policies.md)<br/>
[非同期エージェント](../../parallel/concrt/asynchronous-agents.md)
