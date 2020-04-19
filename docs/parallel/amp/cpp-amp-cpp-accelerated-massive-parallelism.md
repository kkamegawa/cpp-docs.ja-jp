---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: 3dbd7d646b455ac57833d28b18602b533c8388e6
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450350"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++ AMP (C++ Accelerated Massive Parallelism) は、独立したグラフィックス カードの GPU (graphics processing unit) などの一般的なデータ並列ハードウェアを活用して、C++ コードの実行を高速化します。 C++ AMP のプログラミング モデルには、多次元配列、インデックス作成、メモリ転送、およびタイルのサポートが含まれています。 また、数学関数ライブラリも含まれています。 C++ AMP の言語拡張機能を使用して、データを CPU から GPU へ、また GPU から CPU へどのように移動するかを制御できます。

## <a name="related-topics"></a>関連トピック

|タイトル|説明|
|-----------|-----------------|
|[C++ AMP の概要](../../parallel/amp/cpp-amp-overview.md)|C++ AMP および数値演算ライブラリの主な機能について説明します。|
|[ラムダ、関数オブジェクト、および制限関数の使用](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|呼び出しでラムダ式、関数オブジェクト、および制限関数を使用する方法について説明します、 [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)メソッド。|
|[タイルの使用](../../parallel/amp/using-tiles.md)|タイルを使用して C++ AMP コードを高速化する方法について説明します。|
|[アクセラレータおよび accelerator_view オブジェクトの使用](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|アクセラレータを使用して GPU でのコードの実行をカスタマイズする方法について説明します。|
|[UWP アプリでの C++ AMP の使用](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Windows ランタイム型を使用するユニバーサル Windows プラットフォーム (UWP) アプリで C++ AMP を使用する方法について説明します。|
|[グラフィックス (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|C++ AMP のグラフィックス ライブラリを使用する方法について説明します。|
|[チュートリアル: 行列乗算](../../parallel/amp/walkthrough-matrix-multiplication.md)|C++ AMP コードとタイルを使用した行列乗算を示します。|
|[チュートリアル: C++ AMP アプリケーションのデバッグ](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|並列リダクションを使用して整数の大きな配列を合計するアプリケーションを作成してデバッグする方法について説明します。|

## <a name="reference"></a>参照

[リファレンス (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static キーワード](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>その他の参照情報

[ネイティブ コードのブログでの並列プログラミング](https://go.microsoft.com/fwlink/p/?linkid=238472)<br/>
[ダウンロードの C++ AMP サンプル プロジェクト](https://go.microsoft.com/fwlink/p/?linkid=248508)<br/>
[同時実行ビジュアライザーで C++ AMP コードの分析](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)