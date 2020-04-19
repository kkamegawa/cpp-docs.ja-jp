---
title: 例外:例外の内容の調査
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
ms.openlocfilehash: f6f9bca6f6b7ca9d104cb492c760ab89f7163afd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406003"
---
# <a name="exceptions-examining-exception-contents"></a>例外:例外の内容の調査

ただし、**catch**ブロックの引数は、ほぼすべてのデータ型であることができます、MFC 関数がクラスから派生した型の例外をスロー`CException`します。 MFC 関数によってスローされる例外をキャッチし、記述する、**catch**ブロックの引数がポインターを`CException`オブジェクト (から派生したオブジェクトまたは`CException`など`CMemoryException`)。 例外の正確な型、に応じて例外の原因を特定の情報を収集する例外オブジェクトのデータ メンバーを調べることができます。

たとえば、`CFileException`型には、`m_cause`データ メンバーは、ファイルの例外の原因を示す列挙型が含まれています。 考えられる例をいくつかの戻り値は`CFileException::fileNotFound`と`CFileException::readOnly`します。

次の例の内容を確認する方法を示しています、`CFileException`します。 同様に、その他の例外の種類を検証できます。

[!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]

詳細については、「[例外: 例外オブジェクトの解放](../mfc/exceptions-freeing-objects-in-exceptions.md)」と「[例外: キャッチと削除例外](../mfc/exceptions-catching-and-deleting-exceptions.md)」を参照してください。

## <a name="see-also"></a>関連項目

[例外処理](../mfc/exception-handling-in-mfc.md)
