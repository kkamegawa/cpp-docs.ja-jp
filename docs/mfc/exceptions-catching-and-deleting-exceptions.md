---
title: '例外処理 : 例外のキャッチと削除'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
ms.openlocfilehash: 0142ffddfb391ae8da878d9e5fe34629cf16cb52
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246692"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>例外処理 : 例外のキャッチと削除

次の手順と例は、例外をキャッチおよび削除する方法を示しています。 **Try**、 **catch**、および**throw**キーワードの詳細については、 [「 C++例外とエラー処理のための最新のベストプラクティス](../cpp/errors-and-exception-handling-modern-cpp.md)」を参照してください。

例外ハンドラーは、処理する例外オブジェクトを削除する必要があります。そのため、例外を削除しても、そのコードが例外をキャッチするたびにメモリリークが発生します。

**Catch**ブロックでは、次の場合に例外を削除する必要があります。

- **Catch**ブロックは、新しい例外をスローします。

   もちろん、同じ例外を再度スローする場合は、例外を削除しないでください。

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- 実行は、 **catch**ブロック内から返されます。

> [!NOTE]
>  `CException`を削除する場合は、`Delete` メンバー関数を使用して例外を削除します。 例外がヒープにない場合には失敗する可能性があるため、 **delete**キーワードは使用しないでください。

#### <a name="to-catch-and-delete-exceptions"></a>例外をキャッチおよび削除するには

1. **Try ブロックを**設定するには、 **try**キーワードを使用します。 **Try**ブロック内で例外をスローする可能性のあるプログラムステートメントを実行します。

   **Catch キーワードを**使用して、 **catch**ブロックを設定します。 例外処理コードを**catch**ブロックに配置します。 **Catch**ブロック内のコードは、 **catch**ステートメントで指定された型の例外を**スローする場合**にのみ実行されます。

   次のスケルトンは、通常、 **try**ブロックと**catch**ブロックがどのように配置されるかを示しています。

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   例外がスローされると、コントロールは、例外宣言が例外の型と一致する最初の**catch**ブロックに渡されます。 次に示すように、シーケンシャルな**catch**ブロックでは、さまざまな種類の例外を選択して処理できます。

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

詳細については、「[例外: MFC 例外マクロからの変換](../mfc/exceptions-converting-from-mfc-exception-macros.md)」を参照してください。

## <a name="see-also"></a>参照

[例外処理](../mfc/exception-handling-in-mfc.md)
