---
title: 'チュートリアル: フューチャの実装'
ms.date: 04/25/2019
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: 2b9d889dac195bb60651cbb76110d54b6231a5fd
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141981"
---
# <a name="walkthrough-implementing-futures"></a>チュートリアル: フューチャの実装

このトピックでは、アプリケーションにフューチャを実装する方法について説明します。 このトピックでは、コンカレンシー ランタイムの既存の機能を組み合わせて、より効果的に使用する方法を示します。

> [!IMPORTANT]
> このトピックでは、デモンストレーションのために、将来の概念について説明します。 後で使用するために値を計算する非同期タスクが必要な場合は、 [std:: future](../../standard-library/future-class.md)または[concurrency:: task](../../parallel/concrt/reference/task-class.md)を使用することをお勧めします。

*タスク*とは、さらにきめ細かな計算に分解できる計算のことです。 *フューチャ*は、後で使用できるように値を計算する非同期タスクです。

フューチャを実装するために、このトピックでは `async_future` クラスを定義します。 `async_future` クラスは、 [concurrency:: task_group](reference/task-group-class.md)クラスおよび[concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md)クラス同時実行ランタイムのこれらのコンポーネントを使用します。 `async_future` クラスは、`task_group` クラスを使用して非同期的に値を計算し、`single_assignment` クラスを使用して計算結果を格納します。 `async_future` クラスのコンストラクターは、結果を計算する処理関数を受け取り、`get` メソッドが結果を取得します。

### <a name="to-implement-the-async_future-class"></a>async_future クラスを実装するには

1. 計算結果の型でパラメーター化された `async_future` という名前のテンプレート クラスを宣言します。 このクラスに `public` セクションと `private` セクションを追加します。

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. `private` クラスの `async_future` セクションで、`task_group` と `single_assignment` データ メンバーを宣言します。

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. `public` クラスの `async_future` セクションで、コンストラクターを実装します。 コンストラクターは、結果を計算する処理関数でパラメーター化されたテンプレートです。 コンストラクターは、`task_group` データメンバー内の処理関数を非同期に実行し、 [concurrency:: send](reference/concurrency-namespace-functions.md#send)関数を使用して結果を `single_assignment` データメンバーに書き込みます。

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. `public` クラスの `async_future` セクションで、デストラクターを実装します。 デストラクターはタスクが完了するまで待機します。

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. `public` クラスの `async_future` セクションで、`get` メソッドを実装します。 このメソッドは、 [concurrency:: receive](reference/concurrency-namespace-functions.md#receive)関数を使用して、作業関数の結果を取得します。

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>例

### <a name="description"></a>説明

完全な `async_future` クラスとその使用例を次に示します。 `wmain` 関数は、1万のランダムな整数値を格納する std::[vector](../../standard-library/vector-class.md)オブジェクトを作成します。 次に `async_future` オブジェクトを使用して、`vector` オブジェクト内の最小値と最大値を見つけます。

### <a name="code"></a>コード

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>コメント

この例の結果は、次のようになります。

```Output
smallest: 0
largest:  9999
average:  4981
```

この例では `async_future::get` メソッドを使用して、計算の結果を取得しています。 `async_future::get` メソッドは、計算がアクティブな場合は、計算が完了するまで待機します。

## <a name="robust-programming"></a>堅牢性の高いプログラミング

`async_future` クラスを拡張して、処理関数によってスローされた例外を処理するには、 [concurrency:: task_group:: wait](reference/task-group-class.md#wait)メソッドを呼び出すように `async_future::get` メソッドを変更します。 `task_group::wait` メソッドは、処理関数によって生成されたすべての例外をスローします。

`async_future` クラスを変更した例を次に示します。 `wmain` 関数は、`try`-`catch` ブロックを使用して、`async_future` オブジェクトの結果を出力します。または、処理関数によって生成される例外の値を出力します。

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

この例の結果は、次のようになります。

```Output
caught exception: error
```

同時実行ランタイムにおける例外処理モデルの詳細については、「[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)」を参照してください。

## <a name="compiling-the-code"></a>コードのコンパイル

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`futures.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

**cl.exe/EHsc。 .cpp**

## <a name="see-also"></a>参照

[コンカレンシー ランタイムのチュートリアル](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[例外処理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[task_group クラス](reference/task-group-class.md)<br/>
[single_assignment クラス](../../parallel/concrt/reference/single-assignment-class.md)
