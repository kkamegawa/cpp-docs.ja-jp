---
title: '方法: combinable を使用してパフォーマンスを向上させる'
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
ms.openlocfilehash: db27a791b2b92102118606712db4cbd2920f9619
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142442"
---
# <a name="how-to-use-combinable-to-improve-performance"></a>方法: combinable を使用してパフォーマンスを向上させる

この例では、 [concurrency:: 組み合わせ](../../parallel/concrt/reference/combinable-class.md)可能クラスを使用して、素数である[std:: array](../../standard-library/array-class-stl.md)オブジェクト内の数値の合計を計算する方法を示します。 `combinable` クラスは、共有状態を解消することでパフォーマンスを向上します。

> [!TIP]
> 場合によっては、並列マップ ([concurrency::p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)) と reduce ([concurrency:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)) によって `combinable`よりもパフォーマンスが向上することがあります。 この例と同じ結果を得るために map および reduce 操作を使用する例については、「[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)」を参照してください。

## <a name="example---accumulate"></a>例-蓄積

次の例では、 [std:: 蓄積](../../standard-library/numeric-functions.md#accumulate)関数を使用して、素数の配列内の要素の合計を計算します。 この例では、`a` は `array` オブジェクトであり、入力値が素数であるかどうかを判定するために `is_prime` 関数を使用します。

[!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]

## <a name="example---parallel_for_each"></a>例-parallel_for_each

次の例では、前の例の並列化を単純な方法で示します。 この例では、 [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)アルゴリズムを使用して配列を並列に処理し、 [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)オブジェクトを使用して `prime_sum` 変数へのアクセスを同期します。 この例では、共有リソースが使用できるようになるのを各スレッドが待機する必要があるため、効率は改善されません。

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]

## <a name="example---combinable"></a>例-組み合わせ可能

`combinable` オブジェクトを使用して、前の例のパフォーマンスを向上する例を次に示します。 この例では、同期オブジェクトが不要となっています。`combinable` オブジェクトを使用することにより、各スレッドがタスクを独立して実行できるため、効率が改善されます。

通常、`combinable` オブジェクトは次の手順で使用します。 最初に、処理を並列で実行して、詳細な計算結果を生成します。 次に、この計算結果を結合 (換算) して最終結果を生成します。 この例では、 [concurrency:: 組み合わせ可能:: local](reference/combinable-class.md#local)メソッドを使用して、ローカルの合計への参照を取得します。 次に、 [concurrency:: 組み合わせ可能:: 組み合わせ](reference/combinable-class.md#combine)メソッドと[std::p lus](../../standard-library/plus-struct.md)オブジェクトを使用して、ローカルの計算を最終結果に結合します。

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]

## <a name="example---serial-and-parallel"></a>例-シリアルと並列

次のコード例全体では、素数の合計を逐次処理と並列処理の両方で計算します。 この例では、両方の計算に要する時間もコンソールに出力します。

[!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]

4 つのプロセッサを備えたコンピューターを使用したときのサンプル出力を次に示します。

```Output
1709600813
serial time: 6178 ms

1709600813
parallel time: 1638 ms
```

## <a name="compiling-the-code"></a>コードのコンパイル

コードをコンパイルするには、コードをコピーし、Visual Studio プロジェクトに貼り付けるか、`parallel-sum-of-primes.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

> **cl.exe/EHsc parallel-sum-of-primes**

## <a name="robust-programming"></a>堅牢性の高いプログラミング

マップ操作と縮小操作を使用して同じ結果を生成する例については、「[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)」を参照してください。

## <a name="see-also"></a>参照

[並列コンテナーと並列オブジェクト](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable クラス](../../parallel/concrt/reference/combinable-class.md)<br/>
[critical_section クラス](../../parallel/concrt/reference/critical-section-class.md)
