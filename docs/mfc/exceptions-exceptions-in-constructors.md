---
title: 例外:コンス トラクターで例外
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 0b11f5be18879d5ad4b9e204bb02e18b4617c6b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405873"
---
# <a name="exceptions-exceptions-in-constructors"></a>例外:コンス トラクターで例外

コンス トラクターで例外をスローするときにで説明したように、例外をスローする前に行われたが任意のオブジェクトとメモリの割り当てをクリーンアップ[例外。独自の関数から例外をスロー](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)します。

コンス トラクターで例外をスローするときに、コンス トラクターが呼び出された時点で、オブジェクト自体のメモリが既に割り当てられました。 そのため、コンパイラは自動的に例外がスローされた後に、オブジェクトによって占有されているメモリを解放します。

詳細については、次を参照してください。[例外。例外オブジェクトの解放](../mfc/exceptions-freeing-objects-in-exceptions.md)します。

## <a name="see-also"></a>関連項目

[例外処理](../mfc/exception-handling-in-mfc.md)
