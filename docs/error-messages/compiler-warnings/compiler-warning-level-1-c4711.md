---
title: コンパイラの警告 (レベル 1) C4711
ms.date: 11/04/2016
f1_keywords:
- C4711
helpviewer_keywords:
- C4711
ms.assetid: 270506ab-fead-4328-b714-2978113be238
ms.openlocfilehash: c10b19b39fcb40527c9e9276f47ecff42ca5a643
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280387"
---
# <a name="compiler-warning-level-1-c4711"></a>コンパイラの警告 (レベル 1) C4711

関数 'function' がインライン展開の選択

コンパイラは実行のマークされていますが、指定された関数のインライン展開インライン化します。

場合に、C4711 が有効になっている[/Ob2](../../build/reference/ob-inline-function-expansion.md)を指定します。

インライン展開は、コンパイラの裁量で実行されます。 これは、情報提供の警告です。

既定では、この警告はオフに設定されています。 警告を有効にするには、 [#pragma warning](../../preprocessor/warning.md)します。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。