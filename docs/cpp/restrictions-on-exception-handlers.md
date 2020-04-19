---
title: 例外ハンドラーに対する制限
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 030d444443b3a6e3e2e0ac0e015619046a76d562
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245158"
---
# <a name="restrictions-on-exception-handlers"></a>例外ハンドラーに対する制限

コードで例外ハンドラーを使用する場合の主な制限事項は、 **goto**ステートメントを使用して **__try**ステートメントブロックに移動できないことです。 代わりに、制御の標準フローに従ってステートメント ブロックに入る必要があります。 **__Try**ステートメントブロックから移動し、選択したとおりに例外ハンドラーを入れ子にすることができます。

## <a name="see-also"></a>参照

[例外ハンドラーの記述](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
