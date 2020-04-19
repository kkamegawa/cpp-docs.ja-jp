---
title: '方法: キャンセル処理を使用して並列ループを中断する'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 21907de6c5625f7774ae788cef0449ac49107e40
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142132"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>方法: キャンセル処理を使用して並列ループを中断する

この例では、キャンセルを使用して基本的な並列検索アルゴリズムを実装する方法を示します。

## <a name="example"></a>例

次の例では、キャンセルを使用して、配列内の要素を検索します。 `parallel_find_any` 関数は、 [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)アルゴリズムと[concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token)関数を使用して、指定された値を含む位置を検索します。 並列ループは、値を検出すると、 [concurrency:: cancellation_token_source:: cancel](reference/cancellation-token-source-class.md#cancel)メソッドを呼び出して、将来の作業をキャンセルします。

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

[Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)アルゴリズムは同時に動作します。 そのため、事前に決められた順序で操作は実行されません。 配列に値の複数のインスタンスが含まれている場合、結果はその位置のいずれかになります。

## <a name="compiling-the-code"></a>コードのコンパイル

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`parallel-array-search.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

> **cl.exe/EHsc parallel-array-search**

## <a name="see-also"></a>参照

[PPL における取り消し処理](cancellation-in-the-ppl.md)<br/>
[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for 関数](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source クラス](../../parallel/concrt/reference/cancellation-token-source-class.md)
