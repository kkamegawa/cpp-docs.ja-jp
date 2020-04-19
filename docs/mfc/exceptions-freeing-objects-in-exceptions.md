---
title: 例外:例外オブジェクトの解放
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
ms.openlocfilehash: 23fe85018d1bc2c41371afec2ad6931755e4e682
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406068"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>例外:例外オブジェクトの解放

この記事では、必要性と例外が発生したときに、オブジェクトを解放する方法について説明します。 ここでは、次の内容について説明します。

- [ローカルでの例外を処理します。](#_core_handling_the_exception_locally)

- [オブジェクトの破棄後に例外のスロー](#_core_throwing_exceptions_after_destroying_objects)

または、アプリケーションの割り込みの通常のプログラム フローで、フレームワークによってスローされる例外。 そのため、例外がスローされた場合に適切に破棄することができますようにオブジェクトを追跡管理を維持する非常に重要ですが。

これを行う 2 つの主な方法があります。

- **try** と **catch** キーワードを使用してローカル例外を処理し、1 つのステートメントを使用してすべてのオブジェクトを破棄します。

- さらに処理するため、ブロックの外側の例外をスローする前に、**catch** ブロック内の任意のオブジェクトを破棄します。

これら 2 つの方法は、問題のある例を次の解決策として次に示します。

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

上記のとおり`myPerson`によって例外がスローされた場合は削除されません`SomeFunc`します。 実行は、通常の関数が終了し、オブジェクトを削除するコードをバイパスして、[次へ] の外側の例外ハンドラーに直接ジャンプします。 オブジェクトへのポインターはスコープから外れる、例外が、関数を離れるし、プログラムが実行されている限り、オブジェクトに占有されたメモリは復旧されません。 これは、メモリ リークが発生します。これについては、メモリ診断を使用して検出します。

##  <a name="_core_handling_the_exception_locally"></a> ローカルでの例外を処理します。

**try/catch** パラダイムのメモリ リークを回避して、例外が発生したときに、オブジェクトが確実に破棄されるように防御的なプログラミング方法を提供します。 たとえば、この記事の前半で示した例は次のように書き換えることができます。

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

この新しい例は、例外をキャッチし、それをローカルで処理するための例外ハンドラーを設定します。 関数が正常終了し、オブジェクトを破棄します。 この例の重要な側面は、例外をキャッチするコンテキストが **try/catch** ブロック確立されていることです。 ローカル例外フレームがなければ、関数は例外がスローされたことがわからなくなり、通常どおりに終了してオブジェクトを破棄することはありません。

##  <a name="_core_throwing_exceptions_after_destroying_objects"></a> オブジェクトの破棄後に例外のスロー

例外を処理する別の方法では、[次へ] の外側の例外処理コンテキストに渡すことです。 **キャッチ**ブロックをローカルで割り当てられたオブジェクトのクリーンアップ処理を実行でき、さらに処理するため例外をスローします。

スロー関数は可能性があります。 またはヒープのオブジェクトの割り当てを解除する必要はありません。 場合は、関数が、通常の場合に返す前に常にヒープのオブジェクトの割り当てを解除し、関数は、する必要がありますも割り当てを解除ヒープ オブジェクト、例外をスローする前に。 その一方で、関数では、オブジェクトは通常は、通常の場合に返す前に解放されない場合する必要がありますで個別にヒープのオブジェクトの割り当てを解除するかどうか。

次の例はローカルでどのように割り当てられているオブジェクトをクリーンアップできます。

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

例外処理機構フレーム オブジェクトを自動的に割り当て解除します。フレーム オブジェクトのデストラクターが呼び出されます。

例外をスローする関数を呼び出す場合 **try/catch**ブロックを使用して、例外をキャッチして、作成した任意のオブジェクトを破棄する可能性があります。 具体的には、MFC 関数の多くが例外をスローすることもあります。

詳細については、[例外: キャッチと削除例外](../mfc/exceptions-catching-and-deleting-exceptions.md) を参照してください。

## <a name="see-also"></a>関連項目

[例外処理](../mfc/exception-handling-in-mfc.md)
