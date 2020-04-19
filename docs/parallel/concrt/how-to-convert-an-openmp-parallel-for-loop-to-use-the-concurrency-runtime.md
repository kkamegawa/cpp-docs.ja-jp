---
title: '方法: OpenMP の parallel for ループを変換し、コンカレンシー ランタイムを使用する'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
ms.openlocfilehash: 2d96ba23582368fe72e61003823826a6f3ab807a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141758"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>方法: OpenMP の parallel for ループを変換し、コンカレンシー ランタイムを使用する

この例では、OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)および[for](../../parallel/openmp/reference/for-openmp.md)ディレクティブを使用する基本的なループを変換して、同時実行ランタイム[Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)アルゴリズムを使用する方法を示します。

## <a name="example---prime-count"></a>例-素数

この例では、OpenMP とコンカレンシー ランタイムの両方を使用して、ランダム値の配列に含まれる素数の数を計算します。

[!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]

この例を実行すると、次の出力が生成されます。

```Output
Using OpenMP...
found 107254 prime numbers.
Using the Concurrency Runtime...
found 107254 prime numbers.
```

`parallel_for` アルゴリズムおよび OpenMP 3.0 では、インデックス型を符号付き整数型として使用することも、符号なし整数型として使用することもできます。 また、`parallel_for` アルゴリズムを使用すると、指定の範囲が符号付きの型をオーバーフローすることがなくなります。 OpenMP Version 2.0 および 2.5 では、符号付き整数のインデックス型しか使用できません。 また、OpenMP でインデックス範囲は検証されません。

同時実行ランタイムを使用するこの例のバージョンでは、 [atomic](../../parallel/openmp/reference/atomic.md)ディレクティブの代わりに[Concurrency:: 組み合わせ](../../parallel/concrt/reference/combinable-class.md)可能オブジェクトを使用して、同期を必要とせずにカウンター値をインクリメントします。

`parallel_for` およびその他の並列アルゴリズムの詳細については、「[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)」を参照してください。 `combinable` クラスの詳細については、「[並列コンテナーとオブジェクト](../../parallel/concrt/parallel-containers-and-objects.md)」を参照してください。

## <a name="example---use-stdarray"></a>例-std:: array を使用する

この例では、前の例を変更して、ネイティブ配列ではなく[std:: array](../../standard-library/array-class-stl.md)オブジェクトを操作します。 OpenMP バージョン2.0 および2.5 では、`parallel_for` コンストラクトでのみ符号付き整数インデックス型が許可されるため、反復子を使用しC++て標準ライブラリコンテナーの要素に並列でアクセスすることはできません。 並列パターンライブラリ (PPL) では、 [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)アルゴリズムが提供されています。これは、 C++標準ライブラリによって提供されるものなど、反復的なコンテナーに対してタスクを並行して実行します。 このアルゴリズムでは、`parallel_for` アルゴリズムで使用されるのと同じ分割ロジックが使用されます。 `parallel_for_each` アルゴリズムはC++標準ライブラリ[std:: for_each](../../standard-library/algorithm-functions.md#for_each)アルゴリズムに似ていますが、`parallel_for_each` アルゴリズムによってタスクが同時に実行される点が異なります。

[!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]

## <a name="compiling-the-code"></a>コードのコンパイル

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`concrt-omp-count-primes.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

> **cl.exe/EHsc/openmp concrt-omp-count-primes**

## <a name="see-also"></a>参照

[OpenMP からコンカレンシー ランタイムへの移行](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)<br/>
[並列コンテナーと並列オブジェクト](../../parallel/concrt/parallel-containers-and-objects.md)
