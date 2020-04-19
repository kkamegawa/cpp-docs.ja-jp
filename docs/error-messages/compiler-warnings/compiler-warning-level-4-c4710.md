---
title: コンパイラの警告 (レベル 4) C4710
ms.date: 11/04/2016
f1_keywords:
- C4710
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
ms.openlocfilehash: 0f8e66982192f8af6498c9151d32a44226e0560a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395197"
---
# <a name="compiler-warning-level-4-c4710"></a>コンパイラの警告 (レベル 4) C4710

'function': 関数のインライン化できません

指定された関数がインライン展開の選択されたが、コンパイラが実行されなかった、インライン化します。

インライン展開は、コンパイラの裁量で実行されます。 **インライン**キーワードと同様に、**登録**キーワードがコンパイラにヒントとして使用します。 コンパイラでは、ヒューリスティックを使用して、速度、コンパイルするときに、コードを高速化する特定の関数をインラインにする必要がありますか場合は領域をコンパイルするときに、コードを小さく特定の関数をインラインにする必要がありますかを判断します。 コンパイラでは、領域をコンパイルするときに、だけがインライン展開が非常に小規模関数には。

場合によっては、コンパイラはインラインではなく、特定の関数の機械的な理由からします。 参照してください[C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)に対して一連の上の理由から、コンパイラがインライン関数ではない可能性があります。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。