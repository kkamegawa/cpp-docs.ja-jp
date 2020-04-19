---
title: '方法: 減少変数を使用する OpenMP ループを変換し、コンカレンシー ランタイムを使用する'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: ee0a600f4234c3ebf4681ad92b5e3623be5665c3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141260"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>方法: 減少変数を使用する OpenMP ループを変換し、コンカレンシー ランタイムを使用する

この例では、[リダクション](../../parallel/openmp/reference/reduction.md)句を使用する OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../../parallel/openmp/reference/for-openmp.md)ループを変換して、同時実行ランタイムを使用する方法を示します。

OpenMP `reduction` 句を使用すると、並列領域の最後にあるリダクション演算の対象となる 1 つ以上のスレッド プライベート変数を指定できます。 OpenMP には、リダクション演算子のセットがあらかじめ定義されています。 各リダクション変数はスカラー (`int`、`long`、`float` など) にする必要があります。 OpenMP には、並列領域でのリダクション変数の使用方法に関する制限事項もいくつか定義されています。

並列パターンライブラリ (PPL) は、 [concurrency:: の組み合わせ](../../parallel/concrt/reference/combinable-class.md)可能なクラスを提供します。これにより、きめ細かな計算を実行し、その計算を最終結果にマージできます。 `combinable` クラスは、スカラー型と複合型の両方に作用するテンプレートです。 `combinable` クラスを使用するには、parallel コンストラクトの本体でサブ計算を実行し、 [concurrency::](reference/combinable-class.md#combine)組み合わせ可能:: 組み合わせまたは[concurrency:: 組み合わせ可能:: combine_each](reference/combinable-class.md#combine_each)メソッドを呼び出して最終的な結果を生成します。 `combine` メソッドと `combine_each` メソッドはそれぞれ、要素の各ペアを結合する方法を指定する*結合関数*を受け取ります。 したがって、`combinable` クラスは、リダクション演算子の固定セットだけに制限されません。

## <a name="example"></a>例

この例では、OpenMP とコンカレンシー ランタイムの両方を使用して、最初の 35 個のフィボナッチ数の合計を計算します。

[!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]

この例を実行すると、次の出力が生成されます。

```Output
Using OpenMP...
The sum of the first 35 Fibonacci numbers is 14930351.
Using the Concurrency Runtime...
The sum of the first 35 Fibonacci numbers is 14930351.
```

`combinable` クラスの詳細については、「[並列コンテナーとオブジェクト](../../parallel/concrt/parallel-containers-and-objects.md)」を参照してください。

## <a name="compiling-the-code"></a>コードのコンパイル

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`concrt-omp-fibonacci-reduction.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

> **cl.exe/EHsc/openmp concrt-omp-fibonacci-reduction**

## <a name="see-also"></a>参照

[OpenMP からコンカレンシー ランタイムへの移行](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[並列コンテナーと並列オブジェクト](../../parallel/concrt/parallel-containers-and-objects.md)
