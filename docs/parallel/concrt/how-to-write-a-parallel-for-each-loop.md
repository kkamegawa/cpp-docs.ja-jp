---
title: '方法: parallel_for_each ループを記述する'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
ms.openlocfilehash: 10c281b7db92e2706b20a1c7377fcdb9d924152d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141874"
---
# <a name="how-to-write-a-parallel_for_each-loop"></a>方法: parallel_for_each ループを記述する

この例では、 [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)アルゴリズムを使用して、 [std:: array](../../standard-library/array-class-stl.md)オブジェクト内の素数の数を並列で計算する方法を示します。

## <a name="example"></a>例

次の例では、配列に含まれる素数の数を 2 回計算します。 この例では、最初に[std:: for_each](../../standard-library/algorithm-functions.md#for_each)アルゴリズムを使用して、連続した数を計算します。 次に、`parallel_for_each` アルゴリズムを使用して、同じタスクを並列に実行します。 また、それぞれの計算に要する時間もコンソールに出力します。

[!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-each-loop_1.cpp)]

4 つのプロセッサを備えたコンピューターを使用したときのサンプル出力を次に示します。

```Output
serial version:
found 17984 prime numbers
took 6115 ms

parallel version:
found 17984 prime numbers
took 1653 ms
```

## <a name="compiling-the-code"></a>コードのコンパイル

コードをコンパイルするには、コードをコピーし、Visual Studio プロジェクトに貼り付けるか、`parallel-count-primes.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

> **cl.exe/EHsc parallel-count-primes**

## <a name="robust-programming"></a>堅牢性の高いプログラミング

この例で `parallel_for_each` アルゴリズムに渡すラムダ式では、`InterlockedIncrement` 関数を使用して、ループの反復処理を並列で行い、カウンターを同時にインクリメントします。 `InterlockedIncrement` などの関数を使用して共有リソースへのアクセスを同期化すると、コードのパフォーマンスのボトルネックを示すことができます。 共有リソースへの同時アクセスを排除するために、たとえば、 [concurrency:: 組み合わせ](../../parallel/concrt/reference/combinable-class.md)可能クラスなどのロックフリーの同期機構を使用できます。 この方法で `combinable` クラスを使用する例については、「[方法: 組み合わせ可能を使用してパフォーマンスを向上](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)させる」を参照してください。

## <a name="see-also"></a>参照

[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for_each 関数](reference/concurrency-namespace-functions.md#parallel_for_each)
