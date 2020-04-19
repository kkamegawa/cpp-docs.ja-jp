---
title: 終了ハンドラーの記述
ms.date: 11/04/2016
helpviewer_keywords:
- structured exception handling [C++], termination handlers
- exceptions [C++], terminating
- termination handlers [C++], writing
- handlers [C++]
- handlers [C++], termination
- termination handlers
- exception handling [C++], termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
ms.openlocfilehash: f0b994075a8d59ce5d0955f10bf8c61d357d2db9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209469"
---
# <a name="writing-a-termination-handler"></a>終了ハンドラーの記述

例外ハンドラーとは異なり、終了ハンドラーは、コードの保護されたブロックが正常に終了したかどうかに関係なく、常に実行されます。 終了ハンドラーの唯一の目的は、コードのセクションの実行がどのように終了したかに関係なく、メモリ、ハンドル、ファイルなどのリソースが適切に閉じられるようにすることです。

終了ハンドラーは、try-finally ステートメントを使用します。

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [Try-finally ステートメント](../cpp/try-finally-statement.md)

- [リソースをクリーンアップします。](../cpp/cleaning-up-resources.md)

- [例外の処理アクションのタイミング](../cpp/timing-of-exception-handling-a-summary.md)

- [終了ハンドラーに関する制約](../cpp/restrictions-on-termination-handlers.md)

## <a name="see-also"></a>関連項目

[構造化例外処理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)