---
title: '方法: データ パイプラインでトランスフォーマーを使用する'
ms.date: 11/04/2016
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
ms.openlocfilehash: c8cf1801d0262e3a2995d520604374ea22352fa0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141895"
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>方法: データ パイプラインでトランスフォーマーを使用する

このトピックには、データパイプラインで[concurrency:: トランスフォーマー](../../parallel/concrt/reference/transformer-class.md)クラスを使用する方法を示す基本的な例が含まれています。 データパイプラインを使用してイメージ処理を実行する詳細な例については、「[チュートリアル: イメージ処理ネットワークの作成](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)」を参照してください。

*データのパイプライン*処理は、同時実行プログラミングにおける一般的なパターンです。 データ パイプラインは一連のステージで構成され、各ステージで処理を実行し、その処理の結果を次のステージに渡します。 `transformer` クラスは、入力値を受け取り、その値に対して処理を実行し、別のコンポーネントで使用する結果を生成するため、データ パイプラインにおいて重要なコンポーネントとなっています。

## <a name="example"></a>例

この例では、次のデータ パイプラインを使用して、渡される初期入力値に対して一連の変換を実行します。

1. 最初のステージは、入力の絶対値を計算します。

1. 2 番目のステージは、入力の平方根を計算します。

1. 3 番目のステージは、入力の 2 乗を計算します。

1. 4 番目のステージは、入力の符号を反転します。

1. 5 番目のステージは、最終的な結果をメッセージ バッファーに書き込みます。

最後に、この例はパイプラインの結果をコンソールに出力します。

[!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]

この例の結果は、次のようになります。

```Output
The result is -42.
```

一般に、データ パイプラインのステージは、入力値と異なる種類の値を出力します。 この例では、2 番目のステージは入力として `int` 型の値を取得し、出力としてその値の平方根 (`double` 型) を生成します。

> [!NOTE]
> この例のデータ パイプラインは、例示のみを目的としています。 各変換操作での処理量が少ないため、メッセージ パッシングを実行するのに必要なオーバーヘッドがデータ パイプラインを使用するメリットを上回る場合があります。

## <a name="compiling-the-code"></a>コードのコンパイル

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`data-pipeline.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

> **cl.exe/EHsc data-pipeline**

## <a name="see-also"></a>参照

[非同期エージェント ライブラリ](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同期メッセージ ブロック](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[チュートリアル: イメージ処理ネットワークの作成](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)
