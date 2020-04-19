---
title: '方法: キャンセル処理を使用する OpenMP ループを変換し、コンカレンシー ランタイムを使用する'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
ms.openlocfilehash: f4d4d8d1b2dbf60d0b4674229043c981d874292d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141819"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>方法: キャンセル処理を使用する OpenMP ループを変換し、コンカレンシー ランタイムを使用する

並列ループによっては、すべての反復を必ずしも実行する必要はありません。 たとえば、値を検索するアルゴリズムは、値が見つかれば終了できます。 OpenMP には、並列ループを抜けるための機構は用意されていません。 ただし、ブール値 (フラグ) を使用して、ループの反復処理時に、解決策が見つかったことを通知できます。 コンカレンシー ランタイムの場合、先行のタスクによって、まだ開始されていない他のタスクを取り消すことができます。

この例では、すべての反復処理を実行する必要のない OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../../parallel/openmp/reference/for-openmp.md)ループを変換して、同時実行ランタイムのキャンセルメカニズムを使用する方法を示します。

## <a name="example"></a>例

この例では、OpenMP と同時実行ランタイムの両方を使用して、 [std:: any_of](../../standard-library/algorithm-functions.md#any_of)アルゴリズムの並列バージョンを実装しています。 この例に示す OpenMP バージョンでは、フラグを使用して、条件が満たされたときにすべての並列ループ反復で調整が行われるようにしています。 同時実行ランタイムを使用するバージョンでは、 [Concurrency:: structured_task_group:: cancel](reference/structured-task-group-class.md#cancel)メソッドを使用して、条件が満たされたときに全体的な操作を停止します。

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

この例を実行すると、次の出力が生成されます。

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

OpenMP を使用するバージョンでは、フラグが設定されている場合でも、すべてのループ反復が実行されます。 さらに、タスクに子タスクが含まれている場合は、それらの子タスクにもフラグによって取り消しが通知される必要があります。 同時実行ランタイムでは、タスクグループが取り消されると、ランタイムは子タスクを含む作業のツリー全体を取り消します。 [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)アルゴリズムでは、タスクを使用して作業を実行します。 したがって、ループの1つの反復処理によってルートタスクが取り消された場合、計算のツリー全体も取り消されます。 作業のツリーがキャンセルされると、ランタイムは新しいタスクを開始しません。 ただし、既に開始されているタスクは終了できます。 したがって、`parallel_for_each` アルゴリズムの場合、アクティブなループ反復によってリソースがクリーンアップされることがあります。

この例に示すどちらのバージョンでも、配列に検索対象値の複数のコピーが含まれている場合は、複数のループ反復でそれぞれ同時に結果が設定され、操作全体が取り消されることがあります。 条件が満たされたときに 1 つのタスクだけが実行されるようにする必要がある場合は、クリティカル セクションなどの同期プリミティブを使用できます。

また、例外処理を使用して、PPL を使用するタスクを取り消すこともできます。 取り消しの詳細については、「 [PPL における取り消し](cancellation-in-the-ppl.md)処理」を参照してください。

`parallel_for_each` およびその他の並列アルゴリズムの詳細については、「[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)」を参照してください。

## <a name="compiling-the-code"></a>コードのコンパイル

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`concrt-omp-parallel-any-of.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

> **cl.exe/EHsc/openmp concrt-omp-parallel-any-of**

## <a name="see-also"></a>参照

[OpenMP からコンカレンシー ランタイムへの移行](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[PPL における取り消し処理](cancellation-in-the-ppl.md)<br/>
[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)
