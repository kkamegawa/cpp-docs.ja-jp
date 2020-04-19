---
title: コンパイラの警告 C4577
description: コンパイラの警告 C4577 の説明と解決策。
ms.date: 09/18/2019
f1_keywords:
- C4577
helpviewer_keywords:
- C4577
ms.openlocfilehash: e29e47b2a268d86f7f6a280b79a1604fe6eff8a4
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810562"
---
# <a name="compiler-warning-level-1-c4577"></a>コンパイラの警告 (レベル 1) C4577

> 例外処理モードが指定されていない ' noexcept ' が使用されています。例外での終了は保証されていません。 /EHsc を指定する

コンパイラは `noexcept` 仕様を検出しましたC++が、標準の例外処理が指定されていませんでした。 [/Ehsc](../../build/reference/eh-exception-handling-model.md) コンパイラオプションが指定されていないC++場合、コンパイラは標準に従って例外処理を完全にサポートしません。 この問題を解決するには、 **/ehsc**コンパイラオプションを設定します。

この警告は Visual Studio 2015 で新しく追加されたものであり、既定ではオフになっています。 詳細については、「[既定でオフになっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)」を参照してください。
