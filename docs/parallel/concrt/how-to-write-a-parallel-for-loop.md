---
title: '方法: parallel_for ループを記述する'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
ms.openlocfilehash: 5903114a12de46dc06929c83e9995b39d0136810
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141859"
---
# <a name="how-to-write-a-parallel_for-loop"></a>方法: parallel_for ループを記述する

この例では、 [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)を使用して2つの行列の積を計算する方法を示します。

## <a name="example"></a>例

2 つの正方行列の積を計算する `matrix_multiply` 関数を次の例に示します。

[!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]

## <a name="example"></a>例

`parallel_matrix_multiply` アルゴリズムを使用して外側のループを並列実行する `parallel_for` 関数を次の例に示します。

[!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]

この例では外側のループを並列化していますが、これは、外側のループでは多くの処理が行われるので、並列処理のオーバーヘッドを削減する効果があるためです。 内側のループを並列化した場合は、パフォーマンス上の利点はあまりありません。これは、内側のループではあまり多くの処理が行われないので、並列処理のオーバーヘッドを抑えることができないためです。 このため、大部分のシステムでは、外側のループだけをコンカレンシーすることで、最大限の効果を得ることができると言えます。

## <a name="example"></a>例

`matrix_multiply` 関数と `parallel_matrix_multiply` 関数のパフォーマンスを比較するコード例全体を次に示します。

[!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]

4 つのプロセッサを備えたコンピューターを使用したときのサンプル出力を次に示します。

```Output
serial: 3853
parallel: 1311
```

## <a name="compiling-the-code"></a>コードのコンパイル

コードをコンパイルするには、コードをコピーし、Visual Studio プロジェクトに貼り付けるか、`parallel-matrix-multiply.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

> **cl.exe/EHsc parallel-matrix-multiply**

## <a name="see-also"></a>参照

[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for 関数](reference/concurrency-namespace-functions.md#parallel_for)
