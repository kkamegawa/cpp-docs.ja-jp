---
title: '方法: call クラスおよび transformer クラスに処理関数を提供する'
ms.date: 11/04/2016
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
ms.openlocfilehash: 4d2b7b3c88b51003a96526ef14d9940a8c26c3b3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142487"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>方法: call クラスおよび transformer クラスに処理関数を提供する

このトピックでは、 [concurrency:: call](../../parallel/concrt/reference/call-class.md)クラスおよび[concurrency:: トランスフォーマー](../../parallel/concrt/reference/transformer-class.md)クラスに処理関数を提供するいくつかの方法について説明します。

最初の例では、ラムダ式を `call` オブジェクトに渡す方法を示します。 2 番目の例では、関数オブジェクトを `call` オブジェクトに渡す方法を示します。 3 番目の例では、クラス メソッドを `call` オブジェクトにバインドする方法を示します。

このトピックの説明では、すべての例で `call` クラスを使用します。 `transformer` クラスを使用する例については、「[方法: データパイプラインでトランスフォーマーを使用](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)する」を参照してください。

## <a name="example"></a>例

次の例は、`call` クラスを使用する一般的な方法を示しています。 この例は、ラムダ関数を `call` コンストラクターに渡します。

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

この例を実行すると、次の出力が生成されます。

```Output
13 squared is 169.
```

## <a name="example"></a>例

次の例は前の例に似ていますが、関数オブジェクト (ファンクタ) と共に `call` クラスを使用する点が異なります。

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example"></a>例

次の例は前の例と似ていますが、 [std:: bind1st](../../standard-library/functional-functions.md#bind1st)関数と[std:: mem_fun](../../standard-library/functional-functions.md#mem_fun)関数を使用して `call` オブジェクトをクラスメソッドにバインドする点が異なります。

この方法は、関数呼び出し演算子 `call` ではなく、特定のクラス メソッドに `transformer` オブジェクトまたは `operator()` オブジェクトをバインドする必要がある場合に使用します。

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

次の例に示すように、`bind1st` 関数の結果を[std:: function](../../standard-library/function-class.md)オブジェクトに割り当てるか、`auto` キーワードを使用することもできます。

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>コードのコンパイル

コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`call.cpp` という名前のファイルに貼り付けてから、Visual Studio のコマンドプロンプトウィンドウで次のコマンドを実行します。

> **cl.exe/EHsc 呼び出し .cpp**

## <a name="see-also"></a>参照

[非同期エージェント ライブラリ](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同期メッセージ ブロック](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[方法: データ パイプラインでトランスフォーマーを使用する](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[call クラス](../../parallel/concrt/reference/call-class.md)<br/>
[transformer クラス](../../parallel/concrt/reference/transformer-class.md)
