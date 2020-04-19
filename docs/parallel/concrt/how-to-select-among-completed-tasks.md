---
title: '方法: 完了したタスクから選択する'
ms.date: 11/04/2016
helpviewer_keywords:
- selecting among completed tasks [Concurrency Runtime]
- completed tasks, selecting among [Concurrency Runtime]
ms.assetid: c8ccc160-043f-4599-847b-32ed270bb257
ms.openlocfilehash: 75ecac8dd0e8845401e3e287e8c95ea614055970
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142470"
---
# <a name="how-to-select-among-completed-tasks"></a>方法: 完了したタスクから選択する

この例では、 [concurrency:: choice](../../parallel/concrt/reference/choice-class.md)クラスおよび[concurrency:: join](../../parallel/concrt/reference/join-class.md)クラスを使用して、検索アルゴリズムを完了するための最初のタスクを選択する方法を示します。

## <a name="example"></a>例

次の例では 2 つの検索アルゴリズムを並列で実行し、最初のアルゴリズムを選択して完了します。 この例では、従業員の数値 ID と給与を格納する `employee` 型を定義します。 `find_employee` 関数は、指定された ID と指定された給与に該当する最初の従業員を検索します。 また、`find_employee` 関数は、指定された ID または指定された給与に該当する従業員がいない場合の処理も行います。 `wmain` 関数は、`employee` オブジェクトの配列を作成して複数の ID および給与の値を検索します。

次の例では、`choice` オブジェクトを使用して、次の事例を選択します。

1. 指定された ID を持つ従業員。

1. 指定された給与の従業員。

1. 指定された ID または給与に該当しない従業員。

最初の2つのケースでは、この例では、 [concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md)オブジェクトを使用して識別子を保持し、別の `single_assignment` オブジェクトを使用して給与を保持します。 この例は、3 番目の事例に対して `join` オブジェクトを使用します。 `join` オブジェクトは、2 つの別の `single_assignment` オブジェクトで構成されます。1 つは、指定された ID を持つ従業員がいない事例に使用し、もう 1 つは指定された給与に該当する従業員がいない事例に使用します。 `join` オブジェクトは、その各メンバーがメッセージを受信したときにメッセージを送信します。 この例では、`join` オブジェクトは、指定された ID または給与に該当する従業員がいない場合にメッセージを送信します。

この例では、 [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)オブジェクトを使用して、両方の検索アルゴリズムを並列で実行します。 各検索タスクが、指定された従業員が存在するかどうかを示す値を `single_assignment` オブジェクトの 1 つに書き込みます。 この例では、 [concurrency:: receive](reference/concurrency-namespace-functions.md#receive)関数を使用して、メッセージを含む最初のバッファーのインデックスと、結果を出力するための `switch` ブロックを取得します。

[!code-cpp[concrt-find-employee#1](../../parallel/concrt/codesnippet/cpp/how-to-select-among-completed-tasks_1.cpp)]

この例を実行すると、次の出力が生成されます。

```Output
Employee with id 14758 has salary 27780.00.
Employee with salary 29150.00 has id 84345.
Employee with id 61935 has salary 29905.00.
No employee has id 899 or salary 31223.00.
```

この例では、 [concurrency:: make_choice](reference/concurrency-namespace-functions.md#make_choice)ヘルパー関数を使用して `choice` オブジェクトを作成し、 [concurrency:: make_join](reference/concurrency-namespace-functions.md#make_join)ヘルパー関数を使用して `join` オブジェクトを作成します。

## <a name="compiling-the-code"></a>コードのコンパイル

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`find-employee.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

> **cl.exe/EHsc find-employee**

## <a name="see-also"></a>参照

[非同期エージェント ライブラリ](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同期メッセージ ブロック](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[メッセージ パッシング関数](../../parallel/concrt/message-passing-functions.md)<br/>
[choice クラス](../../parallel/concrt/reference/choice-class.md)<br/>
[join クラス](../../parallel/concrt/reference/join-class.md)
