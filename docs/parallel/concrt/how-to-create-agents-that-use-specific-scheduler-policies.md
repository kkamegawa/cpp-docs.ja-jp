---
title: "方法: 特定のスケジューラ ポリシーを使用するエージェントを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "スケジューラ ポリシー、エージェント [同時実行ランタイム]"
  - "作成 (特定のポリシーを使用するエージェントを) [同時実行ランタイム]"
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 方法: 特定のスケジューラ ポリシーを使用するエージェントを作成する
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

エージェントは、他のコンポーネントと非同期的にやり取りしてより大きなコンピューティング タスクを解決するアプリケーション コンポーネントです。  通常、エージェントは一定のライフ サイクルを持ち、状態を保持します。  
  
 どのエージェントにも、固有のアプリケーションの要件があります。  たとえば、ユーザーとのやり取り \(入力の取得または出力の表示\) を可能にするエージェントは、コンピューティング リソースに優先的にアクセスできなければならない場合があります。  スケジューラでタスクを管理する場合、スケジューラ ポリシーを使用することで、スケジューラが使用する方法を制御できます。  このトピックでは、特定のスケジューラ ポリシーを使用するエージェントの作成方法を示します。  
  
 カスタム スケジューラ ポリシーを非同期メッセージ ブロックと共に使用する基本的な例については、「[方法: 特定のスケジューラ ポリシーを指定する](../Topic/How%20to:%20Specify%20Specific%20Scheduler%20Policies.md)」を参照してください。  
  
 このトピックでは、エージェント、メッセージ ブロック、メッセージ パッシング関数などの非同期エージェント ライブラリの機能を使用して、処理を行います。  非同期エージェント ライブラリの詳細については、「[非同期エージェント ライブラリ](../../parallel/concrt/asynchronous-agents-library.md)」を参照してください。  
  
## 使用例  
 次の例では、[concurrency::agent](../../parallel/concrt/reference/agent-class.md) から派生する `permutor` クラスと `printer` クラスを定義しています。  `permutor` クラスは、指定された入力文字列のすべての順列を計算します。  `printer` クラスは、進行状況メッセージをコンソールに出力します。  `permutor` クラスは計算量が非常に多い演算を行うため、使用できるコンピューティング リソースが使い果たされる可能性があります。  `printer` クラスを活かすためには、各進行状況メッセージが適時に出力されなければなりません。  
  
 `printer` クラスがコンピューティング リソースに公平にアクセスできるように、この例では、「[方法: スケジューラ インスタンスを管理する](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)」で説明されている手順に従って、カスタム ポリシーを持つスケジューラ インスタンスを作成しています。  このカスタム ポリシーで、スレッドの優先順位が最も高い優先順位クラスとなるように指定します。  
  
 カスタム ポリシーを持つスケジューラを使用する利点を示すため、この例ではタスク全体を 2 度実行しています。  まず、既定のスケジューラを使用して両方のタスクをスケジュールします。  次の例では、既定のスケジューラを使用して `permutor` オブジェクトをスケジュールし、カスタム ポリシーを持つスケジューラを使用して `printer` オブジェクトをスケジュールします。  
  
 [!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/CPP/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]  
  
 この例を実行すると、次の出力が生成されます。  
  
  **With default scheduler:**  
**Computing all permutations of 'Grapefruit'...**  
**100% complete...**  
**With higher context priority:**  
**Computing all permutations of 'Grapefruit'...**  
**100% complete...** どちらのタスク セットでも結果は同じですが、カスタム ポリシーを使用するバージョンでは `printer` オブジェクトを高い優先順位で実行できるため、応答性が高まります。  
  
## コードのコンパイル  
 コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`permute-strings.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。  
  
 **cl.exe \/EHsc permute\-strings.cpp**  
  
## 参照  
 [スケジューラ ポリシー](../../parallel/concrt/scheduler-policies.md)   
 [非同期エージェント](../../parallel/concrt/asynchronous-agents.md)   
 