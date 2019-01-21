---
title: '方法: 同時実行ランタイムを使用する例外処理を使用する OpenMP ループを変換します。'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
ms.openlocfilehash: 9fa5ff2bcdfa6680dde6e9316d143089bf586671
ms.sourcegitcommit: ee0103752884425843556a19cf418a504dc3cd02
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2018
ms.locfileid: "53740500"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>方法: 同時実行ランタイムを使用する例外処理を使用する OpenMP ループを変換します。

OpenMP を変換する方法を示します[並列](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[の](../../parallel/openmp/reference/for-openmp.md)同時実行ランタイムの例外処理メカニズムを使用する例外処理を実行するループします。

OpenMP では、並列領域でスローされた例外は、同じスレッドによって同じ領域でキャッチおよび処理される必要があります。 例外が並列領域をエスケープする場合は、ハンドルされない例外のハンドラーがそれをキャッチし、既定ではプロセスを終了します。

など、タスク グループに渡す処理関数の本体で例外をスローするときに、同時実行ランタイムで、 [concurrency::task_group](reference/task-group-class.md)または[concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)オブジェクト、またはなどの並列アルゴリズムに[concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for)ランタイムはその例外を保存し、タスク グループまたはアルゴリズムを完了するまで待機するコンテキストにマーシャ リングします。 タスク グループの場合は、待機しているコンテキストは呼び出しコンテキスト[::task_group::wait](reference/task-group-class.md#wait)、 [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait)、 [concurrency::task_group::run_and_wait](reference/task-group-class.md#run_and_wait)、または[::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait)します。 並列アルゴリズムの場合、待機しているコンテキストは、そのアルゴリズムを呼び出したコンテキストです。 また、ランタイムは、タスク グループ内のすべてのアクティブ タスク (子タスク グループ内のタスクも含む) を中断すると共に、開始されていないすべてのタスクを破棄します。

## <a name="example"></a>例

この例では、OpenMP `parallel` 領域および `parallel_for` の呼び出しで例外を処理する方法を示します。 `do_work`関数が成功しない場合、型の例外をスローするメモリ割り当て要求を実行します[std::bad_alloc](../../standard-library/bad-alloc-class.md)します。 OpenMP を使用するバージョンでは、例外をスローするスレッドは例外のキャッチも行う必要があります。 つまり、OpenMP 並列ループの各反復で例外が処理される必要があります。 コンカレンシー ランタイムを使用するバージョンでは、メイン スレッドは別のスレッドによってスローされる例外をキャッチします。

[!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-exception-handling_1.cpp)]

この例を実行すると、次の出力が生成されます。

```Output
Using OpenMP...
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
Using the Concurrency Runtime...
An error of type 'class std::bad_alloc' occurred.
```

この例に示す OpenMP を使用するバージョンでは、各ループ反復で例外が発生し、処理されます。 コンカレンシー ランタイムを使用するバージョンでは、ランタイムが例外を保存し、すべてのアクティブ タスクを停止すると共に、まだ開始されていないタスクを破棄し、`parallel_for` を呼び出すコンテキストに例外をマーシャリングします。

OpenMP を使用するバージョンを例外発生後に終了する必要がある場合は、ブール型のフラグを使用して、エラーが発生したことを他のループ反復に通知します。 トピックの例のように[方法。使用してキャンセルはされる同時実行ランタイムを使用する OpenMP ループを変換](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)、後続のループの反復は機能しません、フラグが設定されている場合。 一方、コンカレンシー ランタイムを使用するループを例外発生後に続行する必要がある場合は、並列ループの本体で例外を処理します。

非同期エージェントや軽量タスクなど、コンカレンシー ランタイムの他のコンポーネントでは、例外は転送されません。 代わりに、ハンドルされない例外のハンドラーが例外をキャッチし、既定ではプロセスを終了します。 例外処理の詳細については、次を参照してください。[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)します。

詳細については`parallel_for`およびその他の並列アルゴリズムは、「[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)します。

## <a name="compiling-the-code"></a>コードのコンパイル

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、という名前のファイルに貼り付ける`concrt-omp-exceptions.cpp`Visual Studio コマンド プロンプト ウィンドウで、次のコマンドを実行します。

**cl.exe/EHsc/openmp concrt-omp-exceptions.cpp**

## <a name="see-also"></a>関連項目

[OpenMP からコンカレンシー ランタイムへの移行](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)

