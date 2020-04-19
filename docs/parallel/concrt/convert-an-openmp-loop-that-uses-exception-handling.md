---
title: '方法: 例外処理を使用する OpenMP ループを変換し、コンカレンシー ランタイムを使用する'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
ms.openlocfilehash: 380a96eedb8a70965197c4a5ce0c5199bc268db5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141815"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>方法: 例外処理を使用する OpenMP ループを変換し、コンカレンシー ランタイムを使用する

この例では、例外処理を実行する OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../../parallel/openmp/reference/for-openmp.md)ループを変換して、同時実行ランタイム例外処理機構を使用する方法を示します。

OpenMP では、並列領域でスローされた例外は、同じスレッドによって同じ領域でキャッチおよび処理される必要があります。 例外が並列領域をエスケープする場合は、ハンドルされない例外のハンドラーがそれをキャッチし、既定ではプロセスを終了します。

同時実行ランタイムでは、 [concurrency:: task_group](reference/task-group-class.md)または[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)オブジェクトなどのタスクグループに渡す処理関数の本体で例外をスローした場合や、 [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)などの並列アルゴリズムに例外をスローした場合、ランタイムはその例外を格納し、タスクグループまたはアルゴリズムが終了するのを待機するコンテキストにマーシャリングします。 タスクグループの場合、待機コンテキストとは、 [concurrency:: task_group:: wait](reference/task-group-class.md#wait)、 [concurrency:: structured_task_group:: wait](reference/structured-task-group-class.md#wait)、concurrency [:: task_group:: run_and_wait](reference/task-group-class.md#run_and_wait)、または[concurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait)を呼び出すコンテキストです。 並列アルゴリズムの場合、待機しているコンテキストは、そのアルゴリズムを呼び出したコンテキストです。 また、ランタイムは、タスク グループ内のすべてのアクティブ タスク (子タスク グループ内のタスクも含む) を中断すると共に、開始されていないすべてのタスクを破棄します。

## <a name="example"></a>例

この例では、OpenMP `parallel` 領域および `parallel_for` の呼び出しで例外を処理する方法を示します。 `do_work` 関数は、成功せず、型[std:: bad_alloc](../../standard-library/bad-alloc-class.md)の例外をスローするメモリ割り当て要求を実行します。 OpenMP を使用するバージョンでは、例外をスローするスレッドは例外のキャッチも行う必要があります。 つまり、OpenMP 並列ループの各反復で例外が処理される必要があります。 コンカレンシー ランタイムを使用するバージョンでは、メイン スレッドは別のスレッドによってスローされる例外をキャッチします。

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

OpenMP を使用するバージョンを例外発生後に終了する必要がある場合は、ブール型のフラグを使用して、エラーが発生したことを他のループ反復に通知します。 「[方法: キャンセルを使用する OpenMP ループを変換](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)して同時実行ランタイムを使用する」の例のように、後続のループの反復では、フラグが設定されている場合は何も実行されません。 一方、コンカレンシー ランタイムを使用するループを例外発生後に続行する必要がある場合は、並列ループの本体で例外を処理します。

非同期エージェントや軽量タスクなど、コンカレンシー ランタイムの他のコンポーネントでは、例外は転送されません。 代わりに、ハンドルされない例外のハンドラーが例外をキャッチし、既定ではプロセスを終了します。 例外処理の詳細については、「[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)」を参照してください。

`parallel_for` およびその他の並列アルゴリズムの詳細については、「[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)」を参照してください。

## <a name="compiling-the-code"></a>コードのコンパイル

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`concrt-omp-exceptions.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

> **cl.exe/EHsc/openmp concrt-omp-exceptions**

## <a name="see-also"></a>参照

[OpenMP からコンカレンシー ランタイムへの移行](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)
